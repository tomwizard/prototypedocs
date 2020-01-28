# End-of-Life announcement for Red Hat Linux package Enterprise Agents: versions 6.3 - 6.6 and 7.0 and

Red Hat Enterprise Linux \(RHEL\) versions 6.3 through 6.6 and for 7.0 and 7.1 have reached the end of [Red Hat's Extended Update Support](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase) period.  Per the **Agent operating system end of life policy** announcement in our [Release Update of April 26, 2017](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoAXCA0), ThousandEyes' support for Enterprise Agents installed on these operating systems will reach end of life with the first ThousandEyes release after June 30, 2017.  Similarly, Agents running on the same versions of CentOS and Oracle Linux will no longer be supported.

## Existing installations

After ThousandEyes' support reaches end of life, enabled Enterprise Agents running on the unsupported operating systems may cease to function in the future without notice. Customers are encouraged to upgrade to a supported version of their operating system.  Supported operating system versions can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC).

We've also added an "Agents with Problems" notice to the platform to let you know that we've identified an Agent running on an end of life operating system.  Users will see this in the Agent Settings page, as well as when clicking the Agent icon in the top navigation bar.

### Upgrading to supported versions

In most cases, customers can simply run

```text
yum update -y
```

to update Red Hat-based systems to the latest minor revision which is supported under the Red Hat Extended Update Support program.

## New installations

After July 7th, 2017, when run on an end-of-life operating system, the ThousandEyes installation script install\_thousandeyes.sh will display an error message similar to:

```text
This machine's operating system is unsupported by ThousandEyes.  Refer to https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK for more details.
```

## Future End-of-Life announcements

In the future, ThousandEyes will end support for Red Hat Enterprise Linux, CentOS and Oracle Linux versions in conjunction with the end of [Extended Update Support](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase).

