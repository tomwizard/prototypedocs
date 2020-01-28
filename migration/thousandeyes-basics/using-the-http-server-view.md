# Using the HTTP Server view

When you create any HTTP Server or Page Load test, you get access to the HTTP Server view.  The HTTP Server view leverages the ThousandEyes standard layout, documented here: [https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).  

This article highlights specifics shown in the HTTP Server view.

## Example

This example shows the result of an HTTP Server test for the website hipchat.com.

IMAGE MISSING

## View Specifics

The HTTP Server test measures the following metrics:

* Availability: Percentage of time that the site is available, aggregated across all agents.
* Response time: Also known as Time-to-first-byte, this is the time elapsed from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the server.
* Throughput: is calculated by dividing the total wire size to the receive time and expressed in MB/s

For more details on available metrics, access the knowledge base article here: [https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC)

The HTTP Server view shows two different data views, depending on whether or not a location is selected, and varies somewhat depending on which metric is selected.  Details for each selected metric are shown below.

### Availability

The Availability for a given agent should be 100% if the HTTP status code is 2xx or 3xx, and 0% otherwise. The average Availability can take any value from 0% to 100%.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area shows a breakdown by error type, when no location
          is selected. Definitions of the possible error types are in the table below:
          <br
          />TABLE MISSING
          <br />IMAGE MISSING</p>
        <p>Without a location selected, the timeline shows a chart showing the average
          availability calculated from all locations globally. The following image
          shows an example of a timeline for the availability metric:
          <br />IMAGE MISSING</p>
        <p>The table view shows by-location metrics for each of locations used in
          the test. This includes Location name, date/time that the data was captured,
          destination server IP, HTTP response code, number of redirects, and error
          type/details, if applicable.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area shows the status (green/red square) and http
          response code, as well as a popup to view the response headers from the
          target website. When you click the response headers, it will pop up a modal
          dialog showing the content of the response.
          <br />IMAGE MISSING</p>
        <p>When you click View headers, a popup will show two tabs showing response
          and request headers:
          <br />IMAGE MISSING</p>
        <p>With a location selected, the timeline shows a chart showing average availability
          for that location, charted against the global availability. The following
          image shows a sample for the availability metric with a location selected.
          As you can see, the agent&apos;s data is charted in a green line, whereas
          the global data is charted as an area.
          <br />IMAGE MISSING</p>
        <p>The detailed metrics area shows a tabular view of by-location metrics
          for each of locations used in the test. This includes Location name, date/time
          that the data was captured, destination server IP, HTTP response code,
          number of redirects, and error type/details, if applicable. When a location
          is selected, it will be highlighted in the detailed metrics list.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>### Response time

Also known as Time-to-first-byte, this is the time elapsed from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the server.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area shows the response time from the selected agent,
          and a pie chart breaking down the response timing into DNS lookup connect,
          wait and SSL negotiation times. Hovering over the chart will show the individual
          timing averages.</p>
        <p>IMAGE MISSING</p>
        <p>Without a location selected, the timeline shows a chart showing the response
          time calculated from all locations globally. The following image shows
          an example of a timeline for the response time metric:</p>
        <p>IMAGE MISSING</p>
        <p>Detailed metrics shows a tabular view of by-location metrics for each
          of the locations used in the test. This includes Location name, date/time
          that the data was captured, total response time, and the component times
          broken down by component (DNS time, Connect time, SSL time, Wait time).</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area shows the response time from the selected agent,
          and a pie chart breaking down the response timing into DNS lookup connect,
          wait and SSL negotiation times. Hovering over the chart will show the individual
          timing.</p>
        <p>IMAGE MISSING</p>
        <p>With a location selected, the timeline shows a chart showing response
          time for that location, charted against the global average. The following
          image shows a sample for the response time metric with a location selected.
          As you can see, the agent&apos;s data is charted in a blue line, whereas
          the global data is charted as an area. Where a red line is indicated for
          the chart, this is an indication that the request timed out for the selected
          agent.</p>
        <p>IMAGE MISSING</p>
        <p>Detailed metrics will be the same as shown in the global view, showing
          a tabular view of by-location metrics for each of the locations used in
          the test. This includes Location name, date/time that the data was captured,
          total response time, and the component times broken down by component (DNS
          time, Connect time, SSL time, Wait time). The selected location will be
          highlighted, if an agent is selected.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>### Throughput

Throughput is the total wire size divided by the receive.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area shows the average throughput (calculated globally),
          and a pie chart breaking down the fetch time into DNS lookup, connect,
          wait, SSL negotiation, and receive times. Hovering over a component of
          the pie chart will show the individual component timing.</p>
        <p>In addition to the throughput and the fetch time, the wire size which
          is the total size of the object in the wire is also shown.</p>
        <p>IMAGE MISSING</p>
        <p>Without a location selected, the timeline shows a chart showing the throughput
          calculated from all locations globally. The following image shows an example
          of a timeline for the throughput metric:</p>
        <p>IMAGE MISSING</p>
        <p>Detailed metrics will be the same as shown in the global view, showing
          a tabular view of by-location metrics for each of the locations used in
          the test. This includes Location name, date/time that the data was captured,
          throughput, wire size and the component times broken down by component
          (DNS time, Connect time, SSL time, Wait time, Receive time). The wire size
          is calculated and is shown as well. The selected location will be highlighted,
          if an agent is selected.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area shows the average throughput (calculated for
          the location), and a pie chart breaking down the fetch time into DNS lookup,
          connect, wait, SSL negotiation, and receive times. Hovering over a component
          of the pie chart will show the individual component timing.</p>
        <p>In addition to the throughput and the fetch time, the wire size which
          is the total size of the object in the wire is also shown.</p>
        <p>IMAGE MISSING</p>
        <p>With a location selected, the timeline shows a chart showing throughput
          for that location, charted against the global average. The following image
          shows a sample for the throughput metric with a location selected. As you
          can see, the agent&apos;s data is charted in a blue line, whereas the global
          data is charted as an area.</p>
        <p>IMAGE MISSING</p>
        <p>Detailed metrics will be the same as shown in the global view, showing
          a tabular view of by-location metrics for each of the locations used in
          the test. This includes Location name, date/time that the data was captured,
          throughput, wire size and the component times broken down by component
          (DNS time, Connect time, SSL time, Wait time, Receive time). The wire size
          is calculated and is shown as well. The selected location will be highlighted,
          if an agent is selected.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>