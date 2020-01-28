# Endpoint Agent proxy configuration for scheduled tests

In addition to user-triggered data collection, Endpoint Agents can also execute [scheduled tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents). These tests can be configured to use custom proxy settings.  
For more information about how proxies operate and how proxy settings can be configured, head over to the [proxy configuration guide for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG_Configuring-an-Enterprise-Agent-to-use-a-proxy-server) and consult the Introduction section.

## Adding an Endpoint Agent proxy configuration

 Endpoint Agent's proxy settings can be configured in the Proxy Settings tab of the [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page, where all existing proxy configurations are listed as below:

IMAGE MISSING

 These proxy settings apply only to Endpoint Agent scheduled tests and does not impact agents connection to ThousandEyes services.

Click the **Add New Proxy Config** button here to add a new proxy setting. Endpoint Agents can also be optionally configured to use **Basic** or **NTLM**  **Authentication Type** when connecting to a proxy server. If not using authentication select **None**.  
Below are the two types of proxy an Endpoint Agent can be configured to use:

### **Static** 

 Configuring an Endpoint Agent to use a proxy server statically. For routing traffic to the destination directly skipping proxy, add them to **Bypass List.**

Here is an example of a completed static proxy configuration with Basic Authentication to route packets through the proxy server at 1.1.1.1:2233 as configured in **Host** and **Port** fields.

Traffic to 3.3.3.3 is set to skip proxy as per the **Bypass List**.

IMAGE MISSING

**Host** and **Port** are required fields. If not using an authentication select **None** in **Authentication Type.** **Endpoint Agents** and **Bypass List** are optional fields and can also be configured later from  [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) Proxy Settings.

### **PAC**

 ****Configure the Endpoint Agent to fetch a [Proxy auto-config](https://en.wikipedia.org/wiki/Proxy_auto-config) file from **PAC File URL** and accordingly choose a proxy server.  
Here is a completed configuration of Endpoint Agent PAC proxy configuration with NTLM authentication to fetch a PAC File from http://www.internet.com/proxy.pac

IMAGE MISSING

Endpoint Agent will fetch the proxy PAC File from URL configured in **PAC File URL** field on every request. 

### **Additional management options**

Additional management options are available at the Proxy Settings tab of [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page.

IMAGE MISSING

1. The current configuration will be displayed on selecting a proxy configuration, changes can be made to an existing proxy configuration from here.
2. Clicking the options\(\) button will reveal controls to **Duplicate** or **Delete** configured proxy settings.

## Applying proxy settings to Endpoint Scheduled test

 Proxy settings created by above process can also be applied to existing [scheduled test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) \(HTTP Server only\) from [Endpoint Agents &gt; Test Settings](https://app.thousandeyes.com/endpoint/test-settings/?tab=tests). Test-based proxy configuration receives precedence over an in-app proxy configuration of Endpoint Agent, which in turn is given precedence over the proxy configuration of Endpoint Agent host. By default, a test would use Endpoint Agent's proxy configuration with **System Proxy** setting. The below screenshot explains how:

IMAGE MISSING

## Related articles

 The below articles will provide more details about Endpoint Agent based scheduled tests:

* [Creating scheduled tests on Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) will guide through creating an Endpoint scheduled test. 
* [Endpoint Agent Views - Scheduled Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpWcCAK_Endpoint-Agent-Views-Scheduled-Tests) will help navigate the Scheduled Tests views.
* [Endpoint Agent FAQ](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpSKAS_Endpoint-Agent-FAQ) answers some common questions about Endpoint Agents.

