# Release Notes: 2015-09-30

It's been another busy couple of weeks for the team here at ThousandEyes.  We're introducing a number of changes in user interface behavior this week, as well as changes to improve the performance of various components of the platform.  Check out our notes below, and let us know if you have any questions!

## Search behavior in path visualization

A few minor behavioral updates to how search works in Path Visualization and BGP visualization interfaces.  When entering search criteria into the search box, elements matching the search will be emphasized on the visualization, by dimming other elements in the visualization.  This will make it simpler to scan the visualization and find matching elements.  We've removed the yellow highlight that was traditionally used to emphasize the elements in the visualization matching the search criteria.

IMAGE MISSING

When one or more objects is found by the search, the number of objects matching the search will be shown below the search box; click this link in order to select the highlighted objects in the visualization.

IMAGE MISSING

## Reports

We've added some major features to our reporting capabilities this week: Stacked and Grouped bar chart widgets have been made available in reporting!

### Stacked Bar Charts

Stacked bar charts are generally useful for composite metric data \(such as HTTP response or fetch time\), and comparing values between multiple tests, or comparing values on a country basis. The following two examples use the same four HTTP server tests and show data breakdown on using different groupings:

IMAGE MISSING

IMAGE MISSING

At present, users can report on representing multi-metric timings, such as:

* **Response time** \(includes DNS, SSL, Connect, Send, Wait times\)
* **Total Fetch time** \(includes DNS, SSL, Connect, Send, Wait, Receive times\)
* **Total Error count** \(breakdown of errors on HTTP server test, broken down by error type\)

Both options can be oriented either vertically or horizontally, however our general recommendation for usability is to report horizontally in order to maximize the individual segments of the charts.

### Grouped Bar Charts

Grouped bar charts can operate either as column \(vertical\) or bar \(horizontal\) charts, in order to represent your data.  As with stacked charts, grouped charts allow breakdown on a regional basis as well, but represent all data as single bars. The example below shows a the same data as in the stacked charts, but breaks down the data on both a test and continent basis.

IMAGE MISSING

For more information on using Bar Charts in reporting, [refer to this article.](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS)

### Performance enhancements

We've made some changes on the back end of our reporting system to make reporting handle generation of reports with very large numbers of data points in more performant manner.

## Bandwidth tests

Users will now be able to run TCP-based bandwidth tests against destinations which do not support selective acknowledgements \(SACK\). Prior to this update, only destinations supporting SACK were able to be tested using TCP-based bandwidth tests.

## BrowserBot update for Red Hat-based linux distributions

We're updating our BrowserBot distribution on Red Hat linux-based distributions to Chromium 40. A few months ago, we updated the BrowserBot component on Ubuntu and Red Hat 7-based systems, in order to modernize and take advantage of some advancements made on the browser. This week, we're moving to a harmonized BrowserBot codebase, which is intended to make browser-based test results \(including waterfall charts\) consistent between installed enterprise agent architectures.  This change affects the following supported linux distributions:

* Red Hat Enterprise Linux, versions 6.3-6.7
* CentOS, versions 6.3-6.7
* Oracle Enterprise Linux, versions 6.3-6.7

## Private BGP peering now supports IPv6

We've added new BGP collectors to our infrastructure in order to accommodate customer requests for IPv6 peering.  If you'd like to set up a peer with our v6 collector, under the settings menu, open the BGP monitors option, and complete the form adding an IPv6 address for a monitor.

## Bugs & minor features

* Corrected a minor issue which could result in a "no route to host" error when running a test from an IPv6 agent running on linux kernel version 4.
* Alert data retrieved via the ThousandEyes API now shows an empty string for the **metricsAtEnd** field, while an alert is active
* Updated **startedDateTime** value in waterfall data returned by ThousandEyes API using http://developer.thousandeyes.com/test\_data/\#/page-load-components endpoint.  Prior to this update, the value was returned as null.
* Exposed **probDetails** field in Page Load test results returned by ThousandEyes API
* Updated main alerts page linked by the permalink field returned in a ThousandEyes API query for an alert, to handle permalinks which are older than 30 days.  Prior to this update, attempts to open such a permalink would result in a "dud link" page.

## Questions & comments?

Yep, even though nobody ever emails us to comment on these release notes, we do love hearing from our customers.  If you have anything you're curious about, or even want to learn more - just [drop us a note](mailto:support@thousandeyes.com?subject=2015-09-30+Release+Update).

