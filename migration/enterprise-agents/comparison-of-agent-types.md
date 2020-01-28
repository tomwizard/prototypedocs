# Comparison of Agent Types

### Comparison of Agent Types

ThousandEyes provides three types of Agents. Cloud Agents are maintained by ThousandEyes in locations worldwide. Enterprise Agents and Endpoint Agents are installed by customers on their own systems and placed in their own networks or other networks which require monitoring or troubleshooting. Although providing some similar capabilities, these three types serve different purposes and exist in different environments.

## Agent Type Descriptions

### Enterprise Agent

An Enterprise Agent can run every ThousandEyes test type \(except Network Layer BGP tests, which are not run by Agents\).  Additionally, Enterprise Agents can be either a source or target of an Agent to Agent test, which provides bi-directional network data \(End to End Metrics and Path Visualization View\) between itself and another ThousandEyes Agent \(Cloud or Enterprise\).

Enterprise Agents are intended to be installed in server-type environments, and be online continually in order to run scheduled tests.  Enterprise Agents require systems administrators to provide resources such as time synchronization and firewall/packet filter rules for test and administrative traffic. 

An Enterprise Agent can be installed in a virtualized environment \(virtual machine or container\) as well as installed directly on native Linux systems, and on certain types of hardware, such as Intel NUC or Cisco ISR and ASR routers.  Installing the Linux package on a supported Linux distribution with administrative \(root\) access will provide extensive flexibility.  Customers can combine Enterprise Agent functionality with other capabilities of the host, such as advanced routing and proxying, PKI/certificate functionality or other authentication, authorization and access control \(AAA\) technologies.

### Endpoint Agent

An Endpoint Agent has the most specialized purpose: to collect Web Layer “waterfall” data \(i.e. HTTP archive format\) and Network Layer data \(including layer 2 information such as WiFi data\) from workstation environments \(although Windows Server installations are supported\). Data collection is often performed on-demand, activated when a user experiences performance or other problems with web-based applications.

Endpoint Agents are quickly and easily deployed as browser plug-ins for Chrome or Internet Explorer, and can monitor any application which Chrome and Internet Explorer can access. Endpoint Agents have few to zero ongoing requirements after installation, but do not provide flexibility to augment their core function of testing web and network resources.

### Cloud Agent

Cloud Agents are available immediately to customers to configure tests, with no administrative responsibilities.  Cloud Agents provide most of the configuration options that Enterprise Agents provide, but because Cloud Agents are used by multiple customers, some features are not available. For example, Cloud Agents cannot be configured to run Web Layer tests through a proxy server, as this would require all tests run by the Agent to use the proxy.  For use cases such as testing a cloud-based proxy server, customers must use Enterprise Agent or Endpoint Agent.

## Related Information

The following ThousandEyes Knowledge Base articles provide additional information on this topic:

* [What is an Enterprise Agent?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC)
* [How to set up the Virtual Appliance​](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC)
* [Enterprise Agent deployment using Linux Package method​](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnRKAS)
* [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS)
* [Installing a Physical Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnOKAS)
* [Enterprise Agent Installation for Cisco IOS XE Containers](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnRKAS)

