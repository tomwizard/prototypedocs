# What is Path Trace?

When working to diagnose a network issue with the ThousandEyes platform you will likely use the Path Visualization. This tool illustrates a visual representation of the Path Trace data collected for a round.

## [How Path Trace Works]()

A single Path Trace works similarly to how a single traceroute would work. Your source, in our case an Agent will send data packets to the target. Depending on your test settings these could be either an ICMP or TCP packets. If the test selection is an Agent to Agent test you have the additional option to choose UDP packets. The Path Trace starts by sending a packet directed at the test target with a Time-to-Live \(TTL\) value set to 1. Think of the TTL value as the expiration date on a packet, each routing device that receives this packet will decrease the value by 1 before routing it to the next hop. When the TTL value equals 0 a standard routing device will drop the incoming packet and reply with an ICMP TTLx packet, indicating that the packet will be dropped at this point. The next packet in the Path Trace sequence will have a TTL value set to 2, then followed by a packet with a TTL of 3 and so on. This process will continue until the Agent receives a response from the intended target, or the path is deemed unresponsive. For more information about how traceroute works, please see https://en.wikipedia.org/wiki/Traceroute or the more recent version https://paris-traceroute.net/about/

One of the key features of Path Trace is the ability to detect multiple routes to the same target. By default, an Agent will complete 3 Path Traces per round, in an attempt to uncover alternate routes.  For tests specifying a TCP target, the Agent will select a unique and random source port for each Path Trace. A unique source port will suggest to intermediary routing devices that each stream of data is unrelated and can be routed on different network paths.

IMAGE MISSING

## [Obtaining node metadata]()

We use the source address listed in the IP header of TTLx packets received from the Path Trace to identify each node. For nodes within the source Agent’s local network we run a reverse DNS lookup to discover the hostname otherwise just the IP address is listed. All other nodes are checked against WHOIS databases and Geo-IP.

IMAGE MISSING

As an example, the image above shows an IP address local to the US, this IP will be searched in ARIN \(American Registry\) where Salesforce.com will be shown as the owner. This can be checked at the following link: http://whois.arin.net/ui/

GeoIP services provide the location of the physical device hosting the IP address is. One such service is Maxmind to see how this works you can check out a demo here; https://www.maxmind.com/en/geoip-demo

## [Path Trace to Path Visualization]()

The Path Visualization displays Path Trace data and node metadata collected for the displayed testing round and presents it in easy to understand format.

To view Path Visualization data in a more traditional manner you can select **Show traceroute style output** from the pop-up menu displayed when hovering over an Agent’s name.

IMAGE MISSING

IMAGE MISSING

For a complete guide on using the Path Visualization consult the [Using the Path Visualization View](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC_Using-the-Path-Visualization-View-1472235331660) article.

## [API Access]()

Raw test data can be access via our [API](https://developer.thousandeyes.com/v6/test_data/):

* [https://developer.thousandeyes.com/v6/test\_data/\#/path-vis](https://developer.thousandeyes.com/v6/test_data/#/path-vis)
* [https://developer.thousandeyes.com/v6/test\_data/\#/traceroute](https://developer.thousandeyes.com/v6/test_data/#/traceroute)

