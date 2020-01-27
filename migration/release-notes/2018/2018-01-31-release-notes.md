# Release Notes: 2018-01-31

Welcome to tonight's release! Lots of new things to tell you about.

For starters... New ThousandEyes blog posts.

Archana Kesavan's new post is an annual favorite: the top outages of the past year.  Check out the [Top Internet and Cloud Outages of 2017](https://blog.thousandeyes.com/top-internet-cloud-outages-2017/).

Archana also brings us the second summary from [ThousandEyes Connect in Chicago](https://www.thousandeyes.com/events/connect/chicago-2017). This post summarizes the presentation from United Airlines' Principle Operations Engineer, Brandon Mangold. Entitled [How United Airlines Manages Visibility for a Global Network](https://blog.thousandeyes.com/how-united-airlines-manages-visibility-global-network/), Brandon describes how his team employs ThousandEyes in the course of monitoring and managing 1000+ offices and over 400,000 employees.

Archana completes the trifecta with [Nerding Out at Networking Field Day 17](https://blog.thousandeyes.com/nerding-out-networking-field-day-17/), summarizing our presentation of the Network Intelligence and Device Layer features.

Lastly, if you're in the neighborhood of Barcelona, Spain, there's still time to drop by Cisco Live, visit with the ThousandEyes crew and pick up a free t-shirt. And if you're not in the neighborhood, maybe there's an [event near you](https://www.thousandeyes.com/events). The next [ThousandEyes Connect](https://www.thousandeyes.com/events/connect/london-2018) event is in London, in March.

On to tonight's release!

## Cloud Agents

Due to provider stability issues, we have removed the Cloud Agent in Sapporo, Japan. A new provider is not available at this time. We will continue to look for additional providers in northern Japan.

## Enterprise Agents

Customers with very old versions of Enterprise Agents which report data to the old collector will no longer be able to connect to the ThousandEyes infrastructure. After tonight, either the Agent must be upgraded or the Agent must be replaced with the current version of the Enterprise Agent software.

## TLS 1.0 deprecation

As [announced back in September](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RwJCAU_Release-Update-2017-09-13), we are [deprecating the use of TLS 1.0](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RwdCAE_TLS-1.0-Deprecation) on ThousandEyes infrastructure. After tonight, clients which use only TLS 1.0 will not be able to access web resources.

## Public BGP Monitors

For Routing - BGP tests and for other tests with **Collect BGP data** checked in the Advanced Settings, we are making a change to the way Public BGP Monitors are assigned to tests. In order to facilitate future improvements, users will now select either all of the Public Monitors or none.

IMAGE MISSING

IMAGE MISSING

Private BGP Monitors will continue to be individually selectable.

Existing tests which had a subset of the Public BGP Monitors will be changed to include all monitors. This may affect a test's data, reports and alerts. In the Reports feature, filters can be configured for any Monitors which customers wish to exclude. For Alerts, individual monitors can be excluded from Alert Rules by using the **Monitors** selector in the Alert Rule and choosing the "All Monitors except" option.

When creating or modifying tests with Public BGP Monitors via the ThousandEyes API, review the next section, "API changes".

## API changes

To stay consistent with the UI behavior for Public BGP Monitor assignment, we've introduced a new field into version 6 of the ThousandEyes API.

When creating or updating a test that uses BGP monitoring, use the new {"usePublicBgp": 1} option to automatically add all available Public BGP Monitors.  Customers can continue to use the bgpMonitors option to assign Private BGP Monitors.  Note that if a public monitor is included in the bgpMonitors list, all public monitors will be assigned to the test, regardless of the setting specified in the usePublicBgp parameter.

## BGP Path Visualization

We've enhanced the information we provide on path changes to the BGP Path Visualization. Along with the number of changes, we now list the AS path of the changes and the timestamps. Mouse over a BGP monitor in the Path Visualization to display the tooltip, and a **View details of path changes** link will be available. Clicking the link will display a modal which lists the changes:

IMAGE MISSING

This information is particularly helpful when a series of changes happens within a round \(15-minute span\) such that the initial path and final path are the same, as with the example above. Now users can see the sequence of changes.

## Endpoint Agent

An Endpoint Agent can now be moved to a new Account Group. On the **Agents &gt; Endpoint Agents** page, click the More Actions icon and select Transfer Ownership.

IMAGE MISSING

A role with the Edit endpoint agent settings permission is required in both the source and target Account Groups.

## New Transaction test command

Two weeks ago we released the **dynamicType** command for Transaction tests, but did not release support for playback in the Transaction Recorder at that time. We have now released a new version, 0.9.4 of Transaction Recorder. Systems with connectivity to the Chrome Store should receive the updated version automatically.

## Alerts

We've added a new "Total Wire Size" metric for Page Load tests and HTTP Server tests. Wire size is the size of the HTTP response payload \(which may be smaller than the object's actual size, due to compression\). In a Page Load test, the Total Wire Size is the sum of all objects' wire sizes. In an HTTP Server test, it's the wire size of the object that is in the final request. Device Layer Alerts are now fully implemented across the ThousandEyes platform. You'll see the Device Layer alert notices in "swim lanes" under the timelines in the Device Layer view, Device Layer alerts in the quick selector links of the Topology view, and everywhere else that the platform displays Alerts.

## Alert Notification emails

Emails sent by Alert Rule Notifications to multiple recipients are now sent to each recipient individually \(i.e. one address in the "To:" field of each email\).

## Minor features and bug fixes

* In a Webhook Alert Notification, we no longer resend all notifications if a subset of the notifications do not receive HTTP 200 responses. Now, only failed notifications are re-sent.
* When an Alert Rule is added to a shared test, the test is no longer unshared from the Account Group to which it was shared.
* When editing a scheduled Report Name, the edit no longer reverts to the original name.
* The legend in a stacked bar chart or an exported image of a stacked bar chart is now present.
* Fixed bugs affecting display of usage data in metered Enterprise Agents.

## Questions and comments

Want to tell us your opinion of our new features, or what you'd like to see for new features in the future? [Send us an email](mailto:support@thousandeyes.com?subject=2018-01-31+Release+Update)!

