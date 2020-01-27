# Using the Path Visualization View

When you create any test which includes network metrics – including Network, HTTP Server \(with network measurements enabled\), Page Load \(with network measurements enabled\), or DNS server \(with network measurements enabled\), or Voice, you get access to the Path Visualization view for the test.

## Interface components

The screenshot below shows the Path Visualization view for an [Agent to Server](https://rglnqsmc.share.thousandeyes.com/) Test.

IMAGE MISSING

1. _**Test selector**_ – use this control to change which test is being displayed in the view.  All tests will be shown here, including disabled tests and saved events.  
2. _**Test settings**_ – use this to open up test configuration for current test.  
3. _**Run Now**_ – Provides options to run current test in instant form with below options
   1. **Without changes** : Run an instant test with existing test configuration.
   2. **With changes**: Allows making changes to existing test configuration and run instant test with updated settings.
4. _**Views** available for this test –_ shows a list of shortcuts to other views for the selected test.
5. _**Metric selector**_– choose between the various network metrics available; these metrics are listed below.  Changing the selected metric will change the timeline \(\#3, below\) to reflect that metric, and change the coloring of agents in the visualization: Refer to   for more information on metrics captured by the platform. By default, the loss metric is selected while for Voice tests, the default metric selected is MOS.
   * _**Loss**_: a timeline with a flat set of results \(showing 0% loss\) is important for stability.  Agents are colored on a scale from green to red, with green indicating 0% end-to-end loss, and red indicating 100% end-to-end loss.   
   * _**Latency**_: a timeline with a flat set of results is an indication of a network with low latency.  Spikes indicate an increase in the amount of latency in the connection, and should be investigated if they are sustained.  Agents are colored on a scale from green to red, with green indicating low latency, and red indicating higher latency.
   * _**Jitter**_: A timeline with a flat set of results is an indication of a very stable network.  Increases in jitter are bad for networks which are used for streaming, and indicate a variation in latency/response time.  Spikes in jitter are usually correlated to increases/dips in latency.
   * _**Bandwidth**_**:** a timeline with flat set of results indicative of stable bandwidth availability. Spikes in the bandwidth graph indicate increase in network traffic load and are bad for streaming networks and bandwidth intensive applications.
   * _**Mean Opinion Score \(MOS\)**_**:** a timeline with a flat set of results indicates stable quality voice call. Agents are colored on a scale from green to red, with green indicating MOS of 5, and red indicating MOS of 1.
   * _**Discards**_**:** a timeline with a flat set of results \(showing 0% discards\) is important for continuous voice playback. Discard spikes indicate intermittent pauses in voice playback. Agents are colored on a scale from green to red, with green indicating 0% discards, and red indicating 100% discards.  
   * _**Packet Delay Variation \(PDV\)**_**:** a flat timeline measures least variation in packets and indicates stable voice call performance. Agents are colored on a scale from green to red, with green indicating least PDV \(0 ms\), and red indicating max PDV \(40 ms\).
6. _**Agents selector**_ – as found elsewhere in ThousandEyes views, this controls which agent is charted on the timeline.  When an agent is selected in this control, it will be automatically selected in the timeline.
7. _**Timeline**_ – shows the lesser of 30 days, or the length of time that the test has been enabled, by charting the average values for the metric selected \(see \#6\).  To change the data displayed, either use the 24h \(trailing 24 hours\) / 7d \(trailing 7 days\) / 14d \(trailing 14 days\) links, click the zoom out and latest buttons, or click and highlight the requested area of the chart, and it will re-draw appropriately.  Using the lower timeline will allow you to select a specific date or time and zoom in on events.
8. _**Date/time label**_ – when an instant in time is selected on the timeline, shown by the grey window on the upper timeline, the time and date of the selection are displayed here.  By default, the date/time selected in the previous view is selected, but if you enter the page directly from the views menu, the latest data will be selected by default.
9. _**Showing**_ - Select data for which Agents is visualized in graph and whether to show or hide  IP address labels.
10. _**Grouping dropdown**_ - Configure grouping of objects in visualization:
    * Agents: Group Agents based on
      * Agent: Individual path for each agent is visualized.
      * Network: Aggregate paths based on agent network.
      * Network & Location: Aggregate paths based on each combination of an agent's network and geographical location.
      * Location: Aggregate path based on agent's  geographic location.
    * Interfaces: Group interfaces by
      * IP Address: Aggregate paths based on an interface IP addresses.
      * Device: Aggregate paths based on device being monitored in ThousandEyes.
      * Network: Aggregate paths based on interface network.
      * Network & Location: Aggregate paths based on each combination of an interface's network and geographical location.
      * Location: Aggregate path based on geographic location of interfaces.
    * Destinations: Grouping destination nodes by
      * IP Addresses: Aggregate paths based on destination IP address.
      * Network: Aggregate paths based on destination's network.
      * Network & Location: Aggregate paths based on each combination of a destination's network and geographical location.
      * Location: Aggregate path based on geographic location destination exists in. 

The path visualization in below snippet has Agents grouped by Location, Interfaces grouped by Network and Destinations grouped by Network & Location: 

IMAGE MISSING

1.  _**Highlighting**_ - Configure thresholds to identify:
   * Nodes with Forwarding Loss above specified threshold.
   * Links with Link Delay higher than specified threshold.
2. _**Selecting**_ - Selecting nodes of interest creates a filter within the Showing link that may be applied to isolate visualization to Agents with paths that traverse selected nodes.
   * Individual nodes may be select to create a filter.  
   * An auto-filled Info drop-down may be selected to display objects with Alert, Error or distinct characteristics \(Info\) such as nodes within an MPLS tunnel or links associated with DSCP changes. IMAGE MISSING 
3. _**Highlight nodes that match**_ - Allows highlighting nodes by Network, Country, IP address, Prefix or Title based on text entered in search field.
4. _**Agent and Endpoint complexity controls**_: This control is also present in the path visualization view, but it effectively allows simplification of the Path Visualization by collapsing routes between various nodes on the Path Visualization.  The further apart the controls on the slider are, the less complex the visualization.  IMAGE MISSING

## Interacting with the Path Visualization view

Hover over any agent/node/link on the path visualization to pop up detailed information. Agents show the name, IP address, prefix, network, location and destination IP, as well as metrics statistics \(\#6 above\). Hovering on the nodes gives information on IP address, prefix, network, location and average response time. Links show their respective source and destination IP address, number of routes using that link, MPLS information and average link delay where possible.

Click a node or a link to select it.  Multiple objects can be selected at once.  Once an object is selected, it will show a moving dashed line surrounding the object.  Entire paths can be selected by double-clicking a node or a link.  All objects which traverse the object which is double clicked will have selection toggled on or off, based on the selection status of the object when it is selected.  

Once one or more objects is selected, the selected objects table link is activated. The link may display anything in the format \(X nodes\) \(and\) \(Y links\) selected.  Expand a table view of selected objects.  This will show two tabs: one for nodes, and one for links.

* nodes shows Node Name, AS number, and an X button to de-select the node.
* links shows the source and destination of each link, the number of routes \(shown in the visualization\) which transit that link, and the average link delay.

All nodes can be repositioned by clicking and dragging the node to a new place on the visualization pane, but the repositioned placement does not persist when the visualization is redrawn due to a change of time/date or display options.

## Legend

| **Object Image** | **What it signifies** | **Comments** |
| :--- | :--- | :--- |
| IMAGE MISSING | Agent location | Agent changes color based on the metric selected.  Scale goes from dark green \(no loss, latency, jitter, etc.\) to red \(severe loss, latency, jitter, etc.\) |
| IMAGE MISSING | Enterprise Agent | The color of a Enterprise Agent is double-ringed, and changes color according to the same scale as a ThousandEyes Cloud Agent. |
| IMAGE MISSING | Identifiable node | A blue node indicates that IP information is available.  |
| IMAGE MISSING | Unidentifiable node  | A white node indicates that IP information is not available. |
| IMAGE MISSING | Node in local network | A dark blue node indicates that a node was identified inside the agent's source network. |
| IMAGE MISSING | Node in destination network  | A node shaded in green indicates a node which was identified as inside the destination network, as specified by the Autonomous System of the customer. |
| IMAGE MISSING | Highlighted node  | A node can be highlighted using the Network, Country, IP address, Prefix or Title selector, while the other nodes are greyed out. This helps to quickly identify nodes based on their information. |
| IMAGE MISSING | Node with loss | A node circled in red indicates that loss is occurring at that point in the path, meeting the percentage threshold specified by the loss slider. |
| IMAGE MISSING | Endpoint node | A node circled in black, and showing an IP address beside it is an endpoint \(or target\) of the test.  |
| IMAGE MISSING | Selected node | A node circled in a moving blue dashed line indicates that the node is selected. |
| IMAGE MISSING | Selected link | A link represented as a moving blue dashed line indicates that the link is selected. |
| IMAGE MISSING | Collapsed path | A path showing a dotted line is an indication of a path which was simplified for visualization purposes.  Expand using the complexity slider, or by clicking the label indicating the number of hops which were collapsed.  |
| IMAGE MISSING | Split path | A path showing a split is an indication that there are multiple routes to the destination.  All path visualization is based on a minimum of three tests running from each agent.    When a path splits, the thickness of the line representing the link between the nodes will show how many of the tests traversed each link. |
| IMAGE MISSING | Link with high delay | A red link will indicate a delay meeting the threshold specified by the latency slider. |
| IMAGE MISSING | Unknown number  of hops between nodes | A dotted link with a question mark indicates insufficient data to determine the number of hops separating these nodes. Typically indicative of differing numbers of unresponsive nodes \(\* characters\) between responsive nodes, or an indication of path trace being unable to reach the destination when the end-to-end measurement was performed successfully. |
| IMAGE MISSING | Unable to reach target node | A dotted link with an `X` symbol indicates a trace that was unable to be completed to the target due to 100% forwarding and 100% end-to-end loss. |

