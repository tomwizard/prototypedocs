# Release Notes: 2017-10-12

Welcome to a special Wednesday night release!

Before the details of the release, some items of possible interest.

Young Xu's latest ThousandEyes blog post summarizes a talk by Donovan Fritz of Netflix, from the recent Silicon Valley ThousandEyes Connect event. The title of Donovan's presentation was [How Netflix Tracks IP Addresses within AWS](https://blog.thousandeyes.com/how-netflix-tracks-ip-addresses-within-aws/). And speaking of...

## ThousandEyes Connect

IMAGE MISSING

For folks in the Northeast US, or anyone who wants to visit the Big Apple, ThousandEyes Connect in New York City will be November 9th on historic 42nd Street! Like the city that never sleeps, registration is open 24 hours a day. There'll be great customer presentations from McGraw Hill Education and Viacom discussing how ThousandEyes helps keep their customers happy. You can also hear and meet our CEO, Mohit Lad, as well as other ThousandEyes employees--a great opportunity to provide feedback.

ThousandEyes will be making the rounds of many great industry events \(Cisco Connect, ONUG, WAN Summit\) this fall. Looking for an event near you? Check out our [Events calendar](https://www.thousandeyes.com/events).

## Joint ThousandEyes/Cisco webinar

Join Archana Kesavan, Sr. Product Marketing Manager at ThousandEyes, and Dax Choksi, Sr. Product Manager, Routing Group at Cisco, on October 24th at 10:00 am PST to learn how to deliver a better experience across your WAN. [Registration](https://events-cisco.webex.com/mw3200/mywebex/default.do?nomenu=true&siteurl=events-cisco&service=6&rnd=0.16814004581502706&main_url=https%3A%2F%2Fevents-cisco.webex.com%2Fec3200%2Feventcenter%2Fevent%2FeventAction.do%3FtheAction%3Ddetail%26%26%26EMK%3D4832534b00000004c9a76d92ce5decd5bad02578884f21297c8aa23a8b7040af548e01c02f62cd2e%26siteurl%3Devents-cisco%26confViewID%3D71109141301604973%26encryptTicket%3DSDJTSwAAAATgqF4H6XM1HT-i-Fl2n5650qziZeuxC4J4Y-34saFDxw2%26) is open!

## Private BGP Monitor infrastructure maintenance

On Monday, October 17th at 0:00 UTC, we will be performing maintenance on the equipment which provides the Private BGP Monitor feature \(a.k.a. BGP Private Peers\) of the ThousandEyes platform. See our [announcement](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SDbCAM) for more details.

Now, on to the release!

## Cloud Unit Calculator updates

We are beginning some updates to the ThousandEyes [Cloud Unit Calculator](https://app.thousandeyes.com/calculator). In this release, we've updated the look and feel of the Calculator. All of the old functionality is still present, and existing links from the old Calculator will continue to work. We've also added the number of servers to the calculations for a DNS Server test. Customers who purchased ThousandEyes through partners now have access to the Calculator.

## New Cloud Agents

A new IPv4 Cloud Agent location: Quebec City, Quebec, Canada. Bienvenue! And welcome to Kiev, Ukraine--both IPv4 and IPv6.

## Cloud and Enterprise Agents

When viewing a tooltip containing Cloud and Enterprise Agent information, we now display IP addresses of both the IPv4 and IPv6 interfaces if the Agent has active interfaces from both address families, rather than displaying a single IP address family. This will assist customers in easily creating IP address-based whitelists, among other uses.

IMAGE MISSING

## Reports

We've added a new metric in the Alerts category, called "All Alerts". This metric includes all types of alerts: Agent alerts, BGP and DNS+ test alerts.

IMAGE MISSING

## API

Per the [change log](http://developer.thousandeyes.com/v6/#/changesummary) of the [API documentation](http://developer.thousandeyes.com/), we've added two parameters to the DNS Domain Trace test endpoint \(/dns/trace\):

* failedQueries
* finalServerQueried

and added two parameters to the Path Visualization endpoints \(/net/path-vis and /net/path-vis/{testId}/{agentId}/{roundId}/\):

* sourceIP
* sourcePrefix

Consult API documentation for the [DNS Domain Trace](http://developer.thousandeyes.com/v6/test_data/#/dns-trace) and [Path Visualization](http://developer.thousandeyes.com/v6/test_data/#/path-vis) endpoints for more information.

## Bugs fixes and minor enhancements

* DNS Trace tests from Enterprise Agents with a "Force IPv6" or "Prefer IPv6" policies \(under the Advanced Settings tab\) now use and display AAAA records from the responses and perform the trace using IPv6.
* Changed the names of the permissions "View groups" and "Edit groups" to "View Labels" and "Edit Labels". The functionality is unchanged.
* Changed behavior of modal dialogs requiring large amounts of configuration to require explicit cancellation, so that accidentally clicking outside the dialog does not cause loss of any configuration which has been entered.
* Fixed an issue causing an "Account group token is invalid" error when installing a ThousandEyes Appliance.
* Fixed an issue displaying the selected Agent data on the timeline when the view's page has been active for multiple data rounds.
* Fixed an issue in Reports snapshots that resulted in "No Data" when data was present in the Report.
* Fixed an issue affecting moving tests between organizations, with an error incorrectly stating the target account had insufficient resources.
* Fixed an issue occurring when a cluster with a disabled Enterprise Agent is added to an Account Group, which re-enabled the disabled Agent.
* Addressed an issue with stacked area widgets in emails of report snapshots.
* In the Endpoint Data's Network view, the Connection Failures metric could be inconsistently reported between timeline and the tooltip from mousing over the Endpoint Agent.

## Questions or comments?

Connect with ThousandEyes! We'd love to hear what's on your mind. [Send us an email](mailto:support@thousandeyes.com?subject=2017-10-11+Release+Update).

