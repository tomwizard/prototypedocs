# Install the Enterprise Agent with BrowserBot on Oracle Linux Server 7

#### Install the Enterprise Agent with BrowserBot on Oracle Linux Server 7

By default, the Linux package installation of the Enterprise Agent on [supported version of Oracle Linux Operating System](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) will show a [warning]() due to missing dependency packages for [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-the-BrowserBot-1472236191200) component. The following step by step guide will enable the repository holding the Enterprise Agent dependency packages, before attempting to run the Enterprise Agent installation script.

* [Installation]()
  * [Step 1: Download Oracle Linux media]()
  * [Step 2: Install Oracle Linux 7]()
  * [Step 3: Enable optional repository]()
  * [Step 4: Install ThousandEyes Enterprise Agent]()
* [Troubleshooting the installation]()
  * [Default ThousandEyes Linux package installation log]()
  * [Verify repositories]()

## Installation

All the commands below should be run as root. To reduce the content repetition, all "sudo" command prefixes have been removed and the whole guide assumes that you are running each command in a root shell.

To reach the root shell, use the following command:

```text
$ sudo -s
```

The **expected output** is marked with **bold characters** on every sample command output below.

### Step 1: Download the Oracle Linux Release 7 Update for x86 \(64 bit\) from the Oracle web site

You need to register with Oracle or use an existing Oracle account to download the installation media from the [Oracle Software Delivery Cloud](https://edelivery.oracle.com/linux).

### Step 2: Install the Oracle Linux 7 Operating System

 Proceed with a [basic installation](https://oracle-base.com/articles/linux/oracle-linux-7-installation). In software selection, we recommend you proceed with the default **Minimal Install** under **Base Environment**.

### Step 3: Enable the Oracle Optional repository \(user either yum-config-manager or manually\)

#### 3.1 With yum-config-manager

```text
# yum install yum-utils -y
# yum-config-manager --enable ol7_optional_latest
```

#### 3.2 Manually

```text
# vi /etc/yum.repos.d/public-yum-ol7.repo
```

Use your preferred text editor to replace **enabled=0** with **enabled=1** on the section below, then save and exit the file.

```text
[ol7_optional_latest]
name=Oracle Linux $releasever Optional Latest ($basearch)
baseurl=https://yum.oracle.com/repo/OracleLinux/OL7/optional/latest/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=1
enabled=1
```

### Step 4: Install ThousandEyes Enterprise Agent

Complete the Linux package installation by following this article: [Enterprise Agent deployment using Linux Package method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS)

## Troubleshooting the installation

The install\_thousandeyes.sh script, used with `-b` switch for installing BrowserBot, will display the warning:

```text
  Installing ThousandEyes' BrowserBot (Package required for Page Load and Transaction tests)    [ WARNING ]
    (Failed installing ThousandEyes' BrowserBot)
Starting ThousandEyes
  Starting ThousandEyes' BrowserBot                                                             [ WARNING ]
    (Failed starting ThousandEyes' BrowserBot)

```

* 
### Default ThousandEyes Linux package installation log

 Look for errors in the default installation log.

```text
# cat /tmp/install_thousandeyes*.log
```

Sample output errors:

```text
...
yum -y -q install te-browserbot
Error: Package: te-browserbot-1.84.2-1.x86_64 (thousandeyes)
           Requires: xorg-x11-server-Xvfb
 You could try using --skip-broken to work around the problem
 You could try running: rpm -Va --nofiles --nodigest

systemctl start te-browserbot
Failed to start te-browserbot.service: Unit not found.

```

### Verify repositories

```text
# yum repolist enabled
```

```text
Loaded plugins: ulninfo
repo id                                    repo name                                                                                                     status
ol7_UEKR4/x86_64                           Latest Unbreakable Enterprise Kernel Release 4 for Oracle Linux 7Server (x86_64) - enabled by default            110
ol7_latest/x86_64                          Oracle Linux 7Server Latest (x86_64) - required, enabled by default                                           12,501
ol7_optional_latest/x86_64                 Oracle Linux 7Server Optional Latest (x86_64) - required, manually enabled at Step 3                           9,608
thousandeyes                               ThousandEyes - required, enabled by the install_thousandeyes.sh script                                            72
repolist: 22,291
```

