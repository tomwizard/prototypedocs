# Release Notes: 2018-04-11

Welcome to tonight's release! We hope you had a great [Poisson d'Avril](https://en.wikipedia.org/wiki/April_Fools%27_Day#April_fish), [aprillipäivä](https://en.wikipedia.org/wiki/April_Fools%27_Day#Nordic_countries), [April Fool's Day](https://en.wikipedia.org/wiki/April_Fools%27_Day) or whatever you called your day of pranks, earlier this month.

No joke--our Technical Marketing Manager, Ameet Naik, has a great blog post for businesses considering migrating to Office 365 applications, or needing monitor Office 365 after migration. Entitled [Monitoring Office 365](https://blog.thousandeyes.com/monitoring-office-365/), Ameet delves into some details of Office 365's network architecture, the differences between some of the specific apps such as Exchange and Sharepoint, and explains how ThousandEyes can provide organizations with the benchmarks and network intelligence needed to ensure performance and availability of their critical applications.

Now for the details of tonight's release...

## Cloud Agents

### Japan

In our [Release Update 2018-01-31](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SSlCAM_Release-Update-2018-01-31), we announced the retirement of the Sapporo, Japan Cloud Agent due to provider issues. We're pleased to announce that not only is Sapporo back, but we've added an IPv6 Cloud Agent in the location as well. And we've added Sendai in Miyagi Prefecture and Kitakyushu in Fukuoka Prefecture. Domo arigatou gozaimasu, Japan!

### IaaS providers

 We're very excited to announce Cloud Agents in major Infrastructure-as-a-Service providers. We've added 15 Cloud Agents in each of Amazon Web Services \(AWS\) and Google Cloud Platform \(GCP\). Here's the list of locations for each:

| **Amazon Web Services** | **Google Cloud Platform** |
| :--- | :--- |
| Ashburn, VA \(AWS us-east-1\) | Ashburn, VA \(GCP us-east4\) |
| Columbus, OH \(AWS us-east-2\) | Changhua, Taiwan \(GCP asia-east1\) |
| Dalles, OR \(AWS us-west-2\) | Council Buffs, IA \(GCP us-central1\) |
| Dublin, Ireland \(AWS eu-west-1\) | Dalles, OR \(GCP us-west1\) |
| Frankfurt, Germany \(AWS eu-central-1\) | Eemshaven, Netherlands \(GCP europe-west4\) |
| London, England \(AWS eu-west-2\) | Frankfurt, Germany \(GCP europe-west3\) |
| Montreal, Canada \(AWS ca-central-1\) | London, England \(GCP europe-west2\) |
| Mumbai, India \(AWS ap-south-1\) | Moncks Corner, SC \(GCP us-east1\) |
| Paris, France \(AWS eu-west-3\) | Montreal, Canada \(GCP northamerica-northeast1\) |
| San Jose, CA \(AWS us-west-1\) | Mumbai, India \(GCP asia-south1\) |
| Seoul, South Korea \(AWS ap-northeast-2\) | Singapore \(GCP asia-southeast1\) |
| Singapore \(AWS ap-southeast-1\) | St Ghislain, Belgium \(GCP europe-west1\) |
| Sydney, Australia \(AWS ap-southeast-2\) | Sydney, Australia \(GCP australia-southeast1\) |
| São Paulo, Brazil \(AWS sa-east-1\) | São Paulo, Brazil \(GCP southamerica-east1\) |
| Tokyo, Japan \(AWS ap-northeast-1\) | Tokyo, Japan \(GCP asia-northeast1\) |

In the future, we will be adding Cloud Agents in China regions.

## Endpoint Agent

We're introducing pagination for the Path Visualization of the Network and Network Topology views. Pagination makes Path Visualizations much easier to read and much faster to load when large numbers of nodes are present. Instead of a single page to view all nodes, we now display groups of 8 nodes. More than 8 groups of nodes results in a new page of nodes. Pagination uses the **Grouping** setting, and can be used in conjunction with filters at the page and view levels. Filters will be applied across the pages of the paginated view.

IMAGE MISSING

When pagination occurs, the next page will be indicated at the bottom of the page with nodes labeled "Next sources" or "Next destinations" or both, as needed. The number of nodes not displayed on the current page is the number within the node. Clicking on a "Next" nodes displays the next page, either using sources or destinations, depending on which node was clicked. To return to the previous page, click on the "Previous sources" or "Previous destinations" nodes which appear at the top of the page.

## SAML Logout

For organizations using Single Sign-On, the app now supports logout when a user logs out of their identity provider's portal. For example, logging out of Okta will now immediately end a user's session in ThousandEyes.

## Agent to Agent test Throughput

Network Agent-Agent tests have a throughput measurement option for tests created between two Enterprise Agents. Checking the **Enable Througput** box will now incur a charge for Enterprise Agents using the metered billing model. The cost is proportional to the Duration setting of the Throughput measurement.

IMAGE MISSING

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* Fixed an issue causing HTTP Server test timing metrics to incorrectly add timings of redirects to the timing of the final request.
* Addressed an issue affecting HTTP Server tests when Basic Authentication credentials are specified as a Custom Header, and the test encounters a redirect to a different domain than the test target.
* Fixed an issue occurring when an Endpoint Agent had checked in but not collected data, potentially causing location information to be inaccurate.
* Fixed an issue preventing devices with duplicate MAC addresses from being discovered. This may result in some additional devices being discovered which were previously not discoverable.
* Fixed a "This field is required" error message when switching back to the default APT repository URL for a Virtual or Physical Appliance.
* Fixed an issue with Live Shares which could cause the Target Agent field to display "Unknown Agent".
* Creating a DNS Server test for a CNAME record no longer produces a spurious warning message.
* The Device Settings page has an improved user interface, featuring device icons.
* Warnings \(the red triangle icon with exclamation mark\) for devices are now shown in the Device Settings page.
* Display of Alerts has been simplified to show only metrics that contribute to the triggering or ending of the Alert Rule.
* Enterprise Agents configured to use PAC files now display the PAC file in the System Info under "Proxy Config".
* Nodes which have no data are displayed in the lower left corner of the Path Visualization view, for greater clarity.
* Selection of the protocol \(TCP or ICMP\) for the Network Measurements in Network tests via the API is now possible.

## Questions and comments

Comments or questions about tonight's release? Got any good April Fool's Day stories about emails with [spoofed From: fields](https://en.wikipedia.org/wiki/Email_spoofing) you sent? [Send us an email](mailto:support@thousandeyes.com?subject=2018-04-11+Release+Update)!

