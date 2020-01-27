# Release Notes: 2017-09-27

Welcome to the first release of the fall season!

IMAGE MISSING

### ThousandEyes Connect

We'll be having our next ThousandEyes Connect event in Chicago on October, 11. [Registration](https://www.thousandeyes.com/events/connect) is now open. Come swing by the Windy City, the Second City, the [City of Big Shoulders](https://www.poetryfoundation.org/poetrymagazine/poems/12840/chicago) to hear some great presentations from ThousandEyes users and employees!

### NANOG

[NANOG 71](http://www.cvent.com/events/nanog-71/event-summary-4f71b2f3181e49c1ab199f5d5d405bb8.aspx) will be in San Jose, California starting Monday, October 1st, with a hackathon starting the prior weekend. If you're headed to the event, we'll be sponsoring lunch on Tuesday, doing product demo's, and of course, there will be t-shirts.

### WAN Summit

If you're in Europe and plan to be attending the [WAN Summit](https://www.wansummit.com/london/index/) on October 17th and 18th in London, come say hello to the folks from our London office, who will be manning our exhibition booth.

### Cisco Connect

If you want to connect with ThousandEyes, there's lots of opportunity to meet us face-to-face in the coming weeks. We'll be attending [Cisco Connect](https://www.cisco.com/c/en/us/training-events/events-webinars/cisco-connect.html) events across the USA and Canada. If you're going to attend one of the following events, come say "hi" to us, chat about your needs, learn about new features in the product, or just get some swag in the form of cool new t-shirts.

| **Location** | **Date** |
| :--- | :--- |
| Minneapolis, Minnesota | October 4 |
| Albuquerque, New Mexico | October 4 |
| Rochester, New York | October 10 |
| Tampa, Florida | October 11 |
| Toronto, Ontario, Canada | October 12 |
| Manhattan, New York City, New York | October 12 |
| Washington, District of Columbia | October 17 |
| Irving, Texas | October 17 |
| Detroit, Michigan | October 18 |
| Nashville, Tennessee | October 24 |
| Austin, Texas | October 26 |

And that's only a partial list. We'll be at [ONUG](https://www.onug.net/) in New York City, [Angelbeat](http://www.angelbeat.com/event-directory/) in Baton Rouge/New Orleans, and [FS-ISAC](https://www.fsisac-summit.com/) in London.

Until we meet, here's tonight's release!

## Cloud Agents

Still more new Cloud Agent locations coming online, courtesy of our Operations team. Here's the new locations:

### IPv4

* Calgary, Canada

### IPv6

* Dublin, Ireland
* Edinburgh, Scotland
* Houston, Texas, USA
* Riyadh, Saudi Arabia

## API version changes

Per our announcement in the [previous Release Update](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RwJCAU), we are changing the default version of the ThousandEyes API from version 5 to version 6. Users whose queries specify version 4 \(queries which begin with [https://api.thousandeyes.com/v4\](https://api.thousandeyes.com/v4\)\) will have 90 days to make the necessary changes to their queries. After the 90-day transition period, version 4 will no longer be available. We recommend updating any v4-based queries to use the current version of the API \(no specification of version in the query\) in order to avoid the need for future changes.

## Reports and Dashboards

### New Reports permission

Previously, the same permission, Set dashboard template as account group default governed setting both the default dashboard the and default report for an Account Group. We now separate the permissions:

* Set dashboard template as account group default \(existing permission\) and
* Set report template as account group default \(new permission\)

For the introduction of this new permission, those roles that have the existing permission will now have the new permission, and those roles which do not have the existing permission will not have the new permission.

### Map widgets

We've improved the iconography for displaying status of multiple Enterprise Agents in a single geographic region. We now display online, offline and disabled Enterprise Agents on a map widget using green, red and grey arcs \(respectively\) on the border of the dot which displays the location and number of the Enterprise Agents. The length of the arc is proportional to the number of Agents in each of the three categories. For example:

IMAGE MISSING

In the region above, there are 8 Enterprise Agents. One is online \(green\), four offline \(red\) and three disabled \(grey\). Mousing over the dot will display a tooltip with the detailed listing of Enterprise Agents, grouped by the status.

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* The Map tab Added source IP address and source prefix to the API's Path Visualization endpoint.
* Improved axis alignment in Time Series widgets so that multiple vertically stacked widgets will fully align.
* Stacked area widgets now display a singe row in their tooltip stating "No Data" if all data sources have no data.
* Test view no longer shows multiple occurrences of the same alert, in some circumstances.
* Too-large POST bodies sent to the API now result in an HTTP status of 400 instead of 500. The maximum size is now 65,535 bytes.
* Fixed an issue in the Path Visualization's traceroute-style output option which could produce missing stars
* Fixed an issue for users who have not been verified but attempt to reset their password for the platform.
* Fixed an issue that caused incorrect page numbering in waterfalls for Transaction tests.

## ​Questions, comments?

Can't make it to an event but still want to connect with ThousandEyes? We'd love to know what's on your mind. [Send us an email](mailto:support@thousandeyes.com?subject=2017-09-27+Release+Update).

