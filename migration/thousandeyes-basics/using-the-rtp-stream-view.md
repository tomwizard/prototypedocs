# Using the RTP Stream view

When you create a RTP Stream test, you get access to the RTP Stream view which leverages the [ThousandEyes standard layout](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC).  
This article highlights specifics shown in the RTP Stream view.

## Example

This example shows a RTP Stream test to Enterprise Agent target called IL-Chicago-SE-01:

IMAGE MISSING

## View Specifics

The RTP Stream view provides the following metrics:

* **Mean Opinion Score \(MOS\):** A measurement of perceived voice quality, ranging from 1 to 5. A MOS of 5 indicates excellent voice call quality while a MOS of 1 indicates poor voice call quality.
* **Loss:**  A stream of UDP packets with RTP as payload is sent to the Target Agent and packet loss is calculated from the number of packets received by the Target.
* **Discards:** Packets that are discarded when they reach the destination due to delay variations greater than the size of the de-jitter buffer setting, expressed as a percentage of packets sent.
* **Latency:** The average of time for each packet in the stream to travel from sender to receiver.
* **Packet Delay Variation \(PDV\):** The variation in delay from sender to receiver. As a general rule, the de-jitter buffer size should be as large as the PDV to avoid frame discards.

For details on available metrics, access the following Knowledge Base article: [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC)  
  
The RTP Stream view shows two different data views, depending on whether an Agent is selected, shown below:

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area (found in the Map tab) displays the worldwide
          average of each selected metric, at the date/time selected in the interface.</p>
        <p></p>
        <p>IMAGE MISSING
          <br />
        </p>
        <p>Without an agent selected, the timeline shows a chart showing the average
          based on the selected metric, calculated across all locations. An example
          of the global chart for the MOS metric is shown below:</p>
        <p></p>
        <p>IMAGE MISSING
          <br />
        </p>
        <p>Detailed metrics will be the same as shown in the global view, showing
          a tabular view of by-location metrics for each of the locations used in
          the test. This includes Location name, date/time that the data was captured,
          MOS, packet loss, discards, latency and PDV.</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area displays the location-based average of each
          selected metric, at the date/time selected in the interface.</p>
        <p></p>
        <p>IMAGE MISSING
          <br />
        </p>
        <p>With a location selected, the timeline shows a chart showing the average
          based on the selected location, charted against the global values for the
          same metric. An example of the location chart for the MOS metric is shown
          below:
          <br />
        </p>
        <p>IMAGE MISSING</p>
        <p></p>
        <p>Detailed metrics will be the same as shown in the global view, showing
          a tabular view of by-location metrics for each of the locations used in
          the test. This includes Location name, date/time that the data was captured,
          MOS, packet loss, discards, latency and PDV. The selected location will
          be highlighted, if an agent is selected.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>