# End-of-Life announcement for Precise-based Virtual Appliances

The original ThousandEyes Virtual Appliance \(VA\) was built on Ubuntu 12.04 LTS \(Ubuntu codename “Precise”\) which reaches [End of Life by Canonical](https://wiki.ubuntu.com/Releases) in April of 2017. Canonical will no longer be publishing security updates or other critical fixes.  As noted in our [Release Update for March 2nd, 2017](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnwuCAC), with Canonical's support for Precise ending, ThousandEyes is ending support for Precise-based Virtual Appliances on June 30th, 2017.   Prior to June 30th, the ThousandEyes Customer Success team will be reaching out to the primary contacts of customers with existing Precise-based Virtual Appliances to discuss approaches for retiring these VA's.

## Existing Installations

On July 7th, 2017, all Precise-based Virtual Appliances will automatically be disabled.

Customers with existing Precise-based Virtual Appliances will need to replace the Virtual Appliances--the normal automatic update feature for Virtual Appliances cannot upgrade the operating system to a newer version of Ubuntu.   Because organizations may have limits or may be billed for overages to their contracted number of concurrently active Enterprise Agents, we strongly encourage our customers either to use the Enterprise Agent replacement process in the ThousandEyes Knowledge Base article [Replacing an Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0), or to work with the ThousandEyes [Customer Success team](mailto:support@thousandeyes.com?subject=Precise-based%20Virtual%20Appliance%20replacement).

## New Installations

As noted in our [Release Update for March 15th, 2017](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnylCAC), we introduced a feature that will prevent any new Virtual Appliances from registering in the ThousandEyes platform if installed using a virtual machine image based on Precise.  If a Precise-based Virtual Appliance attempts to register, the Agent's log file, /etc/te-agent.log, will contain a message similar to:

```text
2017-03-13 19:45:00.761 FATAL [b6adc740] [te] {} The agent's operating system is no longer supported. Please contact support@thousandeyes.com for assistance.
```

​Customers who see this message will need to reinstall the Virtual Appliance, using a virtual machine image from the ThousandEyes download link that is relevant to your hypervisor platform.  The download links are available from the **+ Add New Agent** section of the [Enterprise Agents page](https://app.thousandeyes.com/settings/agents/enterprise/). We encourage customers to delete .ova or .zip files used to install Precise-based virtual machine images.

## Future Virtual Appliance End-of-Life

Current Virtual Appliance images are now built to be upgradable, should a Virtual Appliance be in operation when the 14.04 LTS Ubuntu operating system, Trusty, reaches end-of-life per Canonical.

