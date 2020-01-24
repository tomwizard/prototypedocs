# Working with Agent settings

ThousandEyes Agents provide a variety of settings to customize their behavior to your needs. This article describes menu choices under the Cloud & Enterprise Agents and Endpoint Agent areas.

## Cloud & Enterprise Agents

Cloud and Enterprise Agents can be configured When navigating to the [**Cloud & Enterprise Agents &gt; Agents Settings**](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) menu, you'll see some or all of the following menus, depending on your account's permissions and those of your organization. Agent configuration in the UI is organized as follows.:

1. Agents tab containing Clusters, Notifications, Kerberos Settings tabs
2. Cloud Agents listing tab
3. Agent Labels list and label creation tab
4. Proxy Settings list and proxy configuration tab

## Enterprise Agents

Enterprise Agents are lightweight Linux-based software agents that run tests configured in the ThousandEyes platform, and upload the results to ThousandEyes for aggregation and analysis.  Refer to this [Knowledge Base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnbKAC) for a fuller description of Enterprise Agents.  If you have a role with the _View agents in account group_ permission, such as the default Account Admin or Organization Admin roles, you can view the Enterprise Agents listing.

### Agents tab

If the Account Group has installed at least one Enterprise Agent, then navigating to the  [**Cloud & Enterprise Agents &gt;** ](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents)[ **Agent Settings &gt; Enterprise Agents**](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) menu will display a listing of the Enterprise Agents, under the **Agents** tab:

IMAGE MISSING

1. **Agents/Clusters/Notifications/Kerberos tab:** Click the tab to display listings of either individual Enterprise Agents, Enterprise Agent Clusters.  Select or configure Notification Rules and Kerberos Settings under these tabs.
2. **Search box:** Enter a text string to search for your Agent\(s\).  The string can be either text or an IP address.  The Agent Name, Hostname and public and private IP address fields \(visible when an Agent's row is expanded\) will be searched.  Matches are displayed in the listing.
3. **Total Agents:** The number of Enterprise Agents assigned to this organization.
4. **Account Group filter:** Display either the Enterprise Agents assigned to the current Account Group or those Enterprise Agents not in the current account group. The sum of the two categories should be the number displayed in \#3.  The user must have _View agents in account group_ permission to view Enterprise Agents in the relevant account groups. Click the column header to sort in one of two directions.
5. **Agent Name:** Displays the name given to the Enterprise Agent, located in the Agent Name field. Click the column header to sort in one of two directions.
6. **Hostname:** Displays the hostname given to the Enterprise Agent. The hostname is either a name or a domain name, taken from the 'hostname' command run on the Agent. Click the column header to sort in one of two directions.

    To the left of the hostname are icons indicating the following:  
   IMAGE AND BULLET MISSING  
   IMAGE AND BULLET MISSING  
   IMAGE AND BULLET MISSING  
   IMAGE AND BULLET MISSING

7. **Utilization:** The highest percentage of the currently active Agent Utilization queues \(visible when an Agent's row is expanded\). Utilization queues  measure the amount of test time slots used for various types of tests.  As utilization values near 100%, tests of the type measured by the queue are more likely to fail to run before the next round of tests commences, producing a "No data" result for the Agent running the test. Click the column header to sort in one of two directions.
8. **Status/Last Contact:** The time since the Enterprise Agent last contacted the ThousandEyes collector. The Last Contact of the Agent--Collector connection is rendered with a green dot if the Agent status is "Online". If the Agent has not contacted the ThousandEyes collector for more than .5 hour, the status is set to "Offline" and rendered with a red dot.  If the Agent has been disabled, the status is set to "Disabled" and rendered in grey.  Click the column header to sort in one of two directions.
9. **Options** menu**:** Reveals options to perform below specified actions on the agent: 
   * **Delete:** Clicking this option permanently deletes the Agent from the Account Group.
   * **Disable:** Click this to disable the Agent. Disabled Agents will continue to contact the ThousandEyes collector to determine whether they have been reenabled. Disabled Agents do not collect test results, but do remain configured, allowing for easy re-enabling in the future. Disabled Agents do not count towards an organization's limit of concurrent Enterprise Agents, but may count towards the monthly quota, depending on when and how long the Enterprise Agent was deployed.
10. **Add New Enterprise Agent** button**:** Reveals side pane with Enterprise Agent install options arranged in tabs based on Package Type.

#### Agent Settings

Click on the row of any Enterprise Agent to expand the row for access to the Agent Settings.  The Agent Settings will display three tabs: Basic Configuration, Advanced Settings and Agent Statistics. Additionally, panels on the right provide detailed Agent information and some administrative options. Note that the Basic Configuration will not be visible if the Agent is assigned to an Enterprise Agent Cluster, and other parts of the interface will change or to reflect the Agent's membership in the Cluster.  Information no longer available under the Agent will be available under the Agent's Cluster.

**Basic Configuration**

IMAGE MISSING

1. **Agent Name:** _****_The name of the Agent. This can be modified in the ThousandEyes Agent settings UI by a user having a role with the _Edit agents_ permissions.
2. **Country:** Obtained from a geolocation service based on the public IP address of the Agent. Can be overridden using the pull-down selector.
3. **Region:** Obtained from a geolocation service based on the public IP address of the Agent. Can be overridden using the pull-down selector.
4. **Account Groups:** __Displayed for users having a Role with the _Edit Agents_ permissions and whose organizations contain more than one Account Group. Shows the Account Groups to which the Enterprise Agent is assigned and allows Agents to be shared across Account Groups.  To share with another Account Group, expand the pull-down selector and check the box next to the Account Group. __
5.  **Tests:** Displays a list of tests to which the Agent has been assigned.  Users having a Role with the Edit Tests permission can add or remove tests assigned to this Agent.
6. **Agent notifications:** Click this checkbox to enable Agent Notification Rules to the Agent, which will notify users of Agent downtime or other Agent conditions.  The selector below the checkbox is used to assign or edit Notification Rules.
7. **Warnings:** Displays details of agent conditions requiring user attention.
8. **Labels:** A list of the user-defined and built-in Agent Labels to which the Agent belongs.  Click the down-arrow icon to list the names of the Agent Labels or to add the Agent to an Agent Label. The Labels box will not be visible if the Agent is assigned to a Cluster.  To configure an Agent Labels, navigate to **Cloud & Enterprise Agents &gt; Agent Settings &gt; Agent Labels tab.** 
9. **Cluster/Member of Cluster:** Click the **Add agent to cluster** link to add this Enterprise Agent to an Enterprise Agent Cluster.  If the Agent is already assigned to a Cluster then the Cluster's name will be displayed.  Click the **X** next to the Cluster name to remove the Agent from the Cluster.  For more information about adding and removing Agents from a Cluster, please see [Working with Enterprise Agent Clusters](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmngKAC).
10. **General Info:** Displays the following information:
    * Primary Account Group: The name of the Account Group under which the Agent was created \(**Account Group Token for Installation** from the listed group was used to install the Agent\).
    * Created: The date the Agent was installed.   
    * Private IP Address: The IP address assigned to the Agent system's interface, and to which the Agent is bound.
    * Public IP Address: The IP address that the ThousandEyes collector sees during communication with the Agent.
    * Operating System: The Agent's operating system type and version.
    * Agent System Time: Time reported by Agent's clock.
    * Agent Version: The version of the ThousandEyes Agent software \(te-agent package\)
    * BrowserBot Version: The version of the BrowserBot software for Page Load and Transaction tests \(te-browserbot package\)
    * Adobe Flash: Indicates whether the operating system and BrowserBot software support Adobe Flash content.
    * Installation Type: Linux, Virtual Appliance or Docker container
11. **System Info:** Click this link to display several categories of information about the system, including the contents of the Agent's config file \(te-agent.cfg\).
12. **Reset Appliance Password:** Present only for ThousandEyes Virtual Appliances. Click this link to reset the web admin user interface's password back to the default \("welcome"\).  The Agent must have connectivity to the ThousandEyes collector to reset the password in this way. Console access also can be used to reset the password via a text menu.
13. **Cancel:** Click this button to cancel changes to the Agent Settings.
14. **Save Changes:** Click this button to save changes to the Agent configuration.

**Advanced Settings**

IMAGE MISSING

1. IPv6 **Policy:** Choose a name resolution policy for non browser based tests. Below are the available options:
   * IPv4 Only
   * Prefer IPv6
   * Force IPv6
2. **Target for Tests IP Address:** Used by Network/Agent-to-Agent and Voice/RTP tests to specify the IP address that the testing Agents will use to target this Agent. By default, this is the IP address of the Agent's network interface. Normally, if the testing Agents' packets are traversing the public Internet, the **Target for Tests** field should be set to the IP address shown in the **Public IP Address** field on the Basic Configuration tab.  If the testing Agents' packets are traversing a private network, the **Target for Tests** field should be set to the IP address shown in the **Private IP Address** field of this Agent Settings page.
3. **Behind a NAT:** Check this box to enable NAT traversal. Checking this box will allow Agents running Network/Agent-to-Agent tests to initiate connections to this Enterprise Agent if it is behind a NAT'ing firewall or similar device without the need for port forwarding rules on the device. See [NAT Traversal for Agent to Agent tests](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnWKAS) for more information on NAT traversal.
4. **Verify SSL certificates for browser tests:** Check this box to verify the chain of SSL certificates when running Page Load or Transaction tests.  Leave the box unchecked to ignore certificate-related errors, such as self-signed certificates, expired certificates, certificates whose CN fields do not match the URL used to access the resource, etc.  Note that this is an Agent-wide setting, so will apply to all Page Load or Transaction tests assigned to this Agent.
5. **Keep browser cache between tests:** Check this box to retain cacheable objects retrieved in Web layer tests.  Leave the box uncheck to download all objects with each round of Web layer tests.  Note that this is an Agent-wide setting, so will apply to all Web layer tests.  Also note that cookies are not cached, regardless of whether the browser cache is retained between tests.
6. **Proxy Option:** Select an appropriate proxy option for Scheduled tests. Below are available choices:
   * **Direct:** Do not use proxy.
   * Enterprise Agent's proxy configuration: Use proxy configured in agent's config file\(te-agent.cfg\).
   * Specific proxy configuration: Choose from [in-app proxy configurations](). 
7. **Enable Kerberos:** Enables Kerberos authentication for agent. Credentials are configured in [Kerberos Settings]() tab. 

**Agent Statistics**

IMAGE MISSING

1. **Agent Uptime:** A graph of the Agent's connection to the ThousandEyes collector over the past 7 days.
2. **Agent Utilization:** This section charts the Agent Utilization per Test type for the last 24 hours. Only those Test types which the Agent is running are displayed. [Utilization](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnjgCAC_Enterprise-Agent-Utilization) for a ThousandEyes Enterprise Agent means the amount of time slots in the test queue that are filled by running tests. A high utilization indicates that the Agent is barely managing to complete all tests assigned to it, each round.

#### Adding an Enterprise Agent

If you have a role with the _Edit agents_ permission, such as the default Account Admin or Organization Admin roles, you can add new Enterprise Agents. To add a new Agent, Navigate to Agents tab of [**Cloud & Enterprise Agents &gt; Agents Settings**](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) ****and click the **+ Add New Agent** button.  A side modal containing agent install methods with hyperlinks to respective Install Guide will open up classified in tabs based on Package Type. 

IMAGE MISSING

#### Account Group Token

Click on the **Show Account Token for Installation** link, and copy the Account Token to your clipboard or similar location so that you can paste it when needed during the installation.  Be sure to handle the Account Token with appropriate security, as it provides a means of affecting your usage of ThousandEyes resources.  Note that the Account Token is specific to your current Account Group.  All Enterprise Agents installed with this Account Token will belong to this Account Group.

### **Clusters tab**

 If the Account Group has configured at least one Enterprise Agent Cluster, then navigating to the  **Settings &gt; Agents &gt; Enterprise Agents** menu will display a listing of the Enterprise Agent Clusters, under the **Agents** tab:

IMAGE MISSING

For more information about Agent clusters, refer to the ThousandEyes Knowledge Base article [Working with Enterprise Agent Clusters](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmngKAC). 

## Notification Rules

For an organization's Enterprise Agents, notifications can be generated on three types of events:

* _Last Contact_ with the ThousandEyes collector less than or greater than a number of minutes  The default time limit is 30 minutes.  Agents normally contact the ThousandEyes collector every minute.
* _Clock Offset_ of the Enterprise Agent from true value less than or greater than a number of seconds  The data collected by ThousandEyes requires accurate timestamps. If an Enterprise Agent's clock varies from the ThousandEyes collector's time by a significant fraction of the frequency of any test the Agent is running, then the test data can be affected.  Most commonly, this condition arises when the Agent cannot reach the Agent's Network Time Protocol \(NTP\) servers via the network.  Notification rules can be configured to ensure that the Agent's clock drift generates a notification.
* _Agent Version is Outdated_  Triggered when the **Agent Version** from the **Cloud & Enterprise Agents &gt; Agents Settings &gt; Enterprise Agents t**ab indicates the Agent's version is less than the current version available.  Normally, Enterprise Agents automatically update their Agent software, but if conditions prevent update, notification can be generated.

Navigate to the **Cloud & Enterprise Agents &gt; Agents Settings &gt; Enterprise Agents &gt; Notification** tab and click the **Add New Notification Rule** button to add a new Rule or click on a row to expand the row and view the settings of an existing Rule.  As with any Alert or Notification Rule, some period of experimentation may be required to tune the criteria so that the Rule is neither too noisy nor failing to notify users of valuable events.

IMAGE MISSING

1. **Search:** Enter a text string to search for Notification Rules based on the name of the Rule.
2. **Name:** The name of the Notification Rule.  Click the column title to sort in one of two directions.
3. **Conditions:** Lists the conditions of the Notification Rule.
4. **Agents:** Indicates the number of Enterprise Agents to which this Rule has been assigned.
5. **Default:** Check this box to assign the Rule to all Agents created subsequent to the Rule becoming a default.  There is no limit to the number of Default Rules.
6. **Options** button: Reveals options to **Delete** and **Duplicate** the Notification Rule.
7. **Add New Notification Rule** button**:** Opens up a side pane with blank notification rule form. 

### Creating a New Notification Rule

To add a new notification rule, Navigate to Notifications tab of [**Cloud & Enterprise Agents &gt; Agents Settings**](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) ****and click the **+ Add New Notification Rule** button to reveal the below side pane:

IMAGE MISSING

Configure appropriate values for below settings: 

1. **Notification Name:** The name of the Notification Rule.  Be aware that there is no uniqueness constraint on Notification Names.
2. **Enterprise Agents:** Click the selector and check the boxes of the Enterprise Agents to which this Notification Rule will be assigned.
3. **All/Any operator:** Set the selector to _Any_ \(logical OR\) or _All_ \(logical AND\) which applies to the conditions listed below.
4. **Conditions:** As explained above, Last Contact, Clock Offset or _Agent Version is Outdated_, along with the appropriate operator and operand, if applicable.
5. **Add/remove conditions:** Click **+** to add a new condition or **-** to remove an existing condition. A minimum of one condition is required.
6. **Notification tab:** Configure notifications for this rule. 

For information on the Notifications tab, see the [Notifications section](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) of the ThousandEyes Knowledge Base article [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work). Once done click **Add** button to create notification rule.

## Kerberos Settings

The Kerberos Settings tab is where configurations for this method of authentication are listed.  Typically an Enterprise Agent authenticating to a Microsoft Windows Server will use this method.  Navigate to the **Cloud & Enterprise Agents &gt; Agents Settings &gt; Enterprise Agents &gt; Kerberos** tab to list or create a new configuration.  To setup new authentication schemes click the **Add Kerberos Configuration** button. Fill in Configuration Name, Realm, Username, Password, Kerberos Key Distribution Center \(KDC\) Host, KDC Port, Whitelisted IP address range or subnet.  Then add an associated Enterprise Agent.

IMAGE MISSING

## Cloud Agents

If your organization has access to ThousandEyes Cloud Agents, then the Cloud Agents menu will be present.  Navigate to **Cloud & Enterprise Agents &gt; Agents Settings &gt; Cloud Agents** to see this listing.  Our Cloud Agents are installed around the world in major cities and on six continents giving our customers access to performance data from local transit providers and last-mile ISPs to simulate end user performance.  Choose from this list to view the Name, Primary Provider, Country and number of tests using these agents.  To see a map of our existing Cloud Agents visit this [link](https://www.thousandeyes.com/product/cloud-agents) on the ThousandEyes website.

IMAGE MISSING

1. **Search:** Enter a text string to search for Cloud Agents based on the Agent name or location.
2. **Agent Name:** Indicates the geographic location \(city and state or city and country\) as well as indicating an IPv6 Agent. 
3. **Group:** Displays the group to which the Cloud Agent belongs.
4. **Provider:** Provider information shown where a single provider is used for at least 30% of outbound routes.
5. **Country:** The country in which the Cloud Agent is located.
6. **Tests Selector:** Add the Agent to tests within your Account Group by opening the Tests selector and checking the boxes for the required tests.
7. **Labels:** Displays the list of Agent Groups to which the Cloud Agent belongs.
8. **IPv6 Policy:** Shows the name resolution policy for non browser based tests. 

## Agent Labels

Labels can be setup to organize resources listed in the ThousandEyes platform.  To organize Enterprise Agents under a particular group Navigate to the **Cloud & Enterprise Agents &gt; Agents Settings &gt; Agent Labels** tab.  Organizing more than one agent under a particular color and named label can expedite test and alert configuration by selecting the label then leafing through the list.

IMAGE MISSING

## Proxy Settings

List or configure proxy settings under the **Cloud & Enterprise Agents &gt; Agents Settings &gt; Proxy Settings** tab.  Add new settings by clicking the **Add New Proxy Configuration** button.  For a details description of proxy server settings refer to the article on [Enterprise Agent Proxy Configuration](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG_Configuring-an-Enterprise-Agent-to-use-a-proxy-server).

IMAGE MISSING

## Endpoint Agents

Refer to [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBxCAK_Configuring-Endpoint-Agent-setup) for instructions on deploying the right type of Endpoint Agent for your organization.  If you do not have access to the Endpoint Agent and would like more information, please contact your account representative. You can contact ThousandEyes Sales from [Billing tab of the Account Settings view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnGKAS_Working-with-Account-settings#billing-tab).

If your Account Group has access to ThousandEyes Endpoint Agents, then the Endpoint Agents menu will be present. To configure Endpoint Agents navigate to [**Endpoint Agents &gt; Agents Settings**](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents) ****menu to reveal below mentioned configuration tabs:

1. Endpoint Agent listing and configuration tab
2. Endpoint Proxy Settings list and configuration tab
3. Endpoint Agent Labels list and label creation tab IMAGE MISSING
4. **Endpoint Agents/Proxy Settings/Agent Labels:** Access agent list, add New Endpoint Agents.  Configure [Proxy Settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000HlqJSAS_Endpoint-Agent-proxy-configuration-for-Scheduled-tests) and create customer labels for your Endpoint Agents.
5. **Filters:** Available filters for agent list include **Location**, **Status**, **Version**, **Platform**, **Agent Type**, **Label and Browser Extension Status**.
6. **Search:** Search for Endpoint Agents based on the hostname, username, or OS version.
7. **Name:** The hostname of the system as returned by the Endpoint Agent.
8. **Agent Version:** Version of the Endpoint Agent.
9. **Browser Extension:** Shows status of installed Browser.
10. **Current Location:** Displays the Endpoint Agent's current location.
11. **Last Contact:** The time since the report by the Endpoint Agent to the ThousandEyes collector.
12. **Warnings:** When an Agent experiences a condition requiring the user's attention, a red warning triangle will appear next to the Agent Name.  Expand the row to view the details of the warning
13. **OS Version:** The operating system and version as returned by the Endpoint Agent.
14. **Options** button: Reveals options to Delete agent or Transfer Ownership to another Account Group on click.
15. **Proxy:** Select a specific proxy configuration for scheduled HTTP Server test, these configurations can be added from the Proxy Settings tab. By default System Proxy of an Endpoint Agent is used. 
16. **Agent Settings:** Displays a list of properties about the system hosting the Agent.
17. **Disable:** Click this button to block the results from an Endpoint Agent session from appearing in the list of sessions.  If an Endpoint Agent is disabled, this button will become an **Enable** button.

