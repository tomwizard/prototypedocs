# Upgrading Ubuntu OS on Enterprise Agents

**NOTICE:** This article contains a guide for upgrading [Linux package-based Enterprise Agent deployments](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method). For **appliance-related** upgrading information, head over to an article dedicated to [upgrading Ubuntu 14.04 Trusty Tahr-based appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGb4CAG_Upgrading-Ubuntu-14-04-Trusty-Tahr-based-ThousandEyes-Appliances) instead.

## Introduction

The ThousandEyes Enterprise Agent support policy for [Ubuntu](https://www.ubuntu.com/)-based Linux package Enterprise Agents is based on [Ubuntu Long-Term Support maintenance updates](https://wiki.ubuntu.com/Releases) and our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy). Ubuntu version 14.04 LTS \(a.k.a. “Trusty Tahr”\) will reach the end of support on 2019-04-30 and end of life on 2019-06-30.

As per the ThousandEyes Enterprise Agent operating system end-of-life announcement in our [Release Update](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CplcCAC_Release-Update-2018-10-23) [2019-01-08](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqLfCAK_Release-Update-2019-01-08), ThousandEyes' support for Enterprise Agents installed on Ubuntu 14.04 LTS \("Trusty Tahr"\) operating system will end after 2019-06-30.

This article provides you with step-by-step instructions to complete an in-place upgrade of Linux package-based agents from [Ubuntu 14.04 LTS \(Trusty Tahr\)](http://releases.ubuntu.com/14.04/) to [Ubuntu 16.04 LTS \(Xenial Xerus\)](http://releases.ubuntu.com/16.04/) and from Ubuntu 16.04 LTS to [Ubuntu 18.04 LTS \(Bionic Beaver\)](http://releases.ubuntu.com/18.04/).

## Agents running on unsupported operating systems

After an Enterprise Agent reaches its end-of-life, enabled Agents running on the unsupported operating systems will cease to function. At the end-of-life date, the ThousandEyes platform will stop accepting data from such agents without notice. Customers are encouraged to upgrade to a supported version of their operating system. Supported operating system versions can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems).

Additionally, an "Agents with Problems" notice in the platform will let you know that we've identified an Agent running on an end-of-life operating system. Users will see this message in the Agent Settings page, as well as from the Agent icon in the top navigation bar.

## Upgrade procedure

In most cases, customers can upgrade from Ubuntu 14.04 LTS or 16.04 LTS by first ensuring the system is up to date, followed by simply running the standard Ubuntu distribution upgrade process and completed by the reinstallation of Enterprise Agent software.

 To update your Ubuntu system to latest software versions \(within an LTS release\) and thus prepare it for the distribution upgrade, run the following commands:

```text
$ sudo apt-get update
$ sudo apt-get dist-upgrade -y
```

  
To install the distribution upgrade tool, run the following command:

```text
$ sudo apt-get install ubuntu-release-upgrader-core
```

To start the distribution upgrade, run the following command and follow the onscreen instructions \(including the request to reboot the system\):

```text
$ sudo do-release-upgrade
```

Consult the [Ubuntu upgrade documentation](https://help.ubuntu.com/community/Upgrades) for full details about upgrading Ubuntu operating systems in-place.

### Post-reboot tasks

Once the in-place upgrade completes and your system is rebooted, you should be logged into a fresh Ubuntu 16.04 operating system. You can quickly verify this by running the following command:

```text
$ cat /etc/os-release 
NAME="Ubuntu"
VERSION="16.04.5 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.5 LTS"
VERSION_ID="16.04"
```

  
The upgrade process has left the ThousandEyes APT repository disabled. You need to re-enable it. You can do so using the following command:

For upgrading **from Ubuntu 14.04 to Ubuntu 16.04**:

```text
echo "deb https://apt.thousandeyes.com/ xenial main" > /etc/apt/sources.list.d/thousandeyes.list
```

When upgrading **from Ubuntu 16.04 to Ubuntu 18.04**, use this slightly modified command:

```text
echo "deb https://apt.thousandeyes.com/ bionic main" > /etc/apt/sources.list.d/thousandeyes.list
```

Updating the repository metadata should confirm your ThousandEyes APT repository is correctly configured on your updated Ubuntu system. To update the repository metadata, run the following command:

```text
sudo apt-get update
```

Now let's reinstall the ThousandEyes Enterprise Agent software: 

```text
sudo apt-get remove te-agent te-browserbot
sudo apt-get install te-agent te-browserbot
```

The first command above \(removal\) is not required when upgrading Ubuntu 14.04 to 16.04, but it is required when upgrading from 16.04 to 18.04.

Once reinstalled, start the relevant services and enable their boot-time startup as well:

```text
sudo systemctl start te-agent
sudo systemctl start te-browserbot

sudo systemctl enable te-agent
sudo systemctl enable te-browserbot
```

Check the agent and browserbot services are running using the following set of commands:

```text
sudo systemctl status te-agent
sudo systemctl status te-browserbot
```

Example output of status check command:

```text
$ sudo systemctl status te-agent
● te-agent.service - ThousandEyes Agent
   Loaded: loaded (/lib/systemd/system/te-agent.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-04-09 11:50:29 IST; 2min 42s ago
 Main PID: 1020 (te-agent)
    Tasks: 9
   Memory: 24.5M
      CPU: 380ms
   CGroup: /system.slice/te-agent.service
           └─1020 /usr/local/bin/te-agent -C /etc/te-agent.cfg

Apr 09 11:50:29 ubuntu-16-04-lts-xenial-te-package systemd[1]: Started ThousandEyes Agent.
```

If the output states the services are inactive run the following commands:

```text
systemctl start te-agent
systemctl start te-browserbot
```

  
The final check you need to do takes place in the [Cloud & Enterprise Agent &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) section of the web UI. Ensure the agent has contacted the platform and is showing the correct operating system version information, like this:

  
Appliance upgrade verification in web UI 

The important details to pay attention to are:

1. **Agent continuously checking in:** Once the upgrade is complete, the agent should be checking in with the platform roughly once every minute.
2. **Operating system version updated:** The `Ubuntu 16.04.x LTS` text should be displayed \(or 18.04 if you've already upgraded to Ubuntu Bionic - if you have, kudos to you for being proactive!\)
3. **Agent and BrowserBot versions up to date**: The upgrade process installs the latest available software versions. This section should not be showing any red text indicating obsolete software versions.

#### Free up disk space

 Optionally, you can check your free disk space and try to remove unused packages and/or old kernel images that are not needed any longer. To do so, run the following commands:

```text
# This will show you free disk space on each partition
$ sudo df -h

# This will remove all unneeded packages 
$ sudo apt-get autoremove --purge
```

## Related information

The following ThousandEyes Knowledge Base articles and external resources provide additional information on this topic:

* [Ubuntu Long-Term Support maintenance](https://wiki.ubuntu.com/Releases?_ga=1.43815013.1598322379.1485884951) is the official Ubuntu documentation for the past and present releases and their support life cycles.
* [Ubuntu upgrade documentation](https://help.ubuntu.com/community/Upgrades) is the official Ubuntu documentation about how to perform release upgrades.
* [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy) is where you can find information about all our supported agent operating systems.

## Further assistance

If you have an issue not listed here or need further help, [contact our ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

