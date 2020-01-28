# Endpoint Agent Views - Web

All data collected by Endpoint Agents from browsing webpages of domains listed under a monitoring profile from a monitored network is presented under **Views &gt; Endpoint Data** for that Account Group**.** Data collected by manually triggering a recording session will also be shown; see below for an example.

IMAGE MISSING

1. **Add a filter:** Search through data from all user sessions within the selected time period using the following criteria:
   * **Connection**: Network connection of the Endpoint Agent \(e.g. wireless ethernet, wired ethernet, virtualized network\)
   * **Destination IP**: IP address of visited site
   * **Gateway**: IP address of each Endpoint Agent's gateway
   * **Visited Site:** The destination site visited
   * **Location**: Geographical location of the Endpoint Agent
   * **Agent**: Individual Endpoint Agent
   * **Network:** Network block where the request originated
   * **Platform:** Host operating system and version
   * **Proxy Address**: IP address of any configured proxy server on Endpoint Agent
   * **Trigger:** Auto or manual, indicating whether the data collection automatically triggered based on a whitelisted domain inside a registered network, or manually initiated by the user
   * **User**: ****Username of the local account running Endpoint Agent, as shown under the expanded entries in the Settings &gt; Endpoint Agents page
   * **VPN Address**: IP address of VPN endpoint to which the Endpoint Agent is connected 
2. **Bin Size**: View data collected from Endpoint Agent\(s\) in intervals based on this setting..
3. **Timeline:** A line graph of the selected metric \(\#4\) and also a bar chart of the number of visited web pages across all user sessions. You can use the **24h**, **7d** and **14d** quick links, or drag the tabs to show data over a custom range. Click on the timeline to view data for a single round.
4. **Metric:** Under the Web Layer, measurements of the following metrics, averaged over multiple selected agents, are available:
   * **Page Success Rate:** Percentage of completed page load events out of the total number of page load requests per user session.
   * **Response Time:** Also known as time-to-first-byte, this is the time from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the web server.
5. **Agents**: ****For each Agent, see Agent name, date and time of user session\(s\), number of pages visited within that user session, completion percentage, and response time metrics for a specific Agent during the selected time interval.
6. **Number of Pages:** Total number of web pages navigated per Agent within the specified time interval.
7. **Number of Sessions**: Total number of active user sessions within the specified time interval.
8. **Page Success Rate \(%\):** A web page is said to be fully loaded if the page load event is successfully triggered. This metric is a percentage measurement of successful page load events divided by the total page load requests by the browser, displayed for each selected Agent during the specified time interval.
9. **Response Time \(ms\):** Total response time measured from each web page, displayed for each selected Agent during the specified time interval.
10. **Waterfalls:** View waterfall data for each web page visited during the selected user session.  IMAGE MISSING

Click on the **View Waterfall** link to see detailed information about each object on the selected page: object name, domain name of the URL, size \(kB\) and time taken to load the object \(ms\).

IMAGE MISSING

