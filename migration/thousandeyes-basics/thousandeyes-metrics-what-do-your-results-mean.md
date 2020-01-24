# ThousandEyes Metrics: What do your results mean?

The following document explains each of the metrics captured by the ThousandEyes platform. These metrics are used across the platform, and may be of interest to those who are responsible for definition of Alert Rules.

These metrics apply to scheduled tests run on Cloud and Enterprise Agents. For information on Endpoint Agent metrics, review the ThousandEyes Knowledge Base article [Data collected by Endpoint Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpbKAC_Data-collected-by-Endpoint-Agent).

## Network Layer

### End-to-End Metrics

* _**Loss**:_ End-to-end packet loss. The percentage of packets lost is calculated by subtracting the number of reply packets the Agent receives from the target \(responses\) from the number of packets sent by the Agent, then dividing by the number of packets sent, then multiplying by 100.
* _**Latency**:_ The average of the round-trip packet time. Round-trip packet time is the time from which a packet is sent by the Agent to the time the agent receives a reply.
* _**Jitter**:_ The standard deviation of latency.  The standard deviation indicates how widely spread are the measurements around the average.  A larger standard deviation indicates a wider spread of the measurements.
* **Available Bandwidth:** Total available bandwidth between source and destination measured in Mbps. 
* **Capacity**: This metric is present in the Available Bandwidth table. It represents an estimation of the link capacity in Mbps, also used to measure the Available Bandwidth as a subsequent step. 

### Path Visualization Metrics

* **Avg. Response \(node property\):** Time-to-respond, averaged across all probe packet response timings.
* **Delay** and **Min. Delay \(link properties\):** Estimated minimum transmission delay across a given link. The value is calculated by finding the agent that reported the lowest response time for the node on the right-hand side of the link \(the node further from the agent\), then subtracting the same agent's lowest detected response time for the node on the left-hand side of the link \(the node closer to the agent\). When a single Path Trace from a single agent traverses the link, this metric is called **Delay**.
* **No. of Traces \(link property\):** The number of [Path Traces](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RslCAE_What-is-Path-Trace) that traversed a particular network path between two nodes. Expressed as X of Y, where Y is the number of all Path Traces across all agents presented in the test result.

## Routing Layer

### BGP Metrics

* _**Reachability**:_ The percentage of time during a round \(15 minutes\) in which the BGP router had a route to reach the destination prefix.
* _**Path Changes**:_ The number of AS path changes during a round. If a route is withdrawn and re-announced, it counts as 2 changes.
* _**Updates**:_ The plain count of BGP updates during a round of measurements. This number should always be strictly greater than or equal to the number of Path Changes.

## DNS Layer

### Server Metrics

* _**Availability**:_ The DNS server test targets a name resolution to a specific set of DNS servers. Availability can either be per server \(in which case it's 0% or 100% for a given agent\) or average across all the servers. If the name server does not provide a resource record for the specified domain and type, then it is considered an error \(availability&lt;100%\).
* _**Resolution Time**:_ The time it takes to query a specific name server for the given domain.

### Trace Metrics

* _**Availability**:_ The trace test does a resolution over the entire delegation chain for a given domain, similar to "dig +trace". Availability is 100% if the agent was able to resolve the given domain name, and 0% if an error was encountered at some point during the test.
* _**Queries**:_ The number of queries used to produce the trace.
* _**Final Query Time**:_ The resolution time of the very last query in the trace.

## DNS+ Layer

### Availability

* _**Availability**:_ A resolution is successful if the open resolver answers with a resource record for the given domain \(availability=100%\), otherwise the resolver is marked with an error that can be either "No mapping", "NXDOMAIN", "SERVFAIL", or "Truncated". The Availability is typically shown in an aggregated format \(per country or per network\).
* _**Vantage Points**:_ The number of open DNS resolvers used to collect the data.

### Resolution

* _**Resolution Time**:_ The time it takes for the DNS resolver to perform a DNS resolution to the very last name server in the chain. As with the previous metric, this metric is shown in an aggregated format, either per country or per network.

### Mappings

* _**Mappings**:_ A DNS resource record is a mapping of one value to one or more other values. For example, the A record for "google-public-dns-a.google.com" maps to the IP address 8.8.8.8 and the A record for "google-public-dns-b.google.com" maps to the IP address 8.8.4.4.
* _**% of Vantage Points**:_ The fraction of resolvers that reply to the DNS query with a specific resource record. As with all DNS+ metrics, this metric is aggregated either per country or network. For example, a weight of 6.9% for the mapping 69.171.247.21 coming from querying [www.facebook.com](http://www.facebook.com/) A in the United States means that 6.9% of the resolvers that were queried for [www.facebook.com](http://www.facebook.com/) type A had the resource record 69.171.247.21 in the response.

### Server Latency

* _**Latency**:_ The time it takes for a DNS resolver to perform name resolution to a designated name server. As with previous metrics, this metric is shown in an aggregated format, either per country or per network.

## Web Layer

### HTTP Server

* _**Availability**:_ The Availability for a given agent should be 100% if the HTTP status code is 2xx or 3xx, and 0% otherwise. The average Availability can take any value from 0% to 100%.
* _**Response Code**:_ The HTTP status code returned by the agent when fetching the URL. The test follows up to a maximum of 10 redirects in a row, which is indicated in the table as "Number of redirects". See this [link](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) for definitions of HTTP response codes.
* _**Response Time**:_ Also known as Time-to-first-byte, this is the time from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the web server.
* _**DNS Time**:_ The time required for the agent to perform a DNS resolution of the hostname in the URL.
* _**Connect Time**:_ The time required to establish a TCP connection with the web server.
* _**SSL Negotiation Time**:_ The time required to negotiate SSL/TLS.
* _**Wait Time**:_ The time elapsed between the completion of sending the HTTP request and the time the Agent receives the first byte of the response from the web server.
* _**Receive Time**:_ The time elapsed receiving the response from the server \(time from first byte to last byte of payload\)
* _**Throughput \(MB/s\)**:_ The throughput, measured in megabytes per second.  This is the **Wire Size** divided by the **Receive Time.** 
* _**Wire Size**:_ The size of the object while in transmission.  Often, HTTP responses are compressed prior to transmission, so wire size may be less than actual size if the object is compressed by the server.
* _**Total Time**:_ This is the sum of response time and receive time. In other words: DNS time + Connect time + SSL negotiation time + Wait time + receive time.

### Page Load

* _**Response time**:_ Also known as Time-to-first-byte, this is the time from the beginning of the request \(before DNS request\) until the client receives the first byte of the response from the web server.
* _**Total Wire Size \(kB\):**_ The size of all the objects in the page while in transmission.  Often, HTTP responses are compressed prior to transmission, so wire size may be less than actual size if any objects are compressed by the server.
* _**Throughput \(kB/s\)**:_ The throughput, measured in kilobytes per second.  This is the **Total Wire Size** divided by the sum of the **Receive Times** for each object \(taking into account that some of the downloads are overlapping\). For example, if object A has an overlap of 50% with object B and they both take T time to download, the time that is considered for Throughput computation is 1.5\*T.
* _**Objects**:_ The number of objects in the page, including images, css files, html index page, javascript files, etc.
* _**Component**_ Errors: The number of component errors in the page. For example, an image that fails to load.
* _**DOM Load Time \(ms\)**:_ Also known as Time-to-interaction, the time required for the browser to build the Document Object Model for the page, which is the skeleton of the page, not including images. This maps to the DOMContentLoaded event.
* _**Page Load Time \(ms\)**_: This maps to the load event triggered when the web page is fully loaded. Generally, the Page Load time is higher than the DOM Load time.

### Waterfall Object Timings

* _**Blocking:**_ The time an HTTP request waits for system resources to become available that are needed to make a connection to a web server.  The most common reason for significant blocking time is the per-domain concurrent connection limit.
* _**DNS:**_ The time required for the agent to perform a DNS resolution of the domain name in the request for the object.
* _**Connect**:_ The time required to establish a TCP connection with the web server.
* _**SSL:**_ The time required to negotiate SSL/TLS.
* _**Send:**_ The time required to send the HTTP request to the web server.
* _**Wait**:_ The time elapsed between the completion of sending the HTTP request and the time the Agent receives the first byte of the response from the web server.
* _**Receive**:_ The time elapsed in receiving the response from the server \(time from first byte to last byte of payload\).

### Transaction

* _**Completion**:_ Each web transaction has an initial and final step that can be configured by the user. Completion refers to the fraction of transaction steps that are executed between the initial and final steps.
* _**Transaction Time**:_ The time taken to execute the transaction, counting from the initial step until the final step.

### FTP

* _**Throughput:**_ The throughput, measured in megabits per second \(Mbps\). This is the Wire Size divided by the Transfer Time.
* _**Wire Size:**_ The size in bytes of the data transferred by FTP while in transmission. It is possible that an FTP server can compress data prior to transmission, so wire size may be less than original file size if the object is compressed by the server.
* _**DNS Time**_: The time required for the agent to perform a DNS resolution of the domain name in the request for the object.
* _**Connect Time**_: The time required to establish a TCP connection with the FTP server.
* _**Negotiation Time**_: Beginning after Connect, up to the time the FTP upload, download or list command is issued \(includes login\).
* _**Wait Time**_: Beginning after the FTP upload, download or list command is issued, until the first byte of the transfer..
* _**Transfer Time**:_ The time taken to transmit all bytes of the transfer.
* _**Total Time:**_ The sum of the previous timings.
* _**Response Time:**_ The sum of DNS Time, Connect Time, Negotiation Time and Wait time.

## Voice Layer

### SIP Server

* **Availability:** Percentage of time that the server responds to a request with a successful status code. By default, successful status codes are 2xx/3xx, but can be set to other status codes.
* **Response Time:** Also known as time-to-first-byte, Response Time is the time elapsed from the beginning of the request \(before DNS resolution\) until the client receives the first byte of the response from the server. The Response Time metric is accompanied by the individual timings that comprise Response Time: DNS Time, Connect Time and Wait Time.
* **Total Time:** Total Time represents time spent performing all phases of the test. The Total Time metric is accompanied by the individual timings that comprise Response Time: DNS Time, Connect Time, Redirect Time, Register Time \(if SIP registration is performed\) and Options Time.

### RTP Stream

* _**Mean Opinion Score \(MOS\)**:_ A number indicative of the perceived voice call quality. MOS being highly subjective, individual transmission parameters are transformed into “impairment factors” such as codec characteristics, delay, loss/discard ratio to obtain the R Factor. The following table relates user opinion MOS and R Factor IMAGE MISSING
* _**Loss:**_ **** A percentage of a stream of UDP encapsulated RTP packets that do not reach the destination.
* _**Discards**_: A percentage of the packets that are delayed over the network and are no longer required when they reach the destination.
* _**Latency**:_ The average time taken by the packets to reach the destination.
* _**Packet Delay Variation \(PDV\):**_ The average variation in unidirectional delay for packets reaching the destination.

