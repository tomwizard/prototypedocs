# Release Notes: 2018-05-09

Welcome to tonight's release!

May is an exciting time for graduating students and proud parents. Congratulations to the class of 2018 and those who got them through their education. We wish you luck in your new endeavors.

Some new and educational articles on the ThousandEyes blog: Senior Product Marketing Manager Angelique Medina gives us the scoop on monitoring Salesforce.com instances. Don't pick your instance until you've read her post, [Monitoring Salesforce](https://blog.thousandeyes.com/monitoring-salesforce/)! Senior Product Marketing Manager Archana Kesavan gives us a lesson on monitoring content delivery networks, using a recent outage in one major CDN provider. Details available in [Network Monitoring to Measure CDN Performance](https://blog.thousandeyes.com/network-monitoring-measure-cdn-performance/). A tip of the cap and gown to the Product Marketing team for schooling us!

On to the release details!

## Cloud Agents

We're pleased to welcome another broadband ISP Cloud Agent. This one's in Seattle, on the Charter network.

Also, due to issues with the service provider for the [San Po Kong, Hong Kong Cloud Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q0gECAS), we've switched providers and locations. The new location \(just down the road\) and Agent name is Kwai Chung, Hong Kong. Tests previously assigned to San Po Kong were automatically migrated to Kwai Chung. Customers who have Alert Rules configured for Path Trace may wish to ensure that the changes to the network path do not interfere with their Alert Rules.

## SAML metadata for Single Sign-On

For customers using single sign-on to access the ThousandEyes application, we now provide ThousandEyes' service provider SAML metadata via an XML file. This XML data allows for fast and easy configuration of ThousandEyes in a customer's identity provider. The metadata is accessible from [https://app.thousandeyes.com/saml-metadata](https://app.thousandeyes.com/saml-metadata).

## HTTP Server view

An HTTP Server test or the HTTP Server view of a Page Load test now provides an Advanced Setting to select the version of HTTP:

IMAGE MISSING

The default setting is to prefer HTTP 2.0, and then fall back to HTTP 1.1. Users can select HTTP 1.1 for certain compatibility issues raised in HTTP 2.0, such as handling of client certificate authentication for sub-resources in a single domain.

## Enterprise Agent Settings page

We now provide filters on the Enterprise Agent's Settings page. Filters include Agent Name, Hostname, Cluster, IP Address, IPv6 policy, Label and Location. If multiple filters are applied, a logical AND is applied to the filters. Filters are affected by the **Show agents not assigned to this account group** checkbox.

IMAGE MISSING

The above example shows the Location filter, which uses the value in the **Region/City** field in each Enterprise Agent's listing.

## Alert Rules

Previously, BGP Alert Rules could only alert on prefixes with a length between /16-/32 \(IPv4\) and /32-/128 \(IPv6\), which was not user selectable. We now allow a user to alert on a wider range of prefix lengths, using the new **Prefix Length** setting:

IMAGE MISSING

The default settings are to apply the Alert Rule to lengths between /16-/32 \(IPv4\) and /32-/128 \(IPv6\).

## Reports

Reports widgets now permit time ranges to be specified in minutes, in addition to days and hours, when using the **Fixed Time Span** option on a widget:

IMAGE MISSING

The minimum interval of time is 5 minutes.

Also, the **Custom Time Range** field of a report is now read-only.

IMAGE MISSING

The value of the field reflects the range specified by clicking on the calendar icon in the field, and using the calendar or the **From** and **To** fields to specify date and  time. 

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* When using Endpoint Agent with Internet Explorer and Cisco AnyConnect VPN client, a Command window no longer appears
* Snapshot generation for Endpoint Data now handles the edge case of selecting the latest round of data in the timeline.
* Fixed an issue in the Reports' custom time selector which made some dates not selectable.
* Fixed an issue in the Reports' custom time selector which could cause selection of dates to display the following day and month.
* Fixed an issue in the Reports' custom time selector which would display different times in the **Custom Time Range** field than what was selected on the calendar. 
* An HTTP Server test now sends an "Accept-Encoding: deflate, gzip" header.

## Memorial Day support hours

The Customer Success team will be providing email-only support during the US holiday of Memorial Day between the following hours:

| Time Zone | Date/Hours |
| :--- | :--- |
| GMT/UTC | May 28th, 15:00 to May 29th, 06:00 |
| US EDT | May 28th, 11:00 to May 29th, 02:00  |
| US PDT | May 28th, 08:00 to May 28th, 23:00  |

Live chat-based support will resume thereafter.

## Questions and comments

Have feedback or questions about tonight's release? Just graduated from college and want to [apply for a job](https://www.thousandeyes.com/careers)? [Send us an email](mailto:support@thousandeyes.com?subject=2018-05-09+Release+Update)\*!

\*Just kidding! Job applicants, please apply through our [Careers](https://www.thousandeyes.com/careers) page!

