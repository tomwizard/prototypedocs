# Enterprise Agent support lifecycle policy

In order to ensure proper and consistent data collection, ThousandEyes Enterprise Agents require up-to-date Agent software, running on a fully supported operating system. As operating system providers end support for versions of their operating systems, ThousandEyes will reduce or end support for Enterprise Agents on those operating systems.

This article describes the stages of the ThousandEyes lifecycle of support for Enterprise Agent software and operating systems, relevant operating system provider lifecycle dates, and the notification mechanisms ThousandEyes provides to users.

## Support for Enterprise Agent software

ThousandEyes provides technical support and software updates for issues found in versions of Enterprise Agent software issued within six months of the most recent release date of Agent software. To obtain fixes for Enterprise Agent software, customers must upgrade to the most recent version of Enterprise Agent software. Enterprise Agents normally perform software updates automatically when ThousandEyes makes an update available.

## Support for Operating Systems

Enterprise Agents run on the Ubuntu Linux distribution, and on the Red Hat Enterprise Linux distribution \(along with the CentOS and Oracle Linux variations of Red Hat Enterprise Linux\). ThousandEyes bases support on the currently supported Ubuntu Linux versions designated as Long Term Support \(LTS\) versions and  Red Hat Enterprise Linux versions currently in Full Support Phase or in the subsequent Extended Update Support \(EUS\) period. The ThousandEyes support lifecycle contains three dates which are based on the date an Ubuntu LTS or Red Hat version reaches the end of LTS or EUS, respectively.

### End of Installation Support

The End of Installation Support \(EIS\) occurs when ThousandEyes removes the ability to install Enterprise Agents on a version of an operating system. This date occurs three months prior to the End of Support date.

### End of Support

The End of Support \(EoS\) occurs when ThousandEyes will no longer provide technical support nor guarantee software updates \(including bug fixes\) for customers running Enterprise Agents on the affected version of an operating system. Agents will continue to commit test data to the ThousandEyes platform.

The ThousandEyes End of Support date is the same as the date an Ubuntu LTS or Red Hat version reaches the end of LTS or EUS, respectively. More information about these dates can be found at the following locations:

* [Ubuntu Releases](https://wiki.ubuntu.com/Releases)
* [Red Hat Enterprise Linux Life Cycle](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase)

### End of Life

The End of Life \(EoL\) occurs 60 days after the End of Support. Agents will not be able to commit test data to the ThousandEyes platform. When an operating system version reaches End of Life, ThousandEyes reserves the right to remotely terminate the Enterprise Agent software running on the affected version of an operating system, due to security risks arising from the end of availability of security fixes.

### Example operating system support lifecycle

The following example uses Ubuntu Linux version 14.04 LTS to illustrate the ThousandEyes lifecycle. Ubuntu will end operating system support for version 14.04 LTS at the end of April, 2019. The diagram below illustrates the three phases of the ThousandEyes lifecycle.  
 

## Notifications

Notification of Enterprise Agents which have reached a lifecycle date may be provided by a warning message displayed on the Agent's entry in the [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) of the ThousandEyes application. Additionally, an Agent's log file \(te-agent.log, normally in the /var/log directory\) may contain log messages indicating that the Agent has reached a lifecycle date.

Approaching lifecycle dates are announced in the Release Updates documents which accompany ThousandEyes software releases. Software releases typically occur every other week. Notification of an approaching date will appear in at least one Release Update, typically at least a month in advance of the announced date. To receive an email copy of each Release Update, review the "Subscribing to email notifications" section of the ThousandEyes Knowledge Base article [Notification of upgrades, maintenance and outages](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmUKAS_Notification-of-upgrades-and-maintenance-1472235324995).

## Additional information

The list of currently supported operating systems and lifecycle dates can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems).

ThousandEyes reserves the right to modify this policy at our discretion.

