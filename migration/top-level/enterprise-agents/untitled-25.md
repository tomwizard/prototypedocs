# Installing Enterprise Agent on VirtualBox

This article describes how to set up the ThousandEyes Enterprise Agent using the Virtual Appliance OVA with VirtualBox. To download VirtualBox visit: [https://www.virtualbox.org](https://www.virtualbox.org/). 

Please see the installation guides for VirtualBox as below:

Windows: Section 2.1 here: [https://www.virtualbox.org/manual/ch02.html](https://www.virtualbox.org/manual/ch02.html)  
Mac OS: Section 2.2 here: [https://www.virtualbox.org/manual/ch02.html ](https://www.virtualbox.org/manual/ch02.html)  
For your convenience, ThousandEyes provides an image of a Virtual Machine with the Enterprise Agent installed in OVA \(Open Virtual Appliance\) format updated bi-weekly and hence downloading a recent image for new Enterprise Agent installs is strongly recommended. If your prefer more granular control of the your Enterprise Agent and the underlying Operating System, we recommend the Enterprise Agent deployment using [Linux Package method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method).

## Step-by-step guide

 Please follow the below steps to install ThousandEyes Virtual Appliance

1. To download the most recent [Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent-1472236187506) image, begin by navigating to Agents &gt; Enterprise Agents \([thousandeyes-va-&lt;version&gt;.ova](https://app.thousandeyes.com/install/downloads/appliance/thousandeyes-appliance.ova)\).  
2. Click on the **Add New Enterprise Agent** button.
3. The **Add New Enterprise Agent** button will reveal various install options available for the Enterprise Agent. This install guide will cover deployment using the OVA package. Select **Download - OVA** to receive the latest version.
4. Once the image is downloaded open the VirtualBox application and click on File &gt; Import Appliance. The below screenshot is of VirtualBox version 5.2.20 r125813 \(Qt5.6.3\) on MacOS Mojave, depending on version and Operating System, appearance could have minor differences.
5. Click on the Browse button and select the downloaded Virtual Appliance image.                                                                                                                         
6. Once the image is selected click the **Continue** button.
7. The **Appliance settings** menu will display. You will see many options preconfigured. However, the options mentioned below can be re-configured:
   * The Name of VM
   * CPU Count
   * RAM
   * Hard disk Space,
   * Network Interface.

Enterprise Agent hardware requirements are mentioned [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements). The agent is designed to operate within the specifications listed in the article. Choosing settings which are higher than the recommended specifications will not provide additional benefits to Enterprise Agent performance. However, Enterprise Agent performance will be degraded if settings are configured which are below the recommendations. Once finished making changes  click **Import**.

1. Wait for the appliance to be imported and visible in the VirtualBox Manager window. Once the import is complete \(8\), double-click the new machine to start.
2. Once the machine boots up, a welcome screen displays the default values for the Virtual Appliance IP address, username, and password. The Virtual Appliance IP address is obtained via DHCP by default. If you are not using DHCP, you may configure a static IP by pressing "N" and following the interactive setup wizard. The available network configuration options here are the following: Hostname, IPv4/IPv6, and DNS. To reset the Virtual Appliance password to the default value, press "R". The Web UI can be accessed at http://&lt;Virtual Appliance IP address&gt;. The access can be upgraded to HTTPS by following the steps mentioned [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000XofqCAC_Secure-access-to-ThousandEyes-Appliances).                          
3. To open the Web UI, open a web browser and enter the URL displayed on the welcome screen. Once you are at the URL, enter the default username and password. Then, click **Login**. You will be prompted to change the default password. Enter the current and new passwords, then click **Change Password**.     
4. Obtain the Account Group Token as guided [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjrCAA_Where-can-I-get-the-account-group-token). Navigate to the **Agent** tab in the Web UI. Enter the Account Group Token in the **Account Group Token** box, then click **Save Changes.** 
5. The Browser will now be redirected to Review page, click **Complete** to finish setup.                                         
6. If the Review page shows all checks green as in above screenshot, your Enterprise Agent is now ready to run tests. The newly added Enterprise Agent would appear in the Settings &gt; Enterprise Agents window, as seen below:                                                                          

## Basic Troubleshooting 

* If your VM displays just a black screen, virtualization might be disabled or not available. This can be confirmed in Windows machine as instructed [here](https://www.shaileshjha.com/how-to-find-out-if-intel-vt-x-or-amd-v-virtualization-technology-is-supported-in-windows-10-windows-8-windows-vista-or-windows-7-machine/)
* If Path Visualization appears broken or incomplete, this might be due to NAT, [this](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SIHCA2_Virtual-machine-with-NAT-breaks-Path-Visualization) article explains the phenomenon in detail.

## Related Articles:

* Obtaining SSH access to ThousandEyes Appliance from [Mac/Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Mac-Linux) and [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Windows)
* [Firewall configuration for Enterprise Agents ](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents)
* [Installing Enterprise Agents in Proxy Environment](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG_Deploying-Enterprise-Agent-in-Proxy-Environment)
* [Password reset on the Virtual Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmncKAC_Password-reset-on-the-Virtual-Appliance)
* [Unlocking the ThousandEyes Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvrCAC_Unlocking-the-Thousandeyes-Appliance)

