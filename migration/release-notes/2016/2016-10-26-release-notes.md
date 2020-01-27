# Release Notes: 2016-10-26

The Internet is a fantastic platform which has given rise to a massive amount of technological growth over the last 30 years... But, every rose has it's thorn, and there are people in the dark corners of the internet focused on doing bad deeds.  DNS Provider Dyn had its day last Friday, and was hit by said bad apples, with over 1 terabit of traffic per second.  Our team has done some analysis, and Nick Kephart published [this blog post](https://blog.thousandeyes.com/dyn-dns-ddos-attack/) today - we'll be following this post up with more this week, so stay tuned to the blog!

## Endpoint Agent

 We're on the cusp of the General Availability date for the Endpoint Agent, which means that much of this release is focused on changes we've introduced in that area of the platform.  Check out the list below!

### Path Visualization changes

 The UI has changed rather a lot.  We've made it simpler to filter and group your data, added more information to contextual elements \(such as Network, Prefix and Autonomous System names\), added access points to the paths of Agents connected via wireless, and now show the destination of a trace, even when the destination was unreachable.

There's too much to cover briefly in this article, so check out this article, which covers the [Network view for Endpoint Agent in detail](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpTKAS).

### Pricing information 

 Endpoint Agent will now be shown in the billing tab for organizations whose subscriptions include this feature.  The product is also available in the [pricing calculator](https://app.thousandeyes.com/calculator).

## Path Visualization changes

In the Path Visualization View, where a trace experiences terminal loss en route to the destination, the path from the terminal node to the destination will be shown using a dotted line with a ? in the middle of the link.  Managed on a per-route basis, this will allow users experiencing problems with a path trace to see steps in a path that are common, and then infer the ultimate destination, represented using the dotted line.

For more information on working with Path Visualization, see [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC).

## Trial and Lite organizations can self-delete

 We've added the ability for users who are owners of Trial and Lite organizations to self-delete, such that they can be added to your paying organizations.  To delete a Trial or Lite organization, advise affected users to navigate to **Account Settings** &gt; **Usage** &gt; **Delete** and follow the instructions shown on the page.

## Timeline colors

 We've updated the timeline component of all views to use blue for the chart colors.  Previously the chart color would change based on the view and metric selection between red, green and blue.

## Bugs & minor features

* We've corrected a problem that in some cases either prevented display of the usage meter shown on the **+ Add New Test** page, or caused it to show absurd usage projections.
* We've corrected a problem which prevented outage information from being shown in snapshot shares 
* In the Dashboard, the sparkline charts shown in the Tests widgets now render correctly in all modern browsers.  Previously, users using Microsoft's Edge browser had problems viewing data on these charts.
* Opening and clicking **Save** \(without making changes\) in Agent Settings will no longer create activity log entries if nothing was changed.
* The Alerts' **Enabled** checkbox in Test Settings will now be consistent with the alert setting on live shared tests.
* Users attempting to delete an Enterprise Agent cluster will now be presented with a dialog requiring confirmation before deleting a cluster.
* We've modified our pickers to allow users to select text from the selected element.  Click and drag to select, or click once to expand the list.
* We've corrected a performance issue related to the rendering of the Dashboard's Tests widget, which could fail to load in cases where customers have large numbers of tests shown in a dashboard.
* Agent to Agent tests now show the target IP address from the perspective of the machine initiating the test.  Prior to this change, the target IP address would be shown as the IP address as seen from the target machine, which could be a private IP on a different network.

## Linux vulnerability update

 We've released a statement discussing the Linux vulnerability known as Dirty COW \(CVE-2016-5195\).  See [this article](https://app.thousandeyes.com/sfdc/community/home?communityTabId=Knowledge%20Base&communityObjectId=kA044000000CnKlCAK) for details.

## Customer Success Center changes

 As we mentioned in our last release, we've been making a number of changes to the Customer Success Center.

### Email updates

 We're continuing to refine email notifications from the new system, both in format and content.  If you have any questions, please [drop us a note](mailto:support@thousandeyes.com?subject=email+updates).

### Discontinuing support.thousandeyes.com

 While all articles are currently published in the old site, we're migrating away from that service;  Later this week, all article content hosted on support.thousandeyes.com will be replaced with placeholders which redirect customers to the new location \(success.thousandeyes.com\) for all articles.  

In two weeks, we'll repoint the support.thousandeyes.com domain name to the new site.  There will be a temporary period of broken links, but our team is here to help in the event you're searching for a legacy article and need a link.

