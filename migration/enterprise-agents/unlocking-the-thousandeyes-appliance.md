# Unlocking the ThousandEyes Appliance

The ThousandEyes Virtual Appliance \(VA\) and Physical Appliance \(PA\) provide a limited number of administrative commands via the `sudo` utility, when users access the command line using SSH as user thousandeyes. If greater control over the operating system and the ThousandEyes Agent software is required, the VA can be “unlocked”, which gives the thousandeyes user the ability to use any command via `sudo`.

**NOTE:** Changes which require unlocking the Virtual Appliance will not be supported by ThousandEyes.  A Virtual Appliance which becomes inaccessible, unstable or otherwise unusable after such changes will require reinstallation of the Virtual Appliance.

## Unlocking an Appliance

To unlock the Appliance, install the **te-va-unlock** package from the ThousandEyes APT repository \(apt.thousandeyes.com\). Installing the package is done from the command line of the Appliance.  Access the command line via SSH.  See the following Knowledge Base articles to configure SSH access from your operating system:  
  
[Connecting to the ThousandEyes Virtual Appliance using SSH \(Mac/Linux\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-%28Mac/Linux%29)  
[Connecting to the ThousandEyes Virtual Appliance using SSH \(Windows\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-%28Windows%29)  
  
Once you have accessed the Appliance via SSH, issue the following commands to install the package:

```text
sudo apt-get update
sudo apt-get install te-va-unlock
```

The `te-va` process will be restarted at the conclusion of the installation.

An example of unlocking an Appliance is show below:

```text
thousandeyes@binky-thousandeyes-va:~$ sudo apt-get install te-va-unlock

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:

  te-va-unlock

0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 848 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://apt.thousandeyes.com/ trusty/main te-va-unlock amd64 0.96-1~trusty [848 B]
Fetched 848 B in 0s (3405 B/s)  
Selecting previously unselected package te-va-unlock.
(Reading database ... 37645 files and directories currently installed.)
Preparing to unpack .../te-va-unlock_0.96-1~trusty_amd64.deb ...
Unpacking te-va-unlock (0.96-1~trusty) ...
Setting up te-va-unlock (0.96-1~trusty) ...
te-va stop/waiting
te-va start/running, process 2599
```

An unlocked Appliance's web interface will display a red "Unlocked" icon, as shown in the image below. If the unlock process was run after logging into the Appliance's web interface, then log out and log back into the web interface to see the Unlocked icon.

IMAGE MISSING

