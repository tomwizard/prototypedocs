# Working with Account settings

The [Account Settings view](https://app.thousandeyes.com/settings/account/) provides a management interface for various aspects of your ThousandEyes account, such as your user's settings and contact information. You can also manage information about your organization, its users and account groups. To access your account settings, click on “Account Settings” on the left hand side menu.  This will reveal additional menus.

Selecting the Account Settings submenus will show they are separated into multiple tabs. Users may not see all the tabs depending on their level of assigned permissions.  Tabs which are displayed and their contents will depend on the permissions in the roles assigned to each user.  For example, users with the _Organization Admin_ role will see the **Users** tab, which displays information about users in each Account Group within the organization. The _Account Admin_ role will also see a **Users** tab but is limited to seeing only users present in the account groups assigned to it.  In the Table of contents below, we display all of the possible tabs and settings within each tab and link to detailed descriptions of each.

For information regarding roles and permissions, please refer to the [Role-Based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) article. 

## Users and Roles

## Profile tab

The [Profile tab](https://app.thousandeyes.com/settings/account/?section=profile) displays information about the user's organization\(s\), Account Groups\(s\) and assigned Roles within those Account Groups. Here, users can modify their own username and email address \(used for login to ThousandEyes\), change their password and set their preferred timezone for the web interface. 

If the user is a member of more than one Account Group \(in one or in multiple organizations\), then the user can select their **Login Account Group**. This determines into which Account Group the user is placed upon login. Once logged in, users can switch between Account Groups with the **Current Account Group** selector in the User menu, as described in the [Switching account groups]() section below.

IMAGE MISSING

Under the **User Profile** section, for users with [API access](https://developer.thousandeyes.com/v6/#/authentication) enabled \(i.e. users with the API Access permission\), the **User API Tokens** section will be visible, containing the API authentication tokens:

IMAGE MISSING

Two types of API authentication tokens are available: a token for [HTTP Basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication) and a token for [OAuth-based authentication](https://en.wikipedia.org/wiki/OAuth). The primary purpose of the latter is providing an authentication mechanism for the [SCIM-based automated user provisioning process](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM).

## Roles tab

A user with the View roles permission will be able to see the [Roles tab](https://app.thousandeyes.com/settings/account/?section=roles) containing a table of all security Roles defined within the organization \(1\) and permissions associated with each Role \(2\):

IMAGE MISSING

The extensive list of permissions can be narrowed down by using the search bar \(3\). New roles can be defined by either clicking the **Add New Role** button \(4\) or by cloning one of the existing roles by clicking the  icon under its name.

As previously mentioned in the sections above \(Account Groups tab, Users tab\), refer to the [Role-based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) article for detailed information about ThousandEyes permission system.

## Users tab

The [Users tab](https://app.thousandeyes.com/settings/account/?section=users) is visible for users having the View all users permission. As the name suggests, this section allows general user management:

IMAGE MISSING

Clicking on any entry in the table expands it and presents management options for the user's name, email address and Account Group associations, not unlike what each user sees in their [Profile tab]():

IMAGE MISSING

At the top, the **Add New Users** button opens a similar dialog, displayed in the figure below. This dialog has one additional feature - multiple users can be created in one step, with identical Account Group and Role associations. To create multiple users in one step, simply add multiple email addresses into the **Emails** field. You can add multiple emails by either pressing the Enter key after each email address is typed in, or by pasting a comma-separated list of email addresses into the field:

IMAGE MISSING

As shown in the previous figure \(the Expanded user entry figure above\), each user can be a member of multiple Account Groups. In each Account Group, the user can have more than one Role assigned. The permission list granted to the user within each Account Group is a union of permissions across all Roles assigned to the user in that Account Group. For example, if the user has the Account Admin and Regular User roles, then they will have the combined permissions of both roles.

For an extensive description of the ThousandEyes role-based permission system, consult the [Role-based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) article.

## Account Groups tab

For users with the View all account groups permission, the [Account Groups tab](https://app.thousandeyes.com/settings/account/?section=accountgroups) will be visible. This tab displays all [Account Groups](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjDCAQ_What-is-an-Account-Group) defined in the organization, along with the number of users and [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent) present in each Account Group. Users with the Edit all account groups permission can add, manage and delete Account Groups:

IMAGE MISSING

Expanding a row in the Account Groups table displays the Account Group's details and allows changes to the Account Group's name. The [Account Group Token](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjrCAA_Where-can-I-get-the-Account-Group-Token) is also displayed for users to copy when installing Enterprise Agents. Click the **Regenerate Token** link if circumstances require that a new token should be created \(i.e. if the token is accidentally disclosed to an untrusted party\). Once the new token is generated, Enterprise Agents with the old Account Group token will continue to function normally.

IMAGE MISSING

An Account Group's Enterprise Agents can be displayed in the **Enterprise Agents** drop-down. Enterprise Agents available to the current Account Group are displayed with checked boxes. Agents from other Account Groups can be checked to make them available to this Account Group or can be unchecked to remove them from the current Account Group. A checked and greyed out entry indicates an Agent for which the current Account Group is the primary Account Group \(i.e. the Agent was created with the current Account Group's Token\) and thus cannot be deselected:

IMAGE MISSING

Refer to the [What is an Account Group?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjDCAQ_What-is-an-Account-Group) article for further information about what an Account Group is and why having multiple Account Groups might be useful for you.

### Switching account groups

As explained above, each user can have access to more than one Account Group. Those Account Groups can even span across multiple organizations. Additionally, users with the Organization Admin role \(or similar\) have access to all Account Groups defined within the organization. This allows the user to view tests, shares, reports and agents assigned to each of the Account Groups belonging to the organization.

To change the current Account Group context, click on the  icon in the upper right corner of the ThousandEyes web portal and expand the **Current Account Group** drop-down menu. This will allow you to switch into another Account Group context.

The following figure on the left shows the currently active context of the "QA PROD" Account Group \(1\). The figure on the right shows the expanded drop-down listing all Account Groups available to the user, from multiple organizations \(2\). Below the ThousandEyes Support Organization \(in gray\) is the "ThousandEyes Support" \(3\) Account Group.  Under the ThousandEyes Internal Organization there are 4 other Account Groups.  In this example QA PROD is listed in another organization further up in the menu selection :

IMAGE MISSING

IMAGE MISSING

## Usage and BillingUsage tab

The [Usage tab](https://app.thousandeyes.com/settings/account/?section=organization) shows settings for Plan Usage and Cloud Agent Units. This tab is only accessible by organization administrators - relevant permissions are View billing, View organization usage and View security & authentication settings:

IMAGE MISSING

#### Plan Usage section

The **Plan Usage** section deals with all aspects of Unit and license consumption. The overview section \(1\) shows current usage \(solid green bar\), additional projected usage until the end of the current billing cycle \(dashed green/white bar\) and the remainder of the planned/purchased capacity.

The table below the overview section will enable you to review and understand your account's Unit consumption. You can select between showing the consumption of **Cloud Agent Units** and **Enterprise Agent Units** \(2\) and control the breakdown table content by choosing to show your consumption by **Account Group**, by **Test Type** or by individual **Test** \(3\).

For your convenience, there is a [Calculate the units you need for this account group](https://app.thousandeyes.com/calculator) \(4, above\) link available. This link will lead you to the Unit Calculator, a tool that will allow you to estimate your future usage.

To fully understand ThousandEyes Unit consumption, head over to the [How Unit consumption works](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmoKAC_How-Unit-consumption-works) article.

If you have any questions regarding your usage numbers, please reach out to your ThousandEyes account manager or the Customer Success team via [support@thousandeyes.com](mailto:support@thousandeyes.com).

## Billing tab

The [Billing tab](https://app.thousandeyes.com/settings/account/?section=billing) shows current billing information for your organization. This tab is only accessible by users with the View billing permission:

IMAGE MISSING

The following sections are visible in this tab:

1. **Plan Details**: The details of your contracted ThousandEyes usage plan.
2. **Billing Address**: The address to be included on the invoices and the email address to which invoices are sent.
3. **Payment Method**: Displays payment information which is sent to a third party provider used by ThousandEyes for credit card processing. This form is a secure element connecting you directly to the third party provider. ThousandEyes never receives the credit card information, but rather obtains an authorization on behalf of the payment processor.
4. **Billing History**: Displays billing information generated over previous billing cycles.

If you have any questions regarding your plan details, please reach out to your ThousandEyes account manager or the Customer Success team via [support@thousandeyes.com](mailto:support@thousandeyes.com).

## Quotas tab

An Account Group\(s\) can be limited to a fixed quota of units from here. A user with the Can assign and edit quota permission will be able to see the [Quotas tab](https://app.thousandeyes.com/settings/account/?section=quotas):

IMAGE MISSING

Components of the Quotas tab:

1. **Plan**: Total units allocated to an organization per month.
2. **Organization Current Usage Rate**: Current rate at which an organization is utilizing units in their plan. Shown in terms of % of Plan used and units consumed. 
3. **Organization Quota**: Total units assigned to an organization. Enabled and value set to total plan by default. Can be toggled depending upon plan of an organization.
4. **Unallocated Usage**: Available units not allocated to any Account Group.
5. **Account Group**: This column contains names of Account Groups defined in the organization.
6. **Current Usage Rate**: Current rate at which an Account Group is utilizing units. Shown in terms of % of Plan and units consumed.
7. **Quota Switch**: Enable/Disable fixed quota of units for an Account Group.
8. Slider to configure a value for Usage Selector field
9. **Usage Selector**: Amount of units allocated to an Account Group.
10. Two options are available to configure **Usage Selector** value as below:
    * **Units**: Maximum number of units an Account Group can use per month.
    * **% of Plan:** Maximum proportion of organization's total units an Account Group can use per month.

Once done configuring quotas click **Save Changes** for the changes to take effect.

### [Unit quotas use cases]()

**Use case \#1: I don't want a single account group consuming all my units unexpectedly.**

Configure quota settings for all your account groups. This way none of your account groups will be able to consume all available units, preventing \(unintended\) increased unit usage in one account group from adversely affecting your other account groups.

**Use case \#2: My users are located all over the world. I want to allocate units to users based on regions.**

Create one account group per region. Then configure unit quotas for each region.

**Use case \#3: I want to keep my operations team uncapped while limiting units for all other account groups.**

If you have enabled quotas for all your account groups, you can always disable unit quota allocation for a particular account group while leaving other account groups capped.

**Use case \#4: I don't know how many units my new account groups will consume, but I don't want them to consume all available units.**

Quotas allocated to your account groups can add up to more than 100% of available units. Configure your new account group\(s\) with quota allocations below 100% for each individual account group. This enables an early warning about individual account group consuming more units than expected while not immediately affecting your other account groups.

**Use case \#5: I've set up account group quotas, the setup is working as expected. How can I make sure my quotas configuration is unchanged?**

Every ThousandEyes user in your account with the Can assign and edit quota permission will be able to adjust quotas. You will need to remove this permission \(only available to Organization Admins by default\) from all users unauthorized to perform quota allocation changes. You will need to communicate your requirement to other ThousandEyes administrators in your organization. If unexpected changes do happen, you can always inspect the [Activity Log]() for further details.  
 

## Activity Log

When the user has at least one of the View own activity log, View activity log for all users in account group or View user activity in all account groups permissions, the [Activity Log](https://app.thousandeyes.com/settings/account/?section=activityLog) is available showing events that have happened in your ThousandEyes account and is now visible from the Account Settings &gt; Activity Log:

IMAGE MISSING

[Working with the Activity Log](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnNKAS_Working-with-the-Activity-Log) explains all the details of the Activity Log usage.  
 

## Organization Settings

Security & Authentication, SSO setup and Organization Default Time Zone Settings are found under Account Settings &gt; Organization Settings

IMAGE MISSING  
 

#### Security & Authentication tab

The **Security & Authentication** tab provides configuration of the following aspects of your ThousandEyes account:

**1. SCIM Settings** - To complement the SSO, SCIM-based automatic user provisioning is supported. Consult the [**ThousandEyes support for SCIM**](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM) article for further information.  
 IMAGE MISSING

**2. Single Sign-On** settings, including SCIM-based automatic user provisioning. 

IMAGE MISSING

**3. Password Expiration** policy configuration for users who are allowed to use interactive login.

IMAGE MISSING

There is a series of articles available in our Knowledge Base describing [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language)-based Single Sign-On \(SSO\) configuration settings. Start with the [How to configure Single Sign-On: Metadata](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnEKAS_How-to-configure-Single-Sign-On-SSO-Metadata) article, which contains further links to identity provider-specific SSO setup guides, or use the search feature at the top of this page to find the SSO setup guide for your identity provider \(IdP\).

To complement the SSO, SCIM-based automatic user provisioning is supported as well. Consult the [ThousandEyes support for SCIM](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM) article for further information.  
 

#### Advanced Settings tab

The Advanced Settings Tab provides the ability to change the Organization Default Time Zone settings.

IMAGE MISSING

Organization Default Time Zones can now be set for two feature groups. Each Dropdown Groups timezone settings by European, North America, Asia Pacific as well as Global. In the Global grouping you have the option to set Coordinated Universal Time \(UTC\)

* Web UI Timezone - In addition to being able to set to UTC the option to set the timezone to the User’s System’s time is available here.
* Notification & Snapshot Timezone can also be set independently

##  Related information

The following resources contain further information related to ThousandEyes account management:

*  * [Role-based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) article explains how ThousandEyes permission system works.
  * [How to configure Single Sign-On: Metadata](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnEKAS_How-to-configure-Single-Sign-On-SSO-Metadata) article is a starting point for configuring SSO integration with your SAML-based identity provider.
  * [ThousandEyes support for SCIM](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM) article describes the configuration of SCIM-based automatic user creation.
  * [How Unit consumption works](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmoKAC_How-Unit-consumption-works) article outlines how tests contribute to your account's overall Unit consumption.
  * [Working with the Activity Log](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnNKAS_Working-with-the-Activity-Log) article describes how to audit events happening in your ThousandEyes account.

