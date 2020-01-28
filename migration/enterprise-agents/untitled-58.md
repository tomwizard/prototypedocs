# Enterprise Agent on Docker Advanced Networking

The default Enterprise Agent installation on Docker uses NAT to connect the agent to the network using the host's IP address. A NATted connection gives the enterprise agent sufficient connectivity to the host's network for all measurements, however, advanced users may desire different types of network connectivity between the enterprise agent container and their network.

## NAT

IMAGE MISSING

The default installation connects the agent to host's internal _docker0_ bridge. docker0 bridge is not bridged with any of the external interfaces, i.e. _eth0_. NAT is performed between docker0 bridge \(inside\) and host's default external interface, i.e. _eth0_ \(outside\).

No further configuration is required to run the enterprise agent container in NAT mode.

### Host with multiple physical interfaces

IMAGE MISSING

What happens if we have a host with multiple physical interfaces, for instance _eth0_ and _wlan0_? Default NAT configuration does not favor any of the interfaces, instead it relies on Kernel IP routing to choose the exit interface. You can verify default exit interface by looking for the default route in the Kernel IP routing table:

> \# route  
> Kernel IP routing table  
> Destination  Gateway     Genmask        Flags  Metric  Ref  Use  Iface  
> **default      10.10.40.1  0.0.0.0        UG     0       0    0    eth0**  
> 10.10.40.0   \*           255.255.255.0  U      0       0    0    eth0  
> 10.10.50.0   \*           255.255.255.0  U      0       0    0    wlan0  
> 172.17.0.0   \*           255.255.0.0    U      0       0    0    docker0

What happens if you want the enterprise agent to use the Wireless connection, i.e. _wlan0_ interface instead of _eth0_? You could change the default route to _wlan0_, but this will redirect all traffic from the host server.

A better solution is to change the default route for enterprise agent container only. This can be done with policy routing, or more specifically **source policy routing**:

1. Create a custom policy routing table by adding routing table id \(pick a number that is not already taken, i.e. _200_\) and name \(i.e. _wlan0rt_\) in the _/etc/iproute2/rt\_tables_ file.

   > echo 200 wlan0rt &gt;&gt; /etc/iproute2/rt\_tables

2. Source policy routing routes traffic based on source address. Enterprise agent container may change it's internal IP address between host reboots with default installation and you cannot configure the agent with a static IP address when using default docker bridge. Verify which network is available on _docker0_ bridge:  
  

   > \# ifconfig  
   >  docker0 Link encap:Ethernet HWaddr 02:42:64:92:ee:32  
   >  inet addr:**172.17.0.1** Bcast:0.0.0.0 Mask:**255.255.0.0**  
   >  \[..\]

    Enterprise agent container will be attached to docker0 bridge by default so it must use an IP address from the bridge network. Write down the bridge network \(i.e. 172.17.0.0/16\)  
  

3. Create a policy routing rule that instructs Kernel IP routing to use the wlan0rt routing table for all the traffic coming from _docker0_ bridge network:

   > ip rule add from 172.17.0.0/16 lookup wlan0rt

4. Verify that the IP rule has been added:  
  

   > \# ip rule list  
   >  0: from all lookup local  
   >  **32765: from 172.17.0.0/16 lookup wlan0rt**  
   >  32766: from all lookup main  
   >  32767: from all lookup default

5. Last thing you need to do is add the actual rule that will route the traffic out the _wlan0_ interface in the _wlan0rt_ routing table:

   > ip route add default via 10.10.50.1 dev wlan0 table wlan0rt

  
    Note that part of the configuration is the default gateway for the network _wlan0_ interface is connected to \(i.e. 10.10.50.1\).

6. The _ip rule_ and _ip route_ commands are not persistent, they will be removed upon host reboot or interface state change. To make them persistent, open /etc/network/interfaces with your favorite editor:

   > vi /etc/network/interfaces

  
    Find the section of the interface that we route the traffic to \(i.e. _iface wlan0 inet_\) and add the _ip rule_ and _ip route_ commands inside the interface configuration block:  
  

   > iface wlan0 inet dhcp  
   >    **post-up** ip rule add from 172.17.0.0/16 lookup wlan0rt  
   >    **post-up** ip route add default via 10.10.50.1 dev wlan0 table wlan0rt

## Bridge

IMAGE MISSING

Bridged connectivity allows the enterprise agent to connect directly into user's network, using either private or public IP address. Starting with v1.12, Docker allows you to bridge the enterprise agent container with a host's physical interface using the **macvlan** network driver. If your Docker installation is v1.11.2 or older, you will have to use [pipework](https://github.com/jpetazzo/pipework) tool to bridge the enterprise agent container.

**Warning:** Some wireless NIC drivers or wireless collectors only support a single MAC address per physical wireless NIC. In that case bridge configuration will not work and you should use the NAT configuration.

### Bridging with macvlan \(docker &gt;= 1.12\)

1. First you need to create a new Docker Network using the macvlan network driver. Each macvlan network requires one _parent_ interface. Parent interface is a physical interface of the Docker Host to which the macvlan network will be bridged. You need to configure the subnet and the gateway of the network you are bridging into.

    **Warning:** Docker containers are assigned IP addresses from Docker's IPAM driver from the _subnet_ pool you configure for the network. Enterprise agent container cannot request the IP from the external DHCP server. To avoid IP address collision, you should avoid bridging the Docker macvlan network to an existent physical network with DHCP service.

   > docker network create -d macvlan \  
   >  --subnet=10.10.40.0/24 --gateway=10.10.40.1 \  
   >  -o parent=eth0 \  
   >  macvlan0

2. Ensure that network was created:

   > \# docker network ls
   >
   > NETWORK ID    NAME      DRIVER  
   >  **0f4311081482  macvlan0  macvlan**

3. When utilizing the **docker run** command upon enterprise agent installation, make sure you add the _--net=macvlan0_ parameter before the last line. This will connect the enterprise agent container to the macvlan network you have just created.

   > **--net=macvlan0 \**  
   >  thousandeyes/enterprise-agent /sbin/my\_init

4. Verify enterprise agent connectivity. Container should be able to ping the default gateway you have configured upon macvlan0 network creation:

   > \# docker exec -ti _&lt;agent-container-name&gt;_ ping -c 4 10.10.40.1
   >
   > PING 10.10.40.1 \(10.10.40.1\) 56\(84\) bytes of data.  
   >  64 bytes from 10.10.40.1: icmp\_seq=1 ttl=64 time=0.254 ms  
   >  64 bytes from 10.10.40.1: icmp\_seq=2 ttl=64 time=0.223 ms  
   >  64 bytes from 10.10.40.1: icmp\_seq=3 ttl=64 time=0.237 ms  
   >  64 bytes from 10.10.40.1: icmp\_seq=4 ttl=64 time=0.228 ms
   >
   > --- 10.10.40.1 ping statistics ---  
   >  4 packets transmitted, 4 received, 0% packet loss, time 2997ms  
   >  rtt min/avg/max/mdev = 0.223/0.235/0.254/0.019 ms

### Bridging with pipework \(docker &lt;= 1.11.2\)

1. When utilizing the **docker run** command upon enterprise agent installation, make sure you add the --net=none parameter before be last line. This will disable the default NAT network setting.  
  

   > **--net=none \**  
   >  thousandeyes/enterprise-agent /sbin/my\_init

2. Ensure that the container is running:

   > \# docker ps  
   >  CONTAINER ID IMAGE                         COMMAND         CREATED       STATUS       NAMES  
   >  09cdc2734260 thousandeyes/enterprise-agent "/sbin/my\_init" 1 minutes ago **Up 1 minutes** &lt;agent-name&gt;

3. Get the pipework and make it executable:

   > wget https://raw.githubusercontent.com/jpetazzo/pipework/master/pipework
   >
   >  chmod a+x pipework

4. Copy it to a permanent location on your host, that is already included in PATH, i.e. /usr/local/sbin/:

   > cp pipework /usr/local/sbin/

5. Use pipework to bridge the running container with the physical interface on your host, i.e eth0.

    a. If the network your host is connected to has DHCP server, you can configure the agent to get the IP address and network settings using DHCP:

   > pipework eth0 &lt;agent-name&gt; dhclient

  
    b. Or, you can configure agent's IP address manually

   > pipework eth0 &lt;agent-name&gt; &lt;ip-address&gt;/&lt;subnet-mask&gt;@&lt;gateway-ip&gt;

    i.e.:

   > pipework eth0 &lt;agent-name&gt; 10.0.0.200/24@10.0.0.1

6. Connect to the enterprise agent container and verify network settings/connectivity.
7. Pipework configuration is not persistent, it will be removed upon container or host reboot. To ensure it will be reapplies after host reboot, add it to the /etc/rc.local file. Open /etc/rc.local with your favorite text editor:

   > vi /etc/rc.local

    and add the pipework command before the final exit 0 line

8. > pipework eth0 &lt;agent-name&gt; dhclientexit 0
9. Pipework configuration also needs to be reapplied if the physical interface is altered, so make sure that happens. Open /etc/network/interfaces with your favorite editor:
10. > vi /etc/network/interfaces

  
     Find the section of the interface that we route the traffic to \(i.e. _iface eth0 inet_\) and add the _ip rule_ and _ip route_ commands inside the interface configuration block to be executed once the interface is up:  
  

    > iface eth0 inet dhcp  
    >    **post-up pipework eth0 &lt;agent-name&gt; dhclient**

11. Last, but not least, pipework configuration also needs to be reapplied if you restart the agent container with _docker stop/docker start_ commands.

