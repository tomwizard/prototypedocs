# Running Enterprise Agent Virtual Appliance on RHEL 6 / CentOS 6 as KVM guest

[Red Hat Enterprise Linux](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux) 6 and its twin sister [CentOS](https://www.centos.org/) 6 are getting somewhat dated in terms of provided system software and libraries. [ThousandEyes Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC), especially the [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC) component \(required to perform [Page Load and Transaction tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn7KAC)\), strive to use up-to-date versions of [Chromium browser](https://www.chromium.org/) to perform their tasks. Getting a modern browser to run on these dated platforms is proving harder with each new release.

To pave a solid path forward in terms of future updates, it is strongly recommended to look towards Docker technology and deploy your Enterprise Agents as Docker containers - on systems that support it.

If migration to Docker is not possible, this guide describes a procedure to overcome the limitation of dated OS by not installing Enterprise Agent directly on the host, but rather deploying [ThousandEyes Virtual Appliance \(TEVA\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC) and running it as a virtual machine \(VM\) on a host using [KVM hypervisor](https://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine). KVM technology is natively supported by RHEL/CentOS 6 operating system. 

## Procedure Overview

In order to get TEVA working on a RHEL/CentOS 6, the following steps need to be performed:

1. Verify host hardware requirements
2. Install KVM hypervisor software and services
3. Configure networking
4. Download TEVA, convert to qcow2 disk format, import to KVM hypervisor, start it, configure it to start at boot
5. Connect to TEVA serial console and configure VM's network settings
6. Access TEVA web admin interface to finalize new Enterprise Agent configuration

## Step 1: Verify Host Hardware Requirements

For optimal VM performance, hardware-assisted virtualization feature of the processor needs to be enabled. You can check the status of the feature by using the following commands.

On Intel-based systems:

```text
cat /proc/cpuinfo | grep vmx
```

On AMD-based sysems:

```text
cat /proc/cpuinfo | grep svm
```

If one of the commands above produces an output, your host supports hardware-assisted virtualization.

Additional hardware requirements for ThousandEyes Virtual Appliance are:

* 2x vCPU,
* At least 2GB of available memory \(RAM\),
* 20GB of available disk space.

## Step 2: Install KVM Hypervisor Software and Services

If your host is Red Hat Enterprise Linux \(RHEL\), make sure it is registered to RHSM. If not, use the following commands to complete the registration \(skip the following two commands on CentOS\):

```text
subscription-manager register
subscription-manager subscribe —auto
```

  
Install the software packages required to run VMs on the host:

```text
yum install kvm libvirt python-virtinst qemu-kvm bridge-utils wget tar iptables chkconfig
```

  
Start the **"libvirtd"** service that manages the VMs \(produces "Starting libvirtd daemon: \[  OK  \]" output\):

```text
/etc/init.d/libvirtd start
```

  
Enable the service startup at boot \(no output is produced\):

```text
chkconfig libvirtd on
```

You can use the following command to verify the installation. If this is your first time using KVM virtualization on this host, the command should return an empty list. If VMs already exist on the host, you will see a list of those.

```text
virsh list --all
```

## Step 3: Configure networking

\(An alternative approach to network configuration is described in Addendum \#2 section of this article.\)

To connect the virtual machine to the rest of the world, an internal virtual network bridge will be created and new virtual machine will connect to it. The bridge will have an IP address configured, which will act as a gateway IP address for virtual machine. Port forwarding between interfaces will be enabled, to pass traffic between internal virtual bridge and physical interface. Virtual machine's IP address masquerading will also be enabled, in order for connections to appear as if they are coming from the host itself. Lastly, connections to TCP ports 4022 and 4080 on uplink interface will be forwarded to virtual machine to allow for HTTP \(web admin interface\) and SSH access to the VM.

Assumptions of this step:

* Host's uplink interface is called eth0.
* Host's internal virtual bridge IP address will be configured as 172.16.16.1/24.
* TEVA's IP address will be configured 172.16.16.2/24.

Create the bridge configuration:

```text
cat <<EOF > /etc/sysconfig/network-scripts/ifcfg-br-teva 
DEVICE="br-teva"
NM_CONTROLLED="no"
ONBOOT=yes
TYPE=Bridge
BOOTPROTO=static
IPADDR=172.16.16.1
PREFIX=24
DEFROUTE=no
NAME="ThousandEyes Network Bridge"
EOF
```

Activate the bridge:

```text
ifup br-teva
```

Enable port forwarding and firewall configuration at boot:

```text
cat <<EOF >> /etc/rc.local

# Enable traffic forwarding between interfaces
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerade outgoing connections
iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE

# Forward ports 4022 (SSH) and 4080 (HTTP) towards the Enterprise Agent
iptables -t nat -I PREROUTING  -i eth0 -p tcp --dport 4022 -j DNAT --to-destination 172.16.16.2:22 
iptables -t nat -I PREROUTING  -i eth0 -p tcp --dport 4080 -j DNAT --to-destination 172.16.16.2:80

# Allow traffic forwarding between br-teva internal bridge and eth0 uplink interface
iptables -I FORWARD     -i eth0 -o br-teva -j ACCEPT
iptables -I FORWARD     -o eth0 -i br-teva -j ACCEPT
EOF
```

Make /etc/rc.local executable:

```text
chmod a+x /etc/rc.local
```

Start the port forwarding and apply firewall configuration immediately:

```text
/etc/rc.local
```

## Step 4: Download and install Virtual Appliance

 Download:

```text
wget https://app.thousandeyes.com/install/downloads/appliance/thousandeyes-appliance.ova
```

Convert to qcow2 format, which is compatible with KVM:

```text
tar -xvf thousandeyes-appliance.ova
qemu-img convert -O qcow2 thousandeyes-va-64-14.04-disk1.vmdk thousandeyes-va-64-14.04-disk1.qcow2
```

Rename and move to appropriate location \(/var/lib/libvirt/images\):

```text
mv thousandeyes-va-64-14.04-disk1.qcow2 thousandeyes-va.qcow2
mv thousandeyes-va.qcow2 /var/lib/libvirt/images
```

Import the image as virtual machine in the libvirtd. VM will be called "thousandeyes-va":

```text
virt-install \
 -n thousandeyes-va \
 --description "My ThousandEyes Virtual Appliance" \
 --os-type=Linux \
 --os-variant=rhel6 \
 --ram=2048 \
 --vcpus=2 \
 --graphics vnc,listen=127.0.0.1 --noautoconsole \
 --network bridge:br-teva \
 --disk path=/var/lib/libvirt/images/thousandeyes-va.qcow2,format=qcow2,bus=ide --import
```

Configure the automatic start of the VM on boot:

```text
virsh autostart thousandeyes-va
```

## Step 5: Connect to TEVA serial console and configure VM's network settings

 Now it is time to configure VM's network interface. Usually this is performed by using VM console \(virtual keyboard input and video output\), as provided by the hypervisor. However, to make it simpler, TEVA has a serial console configured, to which you can connect using this simple command:

```text
virsh console thousandeyes-va
```

**NOTICE:** Initially your console may seems stuck and could look like this:

```text
[root@your-rhel-or-centos-6-host ~]# virsh console thousandeyes-va
Connected to domain thousandeyes-va
Escape character is ^]
```

 There might be two reasons for this:

* Console does not refresh automatically. Hitting "Enter" key will refresh the screen.
* The VM is not yet fully booted, therefore console is not enabled yet. The VM needs some time to fully boot before console appears, and initially it is waiting for non-existent DHCP server response, which adds up to the amount of time needed to see the console output. **Total time needed for console output to appear after startin up the VM ranges between 3 and 5 minutes.**

Once the VM is fully booted, after pressing "Enter", you should see a console output containing the following:

```text
ThousandEyes Virtual Appliance
...
Press N to begin the network configuration.
Press Enter to update this screen.
```

To configure the network, follow these steps \(values are quoted, but quotes must not be copied\):

1. Press **"n"** to enter network configuration wizard
2. Adjust hostname to your liking
3. Choose "**static"** network configuration \(select it using the "space" key\)
4. Ener IP address: **"172.16.16.2"**
5. Netmask: **"255.255.255.0"**
6. Broadcast: **"172.16.16.255"**
7. Gateway: **"172.16.16.1"**
8. IPv6 configuration: choose **"disable"**
9. Primary DNS: **"8.8.8.8"** - needs adjustment to your environment
10. Secondary DNS: **"8.8.4.4"** - needs adjustment to your environment
11. Confirm the configuration by selecting **"Yes"**.

**NOTICE:** Network reconfiguration process might get stuck at the following screen:

IMAGE MISSING

If this happens, it takes about 5 minutes for the process to continue. Keep pressing "Enter" key to see the screen refreshed after 5 minutes have passed.

**INFO:** Console can be disconnect from the VM at any time, by using ctrl+\] key combination.

## Step 6: Access TEVA web admin interface to finalize new Enterprise Agent configuration

 Now it is time to visit your new Enterprise Agent's web admin interface, using this URL \(replace "YOUR.HOST.IP.ADDRESS" with the actual IP of your RHEL/CentOS host:

```text
http://YOUR.HOST.IP.ADDRESS:4080/
```

 Once you can see the login page of the web admin interface, please refer to the [video in this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnfKAC) \(fast forward to 2m17s\). You can skip the network configuration part described there, since you have already configured it in the previous step.

## Conclusion

 Once you have reached this point, you have successfully deployed ThousandEyes Enterprise Agent Virtual Appliance as a virtual machine on your RHEL/CentOS 6 host.

## Caveats

* If firewall is installed on the host, step \#3 needs adjustments to your local environment. These adjustments exceed the scope and context of this guide.
* Caution and adjustment of procedure is needed if your /etc/rc.local file contains additional entries that should not be run multiple times.

##  Addendum \#1: Basic KVM virtual machine management commands

 If you happen to find yourself in need of managing Enterprise Agent virtual machine manually, here is a list of basic commands that may help you on your way:

```text
virsh list                       # List all running VMs
virsh list --all                 # List all VMs (running and stopped)
virsh start    thousandeyes-va   # Start the VM
virsh shutdown thousandeyes-va   # Graceful shutdown (sends ACPI poweroff signal to the VM)
virsh destroy  thousandeyes-va   # Hard poweroff
virsh reset    thousandeyes-va   # Hard reset
```

## Addendum \#2: Alternative network configuration using existing bridge

If your uplink network interface is already configured as bridged, you might want to connect Enterprise Agent directly to your network, without the host acting as an intermediate hop/gateway. In order to do this, you need to adjust the procedure described above, in the following steps:

* Step \#3: This step can be skipped entirely.
* Step \#4: Command for VM import must be adjusted: bridge:br-teva must be replaced with bridge:YOUR-BRIDGE-NAME.
* Step \#5: Network configuration might differ significantly here, and DHCP functionality of the network can be leveraged.

