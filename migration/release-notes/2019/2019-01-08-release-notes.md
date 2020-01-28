# Release Notes: 2019-01-08

Welcome to today's release! Our first release of 2019; we'll try not to break any resolutions...

IMAGE MISSING 

[Registration is open](https://www.thousandeyes.com/events/connect/atlanta-2019) for the next ThousandEyes Connect in Atlanta on January 15th! Check out the guest speakers, who'll be telling us how their companies use ThousandEyes. Take a day trip to Atlanta and come connect with the ThousandEyes community!

In news of the ThousandEyes blog...

We have our first major outage story of 2019. Our Technical Marketing Manager, Ameet Naik, discusses the recent Century Link outage--what we know about this outage, and how to limit an organization's exposure to such events. Check out his post [CenturyLink Outage: Lessons in Managing Internet Risks](https://blog.thousandeyes.com/centurylink-outage-lessons-managing-internet-risks/) for the full scoop.

Angelique Medina, our Senior Product Marketing Manager, has a great checklist for organizations who are deciding on how to provide DNS services to their users, in her post [Choosing a Public DNS Resolver](https://blog.thousandeyes.com/choosing-public-dns-resolver/). Performance isn't the only consideration; privacy and security also come into the decision-making process, as Angelique explains.

And now for the release details...

## Mandatory TLS access for Appliances

As of the next software release on January 22nd, 2019, web access for management of Virtual Appliances and Physical Appliances will require a secure SSL/TLS browser connection \(i.e. encrypted connection on port 443/TCP using an https:// URL\). After the release, connections to the unencrypted http:// URL will be redirected to the secure URL. Note that by default the secure connection uses a self-signed certificate, which will cause standard browsers to display security warnings. To avoid warnings, customers can create a certificate signing request \(if needed\) and upload a valid server certificate chain via the **SSL Settings** tab of the web management interface.

## Enterprise Agent end of lifecycle dates

A number of important dates have arrived or are approaching, in the support lifecycle of Enterprise Agents on some versions of Linux. For a full list of lifecycle dates, consult the ThousandEyes knowledge base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems). For general information on the stages of the support lifecycle for operating systems running ThousandEyes Enterprise Agents, review the ThousandEyes Knowledge Base article [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy).

### Ubuntu 14.04 LTS

Enterprise Agents installed on version 14.04 LTS \(a.k.a. "Trusty Tahr"\) of Ubuntu Linux will soon begin the end of their lifecycle \(this includes Trusty-based Virtual Appliances\). Please note the following dates:

* End of Installation Support: January 31st, 2019
* End of Support: April, 30th, 2019
* End of Life: June 30th, 2019

ThousandEyes will be notifying to customers with Trusty-based Virtual Appliances. Customers with Enterprise Agents installed via the Linux package can identify Ubuntu 14-based Agents from the Enterprise Agents Settings page, per the instructions below.

### Red Hat Enterprise Linux / CentOS / Oracle Linux

Enterprise Agents installed on all minor versions of major version 6 of Red Hat Enterprise Linux, CentOS and Oracle Linux have reached the End of Support, per the [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems). Additionally, version 7.3 has reached the End of Support.

Customers with Enterprise Agents installed via the Linux package can identify Red Hat-based Agents \(or the CentOS or Oracle Linux variants\) from the Enterprise Agents Settings page, per the instructions below.

### Identifying end-of-lifecycle Agents

To identify Enterprise Agents running on a particular version of Linux \(including Enterprise Agents which are part of a cluster\), navigate to the [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents), then add **OS Version** to the Current Filter, and enter a text string appropriate for the version of Linux desired. For example, the filter below displays all Ubuntu 14-based Agents:

IMAGE MISSING

Users with permission to view Enterprise Agents in all of an organization's Account Groups can set the **Account Group** filter to "All" to view a complete list of matching Agents within their organization.

## Enterprise Agents

#### New Edit Test bulk action

Under the **Edit** button on the Enterprise Agents Settings page, we've added a new bulk action: Edit Tests. This action can be used to assign or remove tests across multiple Agents. Saves a lot of clicks!

IMAGE MISSING

Swipe up or down to scroll through the list of tests or access the slider.

## Endpoint Agents

Under the Endpoint Agents' Network Access view, we've changed the timeline of the Network Topology layer. Previously, the timeline displayed the number of network probes sent to targets of the probes, such as DNS servers, proxies, access points, etc. Now we display the number of Agents sending probes, to match the Wireless layer.

IMAGE MISSING

## Reports

#### Download report data in CSV format

Users can now download report data to a comma-separated value \(CSV\) file. To download report data, click the **Download** link of the report, and choose "Download as CSV".

#### Access test views from a Color Grid widget

When a widget's **Cards** setting is "Test", users can now click on cards within a Color Grid widget to be taken to the associated test view.

#### Transaction Steps filter

In addition to being able to filter data in a report by Test, Test Label, Agent and Agent Label, we've added a Transaction Steps filter. For widgets which can set the **Metric** to "Web - Transactions / Transaction Step Time" the **Filter** selector will provide a "Transaction Steps" option. The data can be filtered by one or more Transaction tests' steps, making possible comparisons between steps in different tests, for example. 

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Fixed an issue that split charts in the PDF versions of reports
* Fixed an issue which could cause SSL and FTP timings to be negative
* Fixed an issue displaying "No Group" in a Color Grid widget when grouping cards by Test Labels

## Questions and comments

 Got feedback for us? Have a suggestion for 2020's New Year's resolutions? [Send us an email](mailto:support@thousandeyes.com?subject=2019-01-08+Release+Update)!

