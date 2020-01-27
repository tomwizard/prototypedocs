# Release Notes: 2014-06-11

In the wake of our monster updates last week \(you can check the release notes [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmloKAC)\), our release this week contains a few bug fixes and minor feature additions. Check out the list below and [let us know](mailto:support@thousandeyes.com?subject=Release%20Questions) if you have any questions.

## New BGP alert rule option

When an IP is announced via multiple prefixes, false BGP alerts can be thrown if one of those prefixes is no longer reachable.  

Let's use the example **1.2.3.4**, which is announced through these network prefixes:

* **1.0.0.0/8**
* **1.2.0.0/16**
* **1.2.3.0/24**

The only network prefix we're really interested in is the one with the longest prefix \(**1.2.3.0/24**\).  Therefore, we can craft an alert rule that excludes prefixes 1.0.0.0/8 and 1.2.0.0/16 from alerting.  To do so, I would create the alert with the following criteria.  Note the selection of the second metric and operator.

IMAGE MISSING

This will force the alert processor to consider only the /24 prefix desired when determining whether or not to trigger alerts.

Another approach would be to configure the alert to be based on Prefix is in \(1.2.3.0/24\), however we've gone with the **not in** approach in order to allow this rule to be reused on other tests.  Working with an exclusion list rather than an inclusion list allows for greater flexibility.

## Create ICMP network tests via API

A \`protocol\` field can now be specified when creating network tests via the ThousandEyes API. This can be set to ICMP when creating new network tests. Check the [ThousandEyes developer reference](http://developer.thousandeyes.com/#/changesummary) site for more information.

