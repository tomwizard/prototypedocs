# MPLS Tunnel Inference using Deep Path Analysis

## Deep Path Analysis: Demystifying transit MPLS tunnels

Using Deep Path Analysis, users are able to identify partially obscured transit paths which leverage MPLS.  This allows users leveraging our Deep Path Analysis \(DPA\) technology to view the path taken over the Internet between each agent and destination.  As a refresher, we identify MPLS networks using the quick selection section of the Path Visualization interface, stating that X links are part of an MPLS tunnel.  There are four types of MPLS tunnels which can be in place - controlled through configuration of individual routers within the MPLS network.  

Based on the implementation of various configuration options on transit routers, including [RFC4950](http://www.ietf.org/rfc/rfc4950.txt) and [TTL-propagate option](http://packetlife.net/blog/2008/dec/22/disabling-mpls-ttl-propagation/), MPLS tunnels may be categorized as Explicit, Implicit, Opaque or Invisible.  

| **Tunnel Type** | **RFC4950** | **TTL-propagate** |
| :--- | :--- | :--- |
| Explicit | Enabled | Enabled |
| Implicit | Disabled | Enabled |
| Opaque | Enabled | Disabled |
| Invisible | Disabled | Disabled |

We'll cover the three types of MPLS tunnel inference we support \(Explicit, Implicit, and Opaque\), using the descriptions and explanations below:

### Explicit tunnel

Explicit MPLS tunnels \(tunnels not obscured using router configuration\) are displayed in full, with the links between each hop of an MPLS network being shown, complete with label information.  When an MPLS hop is detected in the path, the quick selection link will identify links which are part of MPLS networks, and display the label stack, when hovered over an affected link. 

IMAGE MISSING

### Implicit Tunnel

When devices are configured not to send MPLS stack entries, we can still infer that the link is part of an MPLS tunnel, and attempt to infer the hop number of the tunnel.  This will be represented in ThousandEyes as **Hop X in an MPLS Tunnel**.  While no label information may be available \(due to provider router configuration\), having the source IPs of the transit network may allow a service provider to cross-reference the externally-visible map against internal documentation, to find the true path taken.

IMAGE MISSING

### Opaque Tunnel

In circumstances where a single MPLS label is encountered but the IP TTL is reset at the ingress router, ThousandEyes will show the single hop, as an **X-hop MPLS tunnel**.  This information can be helpful when diagnosing network connectivity issues while transiting a service provider's network, since some hops may be obscured from the path visualization output, inferring a sometimes incorrect one-hop transit across the MPLS network.

IMAGE MISSING

### Invisible Tunnel

In circumstances where a no MPLS label is shown, and the TTL is not reset, ThousandEyes will be unable to detect the presence of an MPLS tunnel, and an erroneous link may be inferred. 

