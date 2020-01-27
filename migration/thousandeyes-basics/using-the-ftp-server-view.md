# Using the FTP Server view

When you create an FTP Server test, you get access to the FTP Server view.  The FTP Server view uses the [ThousandEyes standard layout](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC). This article highlights elements specific to the FTP Server view.

## Example

This example shows the result of an FTP Server download test to server ftp.ripe.net.

IMAGE MISSING

## View Specifics

The FTP Server test measures the following metrics:

* Availability: Percentage of time that the site is available, aggregated across all agents.
* Response time: Also known as time-to-first-byte, this is the time elapsed from the beginning of the request \(before the DNS request\) until the Agent receives the first byte of the response from the server.
* Throughput: The wire size divided by the receive time, expressed in megabits per second \(Mb/s\).

For more details on available metrics, consult the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC)

The FTP Server view shows two different data views, depending on whether a specific Agent is selected, and varies depending on which metric is selected.  Details for each selected metric are shown below.

### Availability

The Availability for a given Agent will be 100% if the FTP reply code is 2xx or the code specified in the **Desired Reply Code** setting , and 0% otherwise. The Average Availability can take any value from 0% to 100%.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows a breakdown by Error Type, and any Active Alerts.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows the FTP reply code or similar status, along with a green/red
          square icon, and any Active Alerts.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>Definitions of the possible Error Types are in the table below:

| Error Type | Error Definition |
| :--- | :--- |
| DNS | Failure to resolve a domain name to one or more IP addresses using DNS |
| Connect | Failure to complete a TCP 3-way handshake \(SYN, SYN-ACK, ACK\) |
| Negotiation | Failure after Connect, up to the time the upload/download/list command is issued \(including login failure\) |
| Transfer | Failure during the upload/download/list command execution |
| FTP | Receiving an FTP reply code that is not 2XX \(default\), or not the desired FTP reply code configured in Advanced Settings of the test |
| Content  | \(optional\) Failure to match returned content to an expression in the **Verify Content** field |

With or without an Agent selected, the timeline displays a graph of Average Availability.  With an Agent selected, that Agent's Availability data is plotted in addition to the Average Availability.  The following image shows the Availability metric with the Johannesburg Agent selected.  The Agent's data is plotted using a green line, whereas the Average Availability data is plotted as a solid green area. The data round selector, indicated with the inverted yellow triangle at the top of the selector, is placed on a data round where the Johannesburg Agent has 100% availability but the Average Availability is 80% due to one of the other four Agents failing to successfully download the target file.

IMAGE MISSING

The Table tab shows information for each of Agents used in the test.  This includes Agent name, date/time that the data was captured, Target IP address, FTP error type and Error Details \(if applicable\).  In the following image, we see that the 80% Average Availability displayed in the previous image was due to the Maidenhead, UK Agent reaching the test timeout before completing the download. Selecting an Agent will highlight the Agent's row in the table. In the image below, the Johannesburg Agent has been selected.

IMAGE MISSING

### Response Time

Also known as time-to-first-byte, Response Time is the time elapsed from the beginning of the request \(before the DNS request\) until the client receives the first byte of the response from the server.  The Response Time metric is accompanied by the individual timings that make up Response Time.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows the computed averages area, which contains the Response
          Time and Throughput averages from all Agents which completed the test,
          and a pie chart breaking down the Response into DNS lookup, Connect, Negotiation
          and Wait times. Hovering over the chart slices will show the individual
          timing averages via tooltips.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows the computed averages area, which contains the Response
          Time and Throughput from the selected Agent if it has completed the test,
          and a pie chart breaking down the Response into DNS lookup, Connect, Negotiation
          and Wait times. Hovering over the chart slices will show the individual
          timings via tooltips.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>With or without an Agent selected, the timeline displays a graph of Average Response Time.  With an Agent selected, that Agent's Response Time data is plotted in addition to the Average Response Time.  The following image shows the Response Time metric with the Bruges Agent selected.  The Agent's data is plotted using a blue line, whereas the Average Response Time data is plotted as a solid blue area.

IMAGE MISSING

The Table tab shows information for each of Agents used in the test.  This includes Agent name, date/time that the data was captured, Total Response Time, and the components of Response Time: DNS Time, Connect Time, SSL Time and Wait Time. Selecting an Agent will highlight the Agent's row in the table. In the image below, no Agent has been selected.

IMAGE MISSING

### Throughput

Throughput is the total wire size divided by the receive time. The Throughput metric is accompanied by the detailed component timings.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows the computed averages area, which contains the Response
          Time and Throughput averages from all Agents which completed the test,
          and a pie chart breaking down the Throughput into DNS Lookup, Connect,
          Negotiation, Wait and Transfer times. Hovering over the chart will show
          the individual timing averages via tooltips.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows the computed averages area, which contains the Response
          Time and Throughput from the selected Agent if it completed the test, and
          a pie chart breaking down the Throughput into DNS Lookup, Connect, Negotiation,
          Wait and Transfer times. Hovering over the chart will show the individual
          timing averages via tooltips.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>With or without an Agent selected, the timeline displays a graph of Average Throughput.  With an Agent selected, that Agent's Throughput data is plotted in addition to the Average Throughput.  The following image shows the Throughput metric with the Bruges Agent selected.  The Agent's data is plotted using a blue line, whereas the Average Throughput data is plotted as a solid blue area.

IMAGE MISSING

The Table tab shows information for each of Agents used in the test.  This includes Agent name, date/time that the data was captured, Total Throughput, and the detailed timings: DNS Time, Connect Time, Negotiation Time, Wait Time, Transfer Time and Total Time. Selecting an Agent will highlight the Agent's row in the table. In the image below, the Bruges Agent has been selected.

IMAGE MISSING

