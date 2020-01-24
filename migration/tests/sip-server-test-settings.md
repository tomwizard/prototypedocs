# SIP Server test settings

SIP Server tests facilitate network measurements, BGP data collection and, most importantly, SIP service availability and performance testing against SIP-based VoIP infrastructure. [Enterprise and Cloud Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvICAS_Comparison-of-Agent-Types) performing a SIP Server test will verify the SIP service availability by issuing a SIP OPTIONS request \(also known as the SIP "ping" request\) against it and validate the response. Optionally, the following SIP aspects can be configured:

* **SIP Proxy**: A SIP proxy server can be configured to test SIP loose routing to a destination SIP server
* **SIP Registration**: A user/extension information can be configured to test the SIP registration by issuing the SIP REGISTER request. SIP registration may be required for SIP OPTIONS request to be answered successfully.
* **Authentication**: Authentication credentials can be supplied if authentication is required by the SIP server

In addition to testing conventional SIP services, support for [testing Skype for Business Online]() service is also available.

## NOTICE - SIP Server test is not a Voice Call test

**SIP Server** test is not the test type that facilitates performing full voice calls between agents - that is what **Voice Call** test type is for. To read the documentation about Voice Call tests, head to the [Voice Call test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB63CAG_Voice-Call-test-settings) article.

## Basic configuration

A new SIP Server test can be created by visiting the [Settings &gt; Tests](https://app.thousandeyes.com/settings/tests/) section of the web portal, expanding the **Add New Test** dialog and selecting **Voice** layer and **SIP Server** test type. The following test creation dialog should appear:

IMAGE MISSING

Available basic configuration settings:

* **Test Name:** The test's name. When no name is not configured, the value of the **SIP Server** field is used.
* **SIP Server:** The SIP server to be tested, specified as a domain name or an IP address.
* **SIP Proxy:** \(Optional\) Check the **Enable** box if a SIP proxy will be used to send SIP communication to the target, and configure the SIP proxy's domain name or IP address in the field below. The proxy port will be the same as the value in the **Port** field for the target server. Loose routing is used in the SIP messages.
* **Protocol:** Either the TCP, TLS or UDP protocol may be selected. TLS is using TCP as a transport protocol. Choosing UDP will result in ICMP-based path discovery.
* **Port:** The TCP/UDP port number on which the SIP server is reachable. Defaults to 5060 for TCP and UDP, 5061 for TLS.
* **Interval:** How frequently the test will run.
* **Agents:** ThousandEyes Cloud Agents and/or Enterprise Agents that shall run the test.

**IMPORTANT:** In order to successfully perform the test, Cloud and Enterprise Agents must perform this test one after another. Therefore, the number of Cloud and Enterprise Agents which can be assigned to the test is limited by the **Interval** setting in the Basic Configuration tab and the **Timeout** setting in the Advanced Settings tab, in order to ensure all Agents can complete the test within a given test round. To assign more Agents to a test, increase the **Interval** setting or reduce the **SIP Server Timeout** setting as needed.

* **Alerts:** When the **Enable** box is checked, the Alert Rules selected in the drop-down list will be active for the test. You can select Alert Rules with the drop-down list, and create, modify and delete Alert Rules with the **Edit Alert Rules** link. Additionally, Alert Suppression windows can be selected through the second drop-down list.

## Advanced settings

The following screen capture is showing sample SIP Server test's advanced settings:

IMAGE MISSING

#### SIP Server Timing

* **Timeout:** Test timeout
* **Target Time for View:** Sets the scale of the color legend \(green to yellow to red\) for metrics on the world map.

#### Network

* **Data Collection:** Checking this box enables network measurements and data collection which is presented in the Network Overview, Path Visualization and the BGP Route Visualization views.
* **Perform MTU Measurements:** Checking this box enables the test to perform path MTU discovery.
* **Collect BGP data:** Uncheck this box if the BGP Route Visualization view is not needed.
* **BGP Monitors:** Select the BGP monitors used to produce the BGP Route Visualization view.

#### SIP Server

* **Perform SIP Register:** Checking this box makes the agent attempt SIP registration with the target server using the REGISTER request.
* **User:** Username for SIP registration. The username should be unique within a ThousandEyes Account Group.
* **Auth User:** \(Optional\) If the SIP **User** field is not identical to the authentication username, check the **Custom Auth User** box and specify a custom authentication username in the field below.
* **Password:** Password for authentication with the SIP server.
* **Desired Status Code:** The SIP status code returned by the target for which the test is considered successful. By default, 200- and 300-level status codes are considered success. Uncheck the box and enter a status code in the field below to set a different status code expectation.
* **Verify Headers:** Headers returned by the SIP server can be matched against a configured [regular expression](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn6KAC_POSIX-Extended-Regular-Expression-Syntax-%28quick-reference%29) for additional validation.

## Testing Skype for Business Online

We have added support for testing certain deployments of [Skype for Business](https://www.skype.com/en/business/) \(SfB\) solution. Microsoft provides two main deployment options for Skype for Business:

* A cloud-based service called Skype for Business Online \(supported\)
* An on-premises solution called Skype for Business Server \(currently not supported by ThousandEyes\)

Microsoft customers can configure many aspects of their Skype for Business Online account. One of the important configuration aspects is how their users will authenticate with the cloud-based service. Two main authentication mechanisms are supported by Skype for Business Online:

* Interactive authentication at [https://login.microsoftonline.com](https://login.microsoftonline.com/) \(supported\)
* Federated authentication, where authentication responsibility is delegated to a third party using [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) protocol. An example of such setup would be authentication against an ADFS instance \(currently not supported by ThousandEyes\)

**To summarize:** currently, the Online flavor of Skype for Business with interactive authentication is supported.

### Creating a Skype for Business Online test

The following figure shows a stripped-down SIP Server test creation dialog containing only settings essential for creating a test for Skype for Business Online service:

IMAGE MISSING

Description of shown input fields:

1. **SIP Server:** Enter "sipdir.online.lync.com" or "sipdir3a.online.lync.com" value
2. **Server Type:** Select **Skype for Business Online** option
3. **Protocol:** Select **TLS** option
4. **Port:** Enter **443** value
5. **Username:** Username for authentication, as used on [https://login.microsoftonline.com](https://login.microsoftonline.com/)
6. **Password:** Password for authentication, as used on [https://login.microsoftonline.com](https://login.microsoftonline.com/)

Naturally, to conclude your new Skype For Business Online test creation task, agents will have to be selected - agent selector is not shown in Figure 3 above, but it is visible higher up in Figure 1. All other aspects of the test can be configured as well \(alerting, timeouts and so on\).

**IMPORTANT:** Similarly to the [Voice Call test type](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB63CAG_Voice-Call-test-settings), each Cloud and/or Enterprise Agent assigned to a Skype For Business Online test needs to execute the test on its own without other agents interfering with the process. Therefore, the number of Cloud and/or Enterprise Agents that can be assigned to the test is limited by the **Interval** setting in the Basic Configuration tab and **Timeout** setting in the Advanced Settings tab in order to ensure enough time in reach round for each agent to complete the test. To assign more agents to a test, either increase the **Interval** setting or reduce the **Timeout** value.

The actual formula used to calculate the maximum number of agents for a Skype for Business Online test:

```text
maxAgents = floor[ test-interval-in-seconds / (test-timeout-in-seconds + 1) ]
```

## Frequently asked questions

#### When SIP proxy setting is defined, against which target will the agent perform network measurements? SIP server or SIP proxy?

In this case, network measurements will be performed against the **SIP proxy**.

