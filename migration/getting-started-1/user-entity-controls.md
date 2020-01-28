# User Entity Controls

As a cloud service provider we share responsibilities for security with our customers. ThousandEyes User entity \(customer\) is responsible for implementing the following security controls and operational activities:

## Identity Management

 For the customer instance of the SaaS Platform, ThousandEyes creates a user account with administrative permissions for the employee listed as a technical contact on the contract. It is the responsibility of the customer to:

1. Configure single sign-on \([using SAML](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnEKAS_How-to-configure-Single-Sign-On-SSO-Metadata)\) or appropriate password policies \(complexity is always enforced, add password age\);
2. Create other users and accounts with appropriate roles \(use of [SCIM API](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM) is supported for automation\);
3. Periodically review access to the service to make sure only authorized workers have access with proper access levels;
4. Configure groups and users using [role-based access controls](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) \(RBAC\) to ensure only authorized users can access/view sensitive data \(including personal information\);
5. Avoid the use of shared logins \(these are prohibited in most organizations\), there is no charge associated user accounts on the ThousandEyes platform;
6. For customers that use ThousandEyes Appliances \(Virtual and Physical\), customer administrators are required to change the password of the Virtual Appliance as part of the initial setup process.

## Infrastructure Protection Services

 Customers must ensure the security of their endpoints \(end-user computers\) and connectivity.  If Enterprise Agents are in use, it is the customer’s responsibility to protect underlying physical infrastructure, virtualization and containerization \(if present\). If the Enterprise Agent is delivered as a Linux application, the customer must also secure the underlying Linux server.

## Endpoint Agent Management

 If an end-user asset leaves Customer’s operational ownership, it is recommended to uninstall Endpoint agent from the system.  For all uninstalled and/or retired systems with Endpoint agent, ThousandEyes recommends removal of the Endpoint agent entry from ThousandEyes Endpoint agent inventory, as these will not be removed automatically.

## Logging and Monitoring

 Configure [audit log \("Activity log"\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnNKAS_Working-with-the-Activity-Log) download into your log management solution via the [ThousandEyes API](https://developer.thousandeyes.com/v6/) \(or CSV\).

## Session management

 Assign permission "Keep session alive on auto-update" only for those roles containing users who need to have it \(such as a NOC user\). ThousandEyes application has a 30-minute session timeout which does not apply when the user has any of the following views open in their browser:

1. Dashboards view
2. Alerts &gt; Alert list view
3. Cloud & Enterprise Agents &gt; Agent Settings view

 The views listed above implement automatic content refreshing that happens periodically. These content refresh events also reset the session timer, preventing an inactive user's browser session from timing out.

{% hint style="warning" %}
The automatic session prolongation described above requires the "Keep session alive on auto-update" permission enabled for the user. See the [Role-Based Access Control article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) for more details about user roles and permissions.
{% endhint %}

## Policies and Standards

 In relation to the ThousandEyes SaaS Application, the most important steps for customers to execute as part of the “Policies and Standards” domain management are to:

1. Classify data stored and processed by ThousandEyes.
2. Establish a worker awareness and training program.
3. Comply with Data Subject Access Requests requirements \(ThousandEyes will redirect data subjects to your Administrators\).

 Customer should review and understand data retention policies and consider the use of API for export or archival.

## Other security improvements to consider

1. Customer may request from ThousandEyes support removal of access permissions into their organization from ThousandEyes personnel, this permission is enabled by default to facilitate support and other activities related to service operations;
2. Carefully consider who in your organization should have the ability to perform “Snapshot sharing”, this functionality allows your internal users to share network events with your third parties \(such as service providers\) in a way that allows this data to be accessed anonymously;
3. If Enterprise agents are deployed in your network, consider changing Enterprise Agent NTP settings by pointing to your authorized NTP servers \(otherwise, the defaults for your operating systems will be used\);
4. Make sure your users are refreshing their API tokens according to your policy.

## Additional information

 If you have deployed ThousandEyes Enterprise Agent Virtual Appliance \(TEVA\) and have configured it to use proxy that requires authentication, due to limitation of underlying Linux platform, those credentials will be stored on the appliance in clear text.  
 

