# Quick Guide on Endpoint Agent

For a quick start guide to getting started with Endpoint Agent, see the sections below on prerequisites, deployment, recording and viewing data, and creating reports. Click the embedded links to learn more about specific topics.

## 1. Prerequisites

* If you have any firewalls or proxies in the network\(s\) you want to use the Endpoint Agent in, or questions on supported Endpoint Agent platforms and browsers, please refer to our prerequisites documentation: [Endpoint Agent Installation FAQ](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBpCAK_Endpoint-Agent-Installation-FAQ).

## 2. Configuring and deploying the Endpoint Agent

* Log in to ThousandEyes and navigate to [Settings &gt; Agents &gt; Endpoint Agents](https://app.thousandeyes.com/settings/agents/endpoint/) where you will be presented with a brief setup wizard. IMAGE MISSING
* Configure the networks you want to monitor \(‘“anywhere” if you don’t care where your users are, or specific IP/subnets representing the public IPs of the egress locations you want to limit monitoring to\), then click ‘Next’.
* Choose the domains you want to automatically monitor and
  * Check "Collect periodic network statistics" box to gather Endpoint Agent network access metrics for this profile, then click ‘Next’.
* Download the Endpoint Agent installer for the operating system\(s\) on which you want to install it. For detailed installation instructions on how to deploy to a large number of machines via software distribution tools, see our [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBuCAK_Installing-the-Endpoint-Agent-for-Windows) & [Mac](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBvCAK_Installing-the-Endpoint-Agent-for-Mac-OS-X) installation documentation.
* Double click the installer file and follow the on-screen instructions to install both the Endpoint Agent application and browser extension.
* **For Chrome**
  * The ThousandEyes extension will appear in the Toolbar. IMAGE MISSING
* **For IE**
  * You may need to explicitly “Allow” the use of this extension upon the next run of the browser.
  * To view the Endpoint Agent extension, go to View &gt; Toolbars &gt; Command bar. IMAGE MISSING

## 3. Viewing Data

* Data collected by Endpoint Agents installed within your organization will be available under [Views &gt; Endpoint Data](https://app.thousandeyes.com/view/endpoint-agent/). If you are just starting you will get a message stating that "There are no active monitoring profiles configured. Go to [Endpoint Agent Settings](https://app.thousandeyes.com/settings/agents/endpoint/) to create one."
* [Web View](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpYKAS): Metrics such as number of web pages visited, page success rate, response time and the component-level waterfall view for each webpage are shown.
* [Network View](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpTKAS): Metrics such as packet loss, latency, jitter and network paths to target web domains are available. This is the default View.
* [Session Details](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpVKAS): Web and Network Layer data providing details on specific user browsing sessions, gathered from Endpoint Agents.
* [Network Topology](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpaKAC): Access the layer topologies of Endpoint Agents as connected to their Access Points, Gateways, Proxies or VPNs.

## 4. Working with Endpoint Agent

* Open your Chrome/IE browser and browse web domains configured within your Monitoring Profiles. Endpoint Agent will gather web and network layer data for Monitoring Profiles from within monitored networks under [Views &gt; Endpoint Agents](https://app.thousandeyes.com/view/endpoint-agent/).
* For manual recording of a website, click on the ThousandEyes Endpoint Agent browser extension to start recording. Click on it again to stop recording or close browser tab. IMAGE MISSING

## 5. Creating reports

* Go to [Reports &gt; Reports](https://app.thousandeyes.com/reports/) and create a new report by clicking on the ‘Reports’ dropdown and choosing ‘New Blank Report.’
* Provide a report name and hit ‘Enter.’
* Drag the report widgets that you’d like to use into the report, then find the relevant metric you’d like to report on by clicking on the ‘Metric’ dropdown and typing “**endpoint**” to only show Endpoint Agent-related metrics \(if you don’t see any metrics or if there is a limited number of metrics available, the report type you’ve chosen doesn’t support Endpoint Agent metrics\). IMAGE MISSING

Now, that you have a quick understanding, lets get started with [Getting Started with Endpoint Agent.](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpZKAS_Getting-Started-with-Endpoint-Agent)

