# Configuring Endpoint Agent setup

The ThousandEyes [Endpoint Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvICAS_Comparison-of-Agent-Types) is an application that is installed on Windows or Mac OS X machines to collect network and application performance data when users access specific websites from within monitored networks. The Endpoint Agent installer contains a built-in ThousandEyes account key, allowing performance data collected by the Endpoint Agent to be routed to the correct Account Group in ThousandEyes. This document outlines the basic setup process for an Endpoint Agent.

## Adding an Endpoint Agent

To add an Endpoint Agent, navigate to [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings ](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) and click on the **Add New Endpoint Agent** button. An account having a role with the _Download Endpoint Agents_ permission \(such as the built-in Account Admin or Organization Admin roles\) is required to download the Endpoint Agent installer. Download the appropriate installer file based on your operating system architecture. **Allow anyone with the link to download** switch would reveal links to each installer file.

IMAGE MISSING  
Refer the following guides for step-by-step installation instructions:

* [Installing the Endpoint Agent \(Windows\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBuCAK_Installing-the-Endpoint-Agent-for-Windows)
* [Installing the Endpoint Agent \(Mac OS X\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBvCAK_Installing-the-Endpoint-Agent-for-Mac-OS-X)

Once the installation completes, the new Endpoint Agent will be listed under [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents).

## Collecting data using Endpoint Agent

After installing the Endpoint Agent on a supported system, configuring the Endpoint Agent setup has two steps:

1. **Configure monitored networks**: Enable automatic data collection when Endpoint Agents reside inside defined networks.
2. **Configure monitored domains**: Collect data automatically when browsing websites within defined domains.

### Adding a monitored network

1. Click on the **Add New Network** button on the **Monitored Networks** tab of the [Endpoint Agents &gt; Browser Session Settings](https://app.thousandeyes.com/endpoint/browser-session-settings/?section=networks) page.
2. Enter a network in CIDR format \(e.g. 192.150.160.0/24\) or an IP address range \(e.g. 192.150.160.100-192.150.160.150\). If you enter an IP address, the longest matching address block will be looked up. Below the field, a network block containing your current public IP address will be shown.

    **Note \#1:** RFC 1918 networks \(10.0.0.0/8, 192.168.0.0/16, 172.16.0.0/12\) cannot be added. Use the network providing the public IP address for the client when it makes connections to the Internet.  
    **Note \#2:** IPv6 addresses cannot be used at this time.

3. Choose the name for your new network entry.
4. Select a **Monitored Domain Set** that should be applied to your new monitored network.
5. To complete the process, click the **Add** button.

Repeat the process above to define multiple monitored networks. Configured networks and their corresponding monitored domain sets will be listed under **Monitored Networks** tab:

IMAGE MISSING

Optionally, to configure data collection regardless of agent's current public IP address, a built-in entry **All other networks** is available in the list as well. To delete a monitored network, click on the corresponding **Trash** icon on the right-hand side of the network list.

### Defining a monitored domain set

1. Click on the **Add New Monitored Domain Set** button on the **Monitored Domains** tab of the [Endpoint Agents &gt; Browser Session Settings](https://app.thousandeyes.com/endpoint/browser-session-settings/?section=networks) page.
2. Name your new monitored domain set.
3. Add one or more domain names into the **Monitored Domains** field. Don't wildcard your entries - enter the domain suffix only \(ie. "thousandeyes.com", rather than "\*.thousandeyes.com"\).
4. If desired, uncheck the **Periodically collect network topology data** to disable local network measurements.
5. Click **Add** button to conclude the creation process. IMAGE MISSING

**Note:** No data collection occurs against non-monitored domains.

## Managing Endpoint Agents

Once you've started collecting data, you can control which machines collect data and send it to ThousandEyes for analysis. Click through [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings ](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) and click the **Endpoint Agents** tab. This will allow you to search for existing agents, using either agent name \(which defaults to _\[user name\] - \[host name\]\)_, or by hostname directly.

### Disabling Endpoint Agent

An Endpoint Agent can be either enabled or disabled. When enabled and when inside a monitored network, the Endpoint Agent collects performance information for monitored domains. When disabled, the Endpoint Agent still checks in with ThousandEyes every 15 minutes for configuration changes and Endpoint Agent updates. No other information is collected while an Endpoint Agent is disabled. A newly enabled agent's state is reflected in the list immediately, but the agent will receive the updated configuration within 15 minutes \(the next time it checks in\).

To disable an Endpoint Agent, find the agent in the list, expand it and click the **Disable** button \(on the lower left of the expanded Endpoint Agent details panel\):

IMAGE MISSING

Once disabled, the agent's list entry will show the word "Disabled" in the **Last Contact** column and the aforementioned **Disable** button will become an **Enable** button. This change takes effect immediately.

### Deleting Endpoint Agent

To delete an Endpoint Agent navigate to [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) page.

IMAGE MISSING

1. Click the options button \(IMAGE MISSING\) on the Endpoint Agent you wish to delete.
2. Click **Delete.** If the **Delete** option is not available, then your ThousandEyes user account may not have permission to delete Endpoint Agents.
3. Once deleted an Endpoint Agent can be recovered upto 7 days.

Deleting an Endpoint Agent will prevent it from checking in and committing data to our backend services. Normally, administrators should delete Endpoint Agents only to block machines that should not be connecting and sending data to your ThousandEyes account.

### Reinstalling Endpoint Agent

If an Endpoint Agent requires reinstallation to address an issue, simply rerun the Endpoint Agent installer, without deleting the existing installation. The most common scenario requiring reinstallation occurs when the Endpoint Agent cannot auto-update itself. Rerunning the installation using the latest installer will update the Endpoint Agent without generating a new agent instance. Such an upgrade will not affect the data continuity.

**IMPORTANT:** However, if you do uninstall an Endpoint Agent and then reinstall it again \(or select the **Repair** option when running the installer again\), the Endpoint Agent will register with the ThousandEyes platform using a new unique Agent ID. Data collected from the new Endpoint Agent instance will not be continuous with the data collected from the older Endpoint Agent instance. Also, the **Endpoint Agents** tab of the [Endpoint](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) [Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) will display two Endpoint Agent entries with the same name.

## Related articles

* [Views &gt; Endpoint Data - Web](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpYKAS)
* [Views &gt; Endpoint Data - Network](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpTKAS)
* [Views &gt; Endpoint Data - Session Details](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpVKAS)
* [Views &gt; Endpoint Data - Network Topology](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpaKAC)

