# Release Notes: 2019-11-12

Welcome to our latest release!

IMAGE MISSING

The second annual Cloud State Live launch event will be held on November 13th in Austin, Texas, at Pershing. Join us in person or via live stream for the unveiling of this year’s Cloud Performance Benchmark report, as well as another exciting ThousandEyes announcement!

This year’s report adds Alibaba and IBM to the list of cloud providers from last year \(AWS, GCP, and Azure\).

Download last year's report if you're unfamiliar with the Cloud Performance Benchmark report, or if you’re interested in comparing last year's results with the new results.

Two new posts are also available on the ThousandEyes blog:

* Last week, Microsoft announced a new public performance dashboard for their Azure network, powered by ThousandEyes active monitoring. Angelique Medina, ThousandEyes’ Director of Product Marketing, outlines how this is a step forward for cloud transparency in her blog, [Microsoft Azure Releases Performance Dashboard Powered by ThousandEyes](https://blog.thousandeyes.com/microsoft-azure-releases-performance-dashboard-thousandeyes/).
* ThousandEyes continues to expand our Cloud Agent fleet in China, allowing users to leverage a wider collection of vantage points for monitoring and measuring regional performance. ThousandEyes’ Content Marketing Manager Sean R. Coombs explains why these agents are important in his post, [What Expanding Cloud Visibility in China Means for You](https://blog.thousandeyes.com/what-expanding-cloud-visibility-in-china-means/).

And now for the details of our release...

## Endpoint Agents

A couple new features for Endpoint Agents.

### Enable/Disable A​PI endpoint

​​​​​​Endpoint Agents can now be enabled and disabled via the ThousandEyes API. We've added the following two API endpoints for version 6 \(the current version\) and above:

* /endpoint-agents/{agentId}/enable
* /endpoint-agents/{agentId}/disable

When creating the HTTP request use the PUT method to send the enable or disable command, and specify the version in the URL if you're using version 7 of the API:

PUT /v7/endpoint-agents/{agentId}/enable

The response payloads for both endpoints will be identical; the content is specified by the [Endpoint Agent details](https://developer.thousandeyes.com/v6/endpoint/#/endpoint-data-endpoint-agents-agentid) endpoint.

### TCP in Scheduled Tests

In Scheduled Tests, we've removed the "TCP" option from the **Protocol** selector, and added the **TCP Connect** checkbox.

IMAGE MISSING

A new metric, "Connection failures" has been added to the test's Network view, which is the count of TCP connection failures across Agents running the test. Additionally, the Table tab of the test's Network views now displays a TCP Connect column which indicates the status of this portion of the test.

IMAGE MISSING

The TCP Connect message is also available in the tooltip displayed when hovering over an Agent in the Path Visualization.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release. Version numbers in parentheses indicate when a fix first appears \(when relevant, e.g. Endpoint Agent version\):

* Users no longer see a **+ Run Test**  option for Endpoint Agent tests if their roles do not contain the Edit Endpoint Tests permission
* Organizations without Endpoint Agent licenses no longer see Endpoint Agent menus \(which lead to 404 "Dud link" errors\)
* Endpoint Agents on version 0.177.2 no longer generate incorrect warnings that the version is out of date
* On the Agent Labels tab of the Endpoint Agent Settings, the **Filter** drop-down now correctly lists all selected Agents
* Fixed an issue preventing some users with a role containing the Edit User permission from creating new user accounts
* When an Alert List widget is configured to filter by certain Agents, Alerts from other Agents are no longer displayed in the widget

## Questions and comments

Got questions or feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-11-12+Release+Update)!

