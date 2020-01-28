# Endpoint Agent Views - Network Topology

## Endpoint Agent Views - Network Topology

All data collected by Endpoint Agents within an account group as a result of a browser session or scheduled test is presented in [Endpoint Agents &gt; Views](https://app.thousandeyes.com/view/endpoint-agent/). This article focuses on the [Endpoint Agent &gt; Views &gt; Network Access &gt; Network Topology](https://app.thousandeyes.com/view/endpoint-agent/?&scenarioId=eyebrowGateway) ****view ****and explains in detail the information given on that page as well as how to navigate and use all the view features. If you are looking for a detailed explanation on the associated [Endpoint Agent &gt; Network Access &gt; Wireless](https://app.thousandeyes.com/view/endpoint-agent/?roundId=1560158400&metric=interface-metric-signal-quality&scenarioId=eyebrowWireless) view then please refer to the [Endpoint Agent Views - Wireless](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlmWSAS_Endpoint-Agent-Views-Wireless) article. 

  
IMAGE MISSING

**1. Add a filter:** Search through collected data using filters. The network topology filters span all data collected for the selected time span and persists across all Endpoint Agent views i.e. Scheduled Tests, Browser Sessions and the Network Topology view \(4\). The filters available for Network Topology view are broken down into two main categories, Agents and Network. The following is a list of all Network Access filter names and descriptions:

**Agents**

* **Location:** Geographical location of the Endpoint Agent
* **Connection:** Ethernet or Wireless
* **Network:** Endpoint agents public address blocks and names \(names displayed are provided by the Local Internet registry\)
* **Monitored Networks:** As specified in [Endpoint Agents &gt; Browser Session Settings &gt; Monitored Networks](https://app.thousandeyes.com/endpoint/browser-session-settings/?section=networks) tab
* **Agent:** ThousandEyes Endpoint Agents available in your Account Group
* **Agent Type:** The type of agent you have deployed and the two options are Endpoint Agent or Endpoint Agent Pulse
* **Platform:** Windows or Mac
* **Label:** Endpoint Agent Labels specified in [Endpoint Agents &gt; Agent Settings &gt; Agents Labels](https://app.thousandeyes.com/endpoint/agent-settings/?section=labels) tab

**Network**

* **Gateway:** Endpoint Agent gateway IP addresses are shown
* **Proxy Address:** Endpoint Agent proxies by IP address
* **VPN Address:** Endpoint Agent VPNs by IP addresses
* **SSID:** Endpoint Agent SSIDs
* **BSSID:** Endpoint Agent BSSID \(MAC of Wireless Access Point\)
* **DNS Server:** Endpoint Agent DNS servers by IP

**2. Metric Selector:** Under the Network Topology layer, measurements for the following categories of metrics are available and unless filtered \(1\) all results are averaged across all Endpoint Agents by default:

**DNS**

* **DNS Server Loss:** The percentage measurement of lost ICMP Echo Reply packets from the DNS server out of the total ICMP Echo Request packets sent.
* **DNS Server Latency:** The average of the round-trip packet time from all Endpoint Agents to their respective DNS servers. Round-trip packet time is the time from when a packet is sent by an agent to the time the agent receives a reply
* **Domain Resolution Time:** The average DNS resolution time \(in milliseconds\) for DNS requests made by all Endpoint Agents as a result of scheduled tests, recorded browser sessions or DNS, Proxy or VPN server name lookups.

**Gateway**

* **Gateway Loss:** The percentage measurement of lost ICMP Echo Reply packets from the gateway out of the total ICMP Echo Request packets sent.
* **Gateway Latency:** The average of the round-trip packet time from the Endpoint Agent to the Gateway. Round-trip packet time is the time from which a packet is sent by the agent to the time the agent receives a reply.

**Network Access**

* **Link Speed:** The detected Endpoint Agent's interface speed.
* **Wireless Signal Quality:** A percentage value from 0% to 100%. A value of 0% implies an actual RSSI \(Received Signal Strength Indicator\) signal strength of -100 dBm. A value of 100% implies an actual RSSI signal strength of -50 dBm.

**Proxy**

* **Proxy Loss:** The percentage measurement of lost ICMP Echo Reply packets from the proxy out of the total ICMP Echo Request packets sent.
* **Proxy Latency:** The average of the round-trip packet time from the Endpoint Agent to the Proxy server. Round-trip packet time is the time from which a packet is sent by the agent to the time the agent receives a reply.

**VPN**

* **VPN Loss:** Percentage measurement of lost ICMP Echo Reply packets from the VPN out of the total ICMP Echo Request packets sent.
* **VPN Latency:** The average of the round-trip packet time from the Endpoint Agent to the VPN server. Round-trip packet time is the time from which a packet is sent by the Agent to the time the agent receives a reply.

**3. Timeline:** The interactive timeline is designed to allow you to quickly and easily analyze your test results. Users will typically set a time period to analyze, jump back or forth in time by a set period then drill down into smaller periods. The timeline can be set to display any range of test data from 6 test rounds all the way up to 31 days of data. 

To set a time period:

* To `24h` \(24 hours\), `7d` \(7 days\) or `14d` \(14 days\) use the quick links located at the top left of the timeline
* Drag the beginning and end sliders in the lower timeline
* Do a single-click and drag on the main timeline 

 To move along the timeline:

* Click anywhere in the lower timeline
* Use the `Latest` button to jump to the latest results
* Using the next **&gt;** or previous **&lt;** buttons located at the lower right of the timeline
* Click any point in the main timeline

 The selected test round date, time and offset \(from the latest test results\) are displayed below the left corner of the lower timeline.

**4. Network Topology:** A view section that details how Endpoint Agents are connected to their gateways, Proxies, DNS servers or VPN terminators.  
**5. Network Topology filter:** The Network Access - Network Topology filter only applies to the test round selected in the main timeline. You can apply any selected Network Topology Filter to the main timeline \(3\) by clicking the `Apply to the entire view` link. As you span the timeline any filter will persist in the **Network Topology** view. Filters are broken into two main categories, Agents and Network \(see point 1 above for details of all available filters\).  
**6. Network Topology group agents option:** Allows you to group Agents in the Network Topology View by their:

* **Network:** Group agents by their public IP address block
* **Private Network:** Group agents by their private IP subnet
* **Location:** Group agents by their location as found in the [Endpoint Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page
* **Agent:** Group agents by Endpoint Agent name   

**7. Network Topology group wireless option:** In addition to grouping your agents by a network, location etc. you can also group your wireless devices by their:

* **Service Set Identifier:** Service Set Identifier \(SSID\) is a logical network. Users connecting to the same SSID will be grouped together.
* **Base Service Set Identifier:** Base Service Set Identifier \(BSSID\) is the virtual MAC address of device per SSID.
* **Access Point:** Physical MAC address of Access point. All user connecting to a common access point will be grouped together.

  
**8. Highlight:** The slider controls the level of network complexity that is displayed. It effectively allows you to simplify the Network Topology visualization by collapsing nodes on the path between your agents and your proxy, VPN or DNS servers. The further apart the controls on the slider are, the less complex the visualization.  
**9. Highlighting forwarding loss:** The slider control allows the user to quickly identify nodes by the detected forwarding loss. Nodes with forwarding loss &gt; X% are circled with a red outline in the visualization. This option defaults to 10% and runs from 0 to 100%.  
**10. Highlighting link delay:** The slider control that allows the user to quickly identify nodes by the level of detected link delay. A red link will indicate a delay meeting the threshold specified by the latency slider. The slider defaults to 100ms and is based on a sliding scale, beginning at 10ms to 300ms.  
**11. Highlight nodes that match:** A user can quickly highlight and identify nodes based on SSID, BSSID, Gateway, Client or PHY mode. To use this control, enter the desired search term into the search box and select one or more entries from the resulting list. When this option is used, relevant nodes in the visualization will be highlighted.  
**12. Display Node Labels:** Select to display a node's IP address, node's ASN or no label \(default\) next to all applicable nodes on the visualization.

##  Related Articles:

* [Quick Guide to Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpWKAS_Quick-Guide-on-Endpoint-Agent) is a quick guide about how to deploy and use Endpoint Agents.
* [Getting Started with Endpoint Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpZKAS_Getting-Started-with-Endpoint-Agent) is a comprehensive list of many articles relating to Endpoint Agent.
* [How does the Endpoint Agent work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpUKAS_How-does-the-Endpoint-Agent-work) describes how Endpoint Agents communicate with the ThousandEyes platform, what data they collect and how Endpoint Agents update themselves.
* [Endpoint Agent Views - Wireless](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlmWSAS_Endpoint-Agent-Views-Wireless) focusses on the [Endpoint Agent &gt; Views &gt; Network Access &gt; Wireless](https://app.thousandeyes.com/view/endpoint-agent/?roundId=1560158400&metric=interface-metric-signal-quality&scenarioId=eyebrowWireless) ****view ****and explains in detail the information given on Wireless view page as well as how to navigate and use all the view features.

