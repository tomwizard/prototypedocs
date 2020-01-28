# Endpoint Agent Views - Session Details

All data collected by Endpoint Agents from browsing webpages of domains listed under a monitoring profile from a monitored network is presented under **Views &gt; Endpoint Data** for that Account Group**.** Data collected by manually triggering a recording session will also be shown. This article describes the **Session Details** view under Views &gt; Endpoint Agent.

IMAGE MISSING

1. **Add a filter:** Search through collected data from all active user sessions within the selected time period using the following criteria. The selection affects the entire View
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
2. **Timeline:** Plots a line graph of the selected metric \(5\) and also a bar chart of the number of visited web pages across all user sessions, over time. You can use the 24h, 7d and 14d links or drag the tabs to show data over a custom range. Click a time period on the timeline to view data for that period.
3. **Metric:** Under the Network layer, measurements for the following metrics, averaged over the selected agents, are available:
   * _**Page Success Rate:**_ ****Measures the percentage of page load events that are completed, within the specified time interval.
   * _**Response Time:**_ ****Also known as time-to-first-byte, this is the time from the beginning of the request \(before the DNS request\) until the client receives the first byte of the response from the web server.
   * _**Loss**:_ End-to-end packet loss. The percentage of packets lost is calculated by subtracting the number of reply packets the Agent receives from the target \(responses\) from the number of packets sent by the Agent, then dividing by the number of packets sent, then multiplying by 100.
   * _**Latency**:_ The average of the round-trip packet time. Round-trip packet time is the time from which a packet is sent by the Agent to the time the agent receives a reply.
   * _**Jitter**:_ The standard deviation of latency. The standard deviation indicates how widely spread the measurements are around the average.  A larger standard deviation indicates a wider spread of measurements.
   * _**Connection Failures:**_ The number of times the Endpoint Agent failed to establish a TCP connection with the web server or the proxy.
4. **Bin Size**: View data collected from Endpoint Agent\(s\) sorted into equally spaced intervals based on this setting
5. **User Sessions:** A session is a continuous interaction of the user within the same browser tab, domain, port and protocol. All pages visited within this interaction is grouped under the same session. A tabulated view of all user session within the specified time interval. Expand a user session to view detailed information, as shown below. IMAGE MISSING
6. **Computer:** Provides information about the Operating System, Platform, OS version, browser details, network configuration \(IP address, DNS Servers\), manufacturer, model, and memory information. A typical set of of information for a WiFi-connected host machine is shown above.
7. **Connection:** Network type \(Wired/Wireless\). For wired connections, the connection type and the link speed is shown.  Wireless networks also show the network name, WiFi channel, strength, noise and signal quality, transmission rate and wireless networking standard .
8. **See Path Trace**: A complete hop-by-hop path, with delay measured at each hop from the host machine running the Endpoint Agent to the targeted domain. The path trace is obtained using ICMP. Gateway and Proxy nodes along the path are also shown. 
9. **Visited Site**: A user session is created for each unique web domain visited during the selected time interval. For the visited website, waterfall information for each new page is available. Click on the circular destination node for Page Title, DOM Load time, Page Load time, and the number of Component Errors on each page. Click on "View Waterfall" to see detailed information about each object on the selected page, including object name, domain, size \(kB\) and time taken to load the object on the page. An example Waterfall display for "Network - Path Visualization - ThousandEyes" is shown below. IMAGE MISSING

