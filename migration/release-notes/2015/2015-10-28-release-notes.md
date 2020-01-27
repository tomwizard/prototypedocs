# Release Notes: 2015-10-28

Has it been two weeks already?  When we last left our superheroes, we were preparing for [ThousandEyes Connect's inaugural New York City meeting](https://blog.thousandeyes.com/connect-nyc-2015-summary/), and we've tracked a pretty interesting east-coast centric outage on October 15th with [Neustar's UltraDNS service](https://blog.thousandeyes.com/ultradns-outage-october-2015/).  In case you missed some of those sessions, keep an eye on the ThousandEyes Blog at http://blog.thousandeyes.com - we'll be publishing each of the presentations in due course.

Most of today's changes are transparent, but we've made a few visible updates to the reporting interface.  Check out the updates below.

## New cloud agent locations

This week, we've added cloud agents in the following locations:

* Sacramento, California
* Kharkiv, Ukraine

These agents are immediately available to paying customers. Please note that access to these agents is not included in trial subscriptions.

## Reports

We've made a number of updates over the course of the last few weeks to the reporting infrastructure.

### Performance improvements

Some reports - particularly those leveraging large numbers of alerts - were slower to generate than desired.  We made some changes to improve the performance of alert-based reports.

### Time range

First, the default time range will now show 7 days instead of 30 days. To change the window of time shown in the report, drag the scrubber, or click the link above the timeline to change the displayed window of time. 

### ThousandEyes Built-in report

We've made few updates to the ThousandEyes built-in report.

We've also updated the Alert Table report widget to report alerts against each test, by continent.  Prior to this update, the table reported alerts against each test by agent.

## Bugs fixed

We've also made a few minor corrections to features in the application, per the list below:

* Some users have reported issues while rendering test widgets, wherein the test list wouldn't be rendered.  This was due to a race condition, which has been resolved in this release.
* In cases where the _Show HTTP headers in waterfalls_ option is selected in a Page Load or Web Transaction test, clicking the headers icon next to a component in the waterfall view would fail to pop up a list of headers for the object.  This has been corrected.

## SSLv3 removal notice

We are announcing that SSL 3.0 will be disabled on the ThousandEyes API in our next release, on Wednesday, November 11.  

Please note that this applies only to api.thousandeyes.com.  Our main services \(running as app.thousandeyes.com\) have only supported TLS 1.0, 1.2 and 1.2, since October 2014.  Support for SSLv3 on the api.thousandeyes.com endpoint was left enabled until now in order to provide support for some third party integrations, which have subsequently been updated to support the use of TLS 1.0, 1.1 and 1.2.

## Questions & comments?

We really do love hearing from our customers.  If you have anything you're curious about, or even want to learn more - just [drop us a note](mailto:support@thousandeyes.com?subject=2015-10-28+Release+Update).

