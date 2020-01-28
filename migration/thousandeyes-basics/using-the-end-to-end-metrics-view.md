# Using the End-to-End Metrics view

When you create any test in which you include network measurements – such as Network, HTTP Server, Page Load, or DNS Server Tests, you get access to the End-to-End Metrics view.  The End-to-End Metrics view leverages the ThousandEyes standard layout, documented [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC). This article highlights specifics shown in the End-to-End Metrics view.

## Example

The screenshot below shows an End-to-End Metrics view of a Page Load test:

IMAGE MISSING

## View Specifics

There are three metrics available in the metric selector section of the interface:

* **Loss:** packet loss expressed as a percentage of packets sent
* **Latency:** average latency between endpoints
* **Jitter:** variation in latency over time

Tests running from enterprise agents which include the bandwidth measurements option will also show a Bandwidth metric.

For details on available metrics, access the Knowledge Base article [here](https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC).

The End-to-End Metrics view shows two different data views, depending on whether an Agent location is selected, shown below:

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area displays the worldwide average of each selected
          metric, at the date/time selected in the interface.
          <br />IMAGE MISSING</p>
        <p>Without an agent selected, the timeline shows a chart showing the average
          based on the selected metric, calculated across all locations. An example
          of the global chart for the loss metric is shown below:</p>
        <p>IMAGE MISSING</p>
        <p>The detailed metrics area shows by-location metrics for each of the available
          metrics, in a tabular view. The table can be sorted by clicking the table
          header.</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area displays the location-based average of each
          selected metric, at the date/time selected in the interface.</p>
        <p>IMAGE MISSING</p>
        <p>With a location selected, the timeline shows a chart showing the average
          based on the selected location, charted against the global values for the
          same metric. An example of the location chart for the loss metric is shown
          below:</p>
        <p>IMAGE MISSING</p>
        <p>The detailed metrics area shows by-location metrics for each of the available
          metrics, in a tabular view. The table can be sorted by clicking the table
          header. The selected location will be shown highlighted in the table.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## Table view

IMAGE MISSING

