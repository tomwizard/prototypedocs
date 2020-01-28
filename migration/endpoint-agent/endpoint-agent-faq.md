# Endpoint Agent FAQ

**Q. What is Endpoint Agent?**

A. The ThousandEyes Endpoint Agent is an application that is installed on Windows or Mac OS X machines to collect network and application layer performance data when users access specific websites from within monitored networks. Using a custom-built installer \(which contains a built-in account key\), performance data collected by the Endpoint Agent is routed to your account group in ThousandEyes.

**Q.** **What are the prerequisites for installing and working with Endpoint Agents?**

A: Refer to our [Prerequisites](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBp) KB article.

**Q: What is the pricing model?**

A: For pricing, talk to your Sales representative.

**Q. When does the Endpoint Agent update? How often?**

A.The Endpoint Agent will auto-update. Bi-weekly, ThousandEyes will make updates available for all Endpoint Agents. When an update is available, each Endpoint Agent will download \(pull\) the update from downloads.thousandeyes.com. An out-of-date Endpoint Agent will be marked with an exclamation warning sign under Settings &gt; Agents &gt; Endpoint Agents.

**Q. How will an Endpoint Agent update?**

A. The Agent continuously checks for version updates. Once an update is available, the Agent will download the update and store it locally. Once an update is downloaded on the client machine, the Agent will wait for all user browsing activity to stop to apply the update, ie - it is required to quit all browser windows OR have no monitoring of monitored domains for 5 min.

**Q. How often does Endpoint Agent upload data?**

A. For periodic access network data we upload every 5 min, but unrelated to when the data was collected. We try to figure out the clock offset of all agents and collect the data at the exact same time \(or as close as we can\) so the data is looking at the same snapshot of the network. The upload is then done within 5 min of the test completes with a "random phase". This is to avoid all agents committing to our backend at once, but instead have a uniform distribution of uploads.

For user triggered data, we upload the data as soon as it becomes available under a few batching algorithms \(which currently adds maximum 5 sec delay\).

**Q: Can I filter or choose data that is recorded?**

A: Yes, data is only recorded for domains you configure, on networks you specify. When reviewing data, to filter results shown, users can search for samples based on a variety of metadata captured related to the machine, user, destination, etc. 

**Q. How long is data stored?**

A. All Endpoint Agent data is stored for 90 days..

**Q: Can samples be purged?**

A: No, there is currently no ability to purge data from the ThousandEyes service.   

**Q: Is data encrypted?**

A: Yes. Data encrypted during transit to ThousandEyes using HTTPS.

**Q: How is Endpoint Agent data kept private?**

A: Each Endpoint Agent installation contains a unique identifier identifying the account group where the Endpoint Agent installer was created.  Samples sent to ThousandEyes are stored and bound specifically to the account group owning the token.

**Q: Can I restrict data collection from certain countries?**

A: Yes.  Restrict data collection to specific networks, and exclude networks where you are unable or unwilling to collect data. Under Settings &gt; Agents &gt; Endpoint Agents &gt; Monitored Networks, you can "Disable Monitoring" for desired networks.

**Q: Is there a time lag for data collection?**

A: Not typically. Data is collected and uploaded within seconds of being collected. If the Endpoint Agent is unable to send data to ThousandEyes due to network connectivity issues, the data will be sent upon connection stabilization.

**NOTE**: There may be a short lag while network & system data is gathered and associated with its session. In that case, you may need to wait up to a couple of minutes to see all of the context in the Session Details view, for example.

**Q. What is a session?**

A. A session is a continuous interaction of the user within the same browser tab, domain, port and protocol. All pages visited within this interaction is grouped under the same session. Note: A session on the client is not equal to a User Session in the application.

**Q. When does the Endpoint Agent trigger a new session?**

| Navigates to a new domain, port and protocol within same tab | A new session is triggered |
| :--- | :--- |
| Navigates from http to https for same domain, protocol, tab combination | A new session is triggered |
| Navigates to new page\(s\) within same tab, domain, protocol, port combination | Web layer details will be appended to the current session |
| Opens a new tab for same domain, protocol, port already active in another tab | A new session is triggered. |
| Navigates to a different sub-domain within same tab, with no change in protocol, port combination | A new session is triggered. |

**Q. What is an Unknown Hop link? Or what does a “?” on a link indicate?**

A. When the Endpoint Agent is unable to trace the network path to the destination, but able to establish a TCP connection with the destination node, the link connecting the last traced to the destination will be shown as “ICMP blocked by destination” and/or marked with a “?”.

**Q. Hovering over network path says X of Y traces under Views &gt; Endpoint Data &gt; Network**

A. For the selected time period, as per Bin Size, the total number of User Sessions  = Y, and the number of User Sessions to that target node = X .

**Q: Can I generate reports on Endpoint data?**

A: Yes, you can access them via the [Reports](https://app.thousandeyes.com/reports/) section in your ThousandEyes Web UI, and start to track aggregate statistics around:

* Web metrics like completion & response time
* Network-centric metrics like loss & latency for destinations, gateways, proxies, & VPNs.
* Wi-Fi metrics like signal quality & transmission rate

Review our Working with [Reports](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnT) KB article.

**Q: Can I generate alerts on Endpoint data?**

A: Yes, refer to the [Alert](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work-1476477151762) document for more details.

**Q: Which platforms are supported?**

A: Operating Systems: Windows 7+ and above; Mac OS 10.9 and above.

Browsers: Google Chrome version 41+; Internet Explorer version 11+.

For more information, review our [Prerequisites](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBp) KB article.

**Q: Are VDI \(virtual desktop infrastructure\) environments such as Citrix or Terminal Services supported?**

A. There is only partial support for virtual desktop environments in that the Endpoint Agent can support so-called ‘thick client’ virtual desktops where each instance has its own set of resources. In ‘thin client’ environments \(like Terminal Services or Citrix\) where desktop instances are running as a shared pool of lightweight instances on the server, depending on the configuration the Endpoint Agent may not be capable of handling such a multi-homed environment.

**Q: My waterfall seems to go on and on and on… why?**

A: Many modern sites contain elements which constantly update content, shuffle through advertisements, or offer chat capabilities with customer support. Most sites of this nature trigger the onLoad \(Page Load\) event, and then have ongoing AJAX requests to pull content from another location. The Endpoint Agent captures all traffic against a particular site while a session is active - this will allow diagnosis of specific problems encountered while loading up a site.

**Q: How will Antivirus applications coexist with the ThousandEyes Endpoint Agent?**

A: Endpoint Agent working should not interfere with antivirus and content protection applications, however due to differences in enterprise deployment and options for Antivirus support, we may encounter issues during the deployment process. If you have any problems, refer to the article [Getting Support from ThousandEyes](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

**Q: Will there be any performance impact on my browsing experience?**

A: Our testing has shown negligible impact. Monitor the te-agent and te-browserhelper processes to monitor resource utilization related to the Endpoint Agent on your local machine. Windows users will also see a te-notifier process running while using supported versions of Microsoft Internet Explorer.

**Q: What kind of network tests get run?**

A: Similar to the measurements taken from an Enterprise Agent, we collect end-to-end metrics for the endpoint’s connection to the destination.  With the Endpoint Agent, we use a modified version of ping \(in ICMP mode\) and/or TCP connect to test ability to connect to a destination, and target both the gateway and the destination server. We also measure the network path to the gateway, proxy and destination server.

**Q: How is the path trace different from tests running from an enterprise agent?**

A: Pathtrace is run from Endpoint agent in ICMP, using 1 probe, instead of 3 to the destination. Enterprise agents allow path trace to be run in either TCP or ICMP mode. Running a TCP traceroute is on our feature roadmap.

**Q: It looks like information I get from the various platforms is different - why?**

A: The level of information that we can extract/monitor from Internet Explorer is more limited than that we can get from Chrome.  The only information regarding resources that can be obtained from Internet Explorer are wait and receive timings, unlike Chrome, which feeds more relevant and detailed information. We also have varying levels of data returned in path trace attempts between Windows and OS X - though we’ve endeavored to provide as much of the same level of information as possible.

**Q: It looks like information I get from various environments is different - why?**

A: Depending on how they are configured and deployed, the presence of firewalls and/or proxies can influence how much data we can gather for Path Visualizations. In such cases details on what upstream nodes were traversed is impossible to gather because the proxy/firewall may be terminating connections and thus not allowing network probes.

**Q: Which views will be available?**

A: For the Endpoint Agent, we have Web, Network, User sessions and Network Topology view available.

**Q: In which conditions will you not be able to measure network/web layer metrics?**

A: Networks are complex and variable things. Some scenarios when limited data or no data is gathered are:

* Browsers connecting to sites running in compatibility mode
* Networks where ICMP is blocked
* Security software that blocks certain types of network packets on the client or in the network
* ThousandEyes Endpoint Agent cannot reach the ThousandEyes service because of authentication issues or restrictive configurations associated with a proxy

**Q: How long will the Endpoint Agent retain data if it is unable to contact the ThousandEyes Collector?**

A: The Endpoint Agent will retain Browser Session and Network Access data locally for up to 4 days in the event it cannot reach the ThousandEyes Collector. Data generated by [Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) will be cached locally for up to 1 hour.

**Q: Why does the Path Visualization on the Endpoint Agent stop at my proxy?**

A: A proxy is a Layer 7 device, it terminates all lower layers, including Layers 3 & 4 where we do our Path Visualization. Because of this we show the target server as the final node in Path Visualization, but we only perform Path Visualization to the Proxy. We can not gather any data between the proxy and the target server.

**Q: Do endpoint agents automatically stop a manually started capture after a certain time period?**

A: We are currently ending the session after 30 seconds of inactivity. This is in the absence of click and keypress events on the page.

