# Enterprise Agent Port Forwarding

When an Enterprise Agent is installed in a virtual machine as either a Virtual Appliance or a Linux package Enterprise Agent, ThousandEyes recommends configuring the virtual machine with a bridged virtual network adapter.  Bridged adapters allow the Agent to communicate directly with the local physical network. However, some circumstances may prevent customers from using bridged adapters.  Reasons a bridged adapter may fail include lack of DHCP service for the virtual machine or security features of at the media access layer such as port-based MAC address security or wireless connections that permit only a single MAC address.

Under those circumstances, a NAT virtual adapter may be used for the Enterprise Agent. NAT adapters use an IP address and MAC address of the virtual machine's host. However, in order to permit network traffic initiated from other sources to the Enterprise Agent, port forwarding configuration within the hypervisor software will be required.

In this article we provide a port forwarding configuration in the free hypervisor [Oracle VirtualBox](https://www.virtualbox.org/) \(a similar configuration can be replicated in any hypervisor supporting NAT adapters and port forwarding\). Port forwarding creates a mapping from a TCP or UDP port on the virtual machine's host to a port on the Enterprise Agent's virtual machine, allowing TCP and UCP packets initiated inbound to the Agent.

## Configuring port forwarding in VirtualBox

The steps below provide a basic port forwarding configuration for TCP and UDP communication to a ThousandEyes Virtual Appliance. Please note that because the ICMP protocol does not have port numbers, ICMP is not supported as an inbound protocol to the Enterprise Agent.  ThousandEyes tests which use the ICMP protocol will not be able to target an Enterprise Agent using the following configuration, which uses the virtual machine host's IP address as the NAT IP address. For inbound ICMP to an Enterprise Agent \(as opposed to ICMP communication which the Agent initiates\), the host's IP address cannot be used. Instead, a separate IP address will be required.

Also note that port forwarding using the virtual machine host's port numbers below 1024 \(so-called "privileged ports"\) may not work with your host's operating system. In our example below, we use only host ports above 1024.

For additional information on configuration or limitations, consult the VirtualBox [Networking documentation](https://www.virtualbox.org/manual/ch06.html).

1. Run VirtualBox, highlight your Agent's virtual machine and click the Settings icon. IMAGE MISSING
2. Select the Network settings.  For "Adapter 1" configure the network adapter as **NAT.** IMAGE MISSING
3. Click the **Port Forwarding** button, then click the **+** icon to add a port forwarding rule.  Repeat the click to add more rules.

   In the example below, we have added the following rules:

    Rule 1 forwards the host port 8080/TCP to the Agent port 80 for the Virtual Appliance web admin console.  
    Rule 2 forwards the host port 1234/TCP to the Agent port 22 for SSH logins.  
    Rule 3 forwards the host port 49152/UDP to the Agent port 49152 for a ThousandEyes Voice Layer test.  
    Rule 4 forwards the host port 49153/TCP to the Agent port 49153 for a ThousandEyes Agent to Agent test using TCP.  
    Rule 5 forwards the host port 49153/UDP to the Agent port 49153 for a ThousandEyes Agent to Agent test using UDP.

    Click the **OK** button when finished.  
   IMAGE MISSING

4. To test the configuration, using a web browser go to [http://localhost:8080/](http://localhost:8080/#/) in order to access the Agent's web administration console. IMAGE MISSING

 For more information about port numbers used by ThousandEyes Enterprise Agents for tests and other functions, consult the ThousandEyes Knowledge Base article [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK).

