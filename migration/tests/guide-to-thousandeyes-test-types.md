# Guide to ThousandEyes test types

This article will walk you through all available ThousandEyes test types. Enabling you to decide what test type best fits your monitoring intentions, a list of typical usage scenarios is provided for each test type.

For the best reading experience, some general familiarity with ThousandEyes platform is welcome. If you are not yet familiar with ThousandEyes basics, watching the [Getting started with ThousandEyes](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmaKAC_Getting-Started-with-ThousandEyes) video \(~6 minutes\) will provide enough information to get you started.

## Classification of agent types

ThousandEyes collects data from various vantage points deployed around the internet and inside customer networks. For the most part, these vantage points are called "agents" - with a few exceptions outlined below. There are multiple types of agents available, each having a specific purpose:

* **Cloud and Enterprise Agents** are hosts \(or servers, if you will\) containing ThousandEyes software capable of running [instant or scheduled](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlzfSAC_Scheduled-v-s-instant-tests) tests and [device discoveries](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpmKAC_Discovering-Device-Layer-Devices). The main \(and almost only\) difference between Cloud and Enterprise Agents is who deploys and manages them - Cloud Agents are deployed by ThousandEyes, on many locations across the globe, instantly available for your new tests. Enterprise Agents, on the other hand, are deployed by you, our customer, in locations of your interest - your data centers, your branch offices and so on.
* **Endpoint Agents** are your Windows or Mac OS X workstations that have ThousandEyes Endpoint Agent software installed. These agents, whenever they are present in one of the defined networks, collect network and application layer performance data as your users are accessing websites or applications on configured domains. In addition to that, Endpoint Agents provide basic support for running scheduled tests. Pulse version of Endpoint Agents are also available dedicated to running scheduled tests, these can be installed on customer hosts.

There are two test types that are using different vantage points, not described above - routing layer test and DNS+ layer tests. Their vantage point specifics are outlined in the corresponding sections below. Regardless of the outlined data collection vantage point differences, tests from these two layers are listed in the [Cloud and Enterprise Agent-based tests]() section below. Metrics calculated at various layers along with their significance are documented in [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/articles/KB_How_to_Instructions/ThousandEyes-Metrics-What-do-your-results-mean?articleIdParam=kA044000000fyi5CAA_ThousandEyes-Test-Types) article.

To further understand differences between agent types, consult the [Comparison of Agent Types](https://success.thousandeyes.com/articles/KB_How_to_Instructions/Comparison-of-Agent-Types?articleIdParam=kA044000000fyi5CAA_ThousandEyes-Test-Types) article.

## Cloud and Enterprise Agent Based Tests 

 ThousandEyes tests are classified into categories based on layers of operation, as shown in the following diagram: 

IMAGE MISSING

## **Routing Layer**

Routing layer tests provide methods for collecting internet routing-related information. 

### BGP Test

This test type operates on the lowest fabric of the internet - the [BGP routing](https://en.wikipedia.org/wiki/Border_Gateway_Protocol) layer. Relevant BGP routing data is collected from ThousandEyes-provided BGP Monitors \(a.k.a. "Public BGP Monitors"\), from BGP peers that you connect to our infrastructure - the so-called [Private BGP Monitors](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmjKAC_Inside-out-BGP-visibility), or both at the same time. Collected data is presented as [BGP Route Visualization](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmpKAC_Using-the-BGP-Route-Visualization-view), a view that presents information in a cohesive manner, pointing out relevant events on the timeline and in the ASN graph. A BGP test also offers the ability to include prefixes covered by target prefix. 

As a quick start, a short video tutorial [Working with BGP Tests](https://www.youtube.com/watch?v=ezx7s3EfI7Q) should get you up to speed in no time.

#### Typical BGP test use cases: 

* Ensure network prefix reachability from multiple BGP vantage points on the internet.
* Detect and alert on BGP route leaks or BGP route hijacking.
* Validate and alert on active DDoS mitigation measures.
* Monitor presence and activity of multiple upstream network providers.
* Alert on unexpected path changes, unexpected upstream ASNs, route flapping, etc.

#### Example BGP test results:

The following figure is showing BGP path change detected by the St. Petersburg public BGP Monitor, where the network path through ASN20485 is replaced by a path through ASN9002:

IMAGE MISSING

To get a sensation of how interacting with collected BGP data feels like, you can review the contents of the test results depicted above interactively. To do so, visit the following [share-link](https://ascnkau.share.thousandeyes.com/).

## Network Layer

 This category of tests measures network performance and path between an Agent and a target device. Video tutorials: [Working with Network Tests](https://www.youtube.com/watch?v=dKdfPMG1o0Y) , [Working with Path Visualization](https://www.youtube.com/watch?v=H2qJhrNVEi0). 

### Agent to Server test 

 An Agent to Server test measures network performance as seen from ThousandEyes Agent\(s\)  towards a remote server. The target could either be an IP address or a hostname. Measurements in an Agent to Server test combine parameters of both, forward and reverse paths. To measure direction-specific parameters an Agent to Agent test can be utilized. 

#### Typical Agent to Server test use cases: 

* Measuring Network performance when accessing the target remote server from agents assigned to test.
* Understand network path changes between source to destination.
* Verification of target availability.
* Identify network degradation along the network path.
* Verify network management of  DSCP, MTU, and optimization.
* Monitor ingress traffic load distribution across ISPs.

#### Example Agent to Server test results:

 Below is Path Visualization for a test targeting google.com. Restricted access to Google results in 100% packet loss from Cloud Agent Beijing, China \(China Unicom\). The red circles signify nodes with forwarding loss. Hovering over a specific node will provide a modal with detailed information. 

IMAGE MISSING

 Here is a [sample test](https://iqvtkfni.share.thousandeyes.com/) to get your hands wet with an Agent to Server test.

#### Other included tests: 

* [BGP Test]()

### Agent to Agent Test

 Agent to Agent test evaluates the performance of the underlying network between two physical sites. The source and target for performing measurements here are ThousandEyes agents and can be both a Cloud Agent, an Enterprise Agent or a combination of both. For more information visit Agent to Agent Test overview.

#### Typical use cases: 

* Measure bi-directional network throughput.
* Measuring network connectivity characteristics between:

1.  Multiple data centers.
2.  Regional branch offices connecting to data centers.
3.  Regional branch offices connecting to IAAS cloud environments.
4.  Data centers connecting to IAAS environments.

* Branch office to HQ network quality via VPN and so on.
* Detect packet dropping network nodes on the path between source to destination.
* Evaluating the return path by performing bi-directional testing. Measure network performance and throughput between locations.
* Compare end-to-end network performance and characteristics between the forwarding and return paths.
* Measuring network characteristics between data centers, offices, and cloud environments.
* Evaluate network connections for specific applications.
* Detect latency and loss along the network path.

#### Example Agent to Agent test results: 

The below Agent to Agent test depicts a connection error between Cloud Agent Wellington, New Zealand and Cloud Agent Johannesburg, South Africa.

IMAGE MISSING

Visit this [share-link](https://poyrx.share.thousandeyes.com/) to feel an Agent to Agent test. 

#### Other included tests:

* [BGP Test]()

## DNS Layer

 This suite of tests is dedicated to Domain Name System performance measurements. Here is a video tutorial: [Working with DNS Tests](https://www.youtube.com/watch?v=SJ7cDzi6vHI), [DNS Monitoring with ThousandEyes](https://www.youtube.com/watch?v=7GKOvEtrxWc). 

### DNS Server Test

 DNS Server tests provide record validation and service performance metrics. Upon selecting a specific domain, and the servers to be queried, Agents will run DNS and network layer performance metrics for all targeted servers. Complete information is available within the following article:  [Using the DNS Server Metrics view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmrKAC_Using-the-DNS-Server-Metrics-view).

#### Typical use case: 

* Alert on incorrect DNS Record Mapping.
* Measure DNS nameserver performance and availability.
* Monitor network performance between agents and target servers.
* Compare DNS results and performance from around the globe.
* Verify GSLB and GeoDNS performance.

#### Example DNS Server test results:

 The below example depicts an iterative query made to authoritative servers for google.com

IMAGE MISSING

To get your hands dirty with a DNS Server test visit this [share-link](https://gpehi.share.thousandeyes.com/).

Other included tests: 

* [BGP Test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyi5CAA_ThousandEyes-Test-Types#bgp-test)
* [Agent to Server Test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyi5CAA_ThousandEyes-Test-Types#agent-to-server-test)

### DNS Trace Test

 Large DNS zones are divided into various smaller child zones with each child zone having dedicated authoritative DNS servers. When a DNS request is made the parent zone will refer the request to authoritative DNS server in the child zone. In this scenario ensuring DNS requests are correctly pointed to authoritative servers by a parent server and also the authoritative server being correctly configured to assert authority becomes crucial. The DNS Trace test helps validate this critical delegation A DNS Trace test will verify delegations from each parent zone to child zone. 

#### Typical use case:

* Verify the delegation of DNS records are being performed between parent and child zones as expected.
* Observe the DNS hierarchy of a target domain from various vantage points.

#### Example DNS Trace test results:

  Below is the test validating A record for [thousadeyes.com](http://www.thousadeyes.com/). 

IMAGE MISSING

 Here is a [sample test](https://ggjkirvg.share.thousandeyes.com/) to feel a DNS Trace test. Complete trace can be obtained by clicking **View Trace** link in the above screenshot.

### DNSSEC Test

[DNSSEC](https://en.wikipedia.org/wiki/Domain_Name_System_Security_Extensions) tests verify the digital signature of DNS resource records and hence validate the authenticity of resource records according to Domain Name System Security Extensions. A DNSSEC test add security validation to a [DNS Trace test]() and complement the same. 

#### Typical use cases: 

* Verify valid DNS signatures are being sent out along with DNS records.
* Validate DNS records based in DNSSEC.
* Observe the DNSSEC Trust Chain and Data Chain.

#### Example DNSSEC test results:

 Below is a sample DNSSEC test to A record for [dnssec-tools.org](http://dnssec-tools.org/). 

IMAGE MISSING

 Visit this [share-link](https://eipqvw.share.thousandeyes.com/) to get a sensation of DNS Trace test. Click on **Details** to see the Trust Tree showing chain of trust and Data Chain showing actual resource records received during the test. 

## DNS+ Layer

These set of tests are available only to premium ThousandEyes accounts. ThousandEyes DNS+ tests visualize the broadest view of DNS performance and availability as experienced by clients around the world. 

### DNS+ Domain Test

ThousandEyes query open DNS resolvers around the globe for the configured DNS Record and hence offer a panoramic view of DNS availability. Metrics measured are Availability, Resolution Time and Mappings. The latter two grouped by Countries and Networks worldwide. Visit [How DNS+ Domain tests work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBrCAK_How-DNS-Domain-tests-work) for more details.

#### Typical use case:

Observe reachability of a domain over the world from the eyes of ThousandEyes vantage points. 

#### Example DNS+ Domain test results:

Below is a DNS+ Domain test analyzing availability of A record for [thousandeyes.com](http://www.thousandeyes.com/)

IMAGE MISSING

Here is a [sample test](https://qruwodrtc.share.thousandeyes.com/) to know DNS+ Domain test better.

### DNS+ Server Latency Test

This is one of a kind test that will measure the total time taken to resolve a configured DNS record through Authoritative name servers from vantage points. DNS protocol in itself does not have the capability to measure this value making DNS+ Server Latency Tests one of a kind. ThousandEyes use a proprietary algorithm to generate this metric. Visit [How DNS+ Server Latency tests work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpgKAC_How-DNS-Server-Latency-tests-work) for an in-depth overview.

#### Typical use case: 

Measure the performance of DNS resolutions across the globe.

#### Example DNS+ Server Latency test results:

Below is a DNS+ Server Latency test targeting [ns1.google.com](http://ns1.google.com/).

IMAGE MISSING

Here is a [sample](https://royzbbmrl.share.thousandeyes.com/) test.

## Web Layer

These set of tests touch on various Web technologies starting from the most basic measurement of availability of web server all the way up to performing precision transactions on a target. ThousandEyes also support using [Custom User Agent Strings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn2KAC_Custom-User-Agent-strings-in-a-Web-test) for Web layer based tests. Watch [Working with Web Tests](https://www.youtube.com/watch?v=Cht-ehtUaeQ) to get up-to-speed with Web Layer tests quickly.

### HTTP Server test

As the name suggests, an HTTP Server test measures the availability and performance of an HTTP service. Any HTTP service that is exposed to the internet \(or intranet, if Enterprise Agents are deployed in your internal network\) can be tested.

The HTTP Server test is performed as a series of steps \(or phases\): 

1. **DNS**: The domain part of the test target URL is resolved to an IP address.
2. **Connect**: A TCP 3-way handshake is performed.
3. **SSL \(optional\)**: Security mechanisms are negotiated.
4. **Send**: An HTTP request is sent.
5. **Receive**: An HTTP response is waited for and received.
6. **HTTP**: The HTTP response code is validated.
7. **Content verification \(optional\)**: Verification of the received content is performed by matching it against a [regular expression](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnCKAS_POSIX-Extended-Regular-Expression-Syntax).

Many aspects of HTTP Server testing can be configured to suit your individual or corporate testing requirements - various authentication protocols are supported, custom headers can be added, SSL options tweaked and so on.

When HTTP Server test detects an issue, the results pinpoint the phase of a request in which the issue occurred, helping to decrease your mean time to repair. To assist the analysis, information from lower layers is included in this test type, namely [Agent-to-Server]() network and a [BGP routing]() layers are readily available when looking for the root cause. 

#### Typical use cases:  

* Alert on the HTTP service availability or performance issues
* Effectively detect issues with HTTP services served from multiple data-centers concurrently
* Measuring CDN delivery speed, comparison to origin-only serving

#### Example HTTP Server test results:

Here is an HTTP Server view for a test measuring the availability of [https://thousandeyes.okta.com](https://thousandeyes.okta.com/) service: 

IMAGE MISSING

To interactively review the test results depicted above, visit the [share link](https://bnleq.share.thousandeyes.com/) and give it a go.

#### Other included tests:

* [Agent to Server Test]()
* [BGP routing test]()

### Page Load Test 

 Page load tests utilizes te-chromium, a browser based upon the Chromium browser codebase, to obtain in-browser site performance metrics. The metrics include the completed page load time  and phase information for each DOM component. A complete explanation of how ThousandEyes presents DOM information is available here: [Navigating Waterfall Charts for Page Load and Transaction Tests](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Navigating-Waterfall-Charts-for-Page-Load-and-Transaction-Tests).  Instant page load tests provide a screenshot upon test completion,  while scheduled page load tests provide screenshots when errors are recorded. A list of permitted content types is available here:  [Permitted Content Types](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmxKAC_Permitted-Content-types-for-Page-Load-tests-1472236056151).

#### Typical use case: 

* Provide metrics regarding the  in-browser use experience.
* Identify objects preventing or prolonging page load completion.
* Monitor performance across content providers.

#### Example of Page Load test results:

 Below is a page load test targeting [Google](http://www.google.com/):

IMAGE MISSING

 Visit this [share-link](https://kuvtvf.share.thousandeyes.com/) to feel a page load test.

#### Other included tests: 

* [HTTP Server]()
* [Agent to Server Test]()
* [BGP Test]()

### Transaction Test

 Transaction tests emulate user interactions with a website. This test will perform a series of scripted steps, such as entering data into a form or clicking on a button, and provide completion time and performance metrics obtained while performing scripted actions.  Transaction tests utilize the  Selenium RC v1.0 server engine. Instant tests provide a screenshot upon test completion,  while scheduled tests provide screenshots when errors are recorded. A full list of support Selenium commands may be found here: [Transactions - supported Selenium commands](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Transactions-supported-Selenium-commands). 

#### Typical use case: 

* Emulate common user interactions, such as completing a purchase.
* Alert on site performance degradation.

#### Example Transaction test results:

 Here is a test imitating a google search transaction, steps in the transaction are: 

1. Open google.com.
2. click the Search box.
3. type keywords to search for.
4. Click Google Search. IMAGE MISSING

 An error has been purposely inserted into this test to demonstrate screenshots produced when errors are encountered.   
To view the screenshot:

1. Select an Agent with failed test round from dropdown menu.
2. Click the **View Screenshot** in the Map tab.

 Here is the [sample](https://yznurx.share.thousandeyes.com/) transaction test.

### FTP Server Test

 A [File Transfer Protocol](https://en.wikipedia.org/wiki/File_Transfer_Protocol) server is an essential storage component of modern enterprises. This test supports FTP, FTPS and SFTP protocols.

#### Typical use case: 

* Verify availability and performance of FTP server .
* Read, write, and list files within a user's directory .
* Verify SSH operation by selecting SFTP and performing a list test to any SSH enabled server. 

#### Example FTP test results:

 Here is an FTP test to [speedtest.tele2.net:21](http://speedtest.tele2.net:21/).

IMAGE MISSING

 Visit this [share-link](https://pewnnpen.share.thousandeyes.com/) to get a sensation of FTP Server test.

#### Other included tests:

* [Agent to Server Test]()
* [BGP Test]()

## Voice Layer

Voice Layer tests will look at whether a connection can be established \(SIP\) as well as tests the exchange of packets after the connection is made \(RTP\).  SIP stands for Session Initiation Protocol and RTP is an acronym for Real-time Transport Protocol.  These two actions enable Voice over IP connections.  VoIP is a method for delivering voice communications and multimedia sessions over Internet Protocol \(IP\) networks.  ThousandEyes provides a way to test the robustness and quality of these types of connections. Video Tutorial: [Working with Voice Tests](https://www.youtube.com/watch?v=KVFoHtHa_1c), [VoIP Monitoring with ThousandEyes](https://www.youtube.com/watch?v=KVFoHtHa_1c). 

### SIP Server Test

A SIP Server test will check the availability of Session Initiation Protocol VoIP Server. Additionally, this test could be configured to perform SIP register too. Consult [Using the SIP Server view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnW8CAK_Using-the-SIP-Server-view) article for more details.

#### Typical use case: 

* Verifying performance of a VoIP SIP server. 
* Confirming the ability to perform SIP Register with a target server. 
* Identify the phase at which a SIP Register fails.
* Observe the SIP Register and Options request and response.

#### Example SIP Server test results:

Here is a SIP Server test targeting an internal VoIP server.

IMAGE MISSING

Here is a [sample](https://puyxkx.share.thousandeyes.com/) SIP Server test.

#### Other included tests:

* [Agent to Server Test]()

### RTP Stream Test 

RTP Stream test measures the quality of Real-Time Protocol Voice stream between ThousandEyes agents acting as VoIP User Agents. For guidance on creating RTP Stream test please see [RTP Stream test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB7QCAW_RTP-Stream-test-settings) article.

#### Typical use case: 

* Identify the node responsible for degraded RTP Stream.
* Analyze effects of BGP Route changes on RTP Stream.
* Measure call audio quality in terms of
  * Mean Opinion Score
  * Loss
  * Discards
  * Latency
  * Packet Delay Variation

#### Example RTP Stream test results:

Here is an RTP Stream test between two Cloud Agents displaying Packet Delay Variation

IMAGE MISSING

Check out  this [sample](https://khyxaxgy.share.thousandeyes.com/) test to feel an RTP Stream Test.

#### Other included tests:

* [Agent to Server Test]()
* [BGP Test]()

### Voice Call Test

ThousandEyes Voice Call test is a comprehensive test for VoIP. SIP Registers are first performed followed by a call. Call quality is then assessed in terms of MOS for RTP Stream. This enables accurate impersonation of an actual call and depicts true user experience. For more details on how to set up a Voice Call test please see [Voice Call test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB63CAG_Voice-Call-test-settings) article. A point to be noted here is RTP Stream for a Voice Call test will not be available for a test between Cloud Agents.

#### Typical use case: 

* Check successful operation of the VoIP server and measuring quality of voice stream.
* Confirm ability of SIP Server to handle Voice calls.
* Observe voice quality in terms of Mean Opinion Score.
* Identify nodes responsible for causing degradation in call quality.

#### Example Voice Call test results:

Here is a Voice Call test targeting an internal VoIP server.

IMAGE MISSING

Here is a  [sample](https://lrihr.share.thousandeyes.com/) Voice Call test.

#### Other included tests:

* [RTP Stream Test]()
* [Agent to Server Test]()
* [BGP Test]()

## Endpoint Agent-Based Tests

Endpoint Agent tests are classified in below manner: 

IMAGE MISSING

Video Tutorial: [Getting Started with Endpoint Agent](https://www.youtube.com/watch?v=v18ojnn9iS0&t=7s)

## Unscheduled Tests:

Endpoint Agents record in-browser and network performance metrics whenever users navigate to monitored domains from monitored networks. Instructions on Endpoint Agent installation and configuration may be found here: [Configuring Endpoint Agent Setup](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBxCAK_Configuring-Endpoint-Agent-setup).

An Endpoint Agent offers various views for unscheduled tests as below: 

* [Endpoint Agent Views - Web](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Endpoint-Agent-Views-Web-1472238551343)
* [Endpoint Agent Views - Network](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Endpoint-Agent-Views-Network-1472238551289)
* [Endpoint Agent Views - Session Details](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Endpoint-Agent-Views-Session-Details-1472238551243)
* [Endpoint Agent Views - Network Topology](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Endpoint-Agent-Views-Network-Topology-1472238551163)

#### Typical use case: 

* Compare user experience across your organization.
* Identifying networks experiencing performance degradation.
* Identify DOM components affecting application performance.
* Identify network and wireless connectivity issues.

#### Example User Sessions:

Below is a Browser Sessions view showing latency from an Endpoint Agent and visited domain details.

IMAGE MISSING

Visit this [share-link](https://distu.share.thousandeyes.com/) to feel an actual user sessions snapshot. 

## Scheduled Tests

An Endpoint Agent also supports scheduled tests capability limited to Web- HTTP Server and Network:- Agent to Server test. [Creating scheduled tests on Endpoint Agents](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Creating-scheduled-tests-on-Endpoint-Agents) article will guide you through the process of creating a scheduled test on Endpoint Agents  while  [Endpoint Agent Views - Scheduled Tests](http://thousandeyes.atlassian.net/articles/KB_How_to_Instructions/Endpoint-Agent-Views-Scheduled-Tests) helps understand data. 

### Network- Agent to Server

An Agent to Server test measures round-trip network performance between an agent and a remote server. The target may be either be an IP address or hostname. 

#### Typical use case: 

* Measuring round-trip network performance from multiple vantage points.
* Monitor for, and comparing performance as a result of, network path changes.
* Verification of target availability.
* Identify network degradation along the network path.
* Verify network management of  DSCP, MTU, and optimization.
* Monitor ingress traffic load distribution across ISPs.

#### Example Agent to Server test results:

Here is an Endpoint based Agent to Server test targeting [thousandeyes.com](https://www.thousandeyes.com/) with ICMP probing. Links highlighted in blue are parts of MPLS tunnel.

IMAGE MISSING

Visit this [share-link](https://mhphxwbmc.share.thousandeyes.com/) to feel an Endpoint based Agent to Server test.

### Web- HTTP Server Test

An HTTP Server test measures the availability and performance of an HTTP service whether public or private. HTTP server tests included network layer Agent to Server tests using either TCP or ICMP. 

#### **Typical use case:**

* Alert on HTTP Availability and performance metrics by office or group of Agents.  
* Monitor Web application performance from company workstations.

#### Example HTTP Server test results:

Here is an Endpoint HTTP Server test to [youtube.com](http://www.youtube.com/).

IMAGE MISSING

Here is a [sample](https://dpzjmttew.share.thousandeyes.com/) Endpoint HTTP Server test.

## Related Articles:

* For more information on playing with test settings please visit: [Working with Test settings](https://success.thousandeyes.com/articles/KB_How_to_Instructions/Working-with-Test-settings?articleIdParam=kA044000000fyi5CAA_ThousandEyes-Test-Types).
* Transferring tests between Account Groups or Organizations: [Changing Ownership of Test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWcCAK_Changing-ownership-of-a-Test).
* The test data can also be shared by a public link as described here: [Sharing Test Data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data).
* The test data can also be visualized in the form of a report as explained here: [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports).
* ThousandEyes also offer Alert notification when configured event occurs as [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work-1476477151762) describe.
* [The Retaining data beyond the 90-day limit](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn3KAC_Retaining-data-beyond-the-90-day-limit) article explains how to permanently save events of interest.

