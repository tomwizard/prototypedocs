# Replacing an Enterprise Agent using Agent Identity Files

## **Table of contents**

## [Replacement overview]()

ThousandEyes Enterprise Agents can be replaced by using one of the following methods:

1. **Agent Clustering Method:** 

   This method consists of deploying a new agent, clustering together the new agent with the old one, and then deleting the old agent from the cluster. The act of clustering transfers test associations and Agent characteristics. Detailed instructions for this method are available in the following article: ****[**Replacing an Enterprise Agent using the Agent Clustering Method**](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0_Replacing-an-Agent)

    **Customers using the metered billing model are not advised to use this method.** This method creates a new Agent ID, and units consumed by the original Agent will not be applied to the new Agent's maximum number of billed units. 

2. **Transferring Agent Identity Files:** 

   During the installation of a replacement Enterprise Agent, identity files from an existing Enterprise Agent are transferred to the replacement system. The platform will make no distinction between the original Agent and the replacement Agent.

    **Customers using the metered billing model are advised to use this method.** This method does not create a new Agent ID, and the existing monthly unit consumption will be applied to the agent's maximum number of billed units. 

This document will demonstrate how to successfully transfer Enterprise Agent identity files from an existing to a newly deployed agent.  
 

## [Enterprise Agent identity files]()

The Enterprise Agent software package is installed as a service named `te-agent` onto a [supported Linux operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems). The following three files are used by the `te-agent` service during operation and must be transferred from the original Agent to the replacement Agent:

#### /etc/te-agent.cfg

* This is the agent's main configuration file and contains account group information, logging, and proxy settings
* During service start, `te-agent` reads this file and applies configuration settings
* This file is not unique to a specific agent and may be re-used to configure identical settings to multiple agents

#### /var/lib/te-agent/te-agent-config.sqlite

* This file contains the Agent ID, collector assignment, and current runtime configuration settings
* Information within this file is used to authenticate with the ThousandEyes platform
* **WARNING: This file is unique to the agent and must not be used by two agents at the same time. DO NOT copy this file to more than one replacement Agent.**

#### /var/lib/te-agent/te-agent.sqlite

* This file contains the not-yet-submitted test and device layer data
* **WARNING: This file is unique to the agent and must not be used by two agents at the same time. DO NOT copy this file to more than one replacement Agent.**

## [Obtaining identity files from the original Agent]()

### Disable the original Enterprise Agent using the ThousandEyes web application

Prior to obtaining Enterprise Agent identity files, it is recommended to temporarily disable the Enterprise Agent to be replaced:

Select [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) within the left-hand navigation pane

**1.** Review the list of active Enterprise Agents for the name of the Agent to be replaced  
**2.** Click the **options** button in the right-hand side of the Agent information row and select **Disable**  

### Stop and disable the original Enterprise Agent service

ThousandEyes service must be stopped on your original Agent before you may copy identity files. Disabling the service will prevent the decommissioned Agent from communicating with the ThousandEyes platform in the event that the VM is restarted. 

**Operating systems using systemd \(Ubuntu 16.04+, RHEL & CentOS 7+\):**

```text
$ sudo sytemctl stop te-agent.service
$ sudo systemctl disable te-agent.service
```

  
**RHEL 6 & CentOS 6:**

```text
$ sudo service te-agent stop
$ sudo chkconfig te-agent off
```

**Ubuntu 14.04:**

```text
$ sudo stop te-agent
$ sudo update-rc.d -f te-agent remove
```

### Copy Enterprise Agent identity files to a single directory 

Copy identity files to a single directory for ease of management:

```text
$ cd ~
$ sudo mkdir <directory_name>
$ sudo cp /var/lib/te-agent/*.sqlite ~/<directory_name>
$ sudo cp /etc/te-agent.cfg ~/<directory_name>
```

### Compress the directory containing your original Agent identity files 

Compress the directory containing copied identity files for ease of transfer 

```text
$ sudo zip -r <directory_name>.zip <directory_name>
```

### Delete the agent identity files from your original agent

While the original Identity files will be deleted when the VM is destroyed, it is always possible that the VM could be restarted prior to deletion. Removing these files safeguards from errors associated with two Agents connecting to the platform with the same Agent ID. 

```text
original-agent$ sudo rm /etc/te-agent.cfg
original-agent$ sudo rm /var/lib/te-agent/*.sqlite
```

## [Transferring identity files]()

### Use SCP to transfer files between Agents

From your new replacement Agent's terminal, you may use the following command to obtain files from your original Agent \(provided the original and the new Enterprise Agent can communicate with each other directly\):

```text
$ scp <user>@<original-agent-IP>:~/<directory_name>.zip ~
```

Alternatively, from your original Agent's terminal you may use the following command to transfer files to your replacement agent:

```text
$ scp ~/<directory_name>.zip <user>@<replacement-agent-IP>:~
```

**NOTE:** You only need to copy the .zip file once.

## [Installing a replacement Agent using transferred identity files]()

### Install the ThousandEyes repository

You will use the ThousandEyes repository to download and install Enterprise Agent services:

**Ubuntu:**

```text
$ sudo apt-get update
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository https://apt.thousandeyes.com/
```

**RHEL 7:**

```text
$ sudo yum-config-manager --add-repo https://yum.thousandeyes.com/RHEL/7/x86_64
```

  
**CentOS 7:**

```text
$ sudo yum-config-manager --add-repo https://yum.thousandeyes.com/CentOS/7/x86_64
```

###   Install the ThousandEyes repository GPG key

You must install the ThousandEyes repository GPG key in order to validate the authenticity of downloaded packages:

**Ubuntu:**

```text
$ sudo wget -q https://apt.thousandeyes.com/RPM-GPG-KEY-thousandeyes
```

**RHEL & CentOS 7:**

```text
$ sudo  rpm --import https://yum.thousandeyes.com/RPM-GPG-KEY-thousandeyes
```

###  Update your Operating System's package manager

Pulling the repository metadata verifies that the ThousandEyes repository and corresponding GPG key are properly installed:

**Ubuntu:**

```text
$ sudo apt-get update
```

**RHEL & CentOS 7:**

```text
$ sudo yum clean metadata
$ sudo yum updateinfo
```

### Install the ThousandEyes Enterprise Agent using your OS' package manager

The `te-agent` package and service are what constitutes the heart of an Enterprise Agent. The [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-the-BrowserBot-1472236191200) component \(the `te-browserbot` package and service\) is a component that performs browser-based tests.

**Ubuntu:**

```text
$ sudo apt-get install te-agent te-browserbot
```

  
**RHEL & CentOS 7:**

```text
 $ sudo yum install te-agent te-browserbot
```

### Decompress the original Agent identity files within your replacement system

Once decompressed, a directory with the same name as the directory from your original Agent will be available:

```text
$ unzip <directory_name>.zip
```

### Copy the Agent identity files to the target directories within your replacement system

Copy the agent identity files to their final location:

```text
$ sudo cp <directory_name>/*.sqlite /var/lib/te-agent
$ sudo cp <directory_name>/te-agent.cfg /etc
```

###  Start and enable Enterprise Agent services

Starting agent services will activate the ThousandEyes agent. Enabling a service ensures that it will start during system boot. To start and enable relevant services, execute the following commands:

```text
$ sudo systemctl start te-agent.service
$ sudo systemctl start te-browserbot.service
$ sudo systemctl enable te-agent.service
$ sudo systemctl enable te-browserbot.service
```

## [Verifying replacement]()

 Once your replacement agent has been brought online, you may re-enable your Agent within the ThousandEyes web application:

Select [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) within the left-hand navigation pane and:

**1.** Review the list of active Enterprise Agents for the name of the Agent that was replaced.  
**2.** Click the options button in the right-hand side of the Agent information row and select **Enable**.

  
Upon completion, review the **Advanced Settings** section to ensure that the Agent information is correct:

Select the **Advanced Settings** tab of your Enterprise Agent information pane:

**1.** Verify that your Enterprise Agent is checking into the platform regularly  
**2.** Verify that the IP address and listed Operating System are correct  
**3.** Review the proxy settings \(if applicable\) to verify that they are correct

## [Troubleshooting ]()

If you have any questions regarding the described agent replacement procedure or if you hit an obstacle while performing it, [reach out to the ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) and we'll help you out. 

