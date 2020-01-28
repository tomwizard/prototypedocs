# End-of-Life announcement for Ubuntu Precise Linux package Enterprise Agents

Ubuntu version 12.04 LTS \(codename "Precise"\) has reached the end of its [maintenance updates period](https://www.ubuntu.com/info/release-end-of-life).  Per the **Agent operating system end of life policy** announcement in our [Release Update of April 26, 2017](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoAXCA0), ThousandEyes' support for Enterprise Agents installed on these operating systems will reach end of life with the first ThousandEyes release after June 30, 2017.

## Existing installations

After July 7th, 2017, Enterprise Agents running on this unsupported operating system will be automatically disabled.  Customers are encouraged to upgrade to a supported version of their operating system.  Supported operating system versions can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC).

We've also added an "Agents with Problems" notice to the platform to let you know that we've identified an Agent running on an end of life operating system.  Users will see this notice, indicated with a red triangle icon, in the Agent Settings page.  Mousing over the icon will display a tooltip with the notice that the "OS is at end of life".

IMAGE MISSING

Clicking the Agent icon in the top navigation bar IMAGE MISSING  will also display this information.

### Upgrading to supported versions

In most cases, customers can run:

```text
do-release-upgrade
```

to update to Ubuntu 14.04 LTS. Consult the Ubuntu documentation for full details.  To update to Ubuntu 16.04 LTS, repeat the process. Agent software should be automatically upgraded once the operating system upgrade is completed.

## New installations

After July 7th, 2017, when run on an end-of-life operating system, the ThousandEyes installation script install\_thousandeyes.sh will display an error message similar to:

```text
This machine's operating system is unsupported by ThousandEyes.  Refer to https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB1rCAG for more details.
```

## Future End-of-Life announcements

In the future, ThousandEyes will end support for Ubuntu versions in conjunction with the end of [Ubuntu Long-Term Support maintenance updates](https://wiki.ubuntu.com/Releases?_ga=1.43815013.1598322379.1485884951).

