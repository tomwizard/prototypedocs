# How to plan for Enterprise Agent Upgrades

#### How to plan for Enterprise Agent Upgrades

## Table of Contents

[Recent announcements for end of Operating System support]()  
[Identifying which Agents require upgrades]()  
[Obtaining a detailed list of Agents which require upgrades]()  
[Upgrade paths for specific systems]()

[Replacing Enterprise Agents]()  
[Requesting support consultations]()

## [Recent announcements for end of Operating System support]()

The following Operating Systems were announced as "End of Life" by their respective developers within the last year:

* [Red Hat Enterprise Linux / CentOS / Oracle Linux 6x](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK_End-of-Life-announcement-for-Red-Hat-Linux-package-Enterprise-Agents)
* [Red Hat Enterprise Linux / CentOS / Oracle Linux 7.1 to 7.3](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK_End-of-Life-announcement-for-Red-Hat-Linux-package-Enterprise-Agents)
* [Ubuntu 14.04](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqLfCAK_Release-Update-2019-01-08)

 While we have continued to offer extended support for agents running on these Operating Systems, ThousandEyes will no longer provide software updates for these agents starting on May 1st, 2019.

**End of Life agents will no longer be able to connect to our platform beginning July 1st, 2019.**

ThousandEyes Appliances \(both virtual and physical\) and Docker agents will receive a supported upgrade path. Linux package installations require that you replace or upgrade your system with a supported Operating System in compliance with your company's standards. 

## [Identifying which Agents require upgrades]()

You may identify which of your Agents are running on an unsupported Operating System from the [Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page.

 To access the Agent Settings page, select [Cloud & Enterprise Agents &gt; Agent Settings](http://app.thousandeyes.com/settings/agents/enterprise/?section=agents) within the left-hand navigation pane:

#### Identifying Agents

To identify agents requiring an upgrade:

**1.** A red triangle \(attention\) icon will be located next to the name of each agent which requires attention.

**2.** Hovering over an agent's attention icon will display a list of items to be addressed. Agent's requiring an upgrade will display the message "**Agent OS will soon be unsupported"**

#### **Basic Configuration**

When communicating with your team members which agents need to be updated, the following will be useful:

**3. Agent Name:** This is the name used by the ThousandEyes platform and may not match the hostname of the system running the Enterprise Agent

**4. Agent IP Addresses:** This includes both public and private IP addresses

**5. Agent Operating System:** This includes both distribution and version number

**6. Agent Installation Type:** This may be Linux Package, Docker, Physical Appliance, or Virtual Appliance  
 

#### Advanced Settings

The following will be useful for verifying Agent configuration post-upgrade:

**7.** **Target for Tests:** This may be either an IP Address or a domain name

**8. Proxy Settings:** An information icon will appear if your Agent is utilizing a Proxy

## [Obtaining a detailed list of Agents which require upgrades]()

ThousandEyes is conducting a customer outreach program between April 1st and July 1st 2019. Organizational Administrators will be contacted, via email, and provided a list of affected agents. Requests for detailed lists should be submitted to [support@thousandeyes.com]().

## [Upgrade paths for specific systems]()

### Linux Packages:

Customers who choose to install the ThousandEyes Enterprise Agent onto their own Linux system are responsible for system maintenance.

ThousandEyes has tested and documented the upgrade process for supported Linux distributions. The following information may be used as a general guideline for customers to reference when planning upgrades.

#### [Red Hat Enterprise Linux 6.x, CentOS 6.x]()

### [ThousandEyes Virtual Appliances]()

#### Ubuntu 14.04

ThousandEyes has provided an automated upgrade path for customers to update their Virtual Appliance. The upgrade process requires SSH access to the appliance.

[Complete instructions for upgrading a ThousandEyes Appliance are available here.](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGb4CAG_Upgrading-Ubuntu-14-04-Trusty-Tahr-based-ThousandEyes-Appliances)  
 

### [ThousandEyes Physical Appliances]()

#### Ubuntu 14.04

ThousandEyes has provided an automated upgrade path for customers who wish to update their Physical Appliance. This upgrade process requires SSH access to the appliance.

[Complete instructions for upgrading a ThousandEyes Appliance are available here.](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGb4CAG_Upgrading-Ubuntu-14-04-Trusty-Tahr-based-ThousandEyes-Appliances)  
 

### [Docker Enterprise Agents]()

#### Ubuntu 14.04

The current Docker container is built using the base Ubuntu 18.04 container image. When a replacement Enterprise Agent container is deployed using the same volumes as the original Enterprise Agent container, the platform will not distinguish between the original and new containers. 

[Complete instructions for upgrading a ThousandEyes Docker container are available here.](https://support.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52KSAS_Upgrading-Docker-Enterprise-Agents)  
 

## [Replacing Enterprise Agents]()

### ThousandEyes Enterprise Agents may be replaced using two different methods

### **Agent Clustering Method**

This method consists of deploying a new agent, clustering together the new agent with the old one, and then deleting the old agent from the cluster. The act of clustering transfers test associations and Agent characteristics. 

**Customers using the metered billing model are not advised to use this method.** This method creates a new Agent ID, and units consumed by the original Agent will not be applied to the new Agent's maximum number of billed units. 

[Complete instructions for replacing Enterprise Agents the Agent clustering method are available here.](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0_Replacing-an-Agent)

### **Transferring Agent Identity Files**

During the installation of a replacement Enterprise Agent, identity files from an existing Enterprise Agent are transferred to the replacement system. The platform will make no distinction between the original Agent and the replacement Agent.

**Customers using the metered billing model are advised to use this method.** This method does not create a new Agent ID, and the existing monthly unit consumption will be applied to the agent's maximum number of billed units. 

[Complete instructions for replacing Enterprise Agents using Agent identity files are available here.](https://support.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ASAS_Replacing-an-Enterprise-Agent-using-Agent-Identity-Files)

## [Requesting support consultations]()

Some customers may use the upgrade process as an opportunity to consider new Agent deployment options, such as replacing Virtual Machines with containers. ThousandEyes Customer Success is available via our [in-application chat function](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes), or via email at [support@thousandeyes.com]()[,](mailto:support@thousandeyes.com) to answer any questions that you may have. 

