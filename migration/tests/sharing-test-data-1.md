# Path Visualization: edge firewall incorrectly shows single hop to destination

Depending on how internal networks are configured, you can end up in a situation where the path shown from Enterprise Agents shows the path to the edge firewall, and then a single hop to the ultimate destination, not representing the true path between the edge and the destination.

## Problem

Internal web traffic is routed through a proxy, which terminates outbound TCP connections and initiates a new connection for the interaction with the ultimate destination.

## Cause

In an included Network test \(i.e. part of a DNS or Web Layer test\) the ThousandEyes platform uses TCP as the protocol for path tracing rather than ICMP. Because the TCP connection gets terminated on the proxy, hops beyond the proxy cannot be seen. In this scenario, the path visualization will appear something like the image that is shown below. Enterprise Agent 4 is located in a network that does not use an internal proxy, whereas Enterprise Agents 1-3 are in separate data centers, each using a proxy, which is the second hop from the Agents.

IMAGE MISSING

## Workaround

If you encounter this scenario, you may need to change the TCP port of the test \(e.g.use 443 instead of 80\) or local special configuration \(e.g. filters based on the agent source IP\). Contact your network/firewall team to investigate bypassing of edge proxies.

## Resolution

The ThousandEyes team is actively working on alternative solutions to this problem, but we do not have a resolution at this time.

