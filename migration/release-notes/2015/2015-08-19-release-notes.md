# Release Notes: 2015-08-19

Just a few updates this week.  Note that we won't be making a regularly scheduled release on September 1st, so the next release notes won't be released until September 16th.  On behalf of ThousandEyes, enjoy your labor day holidays!

## New ASN, new network prefix

As mentioned in our [release update on August 5th](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmlSKAS), we're now announcing a new network prefix.  We've moved c1.thousandeyes.com to the new prefix as of tonight, and more infrastructure will change over the course of the coming weeks.

* c1.thousandeyes.com now points to 192.150.160.17

Customers who explicitly whitelist the ThousandEyes infrastructure should whitelist the new prefix, 192.150.160.0/24.  IPv6 addressing at this time remains unchanged for these destinations.

## Agent grouping in map views

We've changed our algorithm for how we're displaying agents in the map view.  Rather than showing a number of overlapping circles for agents in close proximity, we now group the agents until they're no longer overlapping based on zoom level.

IMAGE MISSING

IMAGE MISSING

## Virtual Appliance changes

### Operating System, architecture updates

We're now shipping ThousandEyes Virtual Appliances in a 64 bit configuration, running Ubuntu LTS 14.04 \(aka Trusty\).  Prior to this update, Virtual Appliances ran using Ubuntu LTS 12.04 \(aka Precise\), in a 32-bit configuration. 

### Web Proxy signing certificate support

We've added support for customers to use ThousandEyes Enterprise Agents with web proxies that manage SSL decryption. To integrate with such a system, provide the CA certificate as a part of the web proxy settings provided during agent configuration.

IMAGE MISSING

## Responsive view effort, continued

Users will notice that the Views page now leverages the entire canvas of a page.  Users with browsers wider than 1200 pixels will now be able to take advantage of the entire browser area.  This is a continuation of our efforts in the area of responsive design, first introduced into the dashboard and reports interfaces.

IMAGE MISSING

IMAGE MISSING

## Page tours updated

We've updated a lot of content in our page tours.  To launch a page tour, click the ? icon on the right side of the menu bar, and click Page Tour.  You'll be greeted with an interactive guide that walks you through relevant elements on the page, along with giving you pointers to relevant articles and videos, based on your current view.  Check them out and let us know what you think.

IMAGE MISSING

## Questions, comments?

We still like hearing from you! Drop us a line at [support@thousandeyes.com](mailto:support@thousandeyes.com?subject=2015-08-05+Update) and let us know what you think.

