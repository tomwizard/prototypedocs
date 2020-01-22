# Release Update 2018-10-23 - ThousandEyes Customer Success Center

### Release Update 2018-10-23

Welcome to tonight's release!

Here in the USA, Election day is on its way. If the state of you is seeing red and feeling blue, then don't wait to feel great: migrate to Cloud State!

We're very pleased to be hosting [Cloud State 2018](https://www.thousandeyes.com/cloud-state-2018) in San Francisco on November 7th. ThousandEyes will be releasing their first Public Cloud Performance Benchmark Report, comparing the major IaaS providers: Amazon AWS, Google's GCP and Microsoft's Azure. Shake off that election night hangover and come get the scoop on the report from its author, ThousandEyes' Senior Product Marketing Manager, Archana Kesavan. She'll be followed by a slate of great speakers:

## Cloud Agents

 The latest award of a broadband provider-based Cloud Agent goes to Washington \(state\)! Welcome to the Seattle \(AT&T\) Cloud Agent.

## Enterprise Agents

In with the new, out with the old...

* In: We have new bulk actions for Enterprise Agents.
* Out: Red Hat, CentOS and Oracle Linux versions 6.7, 7.2 and 7.3 are approaching their term limits. Details below.

### Bulk Actions

We have new bulk actions for Enterprise Agents:

* Adding, modifying and removing Labels, with the new **Labels** button
* Adding, modifying and removing Agent Notifications, using the **Edit** button to select "Edit Agent Notifications".

Check boxes next to the Enterprise Agents which are the target of the bulk action, and select an action in the bulk actions menu bar which appears once an Agent is checked.

### End of Life for Linux package Enterprise Agents on Red Hat 6.7, 7.2 and 7.3

 Per our End-of-Life policy for Enterprise Agents, we are announcing the upcoming end of life for [End-of-Life announcement for Red Hat Linux package Enterprise Agents: versions 6.7, 7.2 and 7.3](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CppUCAS), and equivalent versions of CentOS and Oracle Linux. ThousandEyes will end support for Agents running on these operating systems on January 1st, 2019. After that date, no new Agent installations will be permitted on these operating systems, and existing installations will not be supported.

The current minimum supported operating systems can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC). We strongly encourage customers to upgrade to the most recent Red Hat 7 version rather than a supported 6.x version, as development by Red Hat on version 6 is limited and will likely have less development over time. Additionally, customers have limited options for new Agent creation, as ThousandEyes does not support [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker) on version 6.x of Red Hat, CentOS or Oracle Linux. Please [contact ThousandEyes Customer Success ](mailto:support@thousandeyes.com?subject=Upgrading+Red+Hat+agents)if you need advice on managing the upgrade or replacement of your Agents.

## Snapshot creation via API

Snapshots \(Saved Events and Share Links\) can now be created via the API with the new snapshot/create endpoint. This endpoint takes a testId, name and date range and generates a Saved Event. Optional parameters include isPublic \(to create a public Share Link\) and selections for the default Metric and Layer that the snapshot will display. The API will return a link to the Saved Event and to the public Share Link \(if selected\). As always, check the API documentation at [developer.thousandeyes.com](https://developer.thousandeyes.com/).

## Endpoint Agent new Wireless View and metrics

 Under [Views &gt;  Endpoint Data &gt; Network Access](https://app.thousandeyes.com/view/endpoint-agent), we have a new Wireless view. The new view provides five new wireless metrics \(in addition to the Signal Quality metric, which is identical to the Wireless Signal Quality metric in the Network Topology view\):

* **Throughput:** The Endpoint's total input and output \(in bits per second\) on its wireless interface in the test round.
* **Retransmission Rate:** Percentage of retransmitted data by the wireless interface. Available for Windows operating systems only.
* **BSSID Changes:** Total BSSID changes \(joins, leaves\) by all Endpoint Agents in the test round. Hovering over a row's BSSID Changes will display a tooltip of all BSSIDs in the test round.
* **Channel Changes:** Total channel changes in the test round by all Endpoint Agents \(an Agent which changes BSSID does not contribute a channel change, even if the channel in the new BSSID is different from the channel in the prior BSSID\).  Hovering over a row's Channel Changes will display a tooltip of all Channels in the test round.
* **Number of Endpoints:** Total unique Endpoint Agents that joined the BSSID in the test round. Number of Endpoints is displayed in the tables but is not selectable available via the **Metric** selector.

 The new view has two tables:

* **Endpoint Table:** Displays metrics of each Endpoint Agent. The BSSID and metrics listed apply to the first BSSID membership during the test round.
* **BSSID Table:** Displays performance of each BSSID, with aggregated metrics from all Endpoint Agents that report data on this BSSID during a test round. Shows a sum of throughput, and an average of retransmission rates and wireless signal quality. Each Endpoint Agent will report data on one BSSID per round, so BSSIDs where an Endpoint Agent joins and leaves during a round may not be represented in this list.

Currently we support these new metrics in snapshots \(Shared Events and Live Shares\). We do not yet support these metrics in Reports or the API.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Widgets in Reports and Dashboards now support decimal values to two decimal places.
* Tooltips now will always display full information when hovering over Tiles in a Color Grid widget of a report.
* Fixed an issue causing links in email Alert Notifications to generate "Invalid parameters" errors when followed.
* Users whose login policy allows both single sign-on \(SSO\) and direct login to the application are no longer forced to use SSO in some circumstances.

## Questions and comments

Got feedback for us? Want to vote for your favorite feature or blog post? [Send us an email](mailto:support@thousandeyes.com?subject=2018-10-23+Release+Update)!

