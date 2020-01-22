# Installing a Physical Appliance - ThousandEyes Customer Success Center

For customers requiring a turnkey solution, the ThousandEyes [Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent) can be installed on an off-the-shelf hardware such as the Intel NUC. The combination provides a convenient form-factor that is easily shipped to branch offices, partner sites, and other environments, where provisioning only requires a power and network connection. A downloadable ISO image is used to install Linux Ubuntu LTS, the ThousandEyes Enterprise Agent and management software onto the Intel NUC.

This article details the hardware requirements and process required to commission the ThousandEyes Enterprise Agent on an Intel NUC.

### Table of contents

* Requirements
  * [Hardware requirements]()
  * [Installation environment requirements]()
* Installation
  * [Downloading the installer]()
  * [Writing the ISO to a USB disk]()
  * [Intel NUC BIOS]()
  * [Installing Physical Appliance software]()
  * [Configuring the Enterprise Agent]()
* [Troubleshooting]()
  * [USB drive not recognized as bootable device]()
  * [Malformed IP Address]()
  * [No Root File System Defined]()
  * ["thousandeyes-va login:" prompt shown on the screen]()
  * [Keyboard not working]()

## Hardware requirements

### Intel NUC 8th generation

<table>
  <thead>
    <tr>
      <th style="text-align:left">Subsystem</th>
      <th style="text-align:left">Manufacturer</th>
      <th style="text-align:left">Component</th>
      <th style="text-align:left">Part Number</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">NUC</td>
      <td style="text-align:left">Intel</td>
      <td style="text-align:left">NUC i7
        <br />NUC i5
        <br />NUC i3</td>
      <td style="text-align:left">NUC8I7BEH
        <br />NUC8I5BEH, NUC8I5BEK
        <br />NUC8I3BEH, NUC8I3BEK</td>
    </tr>
    <tr>
      <td style="text-align:left">Memory</td>
      <td style="text-align:left">
        <p>Any memory configuration supported by the NUC*</p>
        <p>Minimum of 2GB as specified in <a href="https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements">hardware requirements</a>.</p>
      </td>
      <td style="text-align:left">
        <p>Links to Intel- and manufacturer-validated compatible components:</p>
        <ul>
          <li>NUC8I7BEH: <a href="https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i7beh.html">Specification</a> |
            <a
            href="http://compatibleproducts.intel.com/ProductDetails?EPMID=126140">Component compatibility matrix</a>
          </li>
          <li>NUC8I5BEH: <a href="https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i5beh.html">Specification</a> |
            <a
            href="http://compatibleproducts.intel.com/ProductDetails?EPMID=126148">Component compatibility matrix</a>
          </li>
          <li>NUC8I5BEK: <a href="https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i5bek.html">Specification</a> |
            <a
            href="http://compatibleproducts.intel.com/ProductDetails?EPMID=126147">Component compatibility matrix</a>
          </li>
          <li>NUC8I3BEH: <a href="https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i3beh.html">Specification</a> |
            <a
            href="http://compatibleproducts.intel.com/ProductDetails?EPMID=126150">Component compatibility matrix</a>
          </li>
          <li>NUC8I3BEK: <a href="https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc8i3bek.html">Specification</a> |
            <a
            href="http://compatibleproducts.intel.com/ProductDetails?EPMID=126149">Component compatibility matrix</a>
          </li>
        </ul>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Disk</td>
      <td style="text-align:left">
        <p>Any single SSD or NVMe disk supported by the NUC*</p>
        <p>Minimum of 20GB as specified in <a href="https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements">hardware requirements</a>.</p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>\*The following are peripherals that have been tested and approved by ThousandEyes:

* **Memory:** [Vengeance® Series 16GB \(2x8GB\) DDR4 SODIMM 2400MHz CL16 Memory Kit CMSX16GX4M2A2400C16](https://www.corsair.com/us/en/Categories/Products/Memory/Laptop-and-Notebook-Memory/Vengeance%C2%AE-Series-16GB-%282x8GB%29-DDR4-SODIMM-2400MHz-CL16-Memory-Kit/p/CMSX16GX4M2A2400C16#tab-overview)
* **Disk:** M.2 NVMe [Samsung 970 EVO 250GB \(MZ-V7S250B/AM\)](https://www.samsung.com/us/computing/memory-storage/solid-state-drives/ssd-970-evo-plus-nvme-m-2-250gb-mz-v7s250b-am/) and M.2 SSD [Transcend 64GB SATA III 6 Gb/s MTS800](https://www.transcend-info.com/Embedded/Products/No-803)

### Intel NUC 6th & 7th generations - OBSOLETE

**NOTICE:** Intel NUC systems of 6th and 7th generations are only supported for existing deployments.

| Manufacturer | Component | Part Number |
| :--- | :--- | :--- |
| Intel  | NUC i3  NUC i5  NUC i7 | NUC6I3SYH,NUC6I3SYK,NUC7I3BNH,NUC7I3BNK  NUC6i5SYH,NUC6i5SYK,NUC7I5BNH,NUC7I5BNK  NUC6I7SYH,NUC7I7BNH |
| Crucial | 4GB DDR4 2400 MT/S \(PC4-19200\) SODIMM | CT4G4SFS824A |
| Transcend | 64GB SATA III 6 Gb/s M.2 SSD | MTS800 |

### Intel NUC 5th generation - OBSOLETE

**NOTICE:** Intel NUC systems of 5th generation are are only supported for existing deployments.

| Manufacturer | Component | Part Number |
| :--- | :--- | :--- |
| Intel  | NUC i3  NUC i5  NUC i7 | NUC5I3RYK, NUC5I3RYH   NUC5i5RYK, NUC5i5RYH  NUC5I7RYK |
| Crucial | 4GB DDR3 PC3-12800 SODIMM | CT51264BF160B |
| Transcend | 64GB SATA III 6 Gb/s M.2 SSD | MTS800 |

## Installation environment requirements

The following are required:

* **Wired network connection:** The device has to be connected to a network. Wireless connection are not supported.

**Note:** When the NUC is powered off and it is connected to an operational Ethernet switch, the LED on lower right of the RJ-45 port on the NUC will be lit. This indicates that a Link signal from the switch is active.

* **DHCP service:** A DHCP service for the device to obtain an IP address.
* **DNS service:** DHCP service must provide DNS server information to the device.
* **Non-proxied and unrestricted access to the Internet:** The installation process downloads several software packages from online resources. Consult [Enterprise Agent firewall requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) for the list of online locations.

The [Troubleshooting]() section below lists common issues and their resolution.

## Downloading the installer

Download the installer that fits the requirement:

* Generic Appliance. There are no pre-configurations.
* Custom Appliance. Includes Enterprise Agent pre-configurations.

#### Generic Appliance

On the ThousandEyes portal, go to **Cloud & Enterprise Agents&gt; Agent Settings&gt;**, select **Enterprise Agents** \(top line\), click **Add New Enterprise Agent** button. Select Package Type **Appliance.** On **Physical Appliance Installer** click **Download - ISO** button.

#### Custom Appliance

On the ThousandEyes portal, go to **Cloud & Enterprise Agents&gt; Agent Settings&gt;**, select **Enterprise Agents** \(top line\), ****click the **Add New Enterprise Agent** button. Select Package Type **Custom Appliance**. Provide the following information:

* **Appliance Name**. Name of the appliance on the ThousandEyes systems and the Linux host name.
* **Appliance Type**, select Physical.
* If required, select **Add Proxy** and specify the Proxy Host and Proxy Port.
* **Web Server**. If the appliance is to be used for Page Load or Transaction test, select On.
* **SSH Keys**. The **SSH Public key** of the SSH client to be used to access the appliance, for terminal session.

Note that the custom download will include the [Account Group Token](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjrCAA_Where-can-I-get-the-account-group-token) required for the Agent to register itself to the ThousandEyes system.  
Click the **Generate** button. It may take take between 15 and 30 minutes to generate the image. An email will be generated once the image is ready to be downloaded.

## Writing the ISO image to a USB disk

The ISO image can be copied to a USB disk \(flash drive\) and used as a bootable media on the Intel NUC. The following sections describe the process of creating the bootable USB disk on Mac OS X and Windows.

#### Mac OS X / Linux instructions

1. Insert a USB disk that is at least 1GB in size, into a USB port on the Mac. The disk’s content will be overwritten.
2. Open a terminal window
3. Type `diskutil list` \(OS X\) or `fdisk -l` \(Linux\) and identify the physical disk you’re interested in imaging. It should be `/dev/diskN` \(OS X\) or `/dev/sdN` \(Linux\). In the example below, I have a 1GB USB disk in my Mac's USB port:

   ```text
   dave@schadenfreude ~/Downloads> diskutil list
   /dev/disk0 (internal, physical):
      #:                       TYPE NAME                    SIZE       IDENTIFIER
      0:      GUID_partition_scheme                        *500.3 GB   disk0
      1:                        EFI EFI                     209.7 MB   disk0s1
      2:          Apple_CoreStorage Macintosh HD            499.4 GB   disk0s2
      3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   /dev/disk1 (internal, virtual):
      #:                       TYPE NAME                    SIZE       IDENTIFIER
      0:                  Apple_HFS Macintosh HD           +499.1 GB   disk1
                                    Logical Volume on disk0s2
                                    DCA39E1F-1CB4-4386-8E67-0AD63B4A069D
                                    Unencrypted
   /dev/disk2 (external, physical):
      #:                       TYPE NAME                    SIZE       IDENTIFIER
      0:     FDisk_partition_scheme                        *1.0 GB     disk2
      1:             Windows_FAT_32 UBUNTU-SERV             1.0 GB     disk2s1
   ```

4. Run `diskutil unmountDisk /dev/diskN` \(OS X\) or `umount /dev/sdN` \(Linux\) to unmount the device \(replace `N` with the actual disk number from the output above\):

   ```text
   dave@schadenfreude ~/Downloads> diskutil unmountDisk /dev/disk2
   Unmount of all volumes on disk2 was successful
   ```

5. Next, write the image to disk. Run `sudo dd if=<path_to_downloaded_iso> of=/dev/diskN`, wait until it completes:

   ```text
   dave@schadenfreude ~/Downloads> sudo dd if=thousandeyes-pa-1.9.100.iso of=/dev/disk2
   1175552+0 records in
   1175552+0 records out
   601882624 bytes transferred in 267.718384 secs (2248193 bytes/sec)
   ```

#### Windows Instructions

The following instructions are based on Rufus, an open-source application for creating bootable USB flash drives.

1. A copy of Rufus can be obtained from [here](https://rufus.ie/).
2. Start Rufus.
3. Connect a USB drive that is at least 1GB in size. The disk’s content will be overwritten. If there is only one USB drive on the Windows system, Rufus will automatically selects it and it will be displayed under Device. Otherwise, use the down-arrow to select the desired USB drive.
4. Click **SELECT** and browse to select the downloaded ISO image. In the above screen shot, the filename of the selected image is "thousandeyes-pa-0.162.iso." 
5. The screen shot above shows the default settings and they can be left as is. Note that the **Cluster size** default will vary depending on the size of the USB drive. Leave it to the selected default size.
6. Click **START.**
7. On the next screen, select "Write DD Image mode," click **OK**. DD Image Mode is recommended format.
8. Click **OK** to start the boot disk creation.
9. When the process completes, remove the USB drive.

## Intel NUC BIOS

The following are intended to be a check list of configurations required for the ThousandEyes application. The reader should consult the appropriate Intel documentation for the applicable procedures.

* Intel documentation can be found [here](https://www.intel.com/content/www/us/en/support/articles/000005636/mini-pcs.html).
* BIOS update files for the Intel NUC can be found [here](https://downloadcenter.intel.com/search?keyword=bios+nuc).
* Check that the display \(monitor\) used with the NUC are compatible. Check on the Intel documentation. To verify, power up the NUC with the monitor connected, if the Intel splash screen can be seen, the monitor is compatible.
* On the NUC, check that the BIOS version is current. If not the most current, upgrade to the latest version.
* The appliance is intended to the an always-on device. Verify that the following are set in the BIOS:
  * UEFI Boot Support should be disabled.
  * After Power Failure setting should be set to Last State or Power On.

## Installing Physical Appliance software

1. Verify that the [installation environment requirements]() are satisfied.
2. Insert the bootable USB disk in one of the USB slots on the NUC.
3. Power up the NUC.
4. Tap the **F10** key \(on the keyboard\) to force the BIOS to enter the "Boot" menu..
5. On the boot device menu, use the arrow keys to select the USB drive and press &lt;Enter&gt;.

If USB is not shown as an option, power off the NUC, unplug the USB drive, plug it back in and power up the NUC.

**Note:** The BIOS will recognize the USB drive as a bootable device even if the USB flash drive is blank \(nothing in it\). If the BIOS does not recognize the USB drive as a valid bootable device, when there is a USB flash drive inserted, check that the BIOS version is current. If not current upgrade to the latest version.

1. On booting from the USB drive, the installation process will start automatically. `No` user intervention is required, The initial phase will progress fairly quickly, a progress bar will narrate the progress. The final phase is shown by the "Finishing the installation" screen, "Running preseed," the progress bar will show "14%." The installation process are downloading the required software packages. This screen may remain in this state for about 15 minutes, depending on the speed of the network interface and the delays to the download server. Do not power off the NUC. Leave it until it automatically powers off.
2. On completing the installation, the NUC will automatically power off.

## Configuring the Enterprise Agent

 Consult the Knowledge Base "How to set up the Virtual Appliance," available [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) for a comprehensive set of instructions. The following are the minimum required to enable the Physical Agent to communicate with the ThousandEyes portal.

1. Power on the NUC. After the unit boots, the "ThousandEyes Virtual Appliance" screen \(shown below\) will be displayed. The IP address displayed depends on the network environment of the NUC. Note the provided username and password.
2. Using a browser, access the provided URL \(IP address\), and log in using the provided username and password. 
3. The user will be taken to the **Appliance Access** screen to change the default password.
4. Skip this step if the installation is a Custom Appliance, as the Account Group Token is included in the image.

For a Generic Appliance installation, the Account Group Token is obtained on the ISO download screen on the ThousandEyes portal, by clicking "Show Account Group Token for Installation." 

On the **Agent** screen, copy the Account Group Token to the field provided.  
 

1. For information on the other parameters, consult the Knowledge Base "How to set up the Virtual Appliance," available [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance).
2. Verify on the **Status** screen that all diagnostics are green. Follow up and correct any faults shown on the Status screen.
3. If network related parameters were changed, for example disabling IP V6 support, reboot the Agent, through the GUI and verify that all the diagnostics are green.
4. The Enterprise Agent should now appear in the **Cloud & Enterprise Agents&gt; Agent Settings&gt; Enterprise Agents** page of the ThousandEyes portal.

## Troubleshooting

#### USB drive not recognized as bootable device

A USB drive is plugged in, tapping F10 at power-up, on the "Boot" BIOS screen, USB drive is not recognized as a bootable device.

**Resolution:** Disable UEFI boot support.  
                     Check that the BIOS version is current. If not current, upgrade to the latest version.

#### Malformed IP Address

Ubuntu installation fails with a "blue screen" showing "Malformed IP Address."

**Resolution:** Verify that the Ethernet connection to the NUC has a link signal. Verify that the Link LED on the RJ-45 port is lit.  
                     Verify that there is a DHCP server on the network \(broadcast domain\) that the NUC is connected to.

#### No Root File System Defined

Ubuntu installation fails with "No Root File System Defined" message. This situation can occur if USB devices are attached to the NUC via a USB hub. 

**Resolution:** Do not use USB hub to connect keyboard and USB flash drive to the NUC.

#### "thousandeyes-va login:" prompt shown on the screen

The expected blue "ThousandEyes Virtual Appliance" management screen is not displayed. Instead, a black screen with "`thousandeyes-va login:"` prompt is shown.

This is a symptom of an unsuccessful installation. The agent is missing the `te-pa` package which, in addition to the web admin interface, provides the physical console functionality. 

**Resolution:** Components of the Virtual Agent are missing. Most likely caused by the lack of non-proxied and unrestricted access to the internet during the appliance installation. Reinstall the appliance in an environment that satisfies the requirements listed in the [Installation environment requirements]().

#### Keyboard not working

When the installation completes, keypresses are not recognized.

**Resolution:** Most likely incomplete installation. Reinstall the appliance in an environment that satisfies the requirements listed in the [Installation environment requirements]().

#### Do you need further assistance?

For further assistance, contact [ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

