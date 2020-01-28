# Enterprise Agent deployment using Linux Package method

The ThousandEyes Enterprise Agent can be deployed on a variety of Linux distributions such as Ubuntu, RedHat Enterprise Linux \(RHEL\), and CentOS. Supported operating systems can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC).

For Linux distributions not on this list, you may be able to install [Docker](https://www.docker.com/) and the Enterprise Agent Docker container. For more details, please refer to the Knowledge Base article [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS).

## Installation 

 Log in to the Linux system on which you will install the ThousandEyes Enterprise Agent.  Log in either as the root user, or a user which has been granted “sudo” access to the necessary package management and other commands required for the installation.  Then log into the ThousandEyes application and follow the steps found under **Agents &gt; Enterprise Agents &gt; +Add New Agent &gt; Linux Package**, explained in detail below.

The first step downloads the installation script from ThousandEyes:

```text
curl -Os https://downloads.thousandeyes.com/agent/install_thousandeyes.sh
```

The second command enables execute permission for the installation script:

```text
chmod +x install_thousandeyes.sh
```

The third command runs the script:

```text
sudo ./install_thousandeyes.sh -b <Account Group Installation Token>
```

**Notes**

* The -b flag can be removed if BrowserBot is not wanted or if your subscription is "Standard" \(no BrowserBot license\). For more details, please refer to: [What is the BrowserBot?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC)
* The Account Group Installation Token identifies the Agent as belonging to a specific Account Group and can be found under **Agents &gt; Enterprise Agents &gt; +Add New Agent &gt;** **Show Account Group Token for Installation**.
* If there are multiple Account Groups in your organization you will need to copy the token from the Account Group context in which you wish the Agent to be first seen. An Agent can be shared between groups. Additional information could be found here: [Working with Agent settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmsKAC).
* If multiple IP addresses are detected on the system, you will be prompted to choose the appropriate one during installation. 

###  Advanced Options

 To display the advanced options when installing the Agent use either -h or --help flags.

```text
$ ./install_thousandeyes.sh --help
Usage: ./install_thousandeyes.sh [-b [-F] [-L]] [-f] [-h] [-I INSTALL_LOG] [-l LOG_PATH] [-t PROXY_TYPE -P PROXY_LOCATION [-U PROXY_USER -u PROXY_PASS]] [-r REPO] [-s] ACCOUNT_TOKEN
  -b                  Also install BrowserBot, an agent component that collects
                      Page Load and Transaction test data using an instance
                      of the Chromium browser
  -F                  Also install Adobe Flash for BrowserBot (requires -b)
  -L                  Also install international language packages for BrowserBot (requires -b)
  -f                  Force batch mode
  -h                  Print this message
  -I INSTALL_LOG      Set the install log location to INSTALL_LOG
  -l LOG_PATH         Set the log path to LOG_PATH
  -t PROXY_TYPE       Set the proxy type: DIRECT (default, no proxy), STATIC, or PAC
  -P PROXY_LOCATION   Set the proxy location, format depends on PROXY_TYPE
                      DIRECT
                        PROXY_LOCATION is an invalid option for DIRECT
                      STATIC
                        host:port for hostname or IPv4 address
                        [IPv6 IP]:port for IPv6 address
                      PAC
                        URL where PAC file can be found
  -U PROXY_USER       Set the proxy user to PROXY_USER
  -u PROXY_PASS       Set the proxy password to PROXY_PASS
  -r REPO             Force the installer to install from REPO (overriding original ones)
  -s                  Skip the repository creation
```

## Post-Installation

Once the installation completes, the Agent will start automatically. Normally, within a minute the Agent will appear under **Agents &gt; Enterprise Agents.** 

IMAGE MISSING

To avoid synchronization problems with the ThousandEyes collector it is strongly recommended that you install a Network Time Protocol \(NTP\) package. To download and install an NTP package issue the following commands on the Agents host machine:

#### Ubuntu

1. _sudo apt-get install ntp_  \(Download and install NTP service\)
2. _service ntp start_  \(Start the NTP service\)
3. _service ntp status_  \(View current status\)

 If you wish to use alternate NTP servers, edit /etc/ntp.conf:

```text
$ service ntp status
 * NTP server is running

$ cat /etc/ntp.conf
# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

# Specify one or more NTP servers.

# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See http://www.pool.ntp.org/join.html for
# more information.
server 0.ubuntu.pool.ntp.org
server 1.ubuntu.pool.ntp.org
server 2.ubuntu.pool.ntp.org
server 3.ubuntu.pool.ntp.org
```

**Red Hat Enterprise Linux or CentOS**

1. _yum install ntp_  \(Install the NTP service\)
2. systemctl start ntpd  \(Start the NTP service\)
3. systemctl enable ntpd  \(Enable NTP to start on reboots\)
4. systemctl status ntpd  \(Print the current status\)

If you wish to use alternate NTP servers, edit /etc/ntp.conf:

```text
$ systemctl status ntpd
● ntpd.service - Network Time Service
   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Wed 2017-03-01 16:23:16 EST; 15min ago
 Main PID: 12567 (ntpd)
   CGroup: /system.slice/ntpd.service
           └─12567 /usr/sbin/ntpd -u ntp:ntp -g

$ cat /etc/ntp.conf
# For more information about this file, see the man pages
# ntp.conf(5), ntp_acc(5), ntp_auth(5), ntp_clock(5), ntp_misc(5), ntp_mon(5).

# Use public servers from the pool.ntp.org project.
# Please consider joining the pool (http://www.pool.ntp.org/join.html).
server 0.centos.pool.ntp.org iburst
server 1.centos.pool.ntp.org iburst
server 2.centos.pool.ntp.org iburst
server 3.centos.pool.ntp.org iburst
```

We recommend you ensure the NTP service starts at boot time by restarting your system and verifying the ntpd process is automatically started.

