# Release Notes: 2017-12-13

Welcome to tonight's release--the last release of 2017. We'll have the next release in January, to give our team time with family and friends during the holidays.

No new posts from the [ThousandEyes blog](https://blog.thousandeyes.com/) to announce \(but maybe a good time to catch up on some missed posts\) or December [ThousandEyes events](https://www.thousandeyes.com/events).  We promise we'll be back in the new year with more good stuff. But for tonight, we have some great presents in the form of new features. Let's open 'em up!

## 1-minute test frequency

A feature on many a customer wish list... Where previously a frequency of 2 minutes was the highest frequency available \(using the **Interval** selector in the test configuration\) now for the following test types, a test frequency of 1 minute can be selected:

### Network Layer

* Agent to Server

### Web Layer

* HTTP Server
* FTP Server

### DNS Layer

* DNS Server
* DNS Trace
* DNSSEC

### Voice Layer

* RTP Stream

Keep in mind that any test which consumes Cloud Units will use proportionally more when switching from a lower frequency to a higher frequency. For example, switching from a 2-minute frequency to a 1-minute frequency of an HTTP Server test from a Cloud Agent will double the usage of Cloud Units.

## Enterprise Agents

We're very happy to announce that ThousandEyes Virtual Appliances are now available for the Juniper NFX series routers!  [Instructions for installation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SM9CAM) are in our Knowledge Base.

## Reports time selector

We've updated the user interface for specifying the time range of a report to make report creation faster and easier. More preconfigured time ranges can be selected with a single click, and relative ranges are available such as "This Month" and "Previous Month" which automatically use the correct number of days in the indicated month.

IMAGE MISSING

Note that a week is defined as Sunday through Saturday.

Also, a Reports stocking-stuffer: we've added two DNS Trace test metrics to the list of reportable metrics: Query Count and Query Time.

## Device Layer

Device Layer now supports configuration on Enterprise Agent clusters. Previously, only individual Enterprise Agents could be configured to do Device Layer testing. ​As with all other testing performed by clusters, the testing is performed by a single cluster member, selected by the load balancing algorithm when the cluster is configured for Device Layer testing. Removing the Agent performing the Device Layer testing from a cluster will reassign the testing to another cluster member.

Note that if an individual Enterprise Agent is already performing Device Layer testing and is then moved into a cluster, the data collected prior to joining the cluster is no longer available.

## Path Visualization

Users can now select the number of packets sent in parallel, when path tracing is performed for the Path Visualization view, using the "No. of Path Traces" setting of a test:

IMAGE MISSING

Additional path trace packets can be useful for identifying sporadic or small amounts of forwarding loss, or for use in networks with many distinct, active paths to a target. Lowering the number could also help in situations where security devices with low thresholds misidentify the path traces as malicious traffic.

## Bug fixes & minor features

Here's the list of bug fixes and minor features in this week's release:

* BSSID is now available as a Filter setting, when configuring a Label under the Endpoint Agents tab of the Labels page.
* Endpoint Agent Corrected an Endpoint Agent issue which displayed the wrong name of one particular public network.
* Fixed an issue that could cause a blank Account Settings page.
* Fixed an issue causing Gateway Loss on an Endpoint Agent tooltip to be reported as 2x the actual loss seen on the gateway node's tooltip.
* Fixed an issue causing waterfalls of an Endpoint Agent's Session Details view to have mis-ordered page numbers.
* Fixed an issue which caused a selected Agent's timeline to disappear when selecting a direction in an Agent to Agent test Saved Event.
* Fixed an issue which caused missing data points in a snapshot of a report with the Alerts metric from a Transaction test.
* An Alert cleared email now uses the same precision for specifying duration of an alert as do other parts of the Alerts feature.

## ​Questions, comments?

Got a question or a comment? Surprise us with the gift of feedback! [Send us an email](mailto:support@thousandeyes.com?subject=2017-12-13+Release+Update). Happy holidays!

