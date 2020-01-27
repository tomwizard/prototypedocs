# Release Notes: 2018-01-10

Welcome to the first release of 2018! We hope you had a happy holiday season.

First, a quick announcement regarding our next release. Normally, releases occur every other Tuesday. However, we will have our next release next Tuesday, and then return to the usual pattern. Twice the fun to start off 2018!

Our VP of Product Marketing, Alex Henthorn-Iwane, has the first blog post of the new year. Alex summarizes a presentation from [ThousandEyes Connect in Chicago](https://www.thousandeyes.com/events/connect/chicago-2017), given by Jim McKinstry. Jim is a Global Product Manager at JLL, Inc., one of the US's foremost property management firms. Entitled [How JLL Ensures Performance of Business Critical Applications](https://blog.thousandeyes.com/how-jll-ensures-performance-business-critical-applications), Jim's presentation explained how JLL relies on ThousandEyes for monitoring key revenue-generating applications.

And now the details of tonight's release.

## API version 4 deprecation

As of tonight's release, API version 4 will be deprecated, and queries to version 4 endpoints will return results from the lowest supported API version, version 5. Customers who are specifying version 4 in their queries will now need to use version 5 or version 6 \(the current default\). To review the syntax of specifying versions \(or using the default\) in API queries, see our [API documentation](http://developer.thousandeyes.com/v6/#/versioning).

## Alert Rules

### Error details

Previously, Alert Rules for most test types either had an "Error" or "Error Type" option in the Alert Conditions. This release simplifies the options into one "Error" option, and we have added the option to some test types to match \(or not match\) the full error text using a regular expression. For those test types, when "Error" is selected, the "match" and "does not match" actions are selectable, and a text field appears which accepts a regular expression. For example, an HTTP Server Alert Rule of:

IMAGE MISSING

  
will match any text in the **Error Details** field of a test that contains the word "Connection", such as:

IMAGE MISSING

###  BGP Path Visualization

We've revamped the Alert Rules for specifying ASN hops in Alert Rules of type BGP. The Alert Condition "Origin ASN" is now called "BGP Origin" and "Next Hop ASN" has been replaced with "BGP Hop \#" and "Any BGP Hop". BGP Hop \# can be specified as a number of hops from either the origin ASN or from the monitor\(s\). This change makes easier the construction of alerts for changes in upstream providers and other peers.

## Endpoint Agent

An issue was discovered in Endpoint Agent which could prevent Endpoint Agents from automatically updating. We've released a [Knowledge Base article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SRYCA2) with additional information.

## Bug fixes & minor features

Here's the list of bug fixes and minor features in this week's release:

* The selectWindow command in a Transaction test now accepts an empty argument in order to select the parent window.
* Fixed an issue with stacked bar charts which could cause an extra bar to be drawn in the widget.
* Fixed an issue with stacked bar charts which could cause long load times when displaying the widget.
* After deleting a DNS Server from an existing DNS Server test, the deleted server is no longer listed in the Table tab.
* Users who have the role "Regular User" and were unable to run certain Web Layer tests as Instant Tests can now do so.
* Alerting behavior has been improved to clear alerts upon reception of all data in a round. Previously, the behavior was to wait until the beginning of the next round to trigger the clearing.

## ​Questions, comments?

Got a question, a comment, or a new year's resolution that you'd like to share with us? [Send us an email](mailto:support@thousandeyes.com?subject=2018-01-10+Release+Update)!

