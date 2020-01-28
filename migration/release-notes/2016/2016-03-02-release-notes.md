# Release Notes: 2016-03-02

If you haven't signed up already, keep in mind that we are two weeks away from **ThousandEyes Connect SF** on March 15, 2016!

IMAGE MISSING

Located in downtown San Francisco, We have some great presenters on deck, including Microsoft, RichRelevance, Zendesk and Cisco! This live event is free, and a great opportunity to network and engage with those who live and breathe networks.  For more details and registration, see the event registration page at: https://www.thousandeyes.com/events/connect/san-francisco-2016

Without further ado, here are our release notes for this week:

## New cloud agent locations

We've added cloud agents in two locations today:

* Riyadh, Saudi Arabia
* Brno, Czech Republic

The full list of cloud agent locations is available on our website, at https://www.thousandeyes.com/product/cloud-agents

Note: Trial accounts are assigned access to Cloud agents from a separate pool of locations, and do not have access to production agents.  If your account does not have access to this new location, please [contact us](mailto:support@thousandeyes.com?subject=Request+for+access+to+GA_PLUS+agent+group) to request it.

## Network tests

We've made two changes to the advanced options on network tests.  First, we've enabled an option to configure the DSCP marking on packets sent during network tests.  A list of available DSCP values can be found [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn1KAC).  We've also added an option to define the payload sizes of the ping packets being sent.  By modifying DSCP values, you'll be able to identify devices in the path from the agent to the destination which modify the DSCP markings on packets sent to the destination.

IMAGE MISSING

The manual ping payload size defaults to 1 byte, and allows values from 0 to 1400 bytes.  Default payload sizes are 0 bytes for ICMP and 1 byte for TCP-based tests.  It should be noted that these values can be set only on explicit network tests, and not on derived network tests \(for example, network tests on HTTP Server, Page Load or DNS Server tests\).  

## Reporting

We've continued to innovate on our reporting component in this release, and are introducing a number of new capabilities and modifying existing behaviors.

### Widget picker

As our widget selection has grown, we've changed how widgets are picked. We've replaced the text and color option for widgets with a representation of the widget that you'll be placing on your reports.  The numbers shown in the image below correspond to the list below.

IMAGE MISSING

1. Stacked bar/column chart
2. Grouped bar/column chart
3. Time series line chart
4. Time series stacked area chart \(new, see below\)
5. Pie chart
6. Table
7. Multi-metric table \(new, see below\)
8. Numbers

### Stacked area widget

As inferred above, we've added a new widget type, allowing charting of composite data types. The stacked area widget will be particularly useful when looking at increases in overall response timing, error counts, and other components. Use the stacked area chart in place of where you're using stacked bar charts today, to show a progression of values over time.

IMAGE MISSING

Stacked area widgets are available at present for response time, total fetch time and total error count metrics on HTTP Server tests.  This list will grow over time.

### Multi-metric widget

I'm excited about this widget, because it enables us to show multiple metrics for a test in a single table.  It simplifies reporting, and allows optimization of space in a report.  Let's look at a couple of scenarios:

Want to see your network latency by test showing min, max, mean, standard deviation, and a percentile value in a single table?  No problem: create a table that shows tests as rows, and each measure/metric combination for columns.

IMAGE MISSING

How about metrics that span layers?  HTTP, Page Load and Loss/Latency all in a single table for a test?  Sure!  No problem: create a table that shows tests as rows, and each measure/metric combination for columns.

IMAGE MISSING

### Server grouping and filters

We've completed the feature adding aggregation and filtering by server \(for HTTP, Page Load, Network and DNS Server tests\), introduced in our last release.  Here's a cool feature - the ability to aggregate performance not by test, but by destination server.  In the example below, I've selected 3 tests, and told the widget to aggregate by server \(destination name:port tuple\).  In the background, the reports engine identifies that we have two tests targeting the same destination server, and aggregates those values into a single chart for each destination.

IMAGE MISSING

### Snapshot autosharing

In addition to the new widgets shown above, we've added the ability to automatically make report snapshots public.  The addition of a checkbox at the bottom of the Schedule Snapshots modal allows you to make snapshots created on a recurring basis to be shared automatically with your recipients. 

IMAGE MISSING

Checking the "Auto Share Snapshots" checkbox will create a public link automatically, which can be used without requiring authentication.  

## Minor feature additions

### Custom header for web tests

All web tests will now include a custom header of "**X-ThousandEyes-Agent: Yes**". Since we introduced the user-agent capability, there has been no definite way to filter out synthetically generated traffic from Web Analytics platforms. This applies to HTTP Server, Page Load and Web Transaction tests.  We'll be phasing out the legacy default user-agent string of User-Agent: Mozilla/5.0 AppleWebKit/999.0 \(KHTML, like Gecko\) Chrome/99.0 Safari/999.0 over the coming 45 days.  

Customers using a mechanism to filter traffic from their destination websites should move to filtering based on the _presence_ of the new custom header, as the value of the header may change over time, but the presence will not.

IMAGE MISSING

### Web Transaction modifications

We've made two tweaks to how we handle web transactions. First, the first step \(step 0\) of a web transaction must be an open command. This is intended to make the transaction creation process more seamless and reduce the support requirement on creating web transactions.  We've also added a custom sleep\(\) command to web transactions. Specify the number of milliseconds to wait without further action between steps of a web transaction. This can now replace the legacy window.waitFor\(\) syntax that we were using to manage a pause.  The ThousandEyes recorder has been updated to reflect this addition.

### Agent test queue optimization

We've also optimized the agent test queuing model to prioritize more frequently-run tests. Prior to the introduction of this feature, if a test running at a high frequency was placed on a highly loaded agent with a number of lower-frequency tests, the higher frequency test could end up skipped due to a FIFO model for testing at the agent level. This fix should result in more consistent execution of higher-frequency tests.

## Bugs squashed

We've corrected a few bugs in this week's release:

* When duplicating tests from the test settings page, certain advanced settings weren't being copied to the new test.
* When using the api /test/{testId} endpoint for DNS servers would display multiple agents for a DNS server test
* Under certain circumstances, it was possible to create a multiple Alert Suppression windows for the same time period.
* We've made a number of fixes related to the performance and resiliency of the BrowserBot component, dealing with issues related to errors thrown by the BrowserBot component during Page Load or Transaction test execution.
* We've made changes to make the bandwidth metrics collection more tolerant of high latencies.

## Feedback?

Seriously, I put this in the release notes every week, and have yet to receive a response.  That's ok, we're not lonely here at ThousandEyes - but, we know that you have an opinion about the application, and we're opening up - we want to hear it!  Just [drop us a note](mailto:support@thousandeyes.com?subject=2016-03-02+release+update), any day, any time.  Feedback is always welcome! 

