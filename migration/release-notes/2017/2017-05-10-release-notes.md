# Release Notes: 2017-05-10

Welcome to tonight's program!

Headed to Interop in Las Vegas next week? Stop by our booth and introduce yourself if you're a new ThousandEyes customer, or renew acquaintances if you're a long-standing ThousandEyes users. Either way, you'll probably get a t-shirt for your efforts.

Archana Kesavan's latest blog post is entitled [Best Practices for an Internet-based SD-WAN](https://blog.thousandeyes.com/best-practices-internet-based-sd-wan/). In addition to info on software-defined wide-area networks, you'll also get a peek of a BGP Visualization from the route leak by a Russian ISP, Rostelecom, affecting major financial and e-commerce sites' networks.

On with the show!

## Enterprise Agents

Agent utilization is a common subject of support cases. We've added two new features to make management of Agent Utilization and of Agents in general easier.

### Utilization in Enterprise Agent clusters

We've changed the way Agent Utilization is reported by clustered Enterprise Agents. Previously, we reported utilization of the cluster members, rather than the cluster itself. We've now switched: utilization of clusters is now reported under a new **Cluster Statistics** tab, and the individual Agents no longer display the **Agent Statistics** tab, as long as they remain in the cluster.

IMAGE MISSING

### Cross-Account Group Test Management

To more quickly address high utilization, we've added a utility for managing tests assigned to Enterprise Agents and Enterprise Agent clusters. A new **Manage** link is available on the Agent Utilization graph under the Agent Statistics tab \(individual Enterprise Agents\) or on Cluster Utilization graph under the Cluster Statistics tab \(Enterprise Agent clusters\). Clicking the link will display a list of the test queues for which the Agent has at least one test assigned.

IMAGE MISSING

In the above image, the Enterprise Agent has utilization graphs for four queues:

* Browser Tests
* HTTP Server + DNS + Network Tests
* Agent To Agent Tests
* Bandwidth + Throughput Tests\)

  The **Manage** link displays three queues. The Agent To Agent Tests selection is absent because this Enterprise Agent has no Agent to Agent tests assigned to it. Note however that if an Agent which is not assigned an Agent to Agent test runs the test because it’s configured in the **Target for Test** setting, utilization occurs in either the Agent To Agent Tests queue or Bandwidth + Throughput Tests queue, depending on whether the test's **Throughput** option is selected.

Clicking on one of the queues displayed by the **Manage** link will open the Manage Utilization window. The window displays a list of Account Groups and the number of tests from each Account Group that the Agent is running. Expand an Account Group and select an individual test, or all tests by selecting the Account Group. Then click the **Remove** button to remove these tests from the Agent.

IMAGE MISSING

When the **Send email notifications to users who made the last change on removed tests** box is checked, an email with a subject of "Tests removed for agent - &lt;Agent name&gt;" is sent to the login email address \(as configured in the user's Profile tab of the Account Settings\) of said user:

IMAGE MISSING

## Bug fixes & minor features

Here's the bugs and minor features in this week's release:

* Updated some of the "Shared by ThousandEyes" tests.
* Fixed an issue in the Virtual Appliance when trying to change the existing IP address.
* Fixed an issue that prevented display of the Agent Groups Filter drop-down menu in an Enterprise Agent Status widget.
* Fixed an issue with Page Load tests indicating a successful load of the page when a timeout is indicated in the data.
* Fixed an issue which prevented disabling Voice Call tests from Cloud Agents \(beta customers\).

## ​Questions, comments?

If we don't see you in person at a trade show, feel free to [virtually introduce yourself](mailto:support@thousandeyes.com?subject=2017-05-10+Release+Update) and tell us what's on your mind, ThousandEyes-wise. We'd love to hear from you!

