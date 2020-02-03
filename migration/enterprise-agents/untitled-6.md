# How to set up the Virtual Appliance

#### How to set up the Virtual Appliance

The Virtual Appliance is a virtual machine containing a pre-built ThousandEyes Enterprise Agent, which can be quickly imported into virtualization software, configured and made available for use in testing. This article describes the requirements and steps required to install and use the ThousandEyes Virtual Appliance.    
 

## System requirements

* Working network to the virtual machine
* At least 2 gigabytes of memory for the virtual machine

## Overview

The installation process for a Virtual Appliance consists of two parts:

1. [Import the Virtual Appliance]() into your virtualization software \(hypervisor\)  Installation instructions fall into one of two groups, depending on the type of hypervisor:
   * Virtualization software that supports Open Virtualization Format \(OVA/OVF\):  Oracle VirtualBox, VMWare products, Microsoft Hyper-V for Windows Server 2012, 2016
   * Virtualization software that does not support Open Virtualization Format \(OVA/OVF\):  Microsoft Hyper-V for Windows Server 2008
2. [Configure the Virtual Appliance]()

###  [Importing the Virtual Appliance]()

#### Where to find what you need

Before starting with the import it is necessary to know where these resources can be accessed. 

* Enterprise Agents are listed in the Agent Settings. 
* If no agents have been installed yet the listing will show **No Enterprise Agents Found**
* To import a Virtual Appliance agent from this area, click the **Add New Enterprise Agent** Button. 
* Follow the steps below to proceed with the Import from this area of the ThousandEyes platform.

####  Import with Open Virtualization Format \(OVA\) <a id="import-ova"></a>

1. Download the latest [thousandeyes-va-&lt;version&gt;.ova](https://app.thousandeyes.com/install/downloads/appliance/thousandeyes-appliance.ova) file from the [Cloud & Enterprise Agents &gt; Agent Settings &gt; Enterprise Agents &gt; Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page.
2. Click the **Add New Enterprise Agent** Button on the left hand side of the Agent Settings Screen.  
3. There are several package types and options under this Menu. Under the **Package Type** “Appliance” should be selected: Click the button in the listing labeled **Download - OVA** for Virtual Appliance shown above the link for this Installation Guide.  
4. Double-click the downloaded thousandeyes-va-latest.ova file, or import it based on the virtualization software if this does not occur automatically.  Click the import button and the progress of the installation will be shown.
5. Go through the steps in the VM application you have.    Note: We recommend at least 2GB RAM memory allocated for the Virtual Appliance.
   * Oracle VirtualBox - instructions can be found on the VirtualBox manuals, at this [link](http://www.virtualbox.org/manual/ch01.html#ovf).
   * VMware Fusion \(5.x\) - instructions can be found on the VMware Fusion knowledgebase, at this [link](http://pubs.vmware.com/fusion-5/topic/com.vmware.fusion.help.doc/GUID-275EF202-CF74-43BF-A9E9-351488E16030.html).
   * VMware Fusion \(4.x\) - to import an OVA file into VMware Fusion 4.x, you first need to convert the .OVA file that we ship to a .VMX.  This is managed through a standalone converter published by VMware, and is available at this [link](http://communities.vmware.com/community/vmtn/server/vsphere/automationtools/ovf).  Once you have converted the file to a .VMX file, then it can be imported by following the instructions found on the VMware Fusion Knowledge Base, at this [link](http://pubs.vmware.com/fusion-4/index.jsp?topic=/com.vmware.fusion.help.doc/GUID-F8B8DD94-4F5F-4BCB-8811-6B48DC3113E7.html).
   * VMware Workstation \(9.x\) - Instructions can be found on the VMware Workstation knowledgebase, at this [link](http://pubs.vmware.com/workstation-9/index.jsp?topic=%2Fcom.vmware.ws.using.doc%2FGUID-DDCBE9C0-0EC9-4D09-8042-18436DA62F7A.html).
   * VMware ESXi \(4.x-6.x\) - Instructions can be found on the VMware Community forum, at this [link.](http://communities.vmware.com/thread/319846)
   * Microsoft Hyper-V - Instructions can be found in [this ThousandEyes Knowledge Base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmndKAC).
6. No matter which platform you choose, you will need to configure your guest \(virtual machine\) to use a bridged network connection, so that the guest has unimpeded network and Internet access.  \([see screenshot below]()\).
   * **NOTE: For VMware hypervisors,** [**VMXNET 3**](https://kb.vmware.com/s/article/1001805) **adapter type is recommended. Flexible adapters are currently not supported.**
7. Configure the Virtual Appliance. 

Imported OVA appearing in VirtualBox

   
Network Settings showing Bridged Adapter selected  
 

  
Virtual Appliance View following Start  
 

Proceed to the section linked here on [Configuring the Virtual Appliance]() to continue configuring of the Open Virtualization Format \(OVA\).

####  Import with Microsoft Hyper-V format <a id="import-hyperv"></a>

1. The instructions below use Hyper-V Manager from Windows Server 2016, but the steps are similar for prior versions of Hyper-V.
2. Download the latest [thousandeyes-va-&lt;version&gt;.zip ](https://app.thousandeyes.com/install/downloads/appliance/thousandeyes-appliance.zip)file from the [Cloud & Enterprise Agents &gt; Agent Settings &gt; Enterprise Agents &gt; Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page.
3. Click the **Add New Enterprise Agent** Button on the left hand side of the Agent Settings Screen.
4. There are several package types and options under this Menu. Under the Package Type “Appliance” should be selected: Click the button in the listing labeled **Download - OVA** for Virtual Appliance shown above the link for this Installation Guide.
5. Extract the zip file to the location that you would like to keep your Virtual Appliance files. We recommend using the default Hyper-V virtual machines folder.  Note: You cannot move the files after completing these steps.
6. Run Hyper-V Manager and click on "Import Virtual Machine...".
7. Click "Browse" to the select location of the extracted files. This folder should contain two folders: "Virtual Hard Disks" and "Virtual Machines" as well as the file "config.xml".
8. Select "Copy the Virtual Machine \(create a new unique ID\)" and leave "Duplicate all files so that the same virtual machine can be imported again" unchecked, then click Import.
9. After the virtual machine has been imported, click "Settings...".
10. Select "Network Adapter" from the left pane.
11. In the drop-down menu under "Network:" select the appropriate network that you would like this virtual machine to connect to. This network should be accessible to you, and have access to the Internet.
12. Click Ok.
13. You can now run the virtual machine by clicking "Connect..." then "Start".
14. Configure the Virtual Appliance.

### [Configuring the Virtual Appliance]()

 In order to get a new agent to appear in the Agents Settings page listing the newly downloaded ThousandEyes Enterprise Agent \(TEVA\) Virtual Appliance will need to be configured. 

1. After the system starts a screen will appear that will show and IP address for the management console and default access credentials
2. Access the ThousandEyes Virtual Appliance interface through the URL in that screen and login with the credentials shown.
3. Open a browser entering the URL presented on the screen.  Enter the default username and password given. 
4. Change the Virtual Appliance management console Web Interface Password and Click the “Change Password” Button. 
5. Following that enter the Account Group Token in the field that will show up under the Agent Section.  This should appear automatically after changing the password.
6. Retrieve the Account Group token from  [Cloud & Enterprise Agents &gt; Agent Settings &gt; Enterprise Agents &gt; Agents &gt; Add New Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) view. It can be found under the link labeled "Show Account Group Token for Installation".  This will reveal the token so it may be copied for use.
7. Paste the Account Group Token into the Account Token field. The field should turn green.
8. Yes is selected for Browserbot by default since this component is required for Page Load and Transaction test types.
9. Click the **Continue** button.
10. Following that The Review Section will appear and Diagnostics will begin to run.  Some errors will show up initially as red then turn to green.  Wait a few minutes.
11. When the agent checks in with the Account Group Token it should appear in the listing.  For convenience if there are a number of agents listed the new Enterprise Agent will be listed.
12. Initially the status of the agent will show up in [Red as Offline]().  Check back in to the management console Web Interface and wait for Appliance Status and Diagnostics to show up in Green. When this happens click the **Complete** Button.  See [Supplemental Screenshots]() for a visual detail of this and the following steps.
13. The Network Section of the Web Interface will be shown.  Select the Status Section once more and [click the **Run Diagnostics** Button]()
14. Flipping back to the Agent Settings page the Agent Status in the Listing should show [Status/Last Contact in Yellow](). 
15. At this point Agent versions will show up in the detail.  The agent will be automatically updating its version with the ThousandEyes Platform.  In order to do this it needs to be able to communicate with the platform.  See the [Related Articles]() section for more.  While this is happening check that your Agent status periodically again: [Cloud & Enterprise Agents &gt; Agent Settings &gt; Enterprise Agents &gt; Agents &gt; Add New Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents).  Wait for the Agent to check and upgrade to the latest version.  This can be confirmed after the [Status/Last Contact field shows up in Green]() and the time following last contact in minutes shows.  Opening up the detail for the agent listing will show the Versions of the Agent and Browserbot components \(no longer in red\) upgraded to the latest version.

##  [Supplemental Screenshots]()

The following screenshots appear while completing configuration.  During this process the agent is communicating with the platform and updating.  Expect to see these views during that process:

* Step 12: Agent Initialization
* [Step 13: Run Diagnostics]()
* [Step 14: Check Status]()
* [Step 15: Check for Green Online Status]()

##  [Related Articles]()

* To know more about Enterprise Agent Hardware recommendations please see [Enterprise Agent Hardware Requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements) article.
* For recommended firewall configurations please see [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents).
* For Enterprise Agent proxy options please see [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG_Configuring-an-Enterprise-Agent-to-use-a-proxy-server) article.
* This article explains process of [Installing Enterprise Agent on VirtualBox](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGYyCAO_Installing-Enterprise-Agent-on-VirtualBox).
* Gaining access to ThousandEyes Appliance using SSH from [Mac/Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Mac-Linux) and [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Windows). 

