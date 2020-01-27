# Release Notes: 2016-07-06

And, with that, we're halfway through the year! Hopefully everybody who's stateside, \(as well as our counterparts north of the border\) have managed to shake off their post-holiday weekend cobwebs.

We've been busy, and have some nice features to show as a part of this week's release.

## Agent installation

### Virtual appliance for Cisco IOS XE Containers

With this release, we're adding support for a virtual appliance that runs natively in the context of Cisco ISR 4000 series and ASR 1000 series routers running IOS XE 3.17 or higher.  

We'll be talking about this feature more in the coming days, and next week at Cisco Live in Las Vegas - come visit us to learn more at booth \#2244.  In the meantime, for system requirements and installation instructions on ISR 4k and ASR 1k series routers running IOS XE 3.17 or higher, see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnRKAS), and watch the [ThousandEyes Blog](https://blog.thousandeyes.com/) for more updates as they become available.

### Ubuntu 16.04 support

We now also support installation of the Enterprise Agent package on Ubuntu 16.04 Server LTS \(64-bit\).

## Node labels in path visualization

We've added a feature to toggle node labels in the Path Visualization view. On the upper left of the controls, a checkbox controls whether or not node labels are shown in the visualization. Simply check this box to show node labels \(which will show the IP address or interface group name\) for the node.

IMAGE MISSING

If a node name is too long to display without obscuring the visualization, the label will be truncated - on a middle-out basis.

## Alerting changes

We've enhanced our alerting options to allow triggering of alerts based on a longer period of time. Previously, users could alert when a minimum threshold of either agents or monitors met alert criteria up to 10 rounds in a row. This feature was great for alert dampening, but could fail to trigger under certain conditions \(such as a flapping condition\).  To set this condition, simply modify your alert rule criteria to set the minimum number of occurrences out of the number of rounds.

IMAGE MISSING

Note for users accessing the ThousandEyes API to pull alert rule metadata: these fields are represented as "roundsViolatingRequired" and "roundsViolatingOutOf", respectively. If you have different values for these fields, then the roundsBeforeTrigger value will not be shown in versions of the API prior to v6.

## DNS server metrics

We've split the tables associated with the Server Metrics view of DNS Server tests has been split into two tabs - one for Servers, and one for Agents.

IMAGE MISSING

For those unfamiliar with DNS Server tests, you can take a refresher by reading [this KB article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmrKAC). In a nutshell, a DNS Server test is essentially a matrix that runs a test to each server in a list from each agent assigned to the test - so, you'll end up with two sets of data to pivot against:

* Servers: success rate and average resolution time, summarized by DNS server
* Agents: success rate and resolution time, summarized by agent

In either case, clicking an element in these tabs changes the content of the timeline to show values for the selected elements and metric, and filters the content of the other tab to scope based on the selection. To de-select an option, clear the selection in the dropdowns found just above the timeline.

## API changes

We've made several updates to version 6 of the ThousandEyes API, which is currently in preview mode. Check out version 6 of the ThousandEyes API at http://developer.thousandeyes.com/v6

## Cloud agent changes

We've made the following changes to our cloud agent infrastructure.

* \(Added\) Sapporo \(Hokkaido\) Japan: this agent is generally available to our paying customers.
* \(Removed\) Mumbai, India: we have discontinued service in this location due to poor service from our service provider.  An evaluation is currently underway of options for new service providers in Mumbai.

## Bugs fixed & minor features

And, our bug-bashers have been busy as well...

* The timestamp of a selection is now visible in the tooltip that appears when you're hovered over an area in the Box & Whiskers chart
* We've corrected a problem that prevented contracted quantities of units and agents from appearing in the billing tab
* Users with management permissions can now manage user assignment to account groups which contain the . character
* We've corrected a problem that caused the table tab of the End to End metrics view for an agent to agent test to show the destination server address as 0.0.0.0
* We've removed disabled agents from the list of agents with problems, shown when hovering over the agent icon in the upper right corner of the platform
* We've added the agent's source IP address to the show traceroute-style output option in Path Visualization

