# Endpoint Agent Views - Scheduled Tests

Endpoint Agents can run two types of Scheduled Tests at regular intervals. The two tests are similar to the Network Layer's Agent to Server test type, and to the Web Layer's HTTP Server test type run by a Cloud or Enterprise Agent.

## Location

Scheduled Test views are nested under [Endpoint Agents &gt; Views](https://app.thousandeyes.com/view/endpoint-agent/). Once there, select **Scheduled Tests** under the Views:

IMAGE MISSING

## Overview

The following figure shows the default Endpoint scheduled test results view, with an HTTP Server test selected:

IMAGE MISSING

The Endpoint Agent scheduled test results view consists of the following components:

1. **Test selector:** Selects the test to display in the view
2. **Layer selector:** Selects the layer to display. The HTTP Server tests have Network layer available when Perform network measurements setting is enabled in test's Advanced Settings tab.
3. **Data filters:** Filters that can be applied to displayed data. The data displayed in the timeline \(5, 6\) and data view \(10\) is affected.
4. **Metric selector:** Choice defines the metric to be displayed on the timeline \(5\).
5. **Colored line on timeline:** Time series visualization of the selected metric \(4\)
6. **Grey area on timeline:** Time series of the number of endpoint agents providing the data
7. **Time interval selector:** Data from the selected time interval is displayed in the data view \(10\) below.
8. **Time range selector:** Colored section defines the displayed data \(5,6\). The remaining data is shown in grey.
9. **Selected time:** Confirmation of the selected time interval
10. **Data view pane for the selected time interval:** Display of data submitted by the endpoint agents that match the configured filters \(3\) in the selected time interval \(7, 9\). 

## Using the HTTP Server test view

In Figure 3 above, the HTTP Server test results view is depicted. The HTTP Server test collects the following metrics:

* **Availability**: Percentage of time that the site is available, aggregated across all displayed agents.
* **Response time**: Also known as time-to-first-byte, this is the time elapsed from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the server.
* **Throughput**: The metric is calculated by dividing the total wire size by the receive time and expressed in MB/s.

 Additional information about the collected metrics is available in the comprehensive [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC) article.

The bottom pane on the HTTP Server view is split into two tabs:

* **Map** view shows the geolocation of the agents in a map and a break down of the connection status by different phases. The informational message below the status bars shows the number of agents that collected data out of the total checked-in agents for the selected test time interval.
* **Table** view provides a break down of the selected metrics collected per agent for the selected time interval.

## Using the Network test view

The Network layer can be opened by clicking on the **Network** link \(1\) as shown below:

IMAGE MISSING

Click on the **Network** link as outlined in the screen capture above leads to the Network test results view. The Network \(Agent to Server\) test on an Endpoint agent measures the following metrics \(2\): 

* **Loss**: End-to-end packet loss. The percentage of packets lost is calculated by subtracting the number of reply packets the agent receives from the target \(responses\) from the number of packets sent by the agent, then dividing by the number of packets sent, then multiplying by 100.
* **Latency**: The average of the round-trip packet time. Round-trip packet time is the time from which a packet is sent by the agent to the time the agent receives a reply.
* **Jitter**: The standard deviation of latency. The standard deviation indicates how widely spread are the measurements around the average. A larger standard deviation indicates a wider spread of the measurements.
* **TCP Connection Failures**: Number of agents that failed to establish TCP connection to the target in the test round. The **TCP Connect** option must be enabled on the test for this data to be available. If a connection failure occurred the relevant error message will be shown under the **TCP Connect** column heading in the **Table** view in the bottom pane.

 Additional information about the collected metrics is available in the comprehensive [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC) article.

The available metrics can be selected for display in the **Metrics** drop-down menu \(pointer \#2 in the Screen capture no.4 above\). Additionally, metrics are also represented and clickable \(2\) on the left side of the **Map** \(1\) tab content on the bottom pane:

IMAGE MISSING

The bottom pane on the Network view is broken down into three tabs:

* **Path Visualization** \(outlined in the screen capture no.6 below\) shows an L3 hop by hop topology view from the source endpoint agent to the test target.
* **Map** view \(outlined above in the screen capture no.5\) shows the geolocation of the agents in a map view \(4\) and the collected metrics \(3\). The informational messages above \(2\) and below \(4\) below the metrics bars show the number of agents that collected data out of the total checked-in agents for the selected test time interval.
* **Table** view provides a break down of the metrics collected per agent for the selected time interval.

### Path Visualization for network tests 

Sample **Path Visualization** view for network tests:

IMAGE MISSING

More information of the Path Visualization view is available in the [Using the Path Visualization View](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC) article.  
 

## Data filtering

Endpoint Agent views provide extensive data filtering capabilities that enable users to drill down the data and present it in the most useful manner. In the following figure, the filtering controls are indicated:

IMAGE MISSING

Available filtering controls:

1. **Configured filters:** Shows currently configured filters. Clicking the **X** icon removes the corresponding filter.
2. **New filter dialogue:** Applies a new filter to the data shown. Multiple filters can be configured. Filters are combined using the logical operator "AND".
3. **Available filters:** Showing the list of filters available.
4. **Path Visualization-specific configured filters:** Shows currently configured filters \(path visualization only\). Clicking the **X** icon removes the corresponding filter.
5. **Path Visualization-specific new filter dialogue:** Applies a new filter to the data shown \(path visualization only\). Multiple filters can be configured. Filters are combined using the logical operator "AND".
6. **Apply to the entire view:** If a filter set configured specifically for the path visualization seems useful, clicking this link will apply the same filter to the entire view - the filters will be copied into the configured filters section at the top of the view \(1\).

 If configured, view filters \(1, 2\) are applied when snapshots are created. Path Visualization-related filters \(4, 5\) have no influence on the snapshot creation process.

## Frequently asked questions

A dedicated section containing questions and answers about scheduled tests on Endpoint Agents is available in the [Creating scheduled tests on Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents#faq) article.

