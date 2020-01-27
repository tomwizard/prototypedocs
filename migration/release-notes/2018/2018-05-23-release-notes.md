# Release Notes: 2018-05-23

Welcome to tonight's release! Some quick announcements before the details of the release.

IMAGE MISSING

We're excited to open registration for [ThousandEyes Connect](https://www.thousandeyes.com/events/connect/santa-clara-2018) in Silicon Valley. Join us on July 12th to meet industry peers, share insights and learn from networking experts. Past speakers have included leaders from Cisco, Intuit, Oracle, and Zendesk. And if that's not enough, we'll give you a cool [t-shirt](https://www.thousandeyes.com/tshirt) for attending!

Lots of great new [ThousandEyes blog](https://blog.thousandeyes.com/) posts to tell you about.

Senior Product Manager, Gopi Gopalakrishnan, has the [end-of-quarter review](https://blog.thousandeyes.com/product-features-whats-new-q1-2018/) of the major new features released over the past three months. If you need to catch up on all the good stuff that's new in ThousandEyes, this blog post is for you!

Senior Product Manager, Archana Kesavan's post [Webex Monitoring](https://blog.thousandeyes.com/webex-monitoring/) provides details for monitoring the performance and availability of the many facets that comprise the Cisco Webex service. Take a peek into the Webex data center architecture and see how your meeting works. If you depend on Webex for business collaboration, you won't want to miss this info.

Exciting news from Senior Site Reliabiity Engineer, Raúl Benencia via the ThousandEyes blog. In his debut post, Raúl describes Shoelaces, a software tool which was written by his team to help manage ThousandEyes' infrastructure. Shoelaces works with DHCP and TFTP to provide bootstrapping of remote servers. The tool is lightweight, flexible and is now [freely available](https://github.com/thousandeyes/shoelaces) under the Apache Public License 2.0! If you provision remote servers, check it out!

On to the release...

## Cloud Agents

Another addition to our growing number of Cloud Agents in broadband ISP networks--this one in the Verizon network, in Seattle Washington. Additionally, we have a new Cloud Agent in Takamatsu, Japan. Konnichiwa!

## Test enhancements

### End to end loss

Previously, when a test performed TCP-based end to end loss measurements for the Overview, the ThousandEyes Agent would first attempt to use TCP selective acknowledgement \(SACK\) to send 50 packets to the target. If the test target did not support TCP SACK, the Agent would fall back to sending 50 separate synchronization \(SYN\) packets. This behavior is now configurable in the test's Advanced Settings. The behavior of each setting:

* **Prefer SACK**: The previous behavior: try SACK mode and fall back to SYN mode if needed. This is the default.
* **Force SACK**: Use SACK mode only
* **Force SYN**: Use SYN mode only IMAGE MISSING

Not all targets will support TCP SACK. If a test is configured to use **Force SACK** mode but the target does not support selective acknowledgements, then the test will display the error "Target doesn't support SACK mode" and will not transmit 50 packets to the target.

For customers interested in learning about TCP selective acknowledgements, a great place to start is Jeremy Stretch's [TCP Selective Acknowledgments \(SACK\)](http://packetlife.net/blog/2010/jun/17/tcp-selective-acknowledgments-sack/) from the PacketLife blog.

## Account Settings

We've revamped some of the tabs in the [Account Settings](https://app.thousandeyes.com/settings/account/?section=profile) page to better group the information as we add more functionality. The Security & Authentication and Usage tabs have been replaced with the Organization and Billing tabs.

The new Organization tab contains information that applies to a customer's entire organization, such as the single sign-on \(SSO\) configuration and password expiry, as well as the organization name and time zone settings in the app. Additionally, the number of licenses used by Enterprise and Endpoint Agents are displayed here, along with past, present and projected Cloud Unit usage, broken out by Account Group, Test type and individual Test.

The new Billing tab has information on the customer's subscription, including total licenses and Cloud Units, billing address and contact, payment method and invoice history.

## Device Layer

### Bulk Actions

In order to make easy the management of large numbers of devices, we're adding a feature to perform bulk actions for Device Layer devices.

IMAGE MISSING 

Each device entry on the Devices tab of the Device Settings page now has a checkbox. When one or more devices' boxes are checked, a bar at the bottom of the page will appear, providing the ability to configure all checked devices. Configuration options include M**onitor** and **Unmonitor** buttons, and an **Edit Devices** button which provides the following actions:

IMAGE MISSING  
 

### Notifications for Slack and Hipchat

When Device Layer's Notifications for new interfaces or devices are sent to Slack or Hipchat, the color of the text is now blue \(informational\) instead of red \(error\).

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* Fixed an issue where Target to Source path trace data was not shown in some bidirectional Agent to Agent tests.
* When configuring a report, the Custom Date Range selector now consistently applies the chosen dates.
* The login field for app.thousandeyes.com now strips trailing whitespace from a username, rather than returning an error.
* Updated the Activity Log's Time selector with the new design used in Reports and Dashboards.
* In the Endpoint Data's Session Details, changed the WiFi access point icon color from blue to grey, consistent with the ethernet connection icon.
* When opening a newly created Endpoint Data Saved Event \(a.k.a. snapshot\), if the data has not finished saving, a "This saved event is still being generated" message is now displayed.

## Questions and comments

Have feedback or questions about tonight's release? Want to comment on your experience trying Shoelaces?  [Send us an email](mailto:support@thousandeyes.com?subject=2018-05-22+Release+Update)!

