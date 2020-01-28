# ServiceNow Integration

ThousandEyes supports routing alert notifications directly into [ServiceNow](https://www.servicenow.com/) [Incident Management Services](https://docs.servicenow.com/bundle/london-it-service-management/page/product/incident-management/concept/c_IncidentManagement.html) - a solution for streamlining the logging, classification, assignment, escalation, and reporting of incidents. The following guide describes the process of configuring ServiceNow and ThousandEyes [Alert Rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) to send alert notifications directly into the ServiceNow platform. 

## Overview

The ThousandEyes platform can notify users whenever their test results trigger an Alert Rule. Alert Rules allow configuring various methods of alert notification delivery. One of the supported methods is direct notification delivery into a ServiceNow account. Once the notification is delivered, ServiceNow processes it and allocates tasks based upon pre-defined workflows. 

To route alert notifications directly into ServiceNow, the following needs to be properly configured:

* A ServiceNow Integration created
* Alert Rules associated with ServiceNow Integration
* ThousandEyes Tests associated with Alert Rules

 The content below will guide you through the process of configuring both, ServiceNow and ThousandEyes. In the end, an alert triggered in ThousandEyes will cause a new incident to be generated within your ServiceNow account instantly. This process should streamline the handling of ThousandEyes-reported events, aligning it with your existing \(ServiceNow-based\) workflow.

## [ServiceNow releases supported by ThousandEyes]()

ThousandEyes support for a Release Family stops at the same date ServiceNow declares a release EOL, however, despite the ServiceNow release reaching EOL ThousandEyes alert integrations should continue to work. If you have any support questions, just get in touch with the [Customer Success Team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

| Table 1. ThousandEyes supported ServiceNow releases |  |
| :--- | :--- |
| **ServiceNow release** | **Supported by ThousandEyes** |
| Istanbul | supported \(EOL\) |
| Jakarta | supported \(EOL\) |
| Kingston | supported \(EOL\) |
| London | supported |
| Madrid | supported |
| New York | supported |

## ServiceNow Configuration

To be able to receive ThousandEyes alert notifications directly, ServiceNow must first be configured to allow it. Here is a summary of the ServiceNow configuration with links to the relevant ServiceNow product documentation:

1. Check [Incident configuration](https://docs.servicenow.com/bundle/london-it-service-management/page/product/incident-management/concept/incident-configuration.html) [form design](https://docs.servicenow.com/bundle/london-platform-administration/page/administer/form-administration/concept/c_FormDesign.html) includes the correct fields for ThousandEyes alert notifications 
2. Configure the System OAuth application for ThousandEyes alert authentication
3. Disable the global system property [state parameter](https://docs.servicenow.com/bundle/london-platform-administration/page/administer/security/reference/oauth-auth-code-flow-state-parm.html) for OAuth authentication

These instructions assume the ServiceNow [Service Management Portal](https://docs.servicenow.com/bundle/london-service-management-for-the-enterprise/page/product/it-services/task/t_ActivateServiceManagement.html) is activated.  
 

**Pre-requisite \(London, Madrid and New York only\): disable** the global system property **state** parameter

 1. Type sys\_properties.list in the filter navigator field then hit return. In the main window, the System Properties table will appear \(see [figure 1]() below\).  
2. Using the table search feature field select the **name** filter, in the search field type `glide.oauth.state.parameter.required` and hit return \(see [figure 1]() below\).

IMAGE MISSING

3. Click `glide.oauth.state.parameter.required` to open the parameter's configuration, change the **Value** text field to `false`, then click **Update** \(See [figure 2]() below\).

IMAGE MISSING

### 1\) Incident form design configuration

1. Log in to your ServiceNow workspace, under the **Application Navigator** expand the [**Self Service**](https://docs.servicenow.com/bundle/london-servicenow-platform/page/use/employee-self-service/reference/r_EmployeeSelfService.html) application and click the edit **Incident** module icon  
2. Click the **Additional actions** menu icon &gt; **Configure** &gt; **Form Design**  
3. Check and if required, add the following fields to the incident form:

* Description
* Short Description
* Category
* State
* Urgency   

**2\) Configure OAuth authentication**

In this step the [**OAuth Application Registry**](https://docs.servicenow.com/bundle/newyork-platform-administration/page/administer/security/task/t_CreateEndpointforExternalClients.html) for external API endpoints is created:

* Select **System OAuth &gt; Application Registries** from ServiceNow's homepage navigation pane
* Click **Create an OAuth API endpoint for external clients**
* Take a copy of the generated **Client ID**. This value will be used when configuring ThousandEyes' ServiceNow integration in the next section
* Unlock the Redirect URL field and assign the following value: [https://app.thousandeyes.com/servicenow-oauth-callback/](https://app.thousandeyes.com/webhooks-oauth-callback/)
* Access and Refresh tokens will require manual re-configuration once their lifespans have been exceeded. Token lifespan should be configured, in seconds, for a time deemed reasonable by your ServiceNow administrator \(eg: 1 year\). 

**NOTE:** ThousandEyes recommends creating a dedicated ServiceNow user for integration management. This user should be assigned the `web_service_admin` role.

IMAGE MISSING

## Creating a ServiceNow Integration within ThousandEyes

A ServiceNow integration must be created before being assigned to Alert Rules.

### 1\) Navigate to the Alerts &gt; Alert Rule page

Start by selecting [Alerts &gt; Alert Rules](https://app.thousandeyes.com/settings/alerts/) within the menu pane. Then either expand any of the existing Alert Rules or click the **Add New Alert Rule** button:

IMAGE MISSING

Click the **Notification** tab to display the **Integrations** section:

IMAGE MISSING

Click **Configure Integrations** or **Edit Configurations** link depending on which is displayed. This will open a new dialog box.

IMAGE MISSING

Click the **Add New Integration** link.

### 2\) Configure ServiceNow integration settings

The following figure depicts the dialog box for creating a new ServiceNow integration:

IMAGE MISSING

Within the dialog box, these fields can be configured:

* **Type:** Make sure "ServiceNow" is selected
* **Name:** Select a name for your ServiceNow integration
* **ServiceNow URL:** The ServiceNow endpoint to which ThousandEyes will send notifications
  * **ServiceNow URL format:** `https://<instance-name>.service-now.com`
* **Auth URL:** The ServiceNow endpoint to which ThousandEyes will authenticate, via [OAuth](https://en.wikipedia.org/wiki/OAuth), prior to submitting notifications
  * **Auth URL format:** `https://<instance-name>.service-now.com/oauth_auth.do`
* **Client ID:** The identifier which ThousandEyes will use when authenticating to ServiceNow

### 3\) Obtain a ServiceNow Authentication Token

 Once the fields in the previous step are configured, retrieval of an authentication token is required. ThousandEyes will retrieve and store the authentication token to be used when notifying ServiceNow of alerts. This step will need to be repeated whenever the token expires. 

* Click the **Get Token** button. You should be redirected to the ServiceNow login page.
* Log into ServiceNow, using an account that has been assigned a role of `web_service_admin`. Once in, enable permissions for ThousandEyes to access this endpoint.

### 4\) Test your integration

The **Test** button is provided to verify the correctness of your integration setup. Click it to send a test notification using your new integration. A new incident should be generated in your ServiceNow account.

## Assigning ServiceNow Integrations to Alert Rules

Once created, ServiceNow integration can be assigned to any Alert Rule by opening the rule's **Notifications** settings and selecting your new integration from the drop-down list:

* Navigate to the **Integrations** section of the desired Alert Rule's **Notifications** configuration tab
* Select the desired ServiceNow integration from the drop-down
* Click **Save Changes**

IMAGE MISSING

Here are some additional details to be aware of:

* Integrations are available on an Account Group basis. An integration can be used by multiple Alert Rules in an Account Group.
* Notification preferences are configured per Alert Rule. Assign your new ServiceNow integration to all Alert Rules that require it.
* Integrations cannot shared between Account Group so must be created per Account Group.
* Multiple integrations may use the same ServiceNow endpoint and authentication token.

## ServiceNow Alert Management

 Upon receiving a new notification from the ThousandEyes platform, ServiceNow will create a corresponding incident:

IMAGE MISSING

The following fields will be mapped upon creation of a new incident:

* **State:** Set to `New` when an alert is triggered and `Resolved` when the alert is cleared.
* **Urgency:** Set to `Medium`
* **Category:** Set to `Network`
* **Short Description:** "ThousandEyes Alert triggered for Test: &lt;Test Name&gt;"
* **Description:** This field will contain alert details including Alert Rule name, number of agents affected, and a URL leading to a view with further details on the ThousandEyes platform.

## Related Information

The following resources provide additional information:

* [October 11th, 2018 ThousandEyes blog post](https://blog.thousandeyes.com/native-servicenow-integration/) provides a general introduction to ThousandEyes ServiceNow integration support.
* [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) article provides detailed information regarding Alert Rules and Alert Notifications.
* [Creating and editing Alert Rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmhKAC_Creating-and-editing-Alert-Rules) is a short guide about how to manage Alert Rules within the ThousandEyes platform.
* [ServiceNow FAQ](https://hi.service-now.com/kb_view.do?sysparm_article=KB0610454#6) on EOL aka unsupported release family upgrades

