# Enterprise Agents: Hypervisor installation

With the introduction of the ThousandEyes Enterprise Agent, we've had a number of customers approach us for installation best practices.  This article lays out what you need to do in order to install a Enterprise Agent in a virtual environment, including prerequisites.

## Choose your virtualization software

Everybody has an underutilized server somewhere in their organization.  In many cases, you can add a Enterprise Agent to existing infrastructure using virtualization software, so that the Enterprise Agent shares the resources allocated to an underutilized server.  Current virtualization packages \(also known as hypervisors\) are among the following:

* VMware Workstation
* VMware Fusion
* VMware vSphere
* Microsoft Hyper-V
* Oracle VirtualBox
* Xen Hypervisor

Unsupported Hypervisor platforms:

* VMware Server \(formerly known as GSX server\) has been discontinued by VMware, and is no longer listed as a supported platform.  Customers using VMware server are strongly recommended to investigate installation of VMware vSphere, using the free single-server license of VMware ESXi.
* VMware Player is available free of charge for non-commercial use and follows the same general instructions as VMware Workstation.  Given the non-commercial use restriction, this hypervisor is not supported by ThousandEyes.

## Enabling CPU virtualization extensions \(required\)

All modern 64-bit processors have the ability to run a hypervisor natively, but you need to enable the appropriate virtualization extension settings in the server's BIOS.  This is absolutely required for any hardware-level virtualization within the host machine.  

To make the change, follow these steps:

1. Power on the machine and open the BIOS settings.
2. Open the **Processor** submenu. The processor settings menu may be hidden in the **Chipset** &gt; **Advanced CPU Configuration** menu
3. Enable **Intel Virtualization Technology** \(also known as Intel **VT-x**\) or **AMD-V** depending on the brand of the processor. The virtualization extensions may be labeled **Virtualization Extensions** or various other names depending on the OEM and system BIOS.
4. Enable Intel VTd or AMD IOMMU, if the options are available. Intel VTd and AMD IOMMU are used for PCI passthrough.
5. **Data Execution Prevention** \(DEP\) must be enabled in the system BIOS. For HP servers, the option is called "**No Execute Memory Protection**"

Where you don't have the option of changing your BIOS settings, or are using a 32-bit processor or 32-bit operating system, you'll need to install a _software_ virtualization package on the computer.  At the moment, the only option for this is Oracle's VirtualBox software.

## Setting up the hypervisor

### Windows Server 2008

Windows Server 2008 \("W2K8"\) comes bundled with virtualization software, called Hyper-V.  Hyper-V can be installed as an additional role on an existing W2K8 environment.  

#### Adding the hypervisor role

To add Hyper-V to an existing W2K8 environment, simply open server manager, navigate down the tree on the left side of the server manager interface, and choose Add Roles.  This will open a dialog and allow you to add the Hyper-V role to the server.

IMAGE MISSING

Installation of the Hyper-V role often requires a reboot, which is a good time to make or confirm the required BIOS settings change.  

See below \(under Windows Server 2012 heading, Configuring Hyper-V\) for further instructions on how to configure they hypervisor.

### Windows Server 2012

There are two versions of Windows Server 2012: GUI and Server Core \(Powershell-based management\) only.  Since running Windows Server in server core mode is at this time an advanced option, installing and operating Windows Server 2012 server in server core only mode is not covered in this document.  If you are running in server core mode, to install the Hyper-V role on your server using these instructions you will need to add the GUI to the server.  

#### Enabling the Management User Interface \(GUI\) on W2K12

Refer to this extremely useful blog posting for instructions on installing the GUI on a server core-only install: http://terrytlslau.tls1.cc/2012/06/minimal-server-interface-on-windows.html

In a nutshell, you need to mount the Windows Installation DVD, then install the GUI core:

```text
PS C:\Users\Administrator>New-Item C:\Sources -Type Directory
PS C:\Users\Administrator>Mount-WindowsImage -ImagePath D:\Sources\Install.wim -path C:\Sources -index 2 -ReadOnly
PS C:\Users\Administrator>Add-WindowsFeature Server-Gui-Shell, Server-Gui-Mgmt-Infra -Source c:\sources\Windows\WinSxS
PS C:\Users\Administrator>shutdown -f -r -t0
```

#### Adding the hypervisor role

Once the server is running in GUI mode, open Server Manager, and navigate to the Dashboard.  Click through the **Add Roles and Features** wizard, and select **Role-based or feature-based installation**, choose your local server, and add the **Hyper-V** role.

Once you have selected Hyper-V, you will need to create a Virtual Switch, to allow network communication.  Create a Virtual Switch, and bind it to your connected network adapter.    You may have to specify an alternate path during this wizard, in order to install the content correctly.  This is accomplished by mounting the windows image \(see above, under Mount-WindowsImage\) and specifying the source path of the mounted WIM image, or by directly specifying WIM:d:\sources\install.wim:2

#### Configuring Hyper-V

Once you've added the Hyper-V role, open Hyper-V manager from the Server Manager Dashboard.  This will allow you to configure the system's hypervisor, and set default settings for VM storage and configuration locations, as well as network settings and behavior on host system shutdown.  

When you launch the Hyper-V manager for the first time, you will be prompted to create a virtual network.  ThousandEyes agents run best when connected to the network using a bridged connection, and when configured on a disk drive with ample space.  Creating a logical structure for your hyper-V files is strongly recommended, as it allows you to manage space on the hard disk.

IMAGE MISSING

The easiest way to deploy a virtual Enterprise Agent is to download the prepackaged Enterprise Agent is to download the agent package, and import the virtual appliance into Hyper-V.  Refer to this [article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnwKAC) for details on how to import the virtual machine.

#### Starting up the hyper-v guest

if you've followed all steps above correctly, then the machine should start up with no issues.  If you encounter the following error, then it's typically an indication that the VT or AMD-V CPU flag hasn't been correctly set in the bios.  

Error text:

> An error occurred while attempting to change the state of virtual machine &lt;your virtual machine name&gt;.  
> &lt;your virtual machine name failed to initialize.  The virtual machine could not be started because the hypervisor is not running.

If this occurs, make the appropriate bios setting changes and attempt to start the virtual machine when running.

### VMware Workstation

VMware Workstation is the windows equivalent of VMware Fusion, but can be accessed as a 30-day evaluation.  For any virtualization effort running on windows using VMware, you will need to enable the VT properties in BIOS settings.  Once this is done, simply double-click to install the hypervisor software.

### VMware Fusion

The great thing about Apple hardware is that it's preconfigured to have VT enabled, so no mucking around in the BIOS.  Fusion isn't a free product, and there's no trial version.  Our deployments are tested against VMware Fusion 5.0.x Professional.

As with any Apple deployment, installation is simple.  Open the DMG and install.  Instructions for importing and starting a virtual machine can be found [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnwKAC).

### VMware vSphere

In order to install vSphere, you need a system that you can wipe.  The system must have a 64-bit processor, and should have ample hard disk space and memory to run multiple virtual machines.  Refer to VMware's Knowledge Base for steps on installing vSphere on an empty server.

If you're already running vSphere, great!  Since running vSphere is a complex process, requiring advanced knowledge on managing virtual guests, our recommendation is that you download the ThousandEyes Virtual Appliance and add a new guest to the existing vSphere server or farm, from the template that you provide.

### Oracle VirtualBox

VirtualBox is the easiest of the hypervisor packages to install, and is the only commercial package that is both free, and allows software-only virtualization \(i.e. runs natively on an x86 system, or on an x64 system without the virtualization extensions enabled in the BIOS for the CPU\).  To get started, download the appropriate package to your host from the VirtualBox Wiki, https://www.virtualbox.org/wiki/Downloads

Once you've installed VirtualBox \(it will look different depending on what kind of host you install it\), follow these [instructions](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnwKAC) to import a ThousandEyes Virtual Appliance.

### Xen Hypervisor

Xen is an open-source hypervisor, used by the virtualization giants \(like Rackspace and Amazon Web Services\).  Given that Xen is a monster to configure and a challenge to administer, and that it's really only for the experts, we're not going to address configuration of it here.  As with VMware vSphere, this requires a bare metal machine to be wiped clean in order to run the hypervisor.  If you're interested in more information on installing/deploying Xen, visit the open-source project website at http://www.xen.org.

### Host vs Guest

Most hypervisor packages contain two roles: _host_ and _guest_.  The host is the machine running the hypervisor, and the guest is a machine running _inside_ the hypervisor.  Guests have a many-1 relationship with their host, and share the resources of the host.  Some hypervisor platforms allow resource sharing, including memory, cpu and disk space.

