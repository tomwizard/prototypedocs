# Using the SIP Server view

### Using the SIP Server view

When you create an SIP Server test, you get access to the SIP Server view. The SIP Server view uses the [ThousandEyes standard layout](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC). This article highlights elements specific to the SIP Server view.  
 

## Example

This example shows a SIP Server test to a target called voip-sfo2.stg.thousandeyes.com:

IMAGE MISSING

## View Specifics

The SIP Server test provides the following metrics:

* **Availability:** Percentage of time that the service responds to a request.
* **Response Time:** Also known as time-to-first-byte, this is the time elapsed from the beginning of the request \(before any DNS resolution\) until the Agent receives the first byte of the response from the server.
* **Total Time:** Time to perform the test, including DNS, Connect \(when using TCP protocol\), Redirects \(if any\), Register and Options phases of the test.

For more details on available metrics, consult the ThousandEyes Knowledge Base article [ThousandEyes Metrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC)

The SIP Server View shown depends on whether a specific Agent is selected, and which metric is selected. Details for each view are shown below.  
 

### Availability

Availability tests the basic connectivity to and response of the target SIP server. The Availability metric will be 100% if the SIP response is 2xx/3xx or the code specified in the **Desired Status Code** setting, or 0% otherwise. The Average Availability across all Agents can take any value from 0% to 100%.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows a breakdown by Error Type (DNS, Connect, Register and
          Options), and any Active Alerts.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows the SIP response code, a clickable link to display REGISTER
          and OPTIONS request headers, along with a green/red square icon, and any
          Active Alerts. In the example below, the 404 response response code is
          the desired code, so the icon is green.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>  
Definitions of the possible Error Types are in the table below:

| Error Type | Error Definition |
| :--- | :--- |
| DNS | Failure to resolve a domain name to one or more IP addresses using DNS |
| Connect | Failure to complete a TCP 3-way handshake. Only present if the TCP protocol is used to perform the test |
| Register | Failure to perform SIP registration \(login failure\) |
| Options | Failure to retrieve the remote endpoint capabilities |

With or without an Agent selected, the timeline displays a graph of Average Availability. With an Agent selected, that Agent's Availability data is plotted in addition to the Average Availability. The following image shows the Availability metric with the Chicago Agent selected. The Agent's data is plotted using a green line, whereas the Average Availability data is plotted as a solid green area. The data round selector, indicated with the inverted yellow triangle at the top of the selector, is placed on a data round where the Chicago Agent has 0% availability. The Average Availability in selected round shown below is 82% due to Chicago and an additional 4 Agents having 0% availability, and the remaining 23 Agents having 100% availability.

IMAGE MISSING

The Table tab shows information for each of the Agents assigned to the test. This information includes Agent name, date and time when the data was captured, Target IP address, SIP response code, number of redirects \(if any\) and the Error Type accompanied by Error Details \(if any\). In the following image, we see that the sub-100% Average Availability displayed in the previous image was due to the first five Agents, Zurich through Atlanta \(by default Agents with errors are listed first\). In this example, the Zurich Agent failed to complete SIP registration successfully; Sydney and Frankfurt Agents received an unexpected SIP response code, while Chicago was unable to retrieve remote endpoint capabilities \(using the OPTIONS request method\). The Atlanta Agent was unable to connect to the SIP server.

Selecting an Agent with the Agent selector will highlight the Agent's row in the table. In the image below, the Chicago Agent has been selected.

IMAGE MISSING

### Response Time

Also known as time-to-first-byte, Response Time is the time elapsed from the beginning of the request \(before DNS resolution\) until the client receives the first byte of the response from the server. The Response Time metric is accompanied by the individual timings that comprise Response Time.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows a pie chart breaking down the Response Time into DNS
          resolution, Connect and Wait times. Hovering over a slice will show the
          component&apos;s average time in a tooltip.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows a pie chart breaking down the Response Time into DNS
          resolution, Connect and Wait times. Hovering over the a slice will show
          the component&apos;s time in a tooltip.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>  
With or without an Agent selected, the timeline displays a graph of Average Response Time.  With an Agent selected, that Agent's Response Time data is plotted in addition to the Average Response Time. The following image shows the Response Time metric with the Chicago Agent selected. The Agent's data is plotted using a dark blue line, whereas the Average Response Time data is plotted as a solid light blue area.

IMAGE MISSING

The Table tab shows timing information for each of the Agents assigned to the test. This includes Agent name, date and time when the data was captured, Response Tim, and the components of Response Time: DNS Time, Connect Time \(TCP only\) and Wait Time. Selecting an Agent will highlight the Agent's row in the table. In the image below, no Agent has been selected.

IMAGE MISSING

### Total Time

Total Time represents time spent performing all phases of the test and is accompanied by timing breakdowns on a per-Agent basis and the averages over all Agents reporting data.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The Map tab shows the Total Time average from all Agents which completed
          the test, and a pie chart breaking down the Total Time into DNS resolution,
          Connect, Register request and Options request times. Hovering over a slice
          will show the component&apos;s average time in a tooltip.</p>
        <p>IMAGE MISSING</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The Map tab shows a pie chart breaking down the Total Time into DNS resolution,
          Connect, Register request and Options request times. Hovering over a slice
          will show the component&apos;s time in a tooltip.</p>
        <p>IMAGE MISSING</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>With or without an Agent selected, the timeline displays a graph of Average Total Time. With an Agent selected, that Agent's Total Time data is plotted in addition to the Average Total Time. The following image shows the Total Time metric with the Chicago Agent selected. The Agent's data is plotted using a dark blue line, whereas the Average Total Time data is plotted as a solid light blue area.

IMAGE MISSING

The Table tab shows information for each of Agents assigned to the test. This includes Agent name, date and time that the data was captured, Total Time, and the component timings: DNS Time, Connect Time, Redirect Time, Register Time and Options Time. Selecting an Agent will highlight the Agent's row in the table. In the image below, none of the Agents has been selected.

IMAGE MISSING

## Notes

* **Connect Time:** This data is only present when TCP is configured in the test's **Protocol** field. Connect Time represents the time to perform a TCP 3-way handshake. If the UDP protocol is configured instead, Connect Time is not present, since UDP is a connectionless protocol without a handshake.

