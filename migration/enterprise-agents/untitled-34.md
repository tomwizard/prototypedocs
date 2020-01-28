# End-of-Life announcement for Red Hat Linux package Enterprise Agents: versions 6.7, 7.2 and 7.3

ThousandEyes support policy for Red Hat-based Linux package Agents is based on Red Hat's [Extended Update Support](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase) \(EUS\) schedules. Red Hat Enterprise Linux \(RHEL\) versions 6.7, 7.2 and 7.3 will reach the end of Red Hat's Extended Update Support period on or before December 31st, 2018. Red Hat will end Extended Update Support for Red Hat version 6.7 on December 31st, 2018 \(Red Hat had previously announced July 31st, 2018, but subsequently moved back the date\). Red Hat will end Extended Update Support for Red Hat version 7.3 on November 30th, 2018.

Per the ThousandEyes Enterprise Agent operating system end-of-life announcement in our Release Update of [Release Update 2018-10-23](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CplcCAC_Release-Update-2018-10-23), ThousandEyes' support for Enterprise Agents installed on these operating systems will end after December 31st, 2018.

## Existing installations

After an Enterprise Agent reaches end of life, enabled Agents running on the unsupported operating systems may cease to function at any time in the future without notice. Customers are encouraged to upgrade to a supported version of their operating system. Supported operating system versions can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems).

Additionally, an "Agents with Problems" notice in the platform will let you know that we've identified an Agent running on an end-of-life operating system.  Users will see this message in the Agent Settings page, as well as from the Agent icon in the top navigation bar.

### Upgrading to supported versions

In most cases, customers can simply run

```text
yum update -y
```

to update Red Hat-based systems to the latest minor revision.

For users of version 6.7 or earlier versions, ThousandEyes strongly encourages customers to upgrade to the most recent Red Hat 7 version rather than a updating to the latest minor revision of version 6.x, as development by Red Hat on version 6 is limited and will likely have less development over time. Additionally, customers have limited options for new Agent creation, as ThousandEyes does not support [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker) on version 6.x of Red Hat, CentOS or Oracle Linux. Please [contact ThousandEyes Customer Success](mailto:support@thousandeyes.com?subject=Upgrading+Red+Hat+agents) if you need advice on managing the upgrade or replacement of your Agents. 

## New installations

After December 31st, 2018, when run on an end-of-life operating system, the ThousandEyes installation script install\_thousandeyes.sh will display an error message similar to:

```text
This machine's operating system is unsupported by ThousandEyes. Refer to https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK for more details.
```

## Future End-of-Life announcements

ThousandEyes will end support for Red Hat Enterprise Linux, CentOS and Oracle Linux versions in conjunction with the Red Hat [Extended Update Support](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase) schedule.

