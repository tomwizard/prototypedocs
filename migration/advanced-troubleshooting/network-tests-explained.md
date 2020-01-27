# Network tests explained

When you create any test with network measurements enabled, such as Agent to Server network test, HTTP Server, Page Load, or a DNS server test, you get access to the network layer data in the [Overview](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmtKAC) and [Path Visualization](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmiKAC) views for the test. This article describes the network measurement details and how gathered metrics are presented in the network layer views.

## Dual origin of network test results

Network measurements are available in a majority of ThousandEyes [tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn7KAC_Working-with-Test-settings). Network data collection is explicitly enabled in the [network layer](https://en.wikipedia.org/wiki/Network_layer) tests such as Agent to Server tests and Agent to Agent tests, where network measurements are the primary objective. On the other hand, for [application layer](https://en.wikipedia.org/wiki/Application_layer) tests, such as HTTP Server or a DNS Server tests, network measurements can be implicitly enabled and network data collected to assist with the application performance analysis.

Regardless of the test type, network layer data is always gathered in a similar fashion - two distinct measurement methods are used:

* [End-to-end network measurement]()
* [Path Visualization measurement]()

The **end-to-end network measurement** provides precise network quality measurement between two points in the network - the agent and the test target. To augment the end-to-end data, a second measurement is performed - the **Path Visualization measurement**, which complements the end-to-end data with network path information.

Once collected, the network data is available in two separate views:

* [Network &gt; Overview](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmtKAC) view
* [Network &gt; Path Visualization](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmiKAC) view

The **Network &gt; Overview** view provides an insight into the end-to-end network measurement results. The data is presented in a manner that enables the viewer to quickly spot any changes in trends and find the affected parts of the network, be it using the map-based visualization or a table view.

On the other hand, the **Network &gt; Path Visualization** view combines the data from both measurements. The objective of this view is to provide the ability to drill down into the network path information when analyzing, say, a network connectivity issue or an unexpected performance change.

In the figure below, an example of Path Visualization view is depicted. Green rectangles mark the areas where end-to-end data is presented, whereas sections enclosed in orange display data collected by the path visualization measurement:

IMAGE MISSING

When switching from Overview to the Path Visualization view, the time series visualization does not change and keeps showing the end-to-end data over time. The network path visualization graph under the time series is where path visualization data is displayed and where the merging of the data from both network measurements happens:

* **Agent nodes** \(marked with a green rectangle on the left side of the path visualization graph\) are colored based on the end-to-end data. For example, nodes with 0% detected end-to-end packet loss will be painted in dark green color, as shown in the figure above.
* **Network path nodes and links** \(enclosed in the orange rectangle on the right\) are representing the path visualization measurement data. The red circle in the example above indicates a network location where packet loss is potentially occurring.

 Now that we have enumerated the network measurement methods and how the collected data is presented in related views, let's get technical and delve into the details of how each measurement is performed.

### End-to-end network overview

The **Network &gt; Overview** view presents the loss, latency, jitter and, for tests running from [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) that enable it, the bandwidth estimation or throughput measurements data. The precise information about how each metric is calculated is available in [this dedicated knowledge base article](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean).

To perform the loss, latency and jitter measurement, a short stream of probe packets is exchanged between the agent performing the test and the target. The properties of this packet stream are used to calculate the network overview metrics. There are certain variations in how measurements are performed for particular test types. The following sections will provide further information for each test type.

#### Agent to Server measurements

Agent to server network measurement is performed whenever the target, be it a host or a service, is not a ThousandEyes agent process. Consequently, since we're measuring network characteristics against a remote target, measurements must by definition rely on target's responses and, therefore, on the assumed target's behavior. Target's behavior is expected to adhere to the specification of the network protocol used to perform the measurement.

Generally, there are three communication protocols used across the ThousandEyes test suite: [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol), [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol), and [ICMP](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol). Out of three, the UDP specification does not provide protocol-level facilities that could be used to generate a target's response - UDP is simply a [transport layer](https://en.wikipedia.org/wiki/List_of_network_protocols_%28OSI_model%29#Layer_4_%28Transport_Layer%29) protocol without any message delivery guarantees. With UDP, the decision about how a service should respond to incoming packets \(if at all\) is left up to the application layer entirely. Therefore, TCP and ICMP are the two protocols supported by the agent to server network measurements. Network measurements using each supported protocol are described in the following sections.

**Note:** While UDP is not supported by the agent to server network measurements, it is supported by the agent to agent tests - more on that in the [Agent to Agent measurements]() section below.

**ICMP-based Agent to Server measurements**

To gather the network layer data, ICMP-based measurement sends [up to]() 50 [ICMP echo request](https://en.wikipedia.org/wiki/Ping_%28networking_utility%29#Echo_request) packets to the destination IP address and expects the same number of responses in return - usually, the [ICMP echo reply](https://en.wikipedia.org/wiki/Ping_%28networking_utility%29#Echo_reply) packets are received. To correlate the responses with the sent packets correctly, each sent packet contains a unique "sequence number". A sequence number is a property of ICMP echo requests and responses - specification is available in [RFC-792](https://tools.ietf.org/html/rfc792) document.

Response packets are generated by the target - when an ICMP echo request packet is received, the target generates a new ICMP echo reply response packet. When doing so, the sequence number found in the request packet is extracted and copied into the response packet.

Back on the agent performing the measurement, when response packets are received, they are matched with outgoing packets using the sequence numbers. This enables the agent to extract the timing information from each request and response packet pair. This Timing information is used to calculate the latency and jitter metrics, whereas network packet loss is calculated from the response packet count.

The following figure demonstrates the [Wireshark](https://en.wikipedia.org/wiki/Wireshark) analysis of ICMP-based network measurement packet capture. The target of this ICMP network test was Google's public DNS service IP address 8.8.8.8:

IMAGE MISSING

In addition to demonstrating the visualization of ICMP-based probe packets and responses, the figure above is showing that the responses may not be received in the same order as probe packets were sent out.

**TCP-based Agent to Server measurements**

Conceptually, TCP-based agent to server network measurement does not differ much from the ICMP-based one - a stream of up to 50 packets is sent and the same number of responses is expected. The only real difference is that now, TCP is used. Previously mentioned ICMP echo request packets are replaced by the [TCP SYN packets](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Connection_establishment). Similarly, instead of ICMP echo replies, TCP SYN+ACK or RST packets are expected in return.

The following figure depicts how a TCP-based agent to server measurement looks like on a packet level. The target here is TCP port 53 of the Cloudflare's 1.1.1.1 DNS service:

IMAGE MISSING

It can be observed above that during the execution of the measurement, up to 50 TCP connections are attempted to be established. After the measurement is concluded, each initiated TCP connection is closed with a corresponding RST packet \(RST packets are not shown in the figure above\).

**Note:** This description of SYN-based network measurement method is a simplification of the actual situation, a simplification that is created for the purpose of the illustration of the concept. While agents are indeed capable of performing network measurements using the SYN-based method, ThousandEyes TCP-based network tests actually prefer another variation of the measurement, a method that is nicer to the target \(from the resource utilization perspective\). The [SACK and SYN-based network measurements]() section below contains further details.

#### Agent to Agent measurements

Network measurements of agent to agent tests are performed somewhat differently compared to the agent to server tests discussed above. The advantage of having access to both ends of the connection is used to enhance the accuracy of the measurement.

A high-level overview of the agent to agent tests is available in the "How ThousandEyes Agent to Agent Tests work" section of the [Agent to Agent Test overview](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmwKAC_Agent-to-Agent-Test-overview) article. Let's briefly summarize it here as well: after opening a regular TCP connection, the source and the target agent start the measurement process by exchanging an initial set of packets \(5 in each direction\) to synchronize their internal clocks. This part of the test is sometimes called a "clock sync preamble". Once clock offset and drift are accounted for, the actual probe packets \(50\) are sent to the target agent. The measurement is concluded by the target agent using the received packet count and timing information to calculate the connection characteristics \(loss, latency, jitter\).

The following screenshot visualizes how agent to agent measurement looks like on a packet level:

IMAGE MISSING

In the figure above, the 3 initial packets constitute the TCP three-way handshake, followed by a clock synchronization preamble of 10 packets \(5 in each direction\). Finally, the actual measurement probes are sent - always 50 packets \(partially shown in the figure above\) and always in one direction only.

**The advantage of** **the agent** **to agent tests is the ability to report true one way characteristics of a single network path.** Due to knowing in advance when, how many and with what rate the probe packets will be sent out by the source agent, the target agent can accurately measure loss, latency and jitter information for a single direction. On the other hand, agent to server tests rely on the target's responses, therefore the packet streams and, consequentially, collected metrics are influenced by network conditions in both network directions, from source to target and back from the target to source.

It must be noted here that in a **bi-directional** agent to agent test, the measurement process happens for **each direction independently**. When network characteristics are measured in the direction from target agent to source agent, the logical roles of source and target agents are reversed.

In addition to TCP, agent to agent tests support performing measurements using the UDP as well. The measurement method is essentially identical to the TCP method discussed above.

### Path Visualization

The Path Visualization view provides a detailed insight into network paths between agents and test destination \(or multiple destinations, in case of DNS load-balanced targets\). In the view, all detected network paths are potentially merged and displayed at once, with modal windows providing additional, network link- or hop-specific information.

Depending on the test type, the agent uses one of the available probing modes to determine the path to the destination. For ICMP-based tests, the ICMP echo requests are used. In TCP-based measurements, TCP SYN packets are used for path discovery and data collection.

The measurement starts with an attempt to estimate the path distance to the destination. Once the distance is estimated, the agent starts sending path discovery probe packets into the network. These packets contain increasing [Time-To-Live \(TTL\)](https://en.wikipedia.org/wiki/Time_to_live#IP_packets) values. The TTL values start from TTL=1 and incrementally increased by 1 until a response from the target is received, or the measurement is interrupted due to TTL rising significantly above the estimated path distance \(in case of suddenly unresponsive target\). In the event of an unresponsive target, the last detected network node is labeled as a "terminal node".

When an intermediate node \(such as a router or a firewall\) receives one of these probe packets, it inspects the TTL field and decrements its value by 1. If TTL is still higher than zero, the packet is forwarded to the next network hop. When TTL gets decremented down to zero, the packet is discarded and the node should reply with an [ICMP Time-To-Live exceeded](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Time_exceeded) message. The word "should" used in the previous sentence indicates a catch - it is not always that intermediate hops generate TTL exceeded messages - if such a message is not received by the agent, a blank \(white\) node is rendered in the path visualization graph. More information on missing information in path visualization view is available [in this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn4KAC_Reasons-for-missing-information-on-the-Path-Visualization-View).

The path discovery process is concluded when a response from the final destination is received, be it ICMP echo reply message, a TCP SYN+ACK packet or a RST packet.

By default, ThousandEyes agents perform 3 parallel path traces from each agent to try and discover multiple paths leading towards the target. In the test's advanced settings, this can be adjusted to up to 10 parallel path traces per agent. For TCP-based path traces, a unique TCP source port is used for each individual path trace \(and not for each individual packet\). This generates a unique five-tuple - in this context, a five-tuple is a data structure containing the protocol, source IP address, source TCP port, destination IP address, and a destination TCP port. Since [consistent hashing](https://en.wikipedia.org/wiki/Consistent_hashing) of five-tuples is usually used as a mechanism for load-balancing network traffic into multiple paths, using a consistent five-tuple per single path trace improves the reliability of multiple [ECMP links](https://en.wikipedia.org/wiki/Equal-cost_multi-path_routing) discovery.

In the following figure, a Wireshark analysis of ICMP-based path trace is shown. Shown are the echo request packets with TTL=1 and TTL=2 and the corresponding TTL exceeded packets:

IMAGE MISSING

In the next figure, TCP-based path trace is analyzed, showing the initial 3 TCP SYN packets and the corresponding Time-To-Live exceeded responses:

IMAGE MISSING

If at any point during the measurement, the agent receives an [ICMP destination unreachable](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Destination_unreachable) or a TCP RST packet, the path discovery process is interrupted and the node that generated such response is marked as a terminal node.

### Summary

To conclude our deep dive into the ThousandEyes network measurement details, it is important to understand that there are two distinct measurements performed \(more or less\) concurrently to gather network data. The data is presented in two network-related views and, more importantly, the data from both measurements are merged in the Path Visualization graph.

## Advanced topics

The following sections describe various details related to how ThousandEyes network measurements are performed.

### SACK and SYN-based TCP network measurements

ThousandEyes TCP-based measurements of loss, latency and jitter network characteristics support two modes of operation:

* SACK-based measurement \(preferred\)
* SYN-based measurement

**SACK-based** network measurements are the preferred choice of ThousandEyes tests. The main reason for the preference is the fact that SACK-based measurements put less strain on the target's TCP stack - only a single TCP connection is required to perform the measurement. To be able to perform the SACK-based measurement, the target needs to support [TCP selective acknowledgment](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Selective_acknowledgments) feature, which is nowadays supported by a majority of TCP implementations.

When an initial TCP three-way handshake is performed, the agent inspects the contents of the SYN+ACK response returned from the target to determine the target's support for SACK. If supported \(and if a few additional conditions are met, see below\), SACK-based measurement is performed by creating a one-byte gap in the data stream sent by the agent, causing the target to respond with selective acknowledgment messages for each received packet. This constitutes a stream of up to 50 probe packets sent and an equivalent number of response packets is expected to be received. The properties of this stream \(response packet count and timing information\) are then used for calculating connection loss, latency, and jitter.

On the other hand, **SYN-based** measurement is a fallback mechanism for situations where SACK-based data collection is not supported \(the following section explains the fallback mechanism\). SYN-based measurement uses a stream of up to 50 SYN packets, each being sent from a unique source TCP port. In turn, the equivalent number of SYN+ACK \(or RST\) responses are expected to be received from the target. Once the response packet count and timing information is collected, network characteristics \(loss, latency, and jitter\) are calculated.

#### Reasons for fallback to SYN mode

ThousandEyes tests provide means for configuring the network probing mode. While **Force SACK** and **Force SYN** modes are available, the default is to use the **Prefer SACK** mode, which instructs agents to, well, prefer SACK method and only use the SYN-based method as a fallback. There are multiple reasons why fallback from SACK to SYN-based measurement happens. The most common reasons are as follows:

* Target's SYN+ACK response packet does not indicate SACK support
* Target's SYN+ACK response packet indicates SACK support, but no SACK response is received within 1 second after sending the first SACK-based probe packet is sent
* Round trip time \(RTT\) of probe packets is considerably lower compared to RTT of packets used for establishing TCP connection \(SYN and SYN+ACK packets\)

Due to reasons above, unless forced to use SACK mode by the test configuration, the agent may switch to SYN-based measurement almost permanently. The switch decision is retained in agent's runtime memory, meaning that restarting the agent will erase the decision and the automatic network probing mode selection will be restarted.

### How the number of end-to-end probe packets is determined

ThousandEyes end-to-end network measurements \(loss, latency, jitter\) are based on a stream of packets, as described above. The number of packets in the stream depends on the following factors:

* The maximum number of probe packets sent is 50
* Measurement timeout is hardcoded at 8 seconds
* The rate at which the probes are sent out is based on a floating average of round trip time \(RTT\) - the inter-packet gap is roughly 1.5 x RTT

Therefore, on low-latency links, the number of probe packets sent will always be 50, as measurement timeout \(8s\) is much higher than 1.5 x RTT x 50. The situation changes on higher-latency links, where RTT is much higher. In such cases, less than 50 probe packets will be sent out before the measurement timeout is reached.

## Related information

The following ThousandEyes Knowledge Base articles provide additional information on this topic:

* [Reasons for Missing Information in the Path Visualization View](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn4KAC) discusses the various reasons for incomplete or missing information about path/nodes in the Path Visualization view.
* [ThousandMetrics: what do your results mean](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC) explains all the different metrics seen for different test types.
* [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) describes the firewall rules required for all the ThousandEyes tests which may be run on Enterprise Agents.

