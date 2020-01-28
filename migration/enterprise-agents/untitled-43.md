# Enterprise Agent Installation for Cisco IOS XE Containers

This article details the steps to install the ThousandEyes Virtual Appliance \(VA\) inside either an Integrated Services Router \(ISR\) or Aggregation Services Router \(ASR\), which is able to host KVM-based virtualized services. The VA is a virtual machine containing a pre-installed ThousandEyes Enterprise Agent, which can be quickly imported into a virtualization environment.

## Requirements

* Cisco IOS XE 16.1 or higher \(or IOS XE 3.17 or higher under the old versioning scheme\)
* ISR 4000 series router, ASR 1000 series router or [ISRv software](http://www.cisco.com/c/en/us/solutions/collateral/enterprise-networks/enterprise-network-functions-virtualization-nfv/datasheet-c78-736768.html) on a supported hardware platform
* Minimum 8 GB RAM \(ISR 4000\) or 16 GB \(ASR 1000\)
* 2GB of free memory per installed Virtual Appliance
* Solid-state drive storage \(NIM-SSD or MSATA-SSD\)
* Internet connectivity from the ISR/ASR

## Overview

In this example we'll install the ThousandEyes VA within an ISR as a virtual service. To assign the VA an IP address, either configure a valid DHCP pool on the router, or use static addressing. In order to connect the VA to the Internet, you need to assign a VirtualPortGroup interface as the default gateway. Make sure the VirtualPortGroup interface IP address is within the same network block as the VA's IP address.  We'll use DHCP for the example, and name our example virtual service **hitman**.  

The installation process for a VA consists of three steps:

1. Installing the Virtual Appliance
2. Activating the Virtual Appliance
3. Initializing the Virtual Appliance

### Installing the Cisco IOS XE Container

* Download the ThousandEyes Virtual Appliance for Cisco IOS XE from the [Settings &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/) page.
* Copy the file onto the router hard disk via one of the following methods:
* * Secure Copy Protocol \(SCP\)
  * File Transfer Protocol \(FTP\)
  * Trivial File Transfer Protocol \(TFTP\)
  * USB storage device
* Install the VA as a Virtual Service 

```text
isr# virtual-service install name hitman package harddisk:teva-cisco.ova
```

**Note**: If you see the following error,

```text
Invalid package::Failed to verify virtual service package-def file::Failed to validate the certificate; 
Package 'te-va.cisco.ova' is 'unsigned', does not match original signing level 'Cisco signed' 
Aug 11 12:06:11.657: %IOSXE_VMAN-3-MSGINITFAIL: Failed to initialize required Virt-manager resource: 
VM [hitman]: Install failed, VM unpacking error
```

please execute the following commands

```text
asr#configure terminal
asr(config)#virtual-service
asr(config-virt-serv-global)#signing level unsigned
```

* Configure a VirtualPortGroup Interface with an IP address from within the same network block \(subnet\) as that of the ThousandEyes VA. Once the ThousandEyes VA is **installed and activated**, enter the default gateway for this IP address

```text
isr# config t
isr(config)# interface VirtualPortGroup3
isr(config-if)# ip address 10.100.152.100 255.255.255.0
```

* Assign a VirtualPortGroup interface as a gateway to virtual-service

```text
isr# config t
isr(config)# virtual-service hitman
isr(config)# vnic gateway VirtualPortGroup3
```

**Note**: VirtualPortGroupX is an interface on the ISR and must have connectivity to the ThousandEyes Collector \(192.150.160.0/24\)  
**Note**: The VirtualPortGroup's Line Status and Line Protocol will change to "up" only after activating the Virtual Appliance.

At this point, the ThousandEyes VA is installed on the router as a virtual service. You can check the status of the VA as follows:

```text
isr# sh virtual-service list
Virtual Service List:

Name     Status     Package Name
------------------------------------------
hitman   Installed  teva-cisco.ova
```

### Activating the Cisco IOS XE Container

* Activate the virtual service

```text
isr# config t
isr(config)# virtual-service hitman
isr(config)# activate
```

The virtual service should now be **activated**. VirtualPortGroup interface should change its status to up and up

```text
isr# sh virtual-service list
Virtual Service List:
Name     Status     Package Name
------------------------------------------
hitman   Activated  teva-cisco.ova
```

```text
isr# sh ip int brief VirtualPortGroup 3

Interface         IP-Address      OK?  Method  Status Protocol

VirtualPortGroup3 10.100.152.100  YES  NVRAM   up     up
```

### Connecting to the Cisco IOS XE Container

* Connect to the VA virtual service via console

```text
virtual-service connect name hitman console
```

###   Initializing the Cisco IOS XE Container

* On connecting to the virtual service console, you should see a prompt message similar to one below. IMAGE MISSING
* On the first run, the Virtual Appliance tries to acquire an IP address via DHCP. I have configured a DHCP pool on the ISR, pointing the default-router to my VirtualPortGroup Interface and also assigning the internal DNS nameserver. The VitrtualPortGroup 3 interface is assigned an IP address from this subnet \(**10.100.152.100**\)

```text
isr(config)# ip dhcp pool ISR-POOL
isr(dhcp-config)# network 10.100.152.0 255.255.255.0
isr(dhcp-config)# default-router 10.100.152.100
isr(dhcp-config)# dns-server 10.100.100.102
```

* If you want to assign a static IP address, press N and after the hostname screen, select "Static configuration parameters" using down arrow key and space bar. IMAGE MISSING

Note: To exit the console - press **"CTRL+C" 3 times**.

* Once the Network Settings are applied, access ThousandEyes Virtual Appliance interface through the URL in that screen and login with the credentials shown in the virtual console. IMAGE MISSING
* Upon login, you will be prompted to change the Web Interface password. IMAGE MISSING
* Obtain your Account Group Token from the menu, using Settings &gt; Agents &gt; Enterprise Agents &gt; Add New Agent &gt; **Show Account Group Token for Installation**.  Copy the token. IMAGE MISSING
* Paste the Account Group Token into the Account Token field. The field should turn green. IMAGE MISSING

1. Select Yes for Browserbot if you wish; this is required for Page Load and Transaction tests.
2. Click Next, and verify/configure Network and Time server settings for the VA.
3. Run the Diagnostics check and continue to proceed to Agent status. IMAGE MISSING

* Check that your Agent appears on the [Agents &gt; Enterprise Agents](https://app.stg.thousandeyes.com/settings/agents/enterprise/) page, inside ThousandEyes. IMAGE MISSING

**That's it! You've installed an enterprise agent in the context of your ISR.**

### Verifying/Debugging the Cisco IOS XE Container 

* List all virtual-service containers installed

```text
isr# sh virtual-service list
```

* View configuration details of a virtual-service container

```text
isr# sh virtual-service detail name hitman
```

* View global information of installed virtual-service containers

```text
isr# sh virtual-service global
```

* View utilization information about a virtual-service container.

```text
isr# sh virtual-service utilization name hitman
```

* View virtual-service trace contents 

```text
isr# sh virtual-service trace message
```

* Debug virtual-service container 

```text
isr# debug virtual-service all
```

### Uninstalling Cisco IOS XE Container 

* If you want to stop the Agent from running tests, but keep the IOS XE Container installed, then,

```text
isr# config t
isr(config)# virtual-service hitman
isr(config)# no activate
isr(config)# end
```

* You can check the status of the virtual-service container using 

```text
isr# sh virtual-service list
Virtual Service List:

Name     Status       Package Name
------------------------------------------
hitman   Deactivated  teva-cisco.ova
```

* If you want to uninstall the virtual-service container from the ISR/ASR, then,

```text
isr# config t
isr(config)# virtual-service hitman
isr(config)# no activate
isr(config)# end
```

* Once the virtual-service container is "deactivated", uninstall the virtual-service container, as 

```text
isr# virtual-service uninstall name hitman
```

* In both cases, the Agent will be shown **OFFLINE** under **Settings &gt; Agents &gt; Enterprise Agents page.**

### FAQ

**Q. How does having an Enterprise Agent on Cisco IOS-XE impact performance?**  
A. We compared a Docker version of the agent running on an Intel NUC to an agent running on the ISR. 3 Enterprise Agents were run in parallel. The performance characteristics of an agent show an approximately 25% decrease in browserbot performance relative to a standalone device running a similar configuration, however, HTTP, network, and DNS tests were within a 2% variance of a single device. Please note that this was NOT a variation in performance on the ISR or other applications within the ISR.

**Q. Does installing an agent have an impact on production traffic handled by the ISR or ASR?**  
A. Enterprise Agents are installed on service-containers within the ISR. By definition, the virtual instances are compartmentalized and should not affect other applications or services on the ISR. However, please make sure that there are enough hardware resources available on the routers to install the agent.

**Q. What is the advantage of collocating Enterprise Agents within a router? Does this new deployment model allow us to expand into newer markets?**  
A. Enterprise Agents, now deployed within an ISR or ASR router, provide an opportunity to expand into markets that might have been previously challenging, for example, retail stores or remote offices that often do not have readily available VMs or servers and procuring new hardware can be challenging and time-consuming. Piggybacking on existing hardware makes it easier for customers to deploy agents as it does not involve new, stand-alone hardware installation or security clearance. Cisco ISRs and ASRs form the vast majority of routers in branch offices across enterprise WAN, so this model can increase the probability of newer deployments.

**Q. I cannot activate the Virtual Appliance.**   
A. It was detected that in some RP's KVM support is disabled, this is shown by issuing "show virtual-service" and checking the "Machine types disabled" list. The root cause was that VTX support on the RP's processor was disabled. The way to enable VTX support is to break into ROMMON mode \(steps 1, 2, 4 and 5 of "[Details of the Password Recovery Procedure](https://www.cisco.com/c/en/us/td/docs/routers/asr1000/install/guide/asr1routers/asr-1000-series-hig/asr-hig-tbl.html#con_1050057)" section\)  of the RP that has VTX disabled, and issuing the following commands:

* ENABLE\_VTX=1 
* sync 
* reset

Once this is done, KVM should be listed in the "Machine types supported" list of "show virtual-service" command output and normal configuration and activation of the Virtual Appliance should follow.

