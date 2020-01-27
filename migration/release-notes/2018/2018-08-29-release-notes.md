# Release Notes: 2018-08-29

Welcome to tonight's release! Lots of major new goodies rolling out in tonight's release. But before that, the blog roll...

It's never too early to start your Christmas preparations, particularly if you're an online retailer. Our VP of Product Marketing, Alex Henthorn-Iwane, writes in [Why Network Visibility is Key to Retail Holiday Success](https://blog.thousandeyes.com/why-network-visibility-is-key-to-retail-holiday-success/), that online retail success during the peak traffic season can depend on the ability to monitor cloud-based components, from DNS and anti-DDoS providers to Infrastructure-as-a-Service vendors. Visibility into the effectiveness of these services will ensure the Christmas retail experience doesn't result in a lump of coal in one's stocking.

ZSecond up: ZSolutions Engineer Nitin Nayar's zsecond article in his zseries, [Troubleshooting Real World Zscaler Issues](https://blog.thousandeyes.com/troubleshooting-real-world-zscaler-issues/). In this article, Nitin discusses a ThousandEyes customer's pre-deployment testing of a cloud-based CRM system. Using ThousandEyes Enterprise Agents to test with and without the Zscaler, the customer was able to determine the new architecture's effects on their application, and work with both service providers to address performance issues. We guarantee this post is no zzzz'er.

Lastly, our Senior Director of Product Management, Nick Kephart, provides us with [What’s New in Q2 2018](https://blog.thousandeyes.com/whats-new-q2-2018-product-updates/), this quarter's roll-up of features we've released over the past few months. If you need a quick way to get up to speed on the summer's new features, this one's for you.

And now for tonight's new features. Drum roll please...

## Cloud Agents

 We've added a new Cloud Agent in Lima, Peru. ¡Hola, rimaykullayki and laphi!

## Endpoint Agent scheduled tests

 For those customers who need the power of a regularly scheduled test from a location of their choosing, but don't want to set up an Enterprise Agent, we now offer scheduled tests on Endpoint Agents. Users may now create HTTP Server and Agent to Server tests and assign them to Endpoint Agents, to be run at regular intervals, automatically--no human required. Under the Tests settings menu, you'll now see Endpoint Tests, where you'll see a listing of your existing tests, and an **+ Add New Test** form:

IMAGE MISSING

Endpoint Tests are assigned to an Agent Label, which contains Endpoint Agents. All Endpoint Agents matching the Label will run the test, subject to the rule that each Endpoint Agent can run a maximum of 3 tests. Endpoint Agents that are no longer in contact with the ThousandEyes collector are removed from their Label\(s\) after 1 hour. Editing or creating Endpoint Tests requires a role with the Edit endpoint tests permission.

Additionally, Alert Rules can be configured for the HTTP Server and Agent to Server test types, and Reports can use Endpoint Agents as a data source.

For more information on Endpoint Agent test configuration, see the ThousandEyes Knowledge Base article [Creating scheduled tests on Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS). For more information on Endpoint Agent test results, see the ThousandEyes Knowledge Base article [Endpoint Agent Views - Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpWcCAK).

## API

### Scheduled Tests for Endpoint Agents

In conjunction with the new Scheduled Tests for Endpoint Agents, we have new API endpoints:

* /endpoint-tests
* /endpoint-data/tests/net/metrics
* /endpoint-data/tests/net/path-viz
* /endpoint-data/tests/web/http-server

In addition. we have added Endpoint Agent Labels and Endpoint Test Labels to the /groups API endpoint.

### Instant Tests for Cloud Agents

We've added the ability to run [Instant Tests](https://developer.thousandeyes.com/v6/instant/) on Cloud Agents using the API's /instant endpoint. Instant Tests consume Units when run on Cloud Agents, and on metered Enterprise Agents.

## Alert Rules

### User interface improvements

On the Alert Rules settings page, we've replaced the **+ Add New Alert Rules** form with a modal, which will also be used when editing existing Alert Rules.

### Alert Conditions for Page Load tests

We've added some new Alert Conditions options for Page Load Alert Rules. Previously the "Page Load" condition had one option: "is incomplete". We've added two options: "timed out" and "has error". In keeping with other Alert Rule types, the default option that will display when creating new rules will be the "has error" option.

## Browser-based tests

### Chromium upgrade

Page Load and Transaction tests \(a.k.a. "browser-based" tests\) are run by code based on the open-source Chromium browser. In tonight's release, we are upgrading our version of Chromium from version 55 to version 68. So if your browser-based test displays an error due to a [Symantec-issued digital certificate](https://security.googleblog.com/2017/09/chromes-plan-to-distrust-symantec.html) after tonight, you'll know why.

### Page Load test increased frequency

Page Load tests can now be run at 2-minute intervals, up from the previous maximum frequency of 5 minutes.

## Activity Log improvements

We have made improvements to the usability and performance of the Activity Log. For starters, we've improved the time selector, allowing easy selection of predefined or custom time ranges.

We have also improved the filtering of the of the Activity Log listing, which now uses the standard filter found in other listings. Some information previously displayed in columns is now moved into the filter. For example, the client IP Address of the user generating an event is now a filter \(IP address is also available as a tool-tip in the Who/Source column, its icon appearing when the user hovers over a row in the listing\).

We have also recategorized and created two new columns in the listing, to better describe the events. The column that was previously called **Events** now becomes **Event Type** and **Component**. Event Types can have the following values: 

* **System**: Events affecting the entire application
* **Administration**: Events performed to administer the application 
* **Operation**: Events that affect a specific part of the application, such as a Test or Agent
* **Exception**: Events that denote an error

Components classify the Event Types based on the elements they act upon, and can have the following values:

Tests, Agents, LiveShares, Dashboards, Alerts, Endpoint Agents, Devices, Snapshots, User, Account Group, Organization, and Integration. 

The values that were previously under the Events column have been moved into the filter as Events.

## Minor enhancements & bug fixes

Here are the minor enhancements in this week's release:

* Device Layer metrics are now available to Reports widgets. Select "Devices" under the Data Source field of the widget.
* Time series widgets in Reports now permit setting the upper and lower values for the Y-axis. Select the values using the Scale field of the widget.
* In Path Visualization, improved the readability and eliminated loops on grouped nodes with common attributes.
* In Path Visualization, we now perform validation of geolocation information with the same algorithm used on public IP addresses.

## Questions and comments

Got questions or feedback on the new features? Want to share a cat video that's got you ROTFL? [Send us an email](mailto:support@thousandeyes.com?subject=2018-08-29+Release+Update)!

