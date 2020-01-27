# Release Notes: 2018-03-28

Welcome to tonight's release! It's a big one, feature-wise and fix-wise.

But before those details, a quick shout out to Solutions Engineer Tim Hale, for the latest ThousandEyes blog post. The first in a two-post series, [Modern Wide Area Network Monitoring: Migrating from MPLS](https://blog.thousandeyes.com/modern-wide-area-network-monitoring-migrating-from-mpls/) looks at migrations from MPLS to Internet- and cloud-centric networks, including reasons why companies are making this change and the change to SD-WAN; pitfalls in these migrations; and how to use network monitoring to ensure success in migration projects.

And now for the details of tonight's release...

## Cloud Agents

We continue to add to our list of [broadband ISP Cloud Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SYoCAM_Release-Update-2018-02-14#Broadband_Cloud_Agents). This release, we've added locations for two providers: Verizon and Charter/Spectrum.

**Verizon**

* Chicago, IL
* Ashburn, VA
* Los Angeles, CA
* Dallas, TX

**Charter/Spectrum**

* Chicago, IL

## HTTP 2.0 support in Web Layer tests

All Web Layer tests \(and the HTTP Server View of a Page Load test\) now can provide metrics based on version 2.0 of the HTTP protocol. Tests will now attempt to negotiate the version of HTTP with the server, and use HTTP 2.0 if the server supports it. Customers may see some changes in test data as a result of this new feature.

For HTTP Server tests \(which request a single object\) the data won't change much based on the negotiation of HTTP protocol version, whether the target URL is http:// or https://.

For BrowserBot-based tests \(Page Load and Transaction tests\) the Waterfall data and other metrics can be substantially different from those produced using HTTP 1.1 \(or HTTP 1.0 if targeting very old servers or some proxies\). For example, HTTP 2.0 waterfalls have fewer objects with **Connect** time \(the time to set up a TCP connection\). HTTP 2.0 will send multiple requests over a single TCP connection without waiting for responses from the initial requests \(solving the "head of line blocking problem" of HTTP 1.1 and earlier versions\). Thus, fewer TCP connections are created. Similarly, for connections which use SSL/TLS, fewer objects will have **SSL** time.

Additionally, new waterfall timings are introduced with HTTP 2.0, such as those for the Server Push message:

IMAGE MISSING

Additionally, BrowserBot now supports [SPDY](https://en.wikipedia.org/wiki/SPDY) \(the precursor to HTTP 2.0\) and [QUIC](https://en.wikipedia.org/wiki/QUIC), a UDP-based implementation for secure web communication.

Customers who see changes in test data can check which protocol was used to request an object:

### HTTP Server

Click the \[Headers\] link in the Response Code column of the Table tab:

IMAGE MISSING

In the **Response Headers**, check the protocol string for "HTTP/2".

IMAGE MISSING

### Page Load and Transaction

Mouse over an object in the Object column of a waterfall to display a tooltip, which includes the Protocol field:

IMAGE MISSING

Possible values are:

* **h2** for HTTP 2.0
* **h2c** for HTTP 2.0 in cleartext \(http:// URL\)
* **http/1.1** for HTTP 1.1
* **quic/1+spdy/3** for QUIC and SPDY

## Other Test improvements

### TCP or ICMP for Network Measurements

For tests which included TCP-based Network Measurements \(under the Advanced Settings tab of the test configuration\) we now provide a choice of TCP or ICMP protocol:

IMAGE MISSING

### SIP over TLS

SIP Server tests now support TLS-encrypted SIP:

IMAGE MISSING

On the Map tab, the test's Status by Phase will include an SSL phase.

### Map tab Agent icons

[Previously](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009S1OCAU_Release-Update-2017-09-27#Map_widgets), we introduced a new icon for representing Agents on a Map widget for the Dashboard. We're now expanding the use of that icon to the Map tab for both Cloud and Enterprise Agents, in tests which have Availability as a Metric \(HTTP, FTP, SIP and DNS Server tests\). The legend will also go digital, replacing the gradient-style legend:

IMAGE MISSING

### Geolocation

We've improved our geolocation algorithm for placing nodes in path traces on the Path Visualization view of scheduled tests, and Network Topology from Endpoint Data. Instead of using static data which can be outdated or incorrect, we're now using active network measurements to help decide which side of the ocean that node in the path really is on.

## Device Layer

### Device Discovery

We have added an **Enabled** checkbox for saved device discoveries, which allows for enabling and disabling of a scheduled device discovery. Previously customers could only delete a scheduled device discovery.

IMAGE MISSING

Additionally, we've improved discovery of devices with non-unique identifiers. Thus, customers may see new devices being discovered for the first time, after their Enterprise Agents download tonight's update.

Last, based on customer feedback and to improve user experience with large network topologies, we have reduced the icon size of Device Layer nodes. This change affects nodes in Path Visualization of tests, in addition to the Device Layer's Topology view.

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* Quick Links in Path Visualization and Route Visualization are now organized by Error, Alert, Warning and Info categories.
* Made fields in alert emails and alert  cleared emails consistent with each other.
* Added the base URL of the alerting test in alert cleared emails.
* Orange borders are now used solely for loss on path nodes, and are no longer used to show Agents with alerts.
* Outage Detection will now provide a year of data, up from 30 days \(since the Outage Detection feature is not yet one year old, there will be less routing and traffic outage data right now, but stick around...\)
* TCP-based Agent to Agent tests no longer break with certain firewall features \(e.g. virtual reassembly mechanisms\) which use sequence numbers.
* BGP data can now be enabled when creating tests via API.
* Sorting by object size now works for Page Load tests.
* Unchecking the Private setting of a Dashboard now works correctly.
* Fixed an issue causing incorrect numbers of days in a Reports snapshot to be displayed.

## Questions and comments

Got feedback on the new features? Exhausted by reading these release notes? [Send us an email](mailto:support@thousandeyes.com?subject=2018-03-28+Release+Update)!

