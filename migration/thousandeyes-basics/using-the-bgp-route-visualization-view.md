# Using the BGP Route Visualization view

When you create any test which includes network measurements – including Network, HTTP Server \(with network measurements enabled\), page load \(with network measurements enabled\), or DNS server \(with network measurements enabled\), you get access to the BGP Route Visualization view.  Many views within ThousandEyes have similar layouts.

## Interface components

The screenshot below shows the BGP Route Visualization view for a site that is monitored using a HTTP Server test, with network measurements enabled:

IMAGE MISSING

1. _**Prefix selector**_ – use this control to change which network prefix is being displayed in the BGP Route Visualization view.  All tests which have network measurements enabled will be shown, including disabled tests.  The test selector shows each test listed, with each destination server prefix shown as a selectable child item in the list of tests.  Using this example \(christianmingle.com\), there is only one prefix listed – this corresponds to the network where the target corresponding to the test is located.

    Prefixes Shown:

   * All announced, matching prefixes are shown for each server address. For example, suppose both 1.2.3.0/24 and 1.2.0.0/16 are announced. A connection has one endpoint: 1.2.3.10. Both matching prefixes will be shown in the list of prefixes. Thus, it is always possible to see the routes that will be used if 1.2.3.0/24 is ever withdrawn.
   * All prefixes used by the test over time are listed.  If the destination server rotates between different IP addresses or networks, each will be shown in the list.  This may be an indication that the test target is hosted on a CDN provider’s servers, such as Akamai. 

2. _**Views** available for this test –_ shows a list of shortcuts to other views for the selected test.
3. _**Timeline**_ – shows the lesser of 30 days, or the length of time that the test has been enabled, by charting the average values for the metric selected \(see \#5\).  To change the data displayed, either use the 24h \(trailing 24 hours\) / 7d \(trailing 7 days\) / 14d \(trailing 14 days\) links, click the zoom out and latest buttons, or click and highlight the requested area of the chart, and it will re-draw appropriately.  The lower timeline will allow you to zoom in on a particular date and time.
4. _**Monitor selector**_ – this control is unique to the BGP route visualization view. The monitors shown are BGP data collectors from the RouteViews project, and Private BGP monitors for your account.  Monitor selection allows users to isolate specific geographies and networks, from these views, users can identify BGP events which occur in relation to a web property they are monitoring. 

    By default, the BGP Route Visualization View shows icons from all BGP monitors. Click on **Add a filter** in the **Showing:** field to select specific Monitors, Monitor Location, Monitor Network or Networks. The images below show the difference in the BGP Route Visualization when all monitors are selected and when a set of monitors are selected.  
   IMAGE MISSING  
   IMAGE MISSING

5. _**Metric selector**_ – choose between the various BGP metrics available.  These metrics are listed below.  Changing the selected metric will change the timeline \(\#x, below\) to reflect that metric:

   * _Path Changes:_ A timeline with a flat set of results is an indication of a very stable network.  Spikes indicate an increase in the number of path changes.
   * _Reachability_: a timeline with a flat set of results \(showing 100% reachability\) is important for stability.  Focus on dips in the timeline to isolate a network event.
   * _Updates_: A timeline with a flat set of results is an indication of a very stable network.  Spikes indicate an increase in the number of updates.

    Refer to knowledge base article [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean) for more information on metrics captured by the platform.   
    Changing the selected metric will change the content of the timeline \(\#6 below\), and the coloring of the monitors in the visualization.  By default, the Reachability metric is selected.

6. _**Date/time label**_ – when an instant in time is selected on the timeline \(shown as a vertical yellow line at that point in time\), the time and date of the selection are displayed here.  By default, the latest available measurement is selected.
7. _**Monitor and origin complexity controls** -_ This control is also present in the path visualization view, but it effectively allows simplification of the BGP route visualization by collapsing routes between various autonomous systems.  The further apart the endpoints on the slider are, the less complex the visualization.   IMAGE MISSING
8. _**Quick selection**_ – not always visible, the quick selection section of the page will highlight areas of interest on the visualization, based on the metric selected \(\#3 above\).  For example, in a scenario a number of links were involved in path changes, the quick selector might show a link to select all links involved in path changes.  In the event that the "other affected tests" hyperlink is shown, this is an indication that other tests access resources in the same network. The " X monitors with path changes" hyperlink will further simplify the diagram by only showing routes with path changes.  If there are no path changes, then this link will not be seen.
9. _**Grouping**_ – controls the way the BGP Monitors are shown. They can be displayed as not grouped \(grouping by "Monitor"\) or grouped by the network in which they reside.
10. _**Selected Link/Node details** -_ when either a link or a node is selected in the route visualization, they appear in the link/node details, which is expandable by clicking the down arrow.  
11. _**Search**_ - search for an autonomous system, IP address, prefix or rDNS entry shown in the visualization.
12. **Next Monitors** - for a clearer visualization, our monitors may be displayed on multiple pages. This button will move the view to the next set of available monitors.

## Understanding what the various visualization monikers mean

The list below shows each type of moniker we use to show items of interest in a BGP view.  Each scenario also includes a sample image, showing what will be shown in the event that you see one of these conditions:

* _**Path collapsed**_– using the monitor and origin complexity controls \(\#7 above\) allows paths to be collapsed in order to view content more easily.  Collapsed content is shown as a black dotted line, with the number of network hops shown as a path label.  Click the label to expand the obscured paths.  The example below shows a connection to a Hurricane Electric, Inc. network \(AS 6939\): the Atlanta, GA-2 monitor is on this network, whereas the Johannesburg, South Africa monitor has a 2-hop path to get to this network. IMAGE MISSING 
* _**Path thickness**_ – thicker paths are indicative of the number of routes which traverse a network.  In the example shown below, 3 routes use AS 16735 - AS 52925 \(link 1\), vs a single route using AS 1916 - AS 52925 \(link 2\), thus the line representing "link 1" is three times as thick as "link 2": IMAGE MISSING
* _**Withdrawn route**_ – when a route is withdrawn, links that are no longer used are shown as red dotted lines.  IMAGE MISSING
* _**Newly Announced route**_ – when a route is added, newly used links are shown in a solid red line, according to the weight of the link \(see above\).  Typically, newly announced routes will be shown in conjunction with withdrawn routes, indicating a routing preference change. IMAGE MISSING
* _**Destination network**_ – the network hosting the network prefix selected in the test selector \(\#1 above\) is shown in green shaded circle, with the network’s autonomous system \(AS\) number shown inside the circle.
* _**Transit network**_ – networks being used in the path from each selected monitor are shown in grey shaded circles, with the network’s autonomous system \(AS\) number shown inside the circle. 
* _**Selected object**_ - a selected object is shown outlined in a moving blue dashed line.  The image below shows the result of a "full path selection" using double-click on the Toronto monitor: the result shows that Toronto's full path is selected. The Atlanta and San Jose monitors' paths remain unselected. IMAGE MISSING

## Interacting with the BGP route visualization

Hover over any object on the visualization to show detailed information about the object, which will appear in the lower right corner of the visualization area.  Networks show the owner, primary country, and number of prefixes announced by that AS.  Links show source and destination information \(AS to AS\), and number of routes using that link, and monitors show information about the monitors, including reverse DNS, IP address, as well as results for each metric listed in the metrics list \(\#3 above\).  An example showing a selected transit network is shown below.

Click a node or a link to select it; multiple objects can be selected at once.  Once an object is selected, it will show a moving dashed line surrounding the object.  Entire paths can be selected by double-clicking a node or a link.  All objects which traverse the object which is double clicked will have selection toggled on or off, based on the selection status of the object when it is selected.  

Once one or more objects is selected, the selected objects table link is activated. The link may display anything in the format \(X nodes\) \(and\) \(Y links\) selected.  Expand a table view of selected objects.  This will show two tabs: one for nodes, and one for links.

* nodes shows Node Name, AS number, and an X button to de-select the node.
* Links shows the source and destination of each link

When you hover over an item in the selected link/node details table, its size doubles, to allow the user to identify the object in the visualization.  Click the link again to hide the table view of selected objects.  The table view \(links tab\) is shown in the example below:

IMAGE MISSING

All nodes can be repositioned by clicking and dragging the node to a new place on the visualization pane, but the repositioned placement does not persist when the visualization is redrawn due to a change of time/date or display options.

