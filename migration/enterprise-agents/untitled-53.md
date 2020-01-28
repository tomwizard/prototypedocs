# What to do if te-agent stops running due to a VACUUM error

## What to do if te-agent stops running due to a VACUUM error

The ThousandEyes Enterprise Agent stores results of tests in a local database. When the agent checks in with the ThousandEyes collector, the contents of the database are uploaded to the collector, and the database is purged. In certain circumstances, the local copy of the database can become corrupted, due in large part to disk I/O errors associated with the filesystem storing the database. This phenomenon is documented at http://www.sqlite.org/howtocorrupt.html.

When database corruption occurs the Agent will stop, and an error message will be seen in /var/log/te-agent.log, similar to the following:

```text
2013-02-06 18:30:06.232 INFO  [te] - Agent version 0.12.1 starting.  Setting max core size to ...
2013-02-06 18:30:06.236 FATAL [te] - Unable to set up agent tables: Error executing "VACUUM", err=11. Please contact support@thousandeyes.com for assistance.
2013-02-06 18:30:06.237 ERROR [te] - Error updating agent status: Error preparing query UPDATE agent_status SET time = datetime('now'), status = 'Unable to set up agent tables: Error executing "VACUUM", err=11. Please contact support@thousandeyes.com for assistance.': err=1
```

As a result, the local database will be stopped and the Agent will be unable to operate. The Agent's status will be shown as "Offline" in the Agent Settings page, with a last contacted date of whenever the first VACUUM error occurred.

IMAGE MISSING

In order to resolve this, follow the instructions below, per the type of Enterprise Agent \(Linux package or Virtual Appliance\).

## Linux Package

**As root**, stop the te-agent process, then go to the /var/lib/te-agent/ directory and remove the te-agent.sqlite file, then restart the te-agent process. The commands to do this depend on your distribution of Linux:

  
**Ubuntu 14.04:**

```text
stop te-agent
cd /var/lib/te-agent
rm te-agent.sqlite
start te-agent
```

  
**Ubuntu 16.04, Red Hat Enterprise Linux 7, CentOS 7:**

```text
systemctl stop te-agent
cd /var/lib/te-agent
rm te-agent.sqlite
systemctl start te-agent
```

Alternative method when package "init-system-helpers" \(Ubuntu 16.04\) or "initscripts" \(RHEL 7, CentOS 7\) is installed:  
 

```text
service te-agent stop
cd /var/lib/te-agent
rm te-agent.sqlite
service te-agent start
```

  
**Red Hat Enterprise Linux 6, CentOS 6:**

```text
stop te-agent
cd /var/lib/te-agent
rm te-agent.sqlite
start te-agent
```

##  Virtual Appliance

Log into the Virtual Appliance web console and click on the Advanced Settings tab. Click the **Clear Result Cache** button and confirm.  
 

## Contacting ThousandEyes Support

If steps described above do not resolve the issue or if the issue keeps reoccurring, please contact ThousandEyes Customer Success Center using chat or support@thousandeyes.com email address.

