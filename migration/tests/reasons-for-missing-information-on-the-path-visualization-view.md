# Reasons for missing information on the Path Visualization View

The ThousandEyes Network test provides a [Path Visualization view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC_Using-the-Path-Visualization-View) which is similar to the **traceroute** command line utility that is available for many operating systems \(Windows systems have the **tracert** command\). This article describes the reasons why devices may not appear on the Path Visualization or not display information, as well as steps that customers can take to increase the amount of information provided in a Path Visualization.

## Path Visualization basics

A ThousandEyes Cloud Agent or Enterprise Agent performing a Path Visualization uses either TCP packets with the synchronize bit set \(SYN\) or ICMP echo request packets \(type 8, code 0\) depending on the Network test's **Protocol** setting. These packets are sent to each "node" or "hop" \(routing device\) between the Agent and the test target by manipulating the Time to Live \(TTL\) field in the IP header of each packet. A packet series is sent with abnormally low \(1, 2, 3...\) TTL values. Because the value in the TTL field is decremented by each router that will forward the packet, these low values ensure that the packets "expire" \(TTL becomes 0\) prior to reaching the target. A packet with a starting TTL = 1 will expire at the first node, a packet with a starting TTL = 2 will expire at the second node, and so on.

An expired packet is discarded, and the discarding router returns an ICMP time to live exceeded packet \(type 11, code 0\) to the sender \(the ThousandEyes Agent\) which notes the source IP address of the ICMP packet. In this way, each node in the path is discovered. For more information on the mechanics of traceroute, see the [traceroute Wikipedia page.](http://en.wikipedia.org/wiki/Traceroute)

When the trace's TCP or ICMP packets have the TTL set high enough to reach the test target, the target normally responds with either a TCP SYN-ACK packet or reset \(RST\) if the TCP port is not open, or an ICMP echo reply \(type 0, code 0\). When the Agent receives one of these types, the tracing process is ended.

In addition to the basic path trace mechanics, a ThousandEyes Path Visualization performs additional probing and packet manipulation to obtain more and better information than is provided by the traditional traceroute program. For example, in addition to the aforementioned packets with artificially low TTL values, the Path Visualization performs an initial "reverse TTL" probe, which sends packets to the target, then inspects the TTL value of packets returned from the target to get an independent measurement of how many nodes are in the path.

A ThousandEyes Path Visualization will graphically display the intermediate nodes between the ThousandEyes Agent and the test target. The Path Visualization will also provide information about each node, such as the node's IP address and DNS hostname \(if available\) as well as the network block \(Prefix\), the network block's owner \(Network\) and geographic location. The graphic below shows a Path Visualization from the Cloud Agent in Boston to the test target 93.185.216.34, with the mouse-over modal displaying the node's IP address and other information. 

IMAGE MISSING

The sections below describe the scenarios for Path Visualizations that do not display full information. A single Path Visualization may be affected by one or a combination of these scenarios.

## General approach

Obtaining information about the path between Agents and targets depends on the protocol used to perform the trace, and on the configuration of each device in the path, including the target. Customers should first try to obtain a Path Visualization using each of the protocols available in the **Protocols** setting. For one-way tests, the **Protocols** options are 'TCP' and 'ICMP'. For bi-directional \(agent to agent\) tests, the options are 'TCP' and 'UDP'.

Devices may negatively affect the Path Visualization either by blocking trace packets or failing to produce responses. The result may be one or more nodes that are rendered without any additional information, or that are not rendered at all. The sections below outline various scenarios' causes and possible steps to increase the amount of information on the Path Visualization.

In some scenarios, the solutions require reconfiguration of devices which do not belong to the organization performing the test, or to a service provider employed by that organization. In such cases, the required changes may not be possible.

## Missing information

### Single white node

A node in the Path Visualization may lack information, which is rendered as a white node in the path, and the modal that appears when mousing over the node will indicate that the Agent received no response from the node.

IMAGE MISSING

If the nodes before and after the white node are fully rendered \(blue or green\) then the most common cause is that the device is configured not to generate ICMP time to live exceeded responses when a packet's TTL expires at that node. Devices may be configured not to issue ICMP packets or a subset of ICMP types in order to avoid network scanning or device fingerprinting by malicious parties.

If the device being rendered as a white node is configurable by the customer, check the device's configuration to determine whether ICMP time to live exceeded packets can be generated and if so, whether these packets are generated but then blocked by an access control list or similar filtering mechanism. These packets can be restricted by access control list or similar mechanism to only be returned to the ThousandEyes Agents performing the Path Visualization, rather than to any source, if security requirements mandate that the device not be discoverable by sources outside of the customer's control.

### Single white node adjacent to target

If the single white node is the node to the left of the target, then the issue is likely to be a firewall or router whose ruleset or access control lists block the ICMP time to live exceeded packets from returning to the Agent.

IMAGE MISSING

### Multiple consecutive white nodes

If multiple consecutive white nodes in the Path Visualization appear, one of two scenarios is likely.

#### 1\) Firewall blocking ICMP time to live exceeded packets

If the consecutive white nodes extend up to the target, then a device leftward of the first white node may be filtering the ICMP time to live exceeded packets from devices beyond \(to the right of\) itself.

IMAGE MISSING

The most common reason is a firewall or router whose ruleset or access control lists block ICMP packets. In the Path Visualization above, the node immediately to the right of the ThousandEyes Enterprise Agent is a firewall which does not permit ICMP packets entering the internal network where the Agent is located. The target is unaffected in this scenario because the Path Visualization uses TCP. The Agent sent TCP SYN packets, and the target responded with TCP SYN-ACK packets to the Agent, which the firewall permitted. If the Path Visualization had used ICMP, the ICMP response \(echo reply\) from the target would have been blocked as well, and no nodes would have been rendered beyond the first node.

If the device suspected of blocking the ICMP time to live exceeded packets sent from the white nodes is configurable by the customer, check the rulesets or access control lists to determine whether ICMP time to live exceeded is permitted to reach the ThousandEyes Agent. Because the IP addresses of senders of these ICMP packets are not known in advance, allow ICMP time to live exceeded packets from any source IP address to the IP address of the ThousandEyes Agent.

#### 2\) Multiple devices not sending ICMP time to live exceeded packets

If the consecutive white nodes do not extend up to the target, then the consecutive nodes likely belong to an organization or organizations which have uniformly configured their devices not to generate ICMP time to live exceeded responses, as described in the [Single white node]() section, above.

IMAGE MISSING

If the devices are customer controlled, the devices may be reconfigured to allow ICMP time to live exceeded responses, as per the [Firewall blocking ICMP time to live exceeded packets]() section.

One or more nodes in the path may lack information \(white node\) or may be missing altogether from the Path Visualization. This often occurs with an Enterprise Agent installed behind a firewall. Below is a Path Visualization from an Enterprise Agent behind a firewall \(which is located before the first node in the path, but does not itself appear as a node; see below for explanation\).

IMAGE MISSING

In the above Path Visualization, the firewall does not have a node displayed because it is configured not to decrement the IP header's Time-to-Live field, so generates no ICMP Time-to-Live Exceeded packets.

The subsequent intermediate nodes send ICMP Time-to-Live Exceeded packets in response to the Agent's TCP or ICMP packets \(whichever the test is configured to use\). However, the firewall filtering ruleset does not permit ICMP Time-to-Live Exceeded packets to reach the Agent, resulting in white nodes for hops \#1 through \#6.

Once the Agent's TCP or ICMP packets reach the target \(208.185.7.123, lb-c1.thousandeyes.com\), the returned packets are no longer ICMP Time-to-Live Exceeded packets. The target responds with TCP SYN-ACK or ICMP Echo Reply, depending on the packets initially sent by the Agent. The firewall in this example can statefully associate these returned packets with the initial packets sent by the Agent, and permits them to reach the Agent. This is seen in hop \#7 of the Path Visualization graph - the target node. From this information, the Path Visualization can tell that there are six prior hops, although the responses from those hops never reached the Enterprise Agent, hence the nodes being rendered in white \(no node information\).

## Missing nodes

One or more nodes in the path may be missing completely from the Path Visualization for a few reasons. Nodes may be known to be missing due to knowledge of the customer, or perhaps the missing nodes are inferred, either by seeing consistent large jumps in latency between two visible nodes without a large distance to explain the additional time, or by a suspiciously small number of nodes in the path.

### Network Address Translation \(NAT\)

When multiple devices in a path are behind a device such as a firewall, load balancer or router which performs network address translation \(NAT\), nodes between the NAT device and the target may not be displayed. If these nodes are not displayed, a routing loop icon may be displayed instead.

### Proxied Agent

If an Enterprise Agent is configured to use a proxy server, a test's included Network metrics \(the Overview and the Path Visualization\) will not be performed unless the test target is configured on the Agent's proxy bypass list. Review the ThousandEyes Knowledge Base article [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#intro-additional-configuration) for more information on configuring a bypass list.

## Increasing the amount of information displayed

To increase the amount of information displayed in the Path Visualization, try both TCP and ICMP as the Network test's **Protocol** setting. One may yield the desired information, or at least display more information. If the results of using a different protocol are not sufficient, the following steps can be used to increase the amount of information displayed. The steps are split into two groups: one for the intermediate nodes, and one for the target of the test.

### Intermediate nodes

If the Path Visualization does not display intermediate nodes, or provides incomplete or no information about intermediate nodes, use the following steps:

* Determine which devices in the Path Visualization do not have a node displayed or do not show complete information for the node

   To determine if a node is missing, you will need knowledge of the devices that are actually in the path. Usually this information is only known about the networks under the control of your organization or an organization which can respond to inquiries from your organization.

* Determine which devices in the Path Visualization are controlled by your organization or an organization which can respond to inquiries from your organization

   If the issue resides with a device you cannot affect, you will not be able to change the Path Visualization. For devices belonging to unrelated network providers, it will typically not be possible to have changes made on the provider's device. However, a node belonging to an unrelated organization which is not correctly displayed may be due to a problem on a device under your control. See the next step for more information.

* For each device your organization controls or can inquire about, determine the answers to the following questions:
  1. **Does the device perform packet filtering?**

      Firewalls, routers, load balancers and other network devices can perform packet filtering. Also, the host operating system for a Linux package Enterprise Agent may have a packet filter such as **iptables**, or the target host may employ a packet filter which blocks the outbound ICMP or TCP packets from the Agent, or blocks the inbound ICMP Time-to-Live Exceeded packets returning to the Agent.

      It is important to keep in mind that a rule permitting the outbound test packets from the Agent may not be sufficient, even in a stateful firewall or stateful packet filter. A second rule or setting permitting the inbound ICMP Time-to-Live packets may be required if the software does not associate and permit the inbound ICMP Time-to-Live packets.

      The effect of packet filtering on the Path Visualization graph depends on which packets are filtered:

     * Filtering the outbound TCP or ICMP packets will prevent nodes between the filter \(possibly including the filtering device\) and the target from appearing on the Path Visualization graph. This will typically include the target node.
     * Filtering the returned/inbound ICMP Time-to-Live Exceeded packets returning to the Agent will render nodes between the filter \(possibly including the filtering device\) and the target as blank nodes on the Path Visualization graph. This will typically not include the target node.

      To address packet filter issues, check your device's packet filtering rules and properties or other global configuration settings, consult your security administrator or the documentation for the device, or contact technical support for the device's manufacturer.

  2. **Does the device perform network address translation \(NAT\)?**

      In addition to packet filtering, network devices such as firewalls, routers, and load balancers can perform network address translation. Translation rules must be in place for NAT'ing the outbound ICMP or TCP packets from the Agent and for NAT'ing the inbound ICMP Time-to-Live Exceeded packets returning to the Agent.

      Address translation can be done in several ways. For example, most implementations of port-based address translation \(PAT, also called one-to-many NAT\) typically will not translate the inbound ICMP Time-to-Live Exceeded packets returning to the Agent because ICMP packets lack port numbers in their headers. In contrast, a static one-to-one NAT should allow the needed ICMP Time-to-Live Exceeded packets returning to the Agent to be correctly translated.

      The effect of missing address translation rules on the Path Visualization graph are similar to the effect of packet filtering.

      To address address translation issues, check your device's translate rules, consult your security administrator or the documentation for the device, or contact technical support for the device's manufacturer.

  3. **Can the device issue ICMP Time-to-Live Exceeded packets?**

      Some devices are configured not to issue ICMP packets or a subset of ICMP packets. For example, a firewall may be configured not to send ICMP packets from itself in order to avoid network scanning or device fingerprinting techniques.

      If a packet is received by a device which does not issue ICMP Time-to-Live Exceeded packets, the TTL may still be decremented. But after decrementing, if the TTL = 0 then the packet will be discarded without generating an ICMP Time-to-Live Exceeded packet. The effect is to render the non-TTL generating device as a white node \(unknown\) on the Path Visualization. See the [Path Visualization Legend](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC_Using-the-Path-Visualization-View) for an example.

      To permit a device to issue Time-to-Live packets, consult your security administrator or the documentation for the device, or contact technical support for the device's manufacturer.

      If your organization's security concerns require that a device not provide information \(not issue Time-to-Live Exceeded packets\) to unapproved destinations, a packet filter rule can typically be used to drop the packets before they leave the device if the destination is not the ThousandEyes Agent.

  4. **Does the device decrement the Time-to-Live field in the IP header?**

      If the device does not decrement the value in the TTL field by 1 before routing the packet, then the device cannot issue an ICMP Time-to-Live Exceeded packet \(ICMP type 11\) because the condition for issuing ICMP type 11 packets is that TTL = 0. A firewall may be configured not to issue ICMP packets in order to avoid network scanning or device fingerprinting techniques, or a router in a multi-protocol label-switched \(MPLS\) network may not decrement the IP header's TTL for packets on a label-switched path.

      If not decrementing the packet's TTL, the device will always forward the packet to the next node. The effect is to omit the non-TTL decrementing device from the Path Visualization graph.

      To permit a device to decrement the Time-to-Live field of routed packets, check your device's configuration settings, consult your security administrator or the documentation for the device, or contact technical support for the device's manufacturer.

### Test target

If the Path Visualization shows 100% packet loss at the target, use the following steps:

* If the **Protocol** field of the Network test is set to TCP, verify that the target has a service listening on the port configured in the Network test's **Port** field.
* Verify that there is no host-based packet filter on the target or a firewall just before the target that is blocking the TCP or ICMP packets sent from or to the Agent \(Linux package-based Agents only\).

**NOTE:** Determining the answers to these questions will often require packet captures on the appropriate interface of the device in question. Keep in mind that if capturing the Time-to-Live Exceeded packets, the source IP address of these packets is not the IP address of the test target, but rather IP addresses belonging to interfaces on the intermediate hop devices. Any packet capture filters or display filters in your packet capture application need to take this into account.

## Related information

The following ThousandEyes Knowledge Base articles provide additional information on this topic:

* [Using the Path Visualization view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC_Using-the-Path-Visualization-View) describes the components in the Path Visualization view, including a legend for the graph's node rendering scheme.
* [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) describes the firewall rules required for all the ThousandEyes tests which may be run on Enterprise Agents.
* [Network tests explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmo3KAC_Network-tests-explained) describes ThousandEyes network measurements at the packet level.

