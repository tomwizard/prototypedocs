# Enterprise Agent Installation for Cisco Catalyst 9000 series switches

This article details the steps to install the ThousandEyes Appliance on a Cisco Catalyst 9000 series switch running IOS XE. The Appliance is a pre-installed ThousandEyes Enterprise Agent with a web-based management UI, which can be quickly imported into a virtualization environment.

## Requirements

* A Cisco Catalyst 9000 switch running IOS XE version 16.9.1 or higher
* DNA-Advantage licensing to enable App-hosting \([Application Licensing](https://developer.cisco.com/docs/iox/#!catalyst-9000-series-application-development/licensing)\)
* 2GB of free memory per installed Appliance \([IOX application resource limitations](https://developer.cisco.com/docs/iox/#!catalyst-9000-series-application-development/application-resource-limit)\)
* Solid-state drive storage \([Installing a USB 3.0 SSD](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/hardware/install/b_c9300_hig/b_c9300_hig_chapter_01010.html)\)
* A DHCP server or a static IP address for the Appliance
* Internet connectivity from the switch
* Familiarity with Cisco Catalyst IOS XE Application hosting. Review Cisco's [Application Hosting](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/prog/configuration/169/b_169_programmability_cg/application_hosting.html) instructions, if needed.

## Overview

The installation process for an Appliance consists of three steps:

1. Installing the Appliance
2. Activating the Appliance
3. Configuring the Appliance

The following example installs, activates and initializes the Appliance on a Cisco Catalyst 9300.  In the example, the name of the virtual service is **teva**.  

To assign the Appliance an IP address, either configure a DHCP server to provide the Appliance a lease, or use static addressing. We'll use DHCP for the example.

To connect the Appliance to the Internet, assign a VirtualPortGroup interface as the default gateway. Make sure the VirtualPortGroup interface IP address is within the same layer 3 network as the Appliance's IP address.

1. 
## Installing the Appliance

* Log in to the ThousandEyes application using a login belonging to the Account Group which will be associated with the Appliance.
* Navigate to the [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents), and click the **Add New Enterprise Agent** button.
* Download the TAR file with the ThousandEyes Appliance for Catalyst 9000 Series Switches.
* Copy the file onto the switch via one of the following methods:
  * Secure Copy Protocol \(SCP\)
  * File Transfer Protocol \(FTP\)
  * Trivial File Transfer Protocol \(TFTP\)
  * USB storage device
* Enable the IOx framework on the switch and wait until all the services are running: 

```text
Enter configuration commands, one per line.  End with CNTL/Z.
Cat9k(config)#iox
Cat9k(config)#end
Cat9k#show iox-service
 
IOx Infrastructure Summary:
---------------------------
IOx service (CAF)    : Running
IOx service (HA)     : Running
IOx service (IOxman) : Running
Libvirtd             : Running
```

* Configure a single virtual network interface card \(vNIC\) for the Appliance.

   Both the management port and data port are supported for use as interfaces. In the case of the data port, you need to configure a VPG \(Virtual Port Group\) as well. The VPG will serve as the default gateway for the Appliance. If a DHCP server is present in the management network, the Appliance will obtain an IP address automatically from the DHCP server. Alternatively, use a static IP address.

**Example of configuration with Management port**

```text
app-hosting appid teva
 vnic management guest-interface 0
end
```

**Example of configuration with a Data port with a DHCP pool to assign IP addresses to the Appliance**

```text
interface VirtualPortGroup1
 ip address 10.100.128.1 255.255.255.0
!
! >>> dhcp start
ip dhcp excluded-address 10.100.128.1 10.100.128.9
ip dhcp pool vpg1pool
 network 10.100.128.0 255.255.255.0
 default-router 10.100.128.1
 dns-server 8.8.8.8
 domain-name example.com
! >>> dhcp end
!
app-hosting appid teva
 vnic gateway0 virtualportgroup 1 guest-interface 0
end<
```

## Activating the Appliance

* Install, activate and start the IOx package containing the ThousandEyes Appliance

```text
Cat9k# app-hosting install appid teva package usbflash0:thousandeyes-va.cisco.tar
	teva installed successfully
	Current state is: DEPLOYED

Cat9k# app-hosting activate appid teva
	teva activated successfully
	Current state is: ACTIVATED

Cat9k# app-hosting start  appid teva
	teva started successfully
	Current state is: RUNNING
```

* Use the "sh app-hosting list" command to verify the virtual machine has been installed and is in the running state:

```text
cat9k#sh app-hosting list

	App id                           State
	------------------------------------------------------
	teva                          RUNNING
```

* Verify the virtual machine details

```text
Cat9k#show app-hosting detail appid teva
	App id                 : teva
	Owner                  : ioxui
	State                  : RUNNING
	Application
	  Type                 : vm
	  Name                 : thousandeyes-va-64-16.04
	  Version              : 0.144
	  Description          : ThousandEyes Cisco Virtual Appliance
	Activated profile name : custom
	 
	Resource reservation
	  Memory               : 2048 MB
	  Disk                 : 20000 MB
	  CPU                  : 1200 units
	 
	Attached devices
	  Type              Name               Alias
	  ---------------------------------------------
	  serial/shell     iox_console_shell   serial0
	  serial/aux       iox_console_aux     serial1
	  serial/syslog    iox_syslog          serial2
	  serial/trace     iox_trace           serial3
	 
	Network interfaces
	   ---------------------------------------
	eth0:
	   MAC address         : 52:54:dd:27:84:b0

```

## Configuring the Appliance

* Connect to the virtual machine console from the IOS XE command-line interface to configure Networking, if needed.

```text
Cat9k#app-hosting connect appid teva console
	Connected to appliance. Exit using ^c^c^c
```

* The default Network configuration uses DHCP. If you want to assign a static IP address, press 'N'. After the hostname screen, select "Static configuration parameters" using the down-arrow key then the space bar. Use the Return key to select 'OK'
* Once the Network settings are applied, access the Appliance's web interface with a browser, using the URL in the first console screen. Log in with the default username 'admin' and password 'welcome'.
* Upon login, you will be shown pages on which to further configure Network and Time settings, and prompted to change the Web Interface password.
* Obtain your Account Group Token from the Enterprise Agents Settings page by clicking the **Add New Enterprise Agent** button then clicking the **Show Account Group Token for Installation** link. Copy the token.
* Paste the Account Group Token into the Account Token field.
* Select **Yes** to install Browserbot if needed. BrowserBot is required for Page Load and Transaction tests.
* Click **Continue**.
* View the Diagnostics page's checks and click **Complete** if all checks pass.
* Verify that your Agent appears on the [Agents &gt; Enterprise Agents](https://app.stg.thousandeyes.com/settings/agents/enterprise/) page.

## Uninstalling the Appliance

* To Uninstall the Appliance and free up the resources on the switch, `stop` the application and `deactivate` it. If it needs to be completely removed the Application has to be `uninstalled.`

```text
Cat9k#config term
Cat9k(config)#no app-hosting appid teva
Cat9k(config)#app-hosting stop appid teva
Cat9k(config)#app-hosting deactivate appid teva
Cat9k(config)#app-hosting uninstall appid teva
```

* Validate whether the files were removed from the disk.

```text
Cat9k# show usbflash1:
 20 22022144000 Nov 22 2018 01:12:45.8847925130 +00:00 iox/datastore/teva_data.ext4
Cat9k# delete usbflash1:/iox/datastore/teva_data.ext4>
```

## FAQ

Q. I see the following error: Platform does not have enough CPU resource.

```text
catalyst#app-hosting activate appid teva
% Error: App Activation error: Platform does not have enough cpu resource, available cpu 7400
```

A. Please log-in to the WebUI iox management console and check your CPU status, if you have enough resources to install the app, please try the \`app-hosting activate appid &lt;name&gt;\` again, if you don't have enough CPU resources available, you can reduce the quantity of CPU in your app, or redistribute the CPU resources between your current applications.

