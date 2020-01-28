# Enterprise Agent Installation on Juniper NFX routers

This article details the steps to install the ThousandEyes Virtual Appliance \(VA\) as a third-party virtual machine on a [Juniper NFX](https://www.juniper.net/documentation/en_US/release-independent/junos/information-products/pathway-pages/nfx-series/product/index.html) router. The NFX series supports Juniper's [Virtual Network Functions](https://www.juniper.net/documentation/en_US/cso1.0/topics/concept/nsd-vnf-overview.html) \(VNF\). A VNF virtual machine provides all the needed functionality for a fully virtualized networking environment.

Virtual Network Functions are managed through the [Juniper Device Manager](https://www.juniper.net/documentation/en_US/junos/information-products/pathway-pages/nfx-series/nfx250-jdm-user-guide.html) \(JDM\).

## Requirements

* Junos OS Release 15.1X53-D45 or higher
* Juniper NFX250 router
* Minimum 8 GB of physical memory
* 2 GB of virtual memory per ThousandEyes Virtual Appliance
* Juniper Device Manager with [enhanced orchestration](https://www.juniper.net/documentation/en_US/junos/topics/task/configuration/enhanced-orchestration-jdm.html) mode enabled
* Internet connectivity from the Juniper Device Manager

## Overview

First configure network settings in Junos OS, consisting of a VLAN containing a physical network interface, and a bridged virtual interface belonging to the VNF containing the ThousandEyes Virtual Appliance. Then use the JDM to install and configure the ThousandEyes VNF. In our example we are going to use VLAN 100, physical interface GigabitEthernet 0/0/1, virtual bridge interface SXE 0/0/0 and "ThousandEyesVNF" as the name of our VNF.

The installation process for a ThousandEyes Virtual Appliance VNF consists of 3 steps:

1. Configuring Network Settings
2. Installing and activating the ThousandEyes Virtual Appliance
3. Initializing the Virtual Appliance

## Configure Network Settings

 To enable the connectivity between the VA and the physical network \(LAN\) a physical network interface \(Ethernet interface\) must be bridged with an internal-facing interface \(SXE interface\) using a routing instance named host-os and a VLAN.

Perform the following steps to configure the interface bridging:

1. Connect to the router's JDM command line interface as the root user

The connection can be made using a console port or via network login \(SSH or telnet\). The example below connects using SSH.

$ ssh root@10.100.50.65's password: \*\*\*\*\*\*\*\*  
Last login: Sun Oct 23 13:35:46 2016 from 10.100.10.239

root@jdm:~\# 

2. Connect to the Junos Control Plane \(JCP\) and enter the JCP command line interface

The JCP provides access to Junos OS and is implemented in a VNF virtual machine called vjunos0. The example below connects using SSH.

root@jdm:~\# ssh vjunos0  
Last login: Wed Oct 19 11:10:20 2016 from 192.168.1.254  
--- JUNOS 15.1X53-D47.4 Kernel 64-bit FLEX JNPR-10.3-20170523.350481\_build

root@:~ \# cli  
{master:0}

root&gt;

 3. Enter configuration mode

root&gt; configure   
Entering configuration mode

{master:0}\[edit\]  
root\# 

 4. Configure the VLAN to be used on the physical network \(LAN\)

The example below uses a VLAN name of vlan100 and a VLAN ID of 100.

root\# set vlans vlan100 vlan-id 100

5. Configure a physical network port \(front panel port\) and add it to the VLAN

The example below uses a gigabit Ethernet port ge-0/0/1.

root\# set interfaces ge-0/0/1 unit 0 family ethernet-switching vlan members vlan100

6. Configure an internal network port as a trunk and add it to the VLAN

The example below uses an internal interface sxe-0/0/0. This interface normally should be a trunk interface in order to support traffic from multiple physical network ports.

root\# set interfaces sxe-0/0/0 unit 0 family ethernet-switching interface-mode trunk  
root\# set interfaces sxe-0/0/0 unit 0 family ethernet-switching vlan members vlan100

7. Save the configuration using the commit command and return to the JDM

root\# commit and-quit  
root\# exit  
Exiting configuration mode

{master:0}  
root@:~&gt;exit

root@jdm:~ \# exit

root@jdm:~ \# 

8. Connect to the JDM and enter configuration mode

root@jdm:~ \# cli  
{master:0}  
root@jdm&gt; configure   
Entering configuration mode

{master:0}\[edit\]  
root@jdm\#

9. Assign the previously configured VLAN name to the host-os routing instance:

root@jdm\# set host-os vlans vlan100 vlan-id 100

##  Installing and activating the ThousandEyes Virtual Appliance

1. Download the Juniper Junos OS Container OVA file from the [Settings &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page of the ThousandEyes app.

2. Copy the file onto the Juniper NFX Series using one of the following methods: 

* Secure Copy Protocol \(SCP\)
* USB storage device

 By default, Juniper saves third-party containers to the /var/third-party/images folder.

3. In the JDM, configure the memory size of the VNF

We recommend at least 2 gigabytes of RAM per ThousandEyes Virtual Appliance.

root@jdm\# set virtual-network-functions ThousandEyesVNF memory size 2097152  
root@jdm\# set virtual-network-functions ThousandEyesVNF memory features hugepages

**Note:** If the JDM does not already have [hugepages](https://www.juniper.net/documentation/en_US/junos/topics/reference/configuration-statement/hugepages-edit-virtual-network-functions.html) configured, then configure the system memory :

root@jdm\# set system memory hugepages page-size 1024 page-count 5

In this example, we configure 5 hugepages with 1 gigabyte of memory each. 1 hugepage is reserved for the JDM and the other 4 hugepages for the user's VNFs. 2 VNFs with 2 gigabytes of memory  or 4 VNFs with 1 gigabyte of memory are two possible configurations, based on this example. Configure the actual number of total gigabytes as needed.

4. Assign a name to our new VNF and select the Virtual Appliance location

In this example, we use the name ThousandEyesVNF and a file path of /var/third-party/images/thousandeyes-va-64-16.04.juniper-ch1.qcow2.

root\# set virtual-network-functions ThousandEyesVNF image /var/third-party/images/thousandeyes-va-64-16.04.juniper-ch1.qcow2

5. Add the quantity of CPUs to be used and CPU hardware features

In this example, two CPUs with hardware virtualization enabled are added.

root\# set virtual-network-functions ThousandEyesVNF virtual-cpu 0 physical-cpu 4  
root\# set virtual-network-functions ThousandEyesVNF virtual-cpu 1 physical-cpu 10  
root\# set virtual-network-functions ThousandEyesVNF virtual-cpu count 2  
root\# set virtual-network-functions ThousandEyesVNF virtual-cpu features hardware-virtualization

6. Configure the ThousandEyes Virtual Appliance interface

Select the interface eth2 because the interfaces eth0 and eth1 are reserved by Juniper NFX Series for management purposes.

root\# set virtual-network-functions ThousandEyesVNF interfaces eth2 mapping vlan members vlan100

7. Save and activate the Virtual Appliance

root@jdm\# commit  
commit complete

{master:0}\[edit\]  
root@jdm\# exit  
root@jdm&gt;

8. Verify that the ThousandEyes Virtual Appliance is running

root@jdm&gt; show virtual-network-functions   
ID   Name                     State         Liveliness  
--------------------------------------------------------------------------------  
44 ThousandEyesVNF Running    alive  

## Initializing the ThousandEyes Virtual Appliance

 1. Connect to the ThousandEyes Virtual Appliance's console

root@jdm&gt; request virtual-network-functions console ThousandEyesVNF

You should see a console with the current Agent’s IP address as follows:

IMAGE MISSING

If a different IP address is needed, type the “N” key, and enter the information to change the Network configuration.

IMAGE MISSING

To exit the console press “CTRL + SHIFT + \] ” 

2. Access the ThousandEyes Virtual Appliance

Using a web browser from a system on the LAN, access the ThousandEyes Virtual Appliance using the URL and login credentials shown in the console screen.

IMAGE MISSING

3. Change the Web Interface password

IMAGE MISSING

4. Obtain and enter the Account Group Token

Click the **ThousandEyes Platform Account Settings** link.

IMAGE MISSING

From the [Settings &gt;  Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page, open the **Add New Agent** form and click the **Show Account Group Token for Installation** link, at the bottom.

IMAGE MISSING

Copy the Token and paste into the **Account Token** field of the ThousandEyes Virtual Appliance Setup.

IMAGE MISSING

Select 'Yes' to install the BrowserBot component if using Page Load or Transaction tests, then click the **Next** button.  
If the Diagnostics check is successful, the Virtual Appliance's Status page should indicate that the ThousandEyes Agent is running.

IMAGE MISSING

The Agent will appear in the ThousandEyes platform, on the [Settings &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page.

IMAGE MISSING

## Uninstalling the ThousandEyes Juniper Virtual Appliance

 To uninstall the ThousandEyes Virtual Appliance, use the following steps:

1. Connect to the JDM Connect to the JDM and enter configuration mode

root@:~ \# cli  
{master:0}  
root&gt; configure   
Entering configuration mode

{master:0}\[edit\]  
root\#

2. Delete the ThousandEyes Virtual Appliance

root\# delete virtual-network-functions ThousandEyesVNF

3. Commit the changes to apply the configuration

root@jdm\# commit   
commit complete

{master:0}\[edit\]  
root@jdm\# exit  
root@jdm&gt;

4. Verify that the Virtual Appliance was deleted

root@jdm&gt; show virtual-network-functions   
ID   Name                     State         Liveliness  
--------------------------------------------------------------------------------

The Agent will also be shown as OFFLINE in the ThousandEyes platform, on the [Settings &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page.

## Managing the ThousandEyes Juniper Virtual Appliance

To connect to the VA using the following command:

root@jdm&gt; request virtual-network-functions console ThousandEyesVNF

To restart to the VA using the following command

root@jdm&gt; request virtual-network-functions restart ThousandEyesVNF

To shut down to the VA using the following command

root@jdm&gt; request virtual-network-functions stop ThousandEyesVNF

To power up to the VA using the following command:

root@jdm&gt; request virtual-network-functions start ThousandEyesVNF

To check the VNF configuration, including the management IP:

root@jdm&gt; show virtual-network-functions ThousandEyesVNF detail   
Virtual Network Function  Information  
-------------------------------------

Id:  :44  
Name::ThousandEyesVNF  
State:  :Running  
Liveliness: :Up  
IP Address: :192.168.1.102  
VCPUs:  :2  
Maximum Memory::2097152 KiB  
Used Memory::2097152 KiB 

 Block Devices  
----------------------------  
Target   \| Source  
----------------------------  
vda\| /var/third-party/images/thousandeyes-va-64-16.04.juniper-ch1.qcow2  

