# Creating and editing Alert Rules

The following article describes the steps in adding or editing an Alert Rule. To understand how alerts work, refer to the ThousandEyes Knowledge Base article [How Alerts work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK).

IMAGE MISSING

To create a new Alert rule, Click on [**Alerts &gt; Alert Rules**](https://app.thousandeyes.com/settings/alerts/?) and the Alert Rules page will open.

Select the desired source from the tabs at the top:

* Cloud and Enterprise Agents
* Endpoint Agents
* BGP Routing
* Devices

then click on **Add New Alert Rule**. The Add New Alert Rule panel will appear, displaying the Settings tab.

IMAGE MISSING

1. **Alert Type Layer:** test layers available to your organization.
2. **Alert Type:** available alert types for the selected test layer.
3. **Rule Name:** the name of the Alert Rule.

## Settings tab

Use the Settings tab to configure the conditions on which an Alert Rule is triggered, and assign the Alert Rule to tests and Agents. Settings will vary with the source tab selected. The above image displays the Cloud and Enterprise Agents tab.

1. **Tests:** a drop-down menu listing the all the tests set up in your Account Group.  Select one or more tests to assign them to this Alert Rule.
2. **Agents**: Select the Agents to which you will assign this Alert Rule.  The options are:
   * All agents: All Agents will be assigned this Alert Rule
   * All agents except: All Agents will be assigned this Alert Rule except for the ones selected
   * Specific agents: Only selected Agents will receive this Alert Rule
3. Specify the number of Agents, **all/any** of the following alerting conditions, and the number of test rounds the conditions must be met before alerting.
4. **Alerting Condition:**alert conditions, particular to the selected test type which must be met in order to trigger the Alert Rule. For a list of alerting conditions, refer [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK#alertconditions).
5. **Compatible Test Types:** lists the test types to which this Alert Rule can be assigned.
6. **Notifications:** tab to display settings for receiving Alert Notifications.  See listing and graphic below.

## Notifications tab

Use the Notifications tab to configure the methods by which users are notified when an Alert Rule is triggered.

IMAGE MISSING

1. **Send emails to:** email addresses that receive the Alert Notification.
2. **Edit emails:** create or edit an email address which can then be added to the **Send emails to** field.
3. **Send an email when alert clears:** if checked, an email is sent when the Alert Rule is no longer triggered.
4. **Add message:** an optional field for text that will be sent in the body of the alert email.
5. **Webhooks:** Webhooks-enabled web services that receive the alert notification.
6. **Edit webhooks:** create or edit [webhooks](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmVKAS_Using-Webhooks-server-sample-code-included) which can then be added to the Webhooks **Send Notifications to** field.
7. **Integrations:** integrations that should receive the Alert Notification. 
8. **Edit Integrations:** create or edit an integration which can then be added to the Integrations **Send Notifications to** field. Currently ThousandEyes offer integrations for  [PagerDuty](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBsCAK_PagerDuty-Integration), [HipChat, Slack](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cn2FCAS_Slack-and-HipChat-Integration) and [ServiceNow](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqJPCA0_ServiceNow-Integration).

