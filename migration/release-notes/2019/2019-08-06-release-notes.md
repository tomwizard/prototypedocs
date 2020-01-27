# Release Notes: 2019-08-06

Welcome to our latest release!

Before the details of the release, one quick plug for our latest ThousandEyes blog post, [Building a Chrome Extension from Scratch](https://blog.thousandeyes.com/building-chrome-extension-from-scratch/), by Software Engineer Florent Garit.  If you're at all curious as to how a browser extension works, Florent explains the architecture of our recently upgraded Endpoint Agent, which is a Chrome extension. Even if you're like me \(not a developer\) who didn't understand everything, seeing what's under the hood of a browser extension is worth the two minutes. And reading a bunch of developer technicalese makes you look like you're doing real work!

And if you're not curious, then just know we are in the process of updating our Endpoint Agent!

And now for the details of the release...

## Cloud Agents

A new addition to the Cloud Agent family: Lisbon, Portugal \(both IPv4 and IPv6\). Bem-vindo!

## Enterprise Agents

We've completed our refresh of the user interface for Enterprise Agent settings. This release adds the finishing touches with the new-look Agents and Clusters tabs. For example, clicking in the listing of Enterprise Agents or clusters will now display details in a sliding modal window instead of expanding a row in the list.

IMAGE MISSING

And warnings previously supplied by hovering over triangular red icons now are available from the yellow or red colored dots in the **Status/Last Contact** column.

IMAGE MISSING

## Endpoint Agent Page Speed metric

We've added a new metric to the Visited Pages view of the Endpoint Agent's Browser Sessions. The Page Speed metric is a qualitative ranking of how fast a user would perceive the page load. Values are "Very fast", "Fast", "Average", "Slow" and "Very Slow", with accompanying green-yellow-red icons.

IMAGE MISSING

The Overview tab displays the scores of each page browsed during the session, and the Pages and Sessions tabs provide an Average Page Speed column which provides the mean value of the session's scores.

## Device Manager CPU and Memory metrics

Device Manager can now collect CPU and memory percentage used from devices which provide that information.

IMAGE MISSING

The Memory and CPU metrics are displayed in the rightmost columns under the **Device Table** tab of the Network view.

## API

An enhancement to the /tests API endpoint \(\#1\); an addition and a change to the /alert-rules endpoint \(\#2 and \#3\), and an addition to the /usage endpoint \(\#4\).

1. Users can now modify the targets of existing tests through the API, bringing the API into parity with the app
2. We've added the optional direction parameter for Alert Rules used on Agent to Agent tests. The parameter is readable and writable. Possible values are "TO\_TARGET", "FROM\_TARGET", and "BIDIRECTIONAL".
3. We've changed the returned value of the expression parameter for Alert Rules and ruleExpression parameter for Active Alerts. Previously, the returned value was in a human-friendly form, but which could not be used when writing to the same parameter. Now the returned value is suitable as a value for expression when writing to the endpoint.
4. The /usage API endpoint now provides the enterpriseUnitsUsed, enterpriseUnitsProjected, and enterpriseUnitsNextBillingPeriod parameters to obtain unit usage in the current billing period, the projection at the end of the current billing period and the projected use the next billing period, respectively. These parameters only apply to Enterprise Agents in an organization with a metered plan.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release:

* The Account Settings menu now has a separate Organization Settings submenu that contains the "Security and Authentication" and "Advanced Settings" tabs for organization-wide configuration
* Dashboards can now include the Endpoint Agent's Experience Score metric in widgets
* Dashboard and Reports widgets can now group by the Source Agents and Target Agents settings when the data source is an Agent to Agent test
* Pie chart widgets now display slices for all metrics in all cases
* Time Series widgets no longer display "Loading Data Failed" error when an Endpoint Agent Label is used as a filter
* Added attributes to SCIM v2 responses for RFC 7643 compliance
* Fixed an issue where an Endpoint Agent could display a 0% Experience Score rather than indicate no data in that session
* Fixed an issue which could lock out an organization's Endpoint Agents when converting from a trial account to a paid subscription
* On the "Get Started with Endpoint Agent" Test Settings page, the **Create New Test** and **Close** buttons now work correctly
* On the HTTP Server view of an Endpoint Agent Scheduled Test, the DNS Time is no longer off by a factor of 10^6

## Questions and comments

Got feedback for us? Want to tell us not to start sentences with "And"? [Send us an email](mailto:support@thousandeyes.com?subject=2019-08-06+Release+Update)!

