# Uninstalling the Enterprise Agent \(Linux package\)

Customers may need to remove the Enterprise Agent software which was installed on a supported Linux operating system from the **te-agent** and \(optionally\) **te-browserbot** packages. Additionally, customers may optionally remove the configuration files created by the Agent. Customers may wish to keep the Agent configuration files if the reason for removal is to fix a broken Agent. Reinstalling Agent software with existing configuration files allows the Agent to resume running with the configuration of tests and other settings present prior to removing the Agent software.

This article describes the steps required to remove an Enterprise Agent from each of the supported Linux distributions.

## Ubuntu 14.04

1. Determine whether the **te-agent** and the **te-browserbot** services are running:

```text
$ service te-agent status
te-agent start/running, process 4686

$ service te-browserbot status 
te-browserbot start/running, process 4785
```

2. Stop the **te-agent** and the **te-browserbot** services:

```text
$ sudo service te-agent stop
te-agent stop/waiting

$ sudo service te-browserbot stop
te-browserbot stop/waiting
```

3. Purge the **te-agent** and the **te-browserbot** packages:

If you're planning to re-install the Agent software use "apt-get remove" instead of "apt-get purge". This will leave the necessary configuration files intact, so that once the Agent is re-installed, there is no need to re-assign tests to the Agent. 

```text
$ sudo apt-get purge te-agent 

$ sudo apt-get purge te-browserbot
```

4. Verify both packages have been removed:

```text
$ service te-agent status
te-agent: unrecognized service

$ service te-browserbot status
te-browserbot: unrecognized service
```

## Ubuntu 16.04 and 18.04

1. Check if the **te-agent** and the **te-browserbot** services are running:

```text
$ sudo systemctl status te-agent
● te-agent.service - ThousandEyes Agent
   Loaded: loaded (/lib/systemd/system/te-agent.service; enabled; vendor preset:
   Active: active (running) since Tue 2017-04-04 12:11:49 CDT; 2min 5s ago
 Main PID: 1052 (te-agent)
    Tasks: 24
   Memory: 29.0M
      CPU: 1.182s
   CGroup: /system.slice/te-agent.service
           └─1052 /usr/local/bin/te-agent -C /etc/te-agent.cfg

$ sudo service te-browserbot status
● te-browserbot.service - ThousandEyes BrowserBot
   Loaded: loaded (/lib/systemd/system/te-browserbot.service; enabled; vendor pr
   Active: active (running) since Tue 2017-04-04 12:12:16 CDT; 2min 17s ago
 Main PID: 1596 (java)
    Tasks: 90
   Memory: 162.0M
      CPU: 14.426s
   CGroup: /system.slice/te-browserbot.service
```

2. Stop the **te-agent** and the **te-browserbot** services:

```text
$ sudo systemctl stop te-agent
$ sudo systemctl status te-agent
● te-agent.service - ThousandEyes Agent
   Loaded: loaded (/lib/systemd/system/te-agent.service; enabled; vendor preset:
   Active: inactive (dead) since Tue 2017-04-04 12:16:29 CDT; 9s ago
  Process: 3632 ExecStart=/usr/local/bin/te-agent -C /etc/te-agent.cfg (code=kil
 Main PID: 3632 (code=killed, signal=TERM)

$ sudo systemctl stop te-browserbot
$ sudo systemctl status te-browserbot
● te-browserbot.service - ThousandEyes BrowserBot
   Loaded: loaded (/lib/systemd/system/te-browserbot.service; enabled; vendor pr
   Active: inactive (dead) since Tue 2017-04-04 12:17:03 CDT; 8s ago
  Process: 3696 ExecStart=/usr/bin/java -Djava.io.tmpdir=/var/lib/te-browserbot/
 Main PID: 3696 (code=exited, status=143)
```

3. Purge the **te-agent** and the **te-browserbot** packages:

If you're planning to re-install the Agent software use "apt-get remove" instead of "apt-get purge". This will leave the necessary configuration files intact, so that once the Agent is re-installed, there is no need to re-assign tests to the Agent. 

```text
$ sudo apt-get purge te-agent
Removing te-agent (1.9.1-1~xenial) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.
Purging configuration files for te-agent (1.9.1-1~xenial) ...
Updating certificates in /etc/ssl/certs...
0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

done.
done.


$ sudo apt-get purge te-browserbot
(Reading database ... 68880 files and directories currently installed.)
Removing te-browserbot (1.38-1~xenial) ...
Removing user `browserbot' ...
Warning: group `browserbot' has no more members.
Done.
```

4. Verify both packages have been removed:

```text
$ sudo systemctl status te-agent
● te-agent.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead) since Tue 2017-04-04 12:16:29 CDT; 7min ago
 Main PID: 3632 (code=killed, signal=TERM)

$ sudo systemctl status te-browserbot
● te-browserbot.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead) since Tue 2017-04-04 12:17:03 CDT; 7min ago
 Main PID: 3696 (code=exited, status=143)
```

## RHEL/CentOS/Oracle Linux 6.x

1. Check if the **te-agent** and the **te-browserbot** services are running:

```text
$ status te-agent
te-agent start/running, process 17228

$ status te-browserbot
te-browserbot start/running, process 17214
```

2. Stop the **te-agent** and the **te-browserbot** services:

```text
$ sudo stop te-agent
te-agent stop/waiting

$ sudo stop te-browserbot
te-browserbot stop/waiting
```

3. Remove the **te-agent** and the **te-browserbot** services:

For those who wish to remove dependencies, use _yum erase_ instead of _yum remove:_

```text
$ sudo yum remove te-agent

$ sudo yum remove te-browserbot
```

4. Verify the **te-agent** and the **te-browserbot** services have been removed:

```text
$ status te-agent
status: Unknown job: te-agent

$ status te-browserbot
status: Unknown job: te-browserbot
```

## RHEL/CentOS/Oracle Linux 7.x

1. Check if the **te-agent** and the t**e-browserbot** services are running:

```text
$ sudo systemctl status te-agent
● te-agent.service - ThousandEyes Agent
   Loaded: loaded (/usr/lib/systemd/system/te-agent.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2017-03-30 11:31:35 EDT; 7s ago

$ sudo systemctl status te-browserbot
● te-browserbot.service - ThousandEyes BrowserBot
   Loaded: loaded (/usr/lib/systemd/system/te-browserbot.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2017-03-30 11:31:41 EDT; 5s ago
```

2. Stop the **te-agent** and the **te-browserbot** services:

```text
$ sudo systemctl stop te-agent
$ sudo systemctl status te-agent
● te-agent.service - ThousandEyes Agent
   Loaded: loaded (/usr/lib/systemd/system/te-agent.service; enabled; vendor preset: disabled)
   Active: inactive (dead) since Thu 2017-03-30 11:25:12 EDT; 4min 46s ago

$ sudo systemctl stop te-browserbot
$ sudo systemctl status te-browserbot
● te-browserbot.service - ThousandEyes BrowserBot
   Loaded: loaded (/usr/lib/systemd/system/te-browserbot.service; enabled; vendor preset: disabled)
   Active: inactive (dead) since Thu 2017-03-30 11:28:25 EDT; 1min 40s ago
```

3. Remove the **te-agent** and the **te-browserbot** services:

For those who wish to remove dependencies, use _yum erase_ instead of _yum remove._

```text
$ sudo yum remove te-agent
Removed:
  te-agent.x86_64 0:1.9.0-1

$ sudo yum remove te-browserbot
Removed:
  te-browserbot.x86_64 0:1.38-1
```

4. Verify the **te-agent** and the **te-browserbot** have been removed:

```text
$ systemctl status te-agent
Unit te-agent.service could not be found.

$ systemctl status te-browserbot
Unit te-browserbot.service could not be found.
```

## **Delete the Agent from the ThousandEyes platform**

If you have removed this Agent with the expectation of replacing it, please see the Knowledge Base article [Replacing an Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0_Replacing-an-Enterprise-Agent).

If you do not plan to replace the Agent you should remove the Agent from the ThousandEyes platform. From the Agent Settings page, expand the Agent row, then click the "More Actions" icon and select "Delete".

**NOTE:** Deleting an Agent will remove the Agent from any tests to which it was assigned, and any tests that have no other Agents assigned will be disabled.

