# ServiceNow

ThousandEyes supports routing alert notifications directly into [ServiceNow](https://www.servicenow.com/) [Incident Management Services](https://docs.servicenow.com/bundle/london-it-service-management/page/product/incident-management/concept/c_IncidentManagement.html) - a solution for streamlining the logging, classification, assignment, escalation, and reporting of incidents. The following guide describes the process of configuring ServiceNow and ThousandEyes [Alert Rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) to send alert notifications directly into the ServiceNow platform. 

#### Table of Contents

[Overview](https://success.thousandeyes.com/Articles?category=Alerts#Overview)  
[ServiceNow releases supported by ThousandEyes](https://success.thousandeyes.com/Articles?category=Alerts#supported_servicenow_releases)  
[ServiceNow Configuration](https://success.thousandeyes.com/Articles?category=Alerts#ServiceNowConfiguration)   
[Creating a ServiceNow Integration within ThousandEyes](https://success.thousandeyes.com/Articles?category=Alerts#CreatingaServiceNowIntegrationwithinThousandeyes)  
[Assigning ServiceNow Integrations to Alert Rules within ThousandEyes](https://success.thousandeyes.com/Articles?category=Alerts#AssigningIntegrationstoAlertRules)  
[ServiceNow Alert Management](https://success.thousandeyes.com/Articles?category=Alerts#ServiceNowAlertManagement)  
[Related Information](https://success.thousandeyes.com/Articles?category=Alerts#AdditionalInformation)

## Overview

The ThousandEyes platform can notify users whenever their test results trigger an Alert Rule. Alert Rules allow configuring various methods of alert notification delivery. One of the supported methods is direct notification delivery into a ServiceNow account. Once the notification is delivered, ServiceNow processes it and allocates tasks based upon pre-defined workflows. 

To route alert notifications directly into ServiceNow, the following needs to be properly configured:

* A ServiceNow Integration created
* Alert Rules associated with ServiceNow Integration
* ThousandEyes Tests associated with Alert Rules

The content below will guide you through the process of configuring both, ServiceNow and ThousandEyes. In the end, an alert triggered in ThousandEyes will cause a new incident to be generated within your ServiceNow account instantly. This process should streamline the handling of ThousandEyes-reported events, aligning it with your existing \(ServiceNow-based\) workflow.

## ServiceNow releases supported by ThousandEyes

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
 

**Pre-requisite \(London, Madrid and New York only\): disable** the global system property **state** parameter1. Type sys\_properties.list in the filter navigator field then hit return. In the main window, the System Properties table will appear \(see [figure 1](https://success.thousandeyes.com/Articles?category=Alerts#fig_1_find_global_state_parameter) below\).  
2. Using the table search feature field select the **name** filter, in the search field type `glide.oauth.state.parameter.required` and hit return \(see [figure 1](https://success.thousandeyes.com/Articles?category=Alerts#figure_2_set_state_parameter) below\).  
  
![Find the global system state parameter](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UNyo&feoid=00NE0000006OT0r&refid=0EM2R000000C5Q4)  
Figure 1. How to find the global system state parameter  
  
3. Click `glide.oauth.state.parameter.required` to open the parameter's configuration, change the **Value** text field to `false`, then click **Update** \(See [figure 2](https://success.thousandeyes.com/Articles?category=Alerts#figure_2_set_state_parameter) below\).  
  
![Update the global system state parameter](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UNyo&feoid=00NE0000006OT0r&refid=0EM2R000000C5QT)

