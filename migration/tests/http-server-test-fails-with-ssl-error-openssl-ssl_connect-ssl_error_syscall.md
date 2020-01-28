# HTTP Server test fails with SSL Error: OpenSSL SSL\_connect: SSL\_ERROR\_SYSCALL

An HTTP Server test or the HTTP Server view of a Page Load test may display the following error message:

```text
OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to <server:port_number>
```

in the **Error Details** column of the test's Table tab, as shown below.

IMAGE MISSING

This error typically occurs when the TCP three-way handshake between Agent and server completes \(successful Connect phase, per the Map tab\) but then a TCP reset packet \(often written as "RST"\) is received by the Agent, terminating the connection during the SSL phase. This error is not produced when an Agent receives a RST packet during the three-way handshake, or after completion of the SSL/TLS negotiation \(SSL phase\).

A packet capture from the Agent can confirm if the error is caused by a RST packet received after a completed TCP three-way handshake. Customers can perform captures using the tcpdump command-line utility from their Enterprise Agents. Contact ThousandEyes Customer Success to obtain packet captures from Cloud Agents.

The screenshot below from the Wireshark packet analysis program displays the RST packet which generated the error in the previous screenshot.

IMAGE MISSING

Customers seeing this error should identify all possible devices in the path between Agent and server that could be sending the RST packet. Some suggestions for identifying devices:

* Review the RST packet in the packet capture for possible indications of the source. For example, in the above packet capture, the RST packet \(frame 5\) has an IP Time to Live \(TTL\) of 63. Since 64 would be the most likely starting TTL for this packet, the system sending this packet is likely one routing hop away from the Enterprise Agent, "hq1eye". Check the Path Visualization View of the test for help in identifying the device.
* If the error occurs when the test is run from one or more ThousandEyes Enterprise Agents, the reset packet is likely issued by a proxy or firewall with application-level \(HTTP\) inspection or similar functionality in the network containing the Enterprise Agents.
* If the error occurs when the test is run from one or more ThousandEyes Cloud Agents, the reset packet is likely issued either by the server, or an intermediate device close to the server, such as a load balancer, reverse proxy, firewall or some similar security device. The more Cloud Agents receiving the error, the more likely the reset is issued close to or from the server.

Once possible devices are identified, review the logs and configurations of those devices for reasons why the reset might be sent. Some examples:

* A web application firewall \(WAF\) or firewall with application-layer features may block access based on parameters in the TLS negotiation, such as the Server Name Indication parameter in the Client Hello or value of the Application Layer Protocol Negotiation \(ALPN\) extension.
* A load balancer can perform TCP three-way handshake proxying, then pass the subsequent data from the Agent to a server which has no listening process bound to the TCP port used, or cannot perform SSL/TLS negotiation. An example of a [common device offering multiple forms of TCP three-way handshake proxying](https://support.f5.com/csp/article/K8082).
* A security device may apply a rate-based mechanism such as SYN flood protection to a client which exceeds the configured rate limit. In addition to checking the logs of security devices in the path for evidence of a SYN flood rate limit being reached. uncheck the **Perform Network measurements** box on the Advanced Settings tab of the test configuration, or change the **Probing Mode** on the Advanced Settings tab to "Force SACK" to try to avoid rate limits caused by the test's Network measurements.

