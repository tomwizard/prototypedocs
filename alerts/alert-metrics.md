# Alert Metrics

The following table shows a list of test types which are available in the ThousandEyes platform, and the test metrics and operators.   

| Test Layer | Alert Type | Metric | Operators | Units |
| :--- | :--- | :--- | :--- | :--- |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Packet loss | ≤,≥ | % |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Latency1 | ≤,≥ | ms |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Jitter | ≤,≥ | ms |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Error | is present, matches, does not match | n/a |
| Network | End-to-End \(Agent\) | Throughput | ≤,≥ | Kbps |
| Network | End-to-End \(Server\) | Available Bandwidth | ≤,≥ | Mbps |
| Network | End-to-End \(Server\) | Capacity | ≤,≥ | Mbps |
| Network | Path Trace | Delay | ≤,≥ | ms |
| Network | Path Trace | IP Address2 | in, not in | IP address or prefix |
| Network | Path Trace | ASN2 | in, not in | List of ASNs |
| Network | Path Trace | rDNS2 | in, not in | exact hostname or wildcard-based match to domain |
| Network | Path Trace | MPLS Label2 | is empty, is not empty |  |
| Network | Path Trace | DSCP2 | is, is not | DSCP value selected from list |
| Network | Path Trace | Server IP | in, not in | IP address, prefix |
| Network | Path Trace | Server MSS | &lt;, &gt; | bytes |
| Network | Path Trace | Path MTU | &lt;, &gt; | bytes |
| Network | Path Trace | Path Length | &lt;, &gt; | hops |
| Network | Path Trace | Trace is incomplete | n/a |  |
| DNS | Server, Trace DNSSEC | Error | is present, matches, does not match | n/a |
| DNS | Server | Resolution time | ≤,≥ | ms |
| DNS | Server, Trace | Mapping | is not in | quoted &lt;comma-separated list of mappings&gt; |
| DNS+ | Server Latency, Domain | Resolution Time | ≤,≥ | ms |
| DNS+ | Domain | Availability | ≤,≥ | % |
| DNS+ | Domain | Mapping | is not in | quoted &lt;comma-separated list of mappings&gt; |
| Web | HTTP Server | Response code | is | any error \(≥ http/400 or no response\) ok \(http/200\) redirect \(http/300 |
| Web | HTTP Server | Response Header | matches, does not match | [POSIX Extended Regular Expression Syntax](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnCKAS) |
| Web | HTTP Server | DNS time | ≤,≥ | ms |
| Web | HTTP Server | Connect time | ≤,≥ | ms |
| Web | HTTP Server | SSL negotiation time | ≤,≥ | ms |
| Web | HTTP Server | Wait time | ≤,≥ | ms |
| Web | HTTP Server | Receive time | ≤,≥ | ms |
| Web | HTTP Server | Response time1 | ≤,≥ | ms |
| Web | HTTP Server | Total Fetch Time | ≤,≥ | ms |
| Web | HTTP Server | Throughput | ≤,≥ | kBps |
| Web | HTTP Server | Error | is present, matches, does not match | n/a |
| Web | HTTP Server | Error type | is, is not | DNS, Connect, SSL, Send, Receive, Content, HTTP, Any |
| Web | HTTP Server | Client SSL Alert Code | is, is not | SSL error type.  eg. Unexpected message \( 10 \), Bad Certificate \(42\) |
| Web | HTTP Server | Server SSL Alert Code | is, is not | SSL error type.  eg. Unexpected message \( 10 \), Bad Certificate \(42\) |
| Web | Page Load | Page load | Is incomplete | n/a |
| Web | Page Load | Response time | ≤,≥ | ms |
| Web | Page Load | DOM load time | ≤,≥ | ms |
| Web | Page Load | Page load time1 | ≤,≥ | ms |
| Web | Page Load | Error Count | ≤,≥ | \# |
| Web | Page Load | Domain Name3 | is in, is not in | quoted &lt;comma-separated list of mappings&gt; |
| Web | Page Load | Total Fetch Time3 | ≤,≥ | ms |
| Web | Page Load | Blocked Time3 | ≤,≥ | ms |
| Web | Page Load | DNS Time3 | ≤,≥ | ms |
| Web | Page Load | Connect Time3 | ≤,≥ | ms |
| Web | Page Load | Send Time3 | ≤,≥ | ms |
| Web | Page Load | Wait Time3 | ≤,≥ | ms |
| Web | Page Load | Receive Time3 | ≤,≥ | ms |
| Web | Page Load | SSL Negotiation Time3 | ≤,≥ | ms |
| Web | Page Load | Component Load3 | is incomplete | n/a |
| Web | Transaction \(Classic\) | Error | is present | n/a |
| Web | Transaction \(Classic\) | Transaction Time | ≤,≥ | ms |
| Web | Transaction \(Classic\) | Completion | ≤,≥ | % |
| Web | Transaction \(Classic\) | Steps Completed | ≤, ≥, is | \# |
| Web | Transaction \(Classic\) | Any Steps meets | any, all | of the following conditions: Step Duration |
| Web | Transaction \(Classic\) | Step \# meets | any, all | of the following conditions: Step Duration |
| Web | Transaction \(Classic\) | Any Page meets | any, all | of the following conditions: Page Duration |
| Web | Transaction \(Classic\) | Page \# meets | any, all | of the following conditions: Step Duration |
| Web | Transaction | Marker | is/is not present, duration ≤, ≥ | ms |
| Web | Transaction | Assert Error | does not match, is present, matches | value |
| Routing | BGP | Reachability | &lt;,&gt; | % |
| Routing | BGP | Path Changes | &lt;,&gt; | n/a |
| Routing | BGP | Origin ASN | is in, is not in | comma-separated list of ASNs. |
| Routing | BGP | Next Hop ASN | is in, is not in | comma-separated list of ASNs. |
| Routing | BGP | Prefix | is in, is not in | comma-separated list of covered prefixes |
| Routing | BGP | Covered Prefix4 | exists, is in, is not in | comma-separated list of sub-prefixes |
| Voice | RTP Stream | Error | is present, matches, does not match | n/a |
| Voice | RTP Stream | MOS | ≤,≥ | \# |
| Voice | RTP Stream | Packet loss | ≤,≥ | % |
| Voice | RTP Stream | Discards | ≤,≥ | % |
| Voice | RTP Stream | DSCP | is, is not | DSCP Values.  eg Best Effort \(0\), Expedited Forwarding \(46\) |
| Voice | RTP Stream | Latency | ≤,≥ | ms |
| Voice | RTP Stream | Packet Delay Variation | ≤,≥ | ms |

1. For some metrics, dynamic baselines can be configured. See [Dynamic Baselines](dynamic-baselines.md) for more information.
2. These metrics are configurable under the "Any Hop", "Last Hop", or "Hop \#" entries in Path Trace alert rules.  Select "Any or "All" for multiple sub-conditions.
3. These metrics are accessed under the "Any Component" alert condition in Page Load Tests. Select "Any or "All" for multiple sub-conditions.
4. Only BGP Routing tests provide Covered Prefix data.  Do not assign a BGP Alert Rule with a Covered Prefix metric to a non-BGP test type that has BGP Path Visualization measurements enabled.  For non-BGP test types, use an Alert Rule that does not include the Covered Prefix metric, and if needed create a separate BGP test and an a separate Alert Rule with the Covered Prefix metric.

Each metric from the table above is defined in the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC)

