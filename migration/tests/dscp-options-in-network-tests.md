# DSCP options in network tests

The ThousandEyes Path Visualization will show changes to a DCSP value for links represented in the Path Visualization of these test results:

* Network \(Agent-to-Server\)
* Network \(Agent-to-Agent\)
* Voice \(RTP Stream\)

Within the Path Visualization View choose Info under the "**Selecting**" Category to view any DSCP changes in your network tracing.

IMAGE MISSING

In this example clicking "3 links with DSCP changes" \(1\) will highlight link\(s\) where these occurred and will detail the specifics of the change \(2\). A change indicates how traffic is reprioritized.

IMAGE MISSING

IMAGE MISSING

## More about DSCP

A Differentiated Services Code Point \(DSCP\) is a value found in an IP packet header which is used to request a level of priority for delivery \(Defined in RFC 2474 [https://www.ietf.org/rfc/rfc2474.txt\)](https://www.ietf.org/rfc/rfc2474.txt%29). It is one of the Quality of Service management tools used in router configuration to protect real-time and high priority data applications.  
The DSCP value marks packets priority level for network device transmission and identifies its class type. A class type defines whether a packet is being used for data streaming, telephony and other uses. A high priority value helps expedite packet transmission to support more real-time dependent transmissions. DSCP markings can help reduce congestion and determine the priority of a packet to be dropped before a queue becomes full.  
Routers that are configured with QoS policies that honor DSCP will prioritize the processing and forwarding of queued packets based upon classification. Many networks do not honor differentiated services and may change the DSCP value to 0 \(best effort\) from another value.  A change will be illustrated if the DSCP value differs between nodes in the path visualization.  Below is a list of common DSCP values.

### The common defined per-hop behaviors are:

* Default Forwarding \(DF\) PHB — which is typically best-effort traffic
* Expedited Forwarding \(EF\) PHB — Expedited Forwarding – high priority, higher drop probability. dedicated to low-loss, low-latency traffic
* Assured Forwarding \(AF\) PHB — Gives assurance of delivery under prescribed conditions. The Assured Forwarding PHB guarantees a certain amount of bandwidth to an AF class and allows access to extra bandwidth, if available. \(See list below for those specifics\)
* CS PHBs — Class Selector network control. These are used for backward compatibility with the IP precedence specification in the former Type of Service \(ToS\) field.

| Name | Decimal Value  \(dscpId\) | Comments |
| :--- | :--- | :--- |
| Best Effort \(DSCP 0\) | 0 | Class 0, default \(routine\) |
| CS1 \(DSCP 8\) | 8 | Class 1 – similar to ToS Precedence \(priority\) |
| CS2 \(DSCP 16\) | 16 | Class 2 – similar to the ToS Precedence \(immediate\) |
| CS3 \(DSCP 24\) | 24 | Class 3 – similar to the ToS Precedence \(flash\) |
| CS4 \(DSCP 32\) | 32 | Class 4 – similar to the ToS Precedence \(flash override\) |
| CS5 \(DSCP 40\) | 40 | Class 5 – similar to the ToS Precedence \(critical\) |
| CS6 \(DSCP 48\) | 48 | Class 6 – similar to the ToS Precedence \(Internetwork Control\) |
| CS7 \(DSCP 56\) | 56 | Class 7 – similar to the ToS Precedence \(Network Control\) |
| AF11 \(DSCP 10\) | 10 | Assured Forwarding \(AF\) Class 1 – low drop precedence |
| AF12 \(DSCP 12\) | 12 | Assured Forwarding \(AF\) Class 1 – medium drop precedence |
| AF13 \(DSCP 14\) | 14 | Assured Forwarding \(AF\) Class 1 – high drop precedence |
| AF21 \(DSCP 18\) | 18 | Assured Forwarding \(AF\) Class 2 – low drop precedence |
| AF22 \(DSCP 20\) | 20 | Assured Forwarding \(AF\) Class 2 – medium drop precedence |
| AF23 \(DSCP 22\) | 22 | Assured Forwarding \(AF\) Class 2 – high drop precedence |
| AF31 \(DSCP 26\) | 26 | Assured Forwarding \(AF\) Class 3 – low drop precedence |
| AF32 \(DSCP 28\) | 28 | Assured Forwarding \(AF\) Class 3 – medium drop precedence |
| AF33 \(DSCP 30\) | 30 | Assured Forwarding \(AF\) Class 3 – high drop precedence |
| AF41 \(DSCP 34\) | 34 | Assured Forwarding \(AF\) Class 4 – low drop precedence      |
| AF42 \(DSCP 36\) | 36 | Assured Forwarding \(AF\) Class 4 – medium drop precedence |
| AF43 \(DSCP 38\) | 38 | Assured Forwarding \(AF\) Class 4 – high drop precedence |
| EF PHB \(DSCP 46\) | 46 | Expedited Forwarding – high priority, higher drop probability  |
| Voice Admit \(DSCP 44\) | 44 | Expedited Forwarding – high priority, higher drop probability |

