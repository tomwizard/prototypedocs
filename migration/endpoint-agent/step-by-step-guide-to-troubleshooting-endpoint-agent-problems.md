# Step by step guide to troubleshooting Endpoint Agent problems

A prerequisite to Endpoint Agent troubleshooting is physical or remote access to the end-user machine and for some steps an un-restricted user account on the end-user machine. 

To resolve any Endpoint Agent problem follow the path in the Endpoint Agent troubleshooting flow diagram below \(see [figure 1.0]()\). This document contains many links to make switching between the flow diagram, sections, diagrams and troubleshooting steps as easy as possible. The section directly below the flow diagram contains the [page links to relevant Endpoint Agent troubleshooting steps](). If the sequence in the flow diagram is followed in the correct order, most Endpoint Agent issues will be resolved. It is important not to skip questions, sections or the steps provided in this document. The green boxes contain a series of questions to capture an Endpoint Agent issue and the teal boxes informs you which troubleshooting steps you need to follow.

If you cannot find the information you are looking for in this Article check the

[Reference Articles]() section at the bottom of this page, it contains links to the Endpoint Agent frequently asked questions articles or reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

IMAGE MISSING

## **Step 1 of 6. Troubleshooting Endpoint Agent deployments and check-in problems**

Endpoint Agents periodically check in every 10 minutes for configuration updates with ThousandEyes controller [https://c1.eb.thousandeyes.com](). If an Endpoint Agent switches networks, the Agent checks-in again. If the Agent is not able to connect to the controller, the Agent will not appear on the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page \(see [figure 1.1]()\).

IMAGE MISSING

  
**Troubleshooting Endpoint Agent deployments and check-in steps:**

**1.1.** To check if an Agent is checking in, head to the [Endpoint Agent &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page and find the Agent by name or use the filters to track down the Agent \(see [figure 1.2]()\). If you have recently installed a new Agent, wait 10 minutes for the Agent to appear.

**1.2.** If the Agent is not present on the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page despite a successful software package installation, then re-installing the package is not the solution. Every time the Endpoint Agent package is removed and installed again a new ID is generated a new Endpoint Agent instance can be created, an Endpoint licence can be consumed and multiple Endpoint Agents with the same name may appear in the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page which can create unnecessary administrative overhead.

**1.3.** If the deployment is working in one network but not on another, then it is most likely a problem with the end-user's deployment environment. Using the correct [Endpoint Agent deployment guide article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpZKAS_Getting-Started-with-Endpoint-Agent#_Toc17387893) for your Operating System check no steps were missed during the installation process. The deployment guides contain information about how to set-up firewalls, VPNs, proxies and end-user machine permissions so the Endpoint Agent software operates correctly.

**1.4.** Check when the Agent last checked-in on the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page \(see [figure 2]()\). If you know for certain the end-user system is online but the Endpoint Agent has not checked-in for 10 minutes or more, check the Endpoint Agent services are running:

* If you are using a Windows machines, check via the [Services Control Manager](https://docs.microsoft.com/en-us/dotnet/framework/windows-services/how-to-start-services) the “ThousandEyes Endpoint Agent” service is running \(see [figure 1.2]()\) IMAGE MISSING  
* If you are using a Mac OSX machine, check via a terminal application the “ThousandEyes Endpoint Agent” service is running \(see [figure 1.3]()\) IMAGE MISSING
* Using the command-line application \(e.g. iTerm for Mac OSX and CMD for Windows\) on the end-user's machine check you get a response when you run the PING command to the ThousandEyes controller “c1.eb.thousandeyes.com” \(see [figure 1.4]()\)  IMAGE MISSING
* Check the controller URL [https://c1.eb.thousandeyes.com]() loads in the end-user's browser \(see [figure 1.5]()\)  IMAGE MISSING  
*  Try restarting the end-user's machine

**1.5.** Check the Endpoint Agent is not disabled \(see [figure 1.1]()\). If the Endpoint Agent is disabled, try to enable it on the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page. If you cannot enable an Agent, check the Endpoint Agent licence usage on the [Usage and Billing](http://app.thousandeyes.com/account-settings/usage-billing/?section=usage) page and ensure the licences in your plan are not all used \(See [figure 1.6]()\). If all licences are used then free up a licence by disabling another Endpoint Agent back on the [Agent Settings](http://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page \(see [figure 2]()\).

IMAGE MISSING

  
**1.6.** If the Agent is now checking-in then revert back to where you left off on the [Endpoint Agent troubleshooting flow diagram]() to continue troubleshooting. If the Agent is still not checking-in reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

## **Step 2 of 6. Troubleshooting Endpoint Agent updates problems**

It is important Endpoint Agents deployments are updated when new releases are made available as they contain product enhancements and may also include bugs fixes. We publish [Release Notes in the Customer Success Centre](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000UIQ3SAO_Release-Update-2019-11-12) along with every release or you can subscribe to the regular [Release Notes via email](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmUKAS_Notification-of-upgrades-and-maintenance). The Release Notes contain a summary of all new Endpoint Agent release changes. New Endpoint Agent packages are released by the ThousandEyes Engineering team every other Tuesday. Once the new Endpoint Agent package is released it is made available to organisations randomly over the following 5 day period immediately after a release. It is possible you'll receive the Release Notes before the update is made available to your organisation. The larger the Endpoint Agent deployment the longer it takes to fully deploy as deployments within an organisation are staggered. For large organisation please expect updates to be completed over a 2-3 day period after your first Agent has updated. Endpoint Agents continually check every 3-4 hours for version updates and provided the download from thousandeyes.com domain is not being blocked no user intervention should be required for Agents to update themselves. 

**Troubleshooting Endpoint Agent update steps:**

**1.1.** Check if the Endpoint Agent is running the latest package release by heading over to the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page. If a warning sign appears next to any Endpoint Agent, the Agent is not up-to-date \(see [figure 1.1]()\). In the Agent table, Agent row on the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page there is a column displaying what version the Agent is actively running \(see [figure 1.1]()\).

**1.2.** For package updates to work the Agent has to be able to check-in regularly so complete the steps in the [Troubleshooting Endpoint Agent deployments and check-in problems]() section.

**1.3.** If the Endpoint Agent has been manually installed and the environment does not allow for automatic updates, reach out to the organisation's senior ThousandEyes system administrators to get the Agent updated.

**1.4.** If after following the previous steps the Agent has updated then revert back to where you left off on the [Endpoint Agent troubleshooting flow diagram]() to continue troubleshooting but if the Endpoint Agent did not update reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

## **Step 3 of 6. Troubleshooting Scheduled Tests problems**

Scheduled Tests are configured to run at set intervals and run in the background on the Agents end-user machine. Schedules Tests are assigned to Agents according to the Agent Label matching criteria. During Scheduled Test runs Network Access layer probes also run. At this stage of troubleshooting ThousandEyes users and administrators may to decide to refresh their knowledge on Scheduled Tests configuration and operations using the [Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) public KnowledgeBase article.

**Troubleshooting Scheduled Tests steps**  
The following steps cover Scheduled Test and Agent Settings checks, end-user machine checks, environment devices such as proxy and firewall device checks and a brief note on Network Access data.

**3.1.** Ensure an Agent Label has been created and contains active Agents \(see [figure 3.1]()\).  
IMAGE MISSING

  
**3.2.** Check the following:

* The correct Agent Label has been applied to the test
* The correct proxy setting has been set \(proxy settings applied here take precedence over system and agent proxy settings\)
* There are Agents actively matching the Agent Label
* The test is enabled \(see [figure 3.2]()\) IMAGE MISSING

  
**3.3.** If the test appears to be configured correctly, check you have not oversubscribed tests to the Endpoint Agents. An Endpoint Enterprise Agent runs a maximum of 3 Scheduled Tests at a time and an Endpoint Pulse Agent runs a maximum of 6 tests at a time. Check you have not  oversubscribed an Agent to tests; ensure the same Agent has not been accidentally matched by several Agent Labels matching conditions or the same label or multiple labels have not been applied to more tests than the Endpoint Agent is capable of running.

**3.4.** When a test is first configured it may take up to 10 minutes for test data to start appearing.

**3.5.** On the end-user machine check the Scheduled Test target is reachable from the end-user machine:

* From the end-user's machine command-line application \(iTerm on Mac OSX or CMD on Windows Operating Systems\) check you get a response when you run the PING command to the Scheduled Test target \(see [figure 3.3]()\) IMAGE MISSING
* If the target is web-based check it will load from the end-user Web Browser \(see [figure 3.4]()\) IMAGE MISSING

  
**3.6.** If the end-user is behind a proxy and the Agent type is **Endpoint Enterprise,** Scheduled Tests by default detect and use the end-user's proxy settings. Endpoint Agent Scheduled Tests will not currently support HTTPS proxies until Q1 of 2020. Whilst the ThousandEyes engineering team work on a HTTPS solution it is useful to know most HTTPS proxies support clients connecting via HTTP \(see section "Proxying HTTPS Requests" in our blog post about "[Measuring Performance with HTTP Proxies](https://blog.thousandeyes.com/measuring-performance-with-http-proxies/)" for details on how HTTP and HTTPS proxies work\). You may want to check the full details on **Endpoint Enterprise** proxy configuration in our [Endpoint Agent proxy configuration for Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlqJSAS_Endpoint-Agent-proxy-configuration-for-Scheduled-tests) Knowledge Base article.

If you deployed **Endpoint Pulse** on a Windows machine, then Scheduled Tests will use the system level proxy setting. It is common the system level proxy is not set and be aware that changing the system proxy setting could affect other application traffic. Changing the system proxy setting on a Windows machine requires administrator privileges. If setting a system proxy is a problem the best approach is to deploy **Endpoint Enterprise** on the end-user machine. To check the Windows end-user machines system proxy settings using the example screenshots in [figure 3.5]() below and ensure you have administrator access prior to starting.

IMAGE MISSING

IMAGE MISSING

IMAGE MISSING

  
**3.7**. If the Endpoint Agent end-user is switching networks e.g. between 2 different wireless networks in 2 different geographical locations, then the services in each of those networks may prevent the scheduled tests from running. Double check the following access control devices or services in each location are not blocking access to the scheduled test target:

* Firewalls
* Proxies
* VPNs

**3.8.** If Network Access layer data is not appearing during periods when Scheduled Tests are being run, ensure you have configured a Monitored Network \(see [figure 3.6]()\).

IMAGE MISSING  
 

**3.9.** If after following the previous steps the Scheduled Tests is still not working, then reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance.

## **Step 4 of 6. Troubleshooting manual Browser Sessions recordings problems**

To start a manual Browser Session recording: the end-user selects a browser tab to record from, clicks on the ThousandEyes Browser Sessions recorder extension icon in the end-user's browser \(see [figure 10]()\) and then in the active tab the recording starts when the user loads a new web page or refreshes the current web page. The recording stops when the end-user activates another tab, after 30 seconds of inactivity or after 5 minutes of continuous recording. When a recording starts or stops: in Google Chrome, the browser extension icon status is updated, in the IE browser, a system notification is displayed. Browser Sessions data appears on the [Endpoint Agents &gt; Views](https://app.thousandeyes.com/view/endpoint-agent/) page and is grouped together in 5 minute intervals. After a new Endpoint Agent installation Browser Sessions recordings may take up to 10 minutes to appear on the Views page but in most cases data appears within 60 seconds from when a recording is started.

**Troubleshooting manual Browser Sessions recordings steps:**  
For troubleshooting Google Chrome Browser Session recordings start at step [4.1.1]() or if you are using IE start at section [4.2.1]() Once you have worked through the browser specific troubleshooting steps, continue to step [4.3.1]().

**4.1.1.**\(**Chrome\)** If you have access to the end-user machine, check the ThousandEyes Browser Sessions recorder extension icon appears in the end user's browser \(see [figure 4.1]()\).

IMAGE MISSING  
 

**4.1.2.** \(**Chrome\)** If the ThousandEyes Browser Sessions recorder extension icon does not appear in the Chrome's toolbar, check the extension is not hidden \(see [figure 4.2]()\).

IMAGE MISSING

  
**4.1.3.** \(**Chrome\)** To check if the browser extension is installed, type the special URL “chrome://extensions” in Chrome’s search bar and look for the ThousandEyes Endpoint Agent extension package \(see [figure 4.3]()\). If the extension is not installed, you can perform a manual installation by opening this link to the [Chrome web store](https://chrome.google.com/webstore/detail/thousandeyes-endpoint-age/ddnennmeinlkhkmajmmfaojcnpddnpgb) on the end-user machine or follow the full installation in our article [Installing the Endpoint Agent for Mac OS X](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBvCAK_Installing-the-Endpoint-Agent-for-Mac-OS-X).

IMAGE MISSING  
 

**4.1.4.** \(**Chrome\)** If the browser extension icon is covered with a small covering red warning sign \(see [figure 4.4]()\), click the icon and the Repair button to resolve the issue. If the repair is unsuccessful restart the browser. Also ensure that you covered everything in sections [1]() and [2]() of the troubleshooting process then try running the repair again. If the alert status persists please reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance. If the extension alert status has been fixed, continue to work through the non-browser specific troubleshooting steps as step [4.3.1]().

IMAGE MISSING

  
**4.2.1. \(IE\)** If the ThousandEyes Browser Sessions recorder extension icon does not appear in the IE's Command bar \(see [figure 4.5]()\), check the Command bar is visible \(see [figure 4.6]()\).

IMAGE MISSING

IMAGE MISSING

  
**4.2.2.** **\(IE\)** Check the IE Add-on is enabled \(see [figure 4.7]()\). If the Add-on does not appear in IE Add-ons after following all the previous steps and the main installation package completed successfully, then reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance.

IMAGE MISSING  
 

**4.3.1.** Check the Endpoint Agent's browser extension status by navigating to the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page \(see [figure 4.8]()\). On the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page Endpoints deployed on a Mac OSX platform show an Apple Logo next to the them and Windows Endpoint deployments show a Windows logo next to them. All Endpoint Agent Windows platforms with Internet Explorer installed show the Internet Explorer logo and Endpoint platforms with Google Chrome installed should show the Chrome icon. A green dot over any browser extension icon in the [Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page means the extension is installed and working. The browser logo and icon status can take up to 10 minutes to appear and switch from amber to green status.

IMAGE MISSING

  
**4.3.2.** If the browser extension appears to be working, the Agent is checking in but no waterfall data appears on the [Endpoint Agents &gt; Views](https://app.thousandeyes.com/view/endpoint-agent/) page try to restart the machine or browser.

**4.3.3.** If after following the previous steps the Browser Sessions recordings are now working then revert back to where you left off on the [Endpoint Agent troubleshooting flow diagram]() for the next troubleshooting steps. If the Browser Sessions recordings are still not working reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

## **Step 5 of 6. Troubleshooting Automatic Browser Sessions recordings problems**

Automatic Browser Session recordings begin when a user browses to a configured target domain from a specified network. The automatic Browser Sessions configuration can be referred to as a “target domain and network set”.

**Troubleshooting Automatic Browser Sessions recordings steps:**

**5.1.** If you have not already done so, follow the steps in the previous section \(see [section 4]()\) as it covers most problems that could occur when trying to perform automatic Browser Sessions recordings.

**5.2.** Check the Monitored Network correctly matches the Agents network. The local Internet provider or Network Administrator should be able to provide you with the public network network address range your Endpoint Agents will use. If you are unsure what Network your Agents will be operating from, set a catch all Monitored Network e.g. 0.0.0.0/0 \(see [figure 3.6]() and [5.1]()\). Check you have applied the correct domains in the Monitored Domain set. Hostnames are valid Monitored Domains.

IMAGE MISSING

​​**5.4.** Recordings can take up to 15 minutes to appear as Agent check-ins run every 10 mins and within Agent application itself processes configuration updates run at 5 minute intervals.

**5.4**. If after following the previous steps the automatic Browser Sessions recordings are working then revert back to where you left off on the [Endpoint Agent troubleshooting flow diagram]() for the next troubleshooting step. If the automatic Browser Sessions recordings are still not working reach out to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

​​​​​

## **Step 6 of 6. Troubleshooting Overview and Views problems**

This section is work in progress and will be added to shortly. If you spot any anomalies in the test data then connect to the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for further assistance.

## **Reference Articles**

* [Endpoint Agent Installation FAQ](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBpCAK_Endpoint-Agent-Installation-FAQ): Contains further useful information about system requirements, supported browsers, VPNs and Proxies and firewall requirements etc.
* [General Endpoint Agent FAQ](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpSKAS_Endpoint-Agent-FAQ): Broad sweeping FAQ on lots of Endpoint Agent topics

