# Release Notes: 2016-05-25

It's been a busy few weeks, over in the land of a ThousandEyes. Last week, we held our second annual ThousandEyes Connect NYC event, and heard speakers from Verisign, AIM Specialty Health and Nasdaq present on how they're using ThousandEyes. It was very well attended - watch our [Blog](https://blog.thousandeyes.com/) for updates and recaps of some of the sessions.

We've also seen rather a number of hiccups with Tier 1 carriers in the last few weeks. Whether it's a Submarine Cable fault, a Level 3 outage, or the Chinese Government's crackdown on VPN and TOR technologies, our product marketing team takes a unique stance on these issues and provides some great insight. Take the time to read through their take on the data, and comment! Check out the following blog posts for more details:

* [Transatlantic Issues in the Level3 Network](https://blog.thousandeyes.com/trans-atlantic-issues-level-3-network/)
* [The Ongoing War between China's Great Firewall and Circumvention Tools](https://blog.thousandeyes.com/the-war-between-chinas-great-firewall-and-circumvention-tools/)
* [Using Anycast for Internet Services](https://blog.thousandeyes.com/using-anycast-for-internet-services/)
* [SEA-ME-WE-4 Cable Fault has Ripple Effects Across Networks](https://blog.thousandeyes.com/smw-4-cable-fault-ripple-effects-across-networks/)

All that, and our product team has been busy too. Without further ado, please see a brief summary of this release below, and let us know if you have any questions.

## Agent to Agent General Availability

We've long-touted the ability to conduct active synthetic testing from our cloud agents. Today's release adds the ability to instrument the target of your tests by deploying an enterprise agent in line with your test targets, and provide bidirectional network data back to your destination.

IMAGE MISSING

Whether it's helping to understand and diagnose asymmetric routing issues \(is my loss on the forward or reverse path?\), or providing additional data around your critical services, Agent to Agent tests will provide an unparalleled look at the flow of packets in your network infrastructure.  In addition, we're now including a feature known as NAT Traversal, which allows bidirectional communication between an Enterprise Agent behind a firewall and a Cloud Agent.

The main capabilities for Agent to Agent tests have been in place for some time, however with the GA announcement of the test type, we're introducing a few new features:

* Cloud agents can now be added to Agent to Agent tests \(Cloud Agents used as either source or target of an agent-to-agent test consume cloud units\)
* Full support for Agent to Agent alerting is now available
* API support is also available \(Via a "preview" endpoint; see below\)
* Agents can now use a feature known as NAT Traversal to run agent to agent tests

For more information on the various aspects of Agent to Agent tests, see the following articles:

* [Agent to Agent test overview](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmwKAC)
* [NAT Traversal for Agent-to-Agent tests](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnWKAS)

## BGP Route Visualization change

Not major from a functionality perspective, but a significant change to how the views look, we've changed the representation of the BGP Route Visualization view to render BGP monitors as diamonds, rather than circles. This is largely in view of differentiating BGP Route Visualization from Path Visualization.

IMAGE MISSING

## Reporting enhancements

As usual, a few changes in the area of reporting:

* We've added a new "Working with Reports" video tutorial to the Help & Support view of reports. In this video, we'll walk through the high level capabilities of our reporting engine for users who are new to the feature.
* In any report widget which supported sorting, we've simplified the user interface by moving from a single dropdown \(which showed the field used for sorting and the direction in parentheses\) to a dropdown which shows just the field and a set of arrow buttons for direction.
* When adding a widget to a report, the widget name will get initial focus, to make renaming the agents simpler. Prior to this change, the only way to update a widget's name was by selecting rename from the widget's context menu.

##  Minor changes and enhancements

As always, we've also made a few minor enhancements.

* In certain cases, throughput on HTTP server tests isn't plotted on the chart. While this typically only ever occurred with issues related to very small payloads downloaded extremely quickly, we've corrected and normalized the display of such information.
* Duplicating a test which included a download limit \(HTTP Server / FTP tests\) now copies the limit into the new test.
* Users with "View agents in account group" permission can now view system information for their agents.
* API calls to update BGP tests by updating the "Include Covered Prefixes" checkbox will now set the value as expected.

##  APIv6 preview

We've launched a preview of APIv6, which includes support for User, Account group and Role management, retrieving usage detail, and includes support for Agent to Agent tests. Check out details on our developer reference site at http://developer.thousandeyes.com/v6

## Questions and comments?

We do love interacting with our customers! Send us your questions and we'll be happy to answer! [Drop us a note!](mailto:support@thousandeyes.com?subject=2016-05-25+release+update)

