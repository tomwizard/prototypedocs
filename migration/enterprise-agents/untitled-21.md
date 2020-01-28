# Upgrading Ubuntu 14.04 Trusty Tahr-based ThousandEyes Appliances

In accordance with our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy), ThousandEyes [virtual](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) and [physical](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnOKAS_Setting-up-a-physical-appliance) appliances based on [Ubuntu 14.04 Trusty Tahr](https://wiki.ubuntu.com/Releases) operating system will reach their [End of Support stage at the end of April 2019](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems), Unless these appliances are upgraded or otherwise migrated to a currently supported operating system, ThousandEyes platform will stop accepting data submitted by these Enterprise Agents at the end of June 2019.

To continue using your Trusty-based appliances, one of the following actions is required:

* **Perform an in-place upgrade:** Performing an in-place upgrade is most likely the simplest method of keeping your appliances supported. The main part of this article describes the in-place upgrade process.
* **Alternatively, migrate the agent:** If an in-place upgrade is not the right option for you, you can migrate the agent to one of the other deployment options or other supported operating systems. Consult the [Related information]() section at the bottom of this article.

### Table of contents

* [Identifying appliances requiring an upgrade]()
* [Performing the in-place upgrade]()
* [Upgrade verification]()
* [Getting help]()
* [Related information]()

## [Identifying appliances requiring an upgrade]()

In the [Cloud & Enterprise Agents &gt; Agent Settings &gt; "Agents" tab](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) section of the web portal, the agents requiring your attention will have a red triangle icon with an exclamation mark inside \(\) visible next to their names, as pointed out with the marker \#1 in the following figure:

  
Agent list with red triangles marking agents requiring your attention

To get more information, you can either hover your mouse over the red triangle icon \(1\) and a brief popup \(2\) will appear, or, alternatively, you can expand the agent list item and observe the version details displayed on the right-hand side panel:

  
Expanded agent panel showing soon-to-be-unsupported operating system warning

The agents that you are looking for have the following information displayed:

* **Operating system version information \(3\)** contains `Ubuntu 14.04.x LTS`. When relevant, this section's text is displayed in red color, as shown in the figure above.
* **Agent installation type \(4\)** should be one of the following: `Virtual Appliance`, `Physical Appliance`, `Hyper-V Appliance`, or `Cisco Container`. Whether the appliance is locked or unlocked should not make a difference, provided that you have not changed the configuration of an unlocked appliance beyond what automatic upgrade process is expecting.

Once you've identified appliances requiring your attention and decided to perform the in-place upgrade, proceed to the next section to find the upgrade instructions.

## [Performing the in-place upgrade]()

### 1. Prerequisites

The following prerequisites need to be met for the appliance to be eligible for the upgrade process described below:

* A 64-bit operating system only
* Ubuntu 14.04 Trusty Tahr-based appliances only
* Enough free disk space \(10GB\)
* Working internet connection \(direct or proxied\)
* Access to Ubuntu and ThousandEyes APT repositories \(connectivity requirements are fully described in the [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) article\)
* Appliance fully updated to the latest ThousandEyes software versions

**NOTICE: Enterprise Agent appliance will not be performing tests or communicate with the platform while the upgrade process is taking place.**

### 2. Upgrade process overview

Once started, the upgrade process runs as follows:

* Initial checks are performed, to make sure the environment is suitable for the upgrade
* The agent process is stopped, to prevent it from interfering with the upgrade
* The operating system upgrade is started \(the "pre-reboot" stage\)
* Once the operating system upgrade completes, the appliance is automatically rebooted
* The "post-reboot" part of the upgrade is started \(reinstalls the ThousandEyes agent software and starts the services\)

Depending on the speed of your internet connection, your ISP's quality of connectivity to the relevant APT repository network, and the CPU and I/O speed of your hardware, the pre-reboot and post-reboot stages can take anywhere from 5 to 30 minutes each.

### 3. Create a VM snapshot \(optional\)

For virtual appliances, if you have the ability to create a snapshot of a virtual machine, it is **highly recommended** to do so. This will enable you to instantly revert the appliance to the last known good state if something unexpected happens during the upgrade.

### 4. Connect to SSH

Appliance in-place upgrades are started from the SSH console. If needed, consult the [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Windows) or [Mac OS X / Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Mac-Linux) guide for instructions on how to connect to the appliance's SSH service.

### 5. Starting the upgrade

A single command starts the upgrade process:

```text
sudo te-appliance-upgrade
```

The start of the output that the upgrade process produces should look something like this:

```text
te-appliance-upgrade: Getting ubuntu release.
te-appliance-upgrade: Currently running on trusty
te-appliance-upgrade: Installing screen temporarily.
te-appliance-upgrade: No lock on apt/dpkg, proceeding.
...
```

**WARNING: It is important the upgrade process is not interrupted!**

### 6. Waiting for the upgrade process to complete

As mentioned in the Upgrade process overview section above, the upgrade process can take anywhere between 10-60 minutes. Once the appliance is rebooted to enter the "post-boot" upgrade stage, there will be no explicit feedback on the appliance's screen about the upgrade process still taking place.

However, customers can leverage the following command to verify if the post-boot upgrade process is still running:

```text
ps aux | grep upgrade | grep -v grep
```

As long as the command above produces any output, the post-boot upgrade process is still running. Example output that is produced when the post-boot upgrade is still ongoing:

```text
root       625  0.0  0.3  22056  3124 ?        S    13:49   0:00 /bin/bash /usr/local/te_upgrade/upgrade.sh
root       626  0.0  0.1  22052  1948 ?        S    13:49   0:00 /bin/bash /usr/local/te_upgrade/upgrade.sh
root       627  0.0  0.1  22056  1952 ?        S    13:49   0:00 /bin/bash /usr/local/te_upgrade/upgrade.sh
root       629  0.0  0.1  25096  1372 ?        S    13:49   0:00 logger -s -t te-appliance-upgrade
root       631  0.0  0.1  25096  1372 ?        S    13:49   0:00 logger -s -t te-appliance-upgrade
```

The actions of the upgrade process can be followed with this command:

```text
tail -f /var/log/syslog \
  /var/log/dpkg.log \
  /var/log/thousandeyes-upgrade-appliance-apt.log
```

Relevant content in the `/var/log/syslog` file will be prefixed with the `te-appliance-upgrade` text:

```text
<TIMESTAMP> <HOSTNAME> te-appliance-upgrade: Test agent package downloaded
<TIMESTAMP> <HOSTNAME> te-appliance-upgrade: ThousandEyes repositories reachable, proceeding with distribution upgrade
<TIMESTAMP> <HOSTNAME> te-appliance-upgrade: Main disk identified and passed to debconf.
<TIMESTAMP> <HOSTNAME> te-appliance-upgrade: Checking for a new Ubuntu release
```

## [Upgrade verification]()

Once the upgrade process has completed successfully, the agent information panel in the web UI will present the following information:

  
Upgrade verification locations

The important details to pay attention to are:

1. **Agent continuously checking in:** Once the upgrade is complete, the agent should be checking in with the platform roughly once every minute.
2. **Operating system version updated:** The `Ubuntu 16.04.x LTS` text should be displayed.
3. **Agent and BrowserBot versions up to date**: The upgrade process installs the latest available software versions. This section should not be showing any red text indicating obsolete software versions.

## [Getting help]()

If you encounter any issues while upgrading your appliances, [contact the ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) and we'll help you out instantly.

## [Related information]()

The following resources contain further information:

* [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy) article explains how ThousandEyes handles Enterprise Agent operating system end-of-life events.
* [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) article lists all currently supported operating systems and related information.
* Connecting to SSH guides for [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Windows) and [Mac OS X / Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Mac-Linux) will help you set up an SSH connection to your appliance\(s\).

