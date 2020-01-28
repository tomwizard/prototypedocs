# Enterprise Agents: what information do we collect?

This article explains the information captured by ThousandEyes Enterprise Agents, and information forwarded to ThousandEyes.

A Enterprise Agent is a system configured to run a supported version of Linux, which is deployed behind the firewalls of an organization in order to measure performance against either internal or Internet-based network assets.  Enterprise Agents are typically deployed using virtualization, and can be installed either as a package, in a supported version of Ubuntu, Red Hat Enterprise Linux, or CentOS, or as a prepackaged virtual appliance, which can be simply deployed into a number of different hypervisor platforms.

The diagram below shows a simple version of the connectivity between a Enterprise Agent, network assets you are monitoring, and ThousandEyes.

IMAGE MISSING

The following steps are repeated during the course of a Enterprise Agent's operation.

1. Wake up
2. Resolve assigned collector hostname
3. Determine operating system and kernel versions
4. Handshake with the agent collector
5. Check for results which have not yet been synchronized with the agent collector
6. Synchronize with the agent collector
7. Check current version against available version
   1. if version is out of date, initiate background update process
   2. determine next available window to apply updates
   3. apply updates
8. Get new task information
9. Go back to sleep until the next task needs to be run

##  Specific test information

The information is exchanged with the assigned agent collector; the type of information exchanged with the collector depends largely upon which kinds of tests are being run from the ThousandEyes agent. In essence, our focus is twofold.  First, collection of timing information for each phase of a request, and second, information about each routable device \(aka "node"\) touched in the path between the agent and the destination, and the links that connect these nodes.

### Network data

Name, IP address, network prefix, and MPLS label information \(if any\), for each node encountered during a traceroute, as well as latency and MTU information for each link transited.  This information is also included in test information for tests have the _enable network measurements_ option checked.

From the example image above, when a network test is targeted for www.saas.com, timing, latency, jitter, and MTU info and identification info will be sent back for the following elements:

* The endpoint \(www.saas.com, 1.2.3.4\)
* Each node transited during the connection \(r1, firewall, r2, r3, r4\)
* Each link transited during the connection \(l1, l3, l4, l5, l6, l7\)

### HTTP Server data

Name, IP address, number of redirects, fetch timing, HTTP status codes and response headers for the target site.  Includes network data if the _enable network measurements_ option is checked.

From the example image above, when an HTTP Server test is targeted for http://internalweb, the following information will be sent back:

* Network information \(Endpoint=http://internalweb, 10.0.0.1, nodes=r1, links=l1, l2\) 
* Http status code, response headers and timing for the attempt to access the website.

### Page Load data

Includes HTTP Server data, plus an HTTP archive \(using HAR output spec\) for page load, which includes detailed timing and descriptive information for each component on the page.  A HAR file is a container which contains a lot of information, and may include the following details:

* Name and path of the agent
* how long it takes to fetch DNS information
* how long each object takes to be requested
* how long it takes to connect to the server
* how long it takes to transfer each object from the server to the browser
* whether or not the object is blocked

The HAR output specification can be found here: [http://www.softwareishard.com/blog/har-12-spec/](http://www.softwareishard.com/blog/har-12-spec/).  To generate a HAR file for yourself \(or see a sample file\) and investigate the contents of the file, see this [article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmo4KAC).

From the example image above, when a page load test is attempted against www.saas.com, the following information will be sent back:

* Network data \(Endpoint = www.saas.com, 1.2.3.4, nodes=r1,firewall,r2,r3,r4, links=l1,l3,l4,l5,l6,l7\)
* HTTP Server data \(status code, response headers, timing\)
* Page load data \(HAR file containing detailed timing and descriptive information about each component on the page\)

### Transaction data

Includes page load data \(HAR content\) for each step page visited during execution of the transaction.  Transactions do not include network or HTTP server information.

### DNS Trace data

Output from dig +trace from the Enterprise Agent to the destination DNS record

From the example image above, when a DNS trace is attempted against www.saas.com A, the following information will be returned:

```text
. 18501 IN NS c.root-servers.net.
(...)
. 18501 IN NS d.root-servers.net.
;; Received 228 bytes from 8.8.8.8#53(8.8.8.8) in 919 ms
com. 172800 IN NS c.gtld-servers.net.
(...)
com. 172800 IN NS d.gtld-servers.net.
;; Received 490 bytes from 202.12.27.33#53(202.12.27.33) in 6797 ms
saas.com. 172800 IN NS ns2.servervault.com.
saas.com. 172800 IN NS ns1.servervault.com.
;; Received 110 bytes from 192.31.80.30#53(192.31.80.30) in 502 ms
www.saas.com. 3600 IN A 216.12.130.234
saas.com. 300 IN NS ns1.servervault.com.
saas.com. 300 IN NS ns2.servervault.com.
;; Received 126 bytes from 216.36.34.197#53(216.36.34.197) in 38 ms
```

### DNS Server data

IP mapping, timing and errors against each authoritative DNS server selected in the test configuration.  

From the example image above, when a DNS Server test is attempted for www.saas.com A, the following information will be returned:

* Authoritative nameservers for the DNS record \(ns1.servervault.com, ns2.servervault.com\), plus associated IP addresses for those servers
* Average availability, error count and resolution time from the Enterprise Agent to the nameservers

### DNSSEC Trace data

Trust tree and data chain information for each nameserver returned in a DNSSEC query, validated from the bottom of the chain up.  DNSSEC data will not apply to most customers.  For DNSSEC data, please refer [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmqKAC) for more information.

### Voice data

Voice metric data \(if the Enterprise Agent is the target of the Voice Test\) and Path Visualization data.

### Other Test data

BGP and DNS+ tests do not use Enterprise Agents.

## Data storage

During a test, and between check-ins with the agent collector, the Enterprise Agent stores all information locally, before uploading to the collector.  Once the information has been synchronized with the collector, it is removed from the agent.

## Security Controls

At ThousandEyes, we implement a number of policies and controls to ensure that customer information is protected from unauthorized access, including the following:

* Information Security policies and standards regulate the business processes and set acceptance criteria for information systems;
* Technical access controls are enforced at the application, system, and network layers;
* Logical data segregation is implemented at the application layer, all data elements are linked to a specific customer and may not be accessible to other customers.

