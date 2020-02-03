# Using the Network Overview

When you create any test in which you include network measurements – such as Network, HTTP Server, Page Load, or DNS Server Tests, you get access to the Network Overview section.  The Network Overview leverages the ThousandEyes [standard layout](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC),. This article highlights specifics shown in the Network Overview.

## Example

The screenshot below shows the Network Overview of a Page Load test:

![Network-Overview](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSAJ)

## View Specifics

There are three metrics available in the metric selector section of the interface:

* **Loss:** packet loss expressed as a percentage of packets sent
* **Latency:** average latency between endpoints
* **Jitter:** variation in latency over time

Tests running from enterprise agents which include the bandwidth measurements option will also show a Bandwidth metric.

For details on available metrics, please visit the [ThousandEyes Metrics: What do your results mean?](https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC) article.

The Network Overview shows two different data views, depending on whether an Agent location is selected, shown below:

**Without a location selected**

The computed averages area displays the worldwide average of each selected metric, at the date/time selected in the interface.

![Map-tab-average](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSAO)

Without an agent selected, the timeline shows a chart showing the average based on the selected metric, calculated across all locations.  An example of the global chart for the loss metric is shown below:  
  
![timeslide-average](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSAY)

The detailed metrics area shows by-location metrics for each of the available metrics, in a tabular view.  The table can be sorted by clicking the table header.  
  
 

**With a location selected**

The computed averages area displays the location-based average of each selected metric, at the date/time selected in the interface.

![map-tab-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSB2)

With a location selected, the timeline shows a chart showing the average based on the selected location, charted against the global values for the same metric.  An example of the location chart for the loss metric is shown below:

![timeslide-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSAd)

The detailed metrics area shows by-location metrics for each of the available metrics, in a tabular view.  The table can be sorted by clicking the table header.  The selected location will be shown highlighted in the table. The below table is sorted in descending order for Packet Loss and with Buenos Aires,Argentina Cloud Agent selected.

## Table view

![table-view](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000USY7&feoid=00NE0000006OT0r&refid=0EM2R000000CSAs)

