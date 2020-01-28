# Release Notes: 2019-07-23

Welcome to our latest release! This one's got a long list of changes, so get comfortable. And before the details of the release, news of new blog posts...

Depending on your location on the globe, July either heralds the heat or the cold comes calling. Not sure whether hot or cold is a better metaphor, but June and July have also seen major internet outages. At the end of June, CDN provider Cloudflare was hit hard by an outage not of their own making. Our Veep of Product Marketing, Alex Henthorne-Iwane lays out the outage in great detail, in his post [Cloudflare Users Burned by Internet Routing Pile-Up](https://blog.thousandeyes.com/cloudflare-users-burned-by-internet-routing-pile-up/).

In a related article, Customer Success Engineer Kemal Sanjta does a great job of explaining the issue at the heart of said Internet routing pile-up and other recent outages: ISPs who fail to implement RPKI. What's that, you ask? Kemal will tell you, in his post [Visualizing the Benefits of RPKI](https://blog.thousandeyes.com/visualizing-the-benefits-of-rpki/).

Another new addition to the blogroll: [Why I’m No Longer Talking About the Cloud](https://blog.thousandeyes.com/why-im-no-longer-talking-about-the-cloud/) by our Director of Solutions Marketing, Ian White. The subtext of his blog: Don’t Tell Me Why, Tell Me How. Spoiler alert: there might even be a plug for letting ThousandEyes tell you how to monitor all that cloud-based infrastructure.

Interested in how Neustar, a major cloud provider, uses ThousandEyes to monitor their DDoS mitigation and other services? Our Content Marketing Director, Sean Coombs, brings us a recap of a talk from the recent ThousandEyes Connect in New York City by Matthew Wilson, Neustar's Director of Network Engineering, in [How Neustar Protects Digital Businesses while Using ThousandEyes to Ensure Service Availability](https://blog.thousandeyes.com/how-neustar-protects-digital-businesses-using-thousandeyes/). And on the lighter side, Sean recaps an annual ThousandEyes tradition, in his second blog post, [\#HackTogether: A Recap of Our Biggest Hack Day Yet](https://blog.thousandeyes.com/hacktogether-hack-day-june-2019/).

And our Director of Technical Marketing, Hans Ashlock, looks deeply into the [DevOps world with Monitoring your DevOps Toolchain](https://blog.thousandeyes.com/monitoring-your-devops-toolchain/). Doing business on the Internet requires DevOps, and DevOps processes require monitoring. There might be another plug, there.

And now for the details of the latest release.

## New Cloud Agent locations

 We've added some new locations for our Cloud Agent fleet. For starters:

* Lagos, Nigeria - IPv4
* Chicago, Illinois \(AT&T\) - IPv4
* Bratislava, Slovakia - IPv4 and IPv6
* Budapest, Hungary - IPv4 and IPv6
* Ahmedabad, India \(Reliance\) - IPv4 and IPv6
* Bangalore, India \(Reliance\) - IPv4 and IPv6
* Chennai, India \(Reliance\) - IPv4 and IPv6
* Mumbai, India \(Reliance\) - IPv4 and IPv6

 And the big news: we've added 19 Cloud Agents in the Alibaba network. Seven are in China, where Alibaba is based, but others can be found across the globe, in North America, Europe, the Middle East, Australia, as well as other places in Asia. The names of the Cloud Agents will contain "Alibaba" and Alibaba's regional specification, for example "Shanghai, China \(Alibaba cn-shanghai\)".

## New default Interval for tests

 To better reflect customer usage, we're changing the default **Interval** setting when creating new tests. When creating a new test, the default setting is now 2 minutes for all test types except Routing/BGP tests and Web/Transaction tests. This change has no effect on existing tests.

## Endpoint Agent

 We've got a number of improvements to your Endpoint Agent experience, starting with a new feature--the Experience Score metric!

### Experience Score

 We've introduced a new metric, Experience Score, which rates a user's experience when loading a particular page. We calculate Experience Score with a formula that is based on the time to load the DOM of a page, which we then map to a score based on our data set of load times. A score of 100 is the top score, 0 is the lowest score. An average experience is in the range of 44 to 89. Average \(mean\) Experience Scores can be displayed by Endpoint Agent, or by domain of pages visited.

### New Overview page

 We've added an Overview page to the other pages under the Endpoint Agents menu. The Overview provides a dashboard-style view of Agent activity, with a variety of widgets highlighting data for Browser Sessions, Scheduled Test and our new Experience Score. Check it out!

IMAGE MISSING

### Browser Session View improvements

 We've improved the Browser Sessions View to better represent the experience of a user interacting with a web application.

### Anonymize IP addresses in Endpoint Agent snapshots

When creating a snapshot of Endpoint Agent data, the **Anonymize data that identifies users** checkbox will now anonymize IP addresses within the networks of the organization with the Endpoint Agents.

IMAGE MISSING

The Network Layer of the Wireless Topology, as well as the Path Visualizations of the Network Sessions and the Scheduled Tests are anonymized.

### Scheduled tests support TCP and IPv6

Endpoint Agent's Scheduled tests now support IPv6 and support TCP as the protocol for the Network view.

## Device Layer

 Some major improvements to the Device Layer feature set.

### Device Layer user interface

 The user interface for Device Layer views has undergone a major revision. Most notably:

* The Topology and Interface Metrics Views have been replaced by a Network View with Topology, Interface Table and Device Table tabs
* Filters have been added to the Device Layer, enabling users to view slices of data with any number of Agents, devices or interfaces. The filter works in all Views \(present and future\) as well as in elements within a View, such as the topology graph and tables. Search boxes in the tables have been removed.
* The Device and Interface selectors have been moved into the filter.
* Tooltips have been redesigned.
* The timeline has been redesigned to display Metrics which have two related values, such as Throughput \(input and output directions\) in an above-below manner:  IMAGE MISSING
* The Topology graph can now display sections \("islands"\) discovered by multiple Agents. Devices not included in an island are faded in the display.
* The Topology graph will paginate automatically when a large number of islands are viewed.

### User-defined IP addresses

 In a device's Advanced Settings, users can now supply a user-defined IP address for the device:

IMAGE MISSING

This setting can be helpful for adding addresses to devices like load balancers or routers where the address is not associated with a specific interface and cannot be obtained by Device Layer discovery. The user-defined address\(es\) will be used to match devices in the Path Visualization in order to render single devices with multiple IP addresses, rather than rendering multiple devices.

## API

* The /agents API endpoint now allows reading and updating an Agent's **Target for Tests** setting via the targetForTests parameter
* The /audit/user-events/search API endpoint now returns resource data associated with the searched-for event
* The /usage API endpoint now provides the cloudUnitsProjected and cloudUnitsNextBillingPeriod parameters to obtain projected unit use at the end of the current billing period and the next billing period, respectively

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release: 

* Configuration of Agent Notifications is now done in a side-panel modal
* Proxy configurations added to a Custom Appliances configuration are now correctly saved in the configuration
* Diagnostics of an Appliance configured to use a proxy with NTLM authentication now work correctly
* The web interface of the ThousandEyes Appliance works with Internet Explorer 11 again
* After editing the test target, an SFTP test now uses the correct target domain in the Network layer
* In the Path Visualization view of an Agent to Agent test, switching Direction from "Source to Target" then "Target to Source" and back again no longer produces a "No Traces" message
* Duplicating an Alert Rule with a Notification having newline characters in the Messages field no longer produces an "Invalid request" error
* Duplicating a non-HTTP Server Alert Rule now maintains the type of Alert Rule in the duplicate
* Fixed an issue which could cause an Enterprise Agent-based HTTP Server test to report Response Times larger than the test timeout
* Fixed an issue which could cause a proxied Enterprise Agent's HTTP Server test to misrepresent a DNS error as a Connect phase error when the request was generated by an HTTP redirect
* Fixed an issue which could cause an Endpoint Agent's Scheduled HTTP Server test to display no results in the Table
* Fixed an issue which could cause the agent process to fail to start on Enterprise Agents with tests that use Kerberos
* Fixed an issue which could cause an Endpoint Agent Scheduled test reports an error in Receive phase but still shows an HTTP 200 status code
* Fixed an issue where the number of Endpoint Agents matching a Label could be underreported on the Agent Labels tab of the Agent Settings page
* Fixed an issue where the total number of Endpoint Agents displayed in a swimlane error on the timeline is higher than the actual number of Endpoint Agents
* Fixed an issue causing an Endpoint Agent's Error Detail in the table view to be blank when ICMP measurements could not be completed
* When a Scheduled test on an Endpoint Agent is configured to use a PAC file to select a proxy, the proxy's domain name is now properly resolved and the Agent correctly performs any proxy authentication
* Fixed an issue which could cause the Packet Discard metric to be incorrect
* Fixed an issue which could cause a Share Link to have incorrect forwarding loss in the Path Visualization
* Fixed an issue which could cause a Table widget or Multi-metric Table widget to have incorrect information in an exported PDF
* Fixed an issue which could cause a Time Series widget to have incorrect information
* The v6/audit/user-events/search API endpoint no longer loops indefinitely when using the next parameter to obtain paginated data

## Questions and comments

Got feedback for us? Want to tell us about your company's Hack Week projects? [Send us an email](mailto:support@thousandeyes.com?subject=2019-07-09+Release+Update)

