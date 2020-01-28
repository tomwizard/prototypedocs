# Getting Started with Endpoint Agent

 This article is your complete guide to getting started with Endpoint Agents. We'll explain: what Endpoint Agents are, where and how to deploy them, configuration options, how to run tests, end-user tools and experience, how to navigate your way through the UI and the layers of test views, how to create reports and dashboards, how to troubleshoot deployments and operations, managing licenses, user permissions and much more.

Alternatively, if you’re new to Endpoint Agents and want to get started quickly check out our [Quick Start Guide](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpW) or watch our [Getting Started with Endpoint Agent](https://www.thousandeyes.com/resources/getting-started-endpoint-agent-tutorial) video from our video tutorial series.

If you're already on your way to becoming an Endpoint Agent pro-user this guide will still help you find what you need to know but feel free to delve straight into the [How does the Endpoint Agent work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpUKAS_How-does-the-Endpoint-Agent-work) article to learn about advanced topics such as system and user services, registration, config and package updates and check-in process.

There are two types of Endpoint Agents: **Endpoint Enterprise** and **Endpoint Pulse.**  The agent and their differences are explained in more detail in the [Endpoint Enterprise vs Endpoint Pulse]() section below. Throughout this guide, all topics discussed apply to both products unless explicitly mentioned.

Where further explanation is required you will find in-text links and lists of relevant articles with a brief summary of their content. If you don't see what you are looking for, try to search our entire Knowledgebase using the search bar above or reach out to our [Customer Success Team](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

## [A brief introduction to Endpoint Agents]()

Endpoint Agents allow customers to leverage regular end-user desktops and laptops as test devices for measuring internal and external application performance. As an Endpoint Agents can be deployed on and off-premise to readily available machines in any location or network, performance measurements can be run from almost every possible user environment. Endpoint Agents can run conventional **Scheduled Tests** and you can capture users’ web experiences of applications using **Browser Sessions**. Whilst Browser Sessions are running the Endpoint Agents record **Network Access** layer performance data. The Network Access layer records the performance of the Endpoints physical wired or wireless connections, gateways, VPNs, proxies and DNS servers.

All the [collected data and metrics]() are displayed in one intuitive [ThousandEyes Views]() page. The Views page separates Scheduled Tests, Browser Sessions and Network Access data by layers and the interactive timeline presents performance data that can be used to rapidly search through historical data. An example of the Views page, the interactive timeline, layers, metrics and filters can be seen in [Figure 2]() below. With your Endpoint Agent data you can create proactive alerts, email regular feature-rich reports and create highly customizable dashboards. All Endpoint Agent data is available via our [API](https://developer.thousandeyes.com/v6/endpoint/). 

You have full control of when and under what conditions Scheduled Tests run or Browser Sessions are recorded. If a Scheduled Test is deployed to a laptop it can be switched on or off as it transits through different locations, wireless and wired networks, VPNs and proxies. Browser Session recordings will only occur when the Endpoint Agent is on a specified network and also limited by configured target domains.

Deploying Endpoints gives you the ability to identify and diagnose end-user issues in near real-time. Unlike [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmsKAC_Working-with-Agent-settings), Endpoint Agents run natively on Windows and Mac OSX operating systems and can be deployed on mass using standard automated deployment tools. [Figure 1]() below shows a typical example of deployment locations for Endpoint, [Enterprise](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmsKAC_Working-with-Agent-settings) and [Cloud](https://www.thousandeyes.com/product/cloud-agents) Agents.

IMAGE MISSING

Once an Endpoint Agent has been deployed it will stream performance data to the ThousandEyes platform. Scheduled Tests, Browser Sessions and Network Access results are displayed in the intuitive interactive [Endpoint Agent &gt; Views](https://app.thousandeyes.com/view/endpoint-agent) page for analysis.

IMAGE MISSING

## [Endpoint Enterprise vs. Endpoint Pulse]()

We have two types of Endpoint Agents: **Endpoint Enterprise** is for almost all deployments scenarios and **Endpoint Pulse** could be used for deployments where a higher scheduled test capacity is required or for headless machines. Endpoint Pulse is strictly for HTTP and Agent-to-Server Scheduled Tests only and it does not have the Endpoint Enterprise components to collect Network Access layer or Browser Sessions data. Endpoint Pulse can run twice the number of Scheduled Tests in comparison to Endpoint Enterprise.

| **Table 1. Endpoint Enterprise and Pulse feature comparison** |  |  |
| :--- | :--- | :--- |
|  | Endpoint Enterprise | Endpoint Pulse |
| Scheduled Tests | yes | yes |
| Browser Sessions | yes | no |
| Browser plugin | yes | no |
| Network Access | yes | no |

## [Deploying Endpoint Agents]()

Typically organizations' have multiple teams that manage their IT estate so to assist in the deployment and planning stages and to ensure the right teams are involved do check the [pre-deployment requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBpCAK_Endpoint-Agent-Installation-FAQ) in the FAQ article. It’s important the teams who manage functions such as software deployments, end-user access control, VPN-access, proxies and anti-virus systems are involved as early as possible, so the Endpoint deployment runs smoothly. Use the following links for detailed instructions on how to install the Endpoint Agents. 

### [Detailed Windows OS installation instructions]()

* Installing Endpoint Agent for [Windows OS](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBu) article
* Installing Endpoint Agent for Windows OS [via Group Policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpXKAS_Installing-Endpoint-Agent-for-Windows-via-Group-Policy) article

### [Detailed Mac OSX installation instructions]()

* Installing Endpoint Agent on [Mac OSX](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBv) article

## [Endpoint HTTP proxy support]()

We currently support the use of HTTP proxies for both types of Endpoint Agents. If you need HTTPS proxy support please contact our [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).  The network performance from an Endpoint Agent to a proxy will be automatically measured during **Scheduled Tests** or **Browser Sessions** recordings. The network performance tests consist of a hop-by-hop path trace and end-end latency, loss and jitter tests. Network tests are unable to reach the final target when a proxy is in use \([Figure 3]() below shows a proxy in use and the Network layer tests unable to reach the final target\), therefore, all network tests are performed to the proxy instead. If you need network layer performance measurements beyond a proxy then please reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

### [Browser Sessions proxy]()

 The proxy used by Browser Sessions is not configurable but automatically detected from the host system. See Figures [3]() and [4]() below for examples of how we present proxy data.

IMAGE MISSING

IMAGE MISSING

#### 

### [Scheduled Tests proxy]()

You can configure and store multiple proxy configurations and apply them to all tests or set a unique per test proxy. The proxy configuration supports static assignments, PAC files and Basic and NTLM proxy authentication methods. To apply a saved proxy configuration for all scheduled tests use the settings on the [Endpoint Agent &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=proxies) page or for a per test proxy scenario apply a proxy configuration on the [Endpoint Agent &gt; Test Settings](https://app.thousandeyes.com/endpoint/test-settings/?tab=tests) page. This was mentioned previously but as a reminder here it is again: we currently only support HTTP proxies and if you need to use Endpoint with an HTTPS proxy get in touch with our [Customer Success Team](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance.

For detailed instructions on proxy configurations and options see the [Proxy Configuration](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlqJSAS_Endpoint-Agent-proxy-configuration-for-Scheduled-tests) article. For more details on how to navigate through the Views page to see your proxy measurements head to the [Test, Browser Sessions and Network Access Views and metrics]() section.

## [Endpoint Agent updates]()

We usually ship Endpoint Agent updates every 2 weeks for both the Windows and Mac OSX operating systems. The Endpoint applications have auto-update process that runs at regular intervals to check, download and install package updates. The Chrome browser extension automatically updates whenever a new Endpoint version is published in the Chrome Store. For full details on how the Endpoint Agent update process works see the [How does the Endpoint Agent work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpUKAS_How-does-the-Endpoint-Agent-work) article.

## [Endpoint Agent permissions]()

We have several Endpoint related permissions for user and user group management. For full details on how to create custom roles with Endpoint permissions see the [Role-based Access Control](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) article.

## [Endpoint Agent licensing]()

With the Endpoint Agent licencing model there is no distinction between the two agent types. A single Endpoint Agent licence can be used to deploy an Endpoint Enterprise or an Endpoint Pulse Agent. An Endpoint Agent license allows you to use all Endpoint Agent features such as Scheduled Tests and Browser Sessions.  All new organizations and trial accounts receive 5 licenses by default. Endpoint Agents consume licences upon check-in to the ThousandEyes platform. If you reach your licence limit all subsequent Endpoint Agents deployed will show as disabled upon check-in on the [Endpoint Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page. The following section explains how to transfer and reclaim licences but if you need your license plan modified contact your ThousandEyes Account Manager or the [Customer Success Team](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance.

### [Viewing, transferring and re-claiming licenses]()

Endpoint Agent licenses are assigned to the organization and can be transferred between your organizations' account-groups. The total number of licenses available in your Plan, Currently Active licenses and licenses used in each Account Group is shown in the Plan Usage, Endpoint Agent Licenses section on the [Account Settings &gt; Usage and Billing](https://app.thousandeyes.com/account-settings/usage-billing/?section=usage) page. See [Figure 5]() below for an example of the Endpoint Agent licensing data shown on the [Account Settings &gt; Usage and Billing](https://app.thousandeyes.com/account-settings/usage-billing/?section=usage) page.

To free up a license you can disable an Endpoint Agent or delete it. The **Currently Active** licenses shown on page [Account Settings &gt; Usage and Billing](https://app.thousandeyes.com/account-settings/usage-billing/?section=usage) is a tally of all licenses used within a billing cycle. If you disable or delete an Endpoint Agent within a billing cycle the reduction of the **Currently Active** licenses will not appear until the following billing cycle. Note: removing the Endpoint Agent software package from an end-user machine will not free up a license until it is deleted from the [Endpoint Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page. 

IMAGE MISSING

## [A brief introduction to Scheduled Tests, Browser Sessions and the Network Access layer]()

Endpoint Enterprise and Pulse both run web-layer HTTP-server and network-layer Agent-to-Server **Scheduled Tests** types, both test types are IPv4 and IPv6 compatible. Scheduled tests can run at set intervals from a minimum of 1 minute to a maximum of 1 hour. All scheduled tests perform network-layer end-end and path trace tests. If a proxy is being used the network layer tests will target the proxy and not the end target \(see [Scheduled Tests proxy]() section on for more details\). Scheduled Tests can be configured to run several types of checks against your target e.g. verify SSL, page content or HTTP response codes.

Endpoint Enterprise in conjunction with its web-browser plugin can be configured to monitor end-users web Browser Sessions automatically or end-users can manually start recording their **Browser Sessions** using their browser extension. When recording Browser Sessions the agent will also perform network-layer end-end and path trace tests and collect Network Access data.

### [Endpoint Agent labels and test distribution and configuration]()

Endpoint Enterprise can be assigned a maximum of 3 Scheduled Tests and Endpoint Pulse can be assigned a maximum of 6 Scheduled Tests, so your total test capacity increases with the number of Endpoints deployed. You have two options to distribute tests to your Endpoint Agents and both options begin with creating an Agent Label. An Agent Label is simply a named group of Endpoint Agents that all share a common property such as a gateway device, wireless SSID, proxy address, subnet, agent name or IP address. The Agent Label is assigned to a test and as Endpoints match or un-match the label’s criteria the test will be added or removed from Endpoint Agents. The more dynamic the agent property used for the Agent Label criteria the greater the test distribution activity. Some Endpoint properties are static, so it is possible to create Agent Labels with no dynamic test distribution activity. If Endpoints do not check-in for 1 hour, they are removed from the agent label pool. For full details on scheduled test configuration options and configuring labels see the [Creating Scheduled Tests on Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) article.

### [Browser Sessions and settings]()

Browser Sessions recordings can be started manually using the browser extension or configured to automatically collect data by specifying groups of Monitored Networks and Target Domains. There is no limit to the number of Browser Sessions you can record. For instructions on how to use the browser extension to manually record a Browser Session see the [Endpoint Agent end-user experience](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpNKAS_End-user-Experience) article and for instructions on configuring automatic Browser Sessions monitoring see the [Configuring automatic data collection](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBx) article.

### [Network Access]()

The Network Access data can be used for troubleshooting errors seen in Browser Sessions recordings or it can be used to proactively track how your Endpoint Agents' local network services are performing. Endpoint Pulse does not collect any Network Access layer. The Network Access layer has two parts, Network Topology and Wireless. Network Topology visualises the devices in use by Endpoint Enterprise Agents for Browser Session recordings and Wireless displays a table of information about wireless data such as SSID, signal strength, channel and much more. Network Access data is continuously collected whilst an Endpoint Enterprise Agent is online and on a configured monitored network \([Browser Session Settings &gt; Monitored Network](https://app.thousandeyes.com/endpoint/browser-session-settings/?section=networks)\). The devices in the Network Access topology include Endpoint Agents' gateway devices, DNS servers and proxy or VPN servers. The following section explains how to navigate the Network Access layer. 

## [Working with Endpoint Agent Views]()

The [Endpoint Agent &gt; Views](https://app.thousandeyes.com/view/endpoint-agent) page has 3 layers: Scheduled Tests, Browser Sessions and Network Access. Each layer contains a menu of sub-layers, a timeline, options to display data in tables and data filters. Depending on the Views layer you have selected you also get geographical maps, network topology diagrams, path visualizations and sliders that scroll into view when table data is selected. There is a lot of information being presented in a very organized and easy to follow format. From the current moment in time, the timeline holds up to 31 days of data. If you wish to keep your data for longer than 31 days then you can run a regular [Reports]() or you have the option to create [Snapshots](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data). Snapshots let you share test data with anyone, regardless of whether they subscribe to the ThousandEyes platform or not.

The following sub-sections contain screenshots and KnowledgeBase article links, the articles explain how to navigate and leverage the features of the **Views** layers, for example they show you how to select Scheduled Tests, sift through the timeline, select metrics and what your metrics mean, apply filters \(e.g. find data on an Endpoint Agent\), find proxy performance data, check page load page waterfall data, use the path visualizations, check wireless strength and display session or Visited Page details.

#### [Views, Scheduled Tests]()

* Views - [Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpWcCAK_Endpoint-Agent-Views-Scheduled-Tests): HTTP Server and Network type tests, Path Visualizations, Maps and Tables

IMAGE MISSING[  
****](https://app.thousandeyes.com/view/endpoint-agent)

#### [Views, Browser Sessions]()

 If a Visited Page and Session is selected a detailed slide-out window appears.

* Views - [Browser Sessions &gt; Visited Pages](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpYKAS_Endpoint-Agent-Views-Web): Web pages recorded manually with the browser extension or automatically via a Monitored Network and Domain groupset.      
* Views - [Browser Sessions &gt; Sessions](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpVKAS_Endpoint-Agent-Views-Session-Details-1472238551243): Web sessions recorded manually with the browser extension or automatically via a Monitored Network and Domain groupset.

IMAGE MISSING  
****

#### [Views, Network Access]()

* Views - [Network Access &gt; Network Topology](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmpa): Visualises the devices in use by Endpoint Enterprise Agents and their performance
* Views - [Network Access &gt; Wireless](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlmWSAS_Endpoint-Agent-Views-Wireless): Endpoint Enterprise Agents wireless network connection performance data

IMAGE MISSING

## [Dashboards and Reports of Endpoint Data]()

Dashboards and Reports are simple to use and fully customizable to display your Endpoint Agent data in a style suited for your target audience. Reports can be run on-demand or scheduled to automatically generate reports at regular intervals. Check out these helpful articles on the topics below:

* [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports): generate a report, either on-demand or on a scheduled basis.
* [Working with Dashboards](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmdKAC_Working-with-the-Dashboard): basic information about Dashboards.
* [Customizing your Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmcKAC_Customizing-your-Dashboard): advanced Dashboard configuration.

## [Alerting]()

For your Scheduled Tests, you can customize your Alert Rules. Simply put, alerting is configured out of the box to alert you when you need information about tests which are failing. If you need to get more granular or change some of the notification rules, check out the [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work-1476477151762) article for more information on fine-tuning and managing alerts.

## [API]()

So now you're a ThousandEyes expert you Rockstar you. There's a whole category of Endpoint API articles found by following this [link](https://developer.thousandeyes.com/v6/).

## [Endpoint data collection and metrics]()

The [Data collected by Endpoint Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpbKAC_Data-collected-by-Endpoint-Agent) article describes what data is generated and collected when running your Endpoint Agent, Scheduled Tests, Browser Sessions and by the Network Access layer.

## [Reference articles]()

* [Getting support from ThousandEyes](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes): How to contact the Customer Success Team
* [Troubleshooting Endpoint Agent issues](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpMKAS_Troubleshooting-Endpoint-Agent-issues): How to generate an Endpoint agent diagnostics log file
* [Deleting Endpoint Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009S1JCAU_Deleting-Endpoint-Agent): How to delete the Endpoint agent
* [Sharing test data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data): How to create Snapshots

