# Endpoint Agent Views - Network

All data from browsing webpages of domains from a monitored network is presented under the **Views &gt; Endpoint Data** page for that Account Group. Data collected by manually triggering a recording session will also be shown. This article describes the **Network** View under **Views &gt; Endpoint Agent**, also the default **Endpoint Agent View**

IMAGE MISSING

1. **Add A Filter:** Search through collected data from all user sessions within the selected time period using the following criteria. The selection affects the entire View.
   * **Connection**: Network connection of the Endpoint Agent \(e.g. wireless, ethernet, virtual\)
   * **Destination IP**: IP address of visited site
   * **Gateway**: IP address of each Endpoint Agent's gateway
   * **Visited Site:** The destination site visited
   * **Location**: Geographical location of the Endpoint Agent
   * **Agent**: Individual Endpoint Agent
   * **Network:** Network block where the request originated
   * **Platform:** Host OS \(e.g., Windows, Mac\)
   * **Proxy Address**: IP address of configured proxy server on Endpoint Agent
   * **Trigger:** Auto or manual, indicating whether the data collection automatically triggered based on a whitelisted domain inside a registered network, or manually initiated by the user
   * **User**: ****Username of the Endpoint Agent machine user, as shown under Settings &gt; Endpoint Agents &gt; expand Agent tab
   * **VPN Address**: IP address of VPN endpoint to which the Endpoint Agent is connected 
2. **Timeline:** A line graph of the selected metric \(5\) and also a bar chart of the number of visited web pages across all user sessions. You can use the **24h**, **7d** and **14d** quick links, or drag the tabs to show data over a custom range. Click on the timeline to view data for a single round.
3. **Metric:** Under the Network layer, measurements for the following metrics are available:
   * _**Loss**:_ End-to-end packet loss. The percentage of packets lost is calculated by subtracting the number of reply packets the Agent receives from the target \(responses\) from the number of packets sent by the Agent, dividing by the number of packets sent, then multiplying by 100.
   * _**Latency**:_ The average of the round-trip packet times. Round-trip packet time is the time from which a packet is sent by the Agent to the time the Agent receives a reply.
   * _**Jitter**:_ The standard deviation of latency. The standard deviation indicates how widely spread the measurements are around the average.  A larger standard deviation indicates a wider spread of measurements.
   * _**Connection Failures:**_ The number of times the Endpoint Agent failed to establish a TCP connection with the web server or the proxy.
4. **Bin Size**: View data collected from Endpoint Agent\(s\) in intervals based on this setting.
5. **Path Visualization:** The network path from each Endpoint Agent to the web servers.
6. **Add a filter**: View data based on applied filters. You can apply multiple filters. The image below provides an example using the "Platform", "Connection", "Visited Site" and "Agent" filters. Clicking on the numbers in the group nodes will automatically apply a filter and expand on that data. IMAGE MISSING
7. **Map**: Uses geo-location data to place Endpoint Agents on a map. The world map is zoomable using the controls to the right of the map or scrolling with your mouse.
   * **Details**: Shows data on the selected Agent's sessions. When no Agent is selected on the map, averages are computed across all Endpoint Agents for the chosen metric in the selected round. IMAGE MISSING
8. **Table:** Each row will show detailed metrics and data for Agents based on the Current Filter \(\#1\) and other filters.

    IMAGE MISSING

