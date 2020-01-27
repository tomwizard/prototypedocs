# Release Notes: 2017-06-06

Welcome to tonight's release. But first a word from our sponsor...

ThousandEyes Connect this week, in the heart of Silicon Valley!

IMAGE MISSING

Still [time to register](https://www.thousandeyes.com/events/connect) and drop by if you're in the area. Come meet the ThousandEyes team, other ThousandEyes users and hear some great speakers from eBay, Intuit and Netflix, as well as ThousandEyes CEO Mohit Lad. Oh yeah, and [t-shirts](https://www.thousandeyes.com/tshirt). We know what you really really want.

Nick Kephart's latest blog post is entitled [Monitoring IPv6 Networks](https://blog.thousandeyes.com/monitoring-ipv6-networks/), and contains some interesting data on who's doing what in terms of IPv6 traffic. IPv6 is the future, and the future is almost now. Have a read.

## API

Starting today, we are beginning the countdown for the change to the default version of our API. In 90 days \(September 13th, 2017\) the default version of the API will be changed from version 5 to version 6. At that time, API queries specified against the non-versioned API will query based on the newer version, and the oldest version of the API \(version 4\) will move into a sunset phase of 90 days. Customers should prepare their API-based applications for the change. Consult the [Change Policy](http://developer.thousandeyes.com/v5/#/versioning) of our API documentation for more information.

## Enterprise Agents

We've updated the queues used to calculate Enterprise Agent utilization. The **HTTP + DNS + Network Tests** queue has been renamed **General Tests**. The **Agent to Agent Tests** queue has been removed, and the Agent to Agent tests are now included in the General queue, or the **Bandwidth and Throughput Tests** queue if the test is configured for Bandwidth and/or Throughput measurements. For more information on Enterprise Agent utilization, check out the new Knowledge Base article [Enterprise Agent Utilization](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnjgCAC).

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* We've made some improvements to BrowserBot on our Cloud Agents, in response to some instability issues from the past two weeks.
* Path Visualization tooltips now show information on target nodes even if the target is unreachable.
* An Endpoint Agent on a system with an active VPN client will now display the VPN termination in the Path Visualization even when the VPN termination does not respond to ICMP echo requests \(pings\).
* In the Network Topology View of Endpoint Data, we now allow the **Wireless by** Grouping to be SSID, BSSID or Access Point.
* Enterprise Agents which are in an "Offline" state \(not contacting ThousandEyes\) no longer display warning messages other than the offline warning.  Once the Agent is in an "Online" state, warnings for other issues will reappear.
* Fixed an issue with BrowserBot \(Page Load and Transaction tests\) which caused authentication credentials to fail to be sent to a proxy.
* Fixed an issue with privileges that prevented running Agent to Agent tests as Instant Tests
* Adding users with email addresses having non-standard top-level domains now works \(domain still requires a valid MX record in DNS\)
* In some limited circumstances, an Alert Grid Dashboard widget would not display the number of alerts.  The alert numbers are now displayed.
* Fixed an issue with Reports Dashboard widgets not refreshing automatically

## ​Questions, comments?

Can't make it to ThousandEyes Connect but still want to connect with ThousandEyes? We'd love to know what's on your mind. [Send us an email](mailto:support@thousandeyes.com?subject=2017-06-06+Release+Update).

