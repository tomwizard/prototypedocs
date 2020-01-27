# Role-Based Access Control explained

The ThousandEyes platform provides a Role-based Access Control \(RBAC\) model for user and user group management.  RBAC provides two principal benefits: First, RBAC eliminates the hierarchical relationships between users, account groups and organizations. Under RBAC, users may belong to more than one Account Group. Second, RBAC provides the flexibility to configure permissions that were previously fixed within the three predefined roles. With RBAC you can create Roles for users which will allow them to do everything which is needed via the UI or API and no more.  

For example, an employee who needs to administer their company’s ThousandEyes users in multiple accounts was previously required to have the Organization Admin role, which provided permissions not only to administer all users in every account but also permissions to access billing information for all accounts.  Under RBAC, you may assign Roles which have permissions for only user administration tasks in only the Account Groups needed, and not grant permissions for billing or other tasks within those account groups.

For a complete list of all available Permissions, their descriptions and what Permissions are assigned to each of the built-in Roles see the [Roles and permissions table]()

## Terminology in RBAC

Account Groups are assigned to Users, who have Roles within each Account Group.  A User can be in one or many Account Groups, and a User can be assigned one of three built-in Roles \(Organization Admin, Account Admin and Regular User\) which have fixed Permissions or a be assigned a custom Role.  Under RBAC, a customer may create multiple new custom Roles and unique permission sets. 

**Note: With RBAC, users are associated with the Organization and the Account Admin role does not have permissions required to create, edit or delete users. To provide this capability, a role having the** _**Edit users**_ **permission must be assigned to the user.**

## Working with RBAC

Managing users is done under the [Account Groups](https://app.thousandeyes.com/settings/account/?section=accountgroups), [Users](https://app.thousandeyes.com/settings/account/?section=users), and [Roles](https://app.thousandeyes.com/settings/account/?section=roles) tabs of the [Account Settings](https://app.thousandeyes.com/settings/account) page. Users may also modify their own settings under the [Profile](https://app.thousandeyes.com/settings/account/?section=profile) tab.

###  Default built-in Roles

All accounts come preloaded with 3 default roles: **Organization Admin, Account Admin** plus the **Regular Users** role. The permission assigned to each of these 3 predefined roles are fixed but you can duplicate any of these Roles and then customize them to suit your requirements. When hovering over a permission title in the UI a tooltip will appear explaining in more detail what the permission does but in general, the titles are self-explanatory. For instructions on how to use the features under the Roles tab please navigate to the following section on [Managing Roles](). Currently, we have more than 90 permissions available for you to choose from. For a full list of permissions assigned to the **Organization Admin**, **Account Admin** plus the **Regular Users** role check the [Roles and Permissions table]().

The permissions assigned to a user with an **Organization Admin** role \(or similar\) enables them to do the following:

* access all **Account Groups** defined within the organization
* fully manage all Users and Roles
* view and create tests, shares, dashboards and reports
* assign agents to any Account Group belonging to the organization
* edit security settings, view billing information and change payment details

The permissions assigned to a user with an **Account Admin** role \(or similar\) are able to do the following:

* access the API
* create, edit and view snapshots
* create, edit and view transaction tests
* edit agents, alerts, notifications, endpoint agent and label settings
* access the [Profile](https://app.thousandeyes.com/settings/account/?section=profile), [Users](https://app.thousandeyes.com/settings/account/?section=users) and [Activity Log](https://app.thousandeyes.com/settings/account/?section=activityLog) tabs under the [Account Settings](https://app.thousandeyes.com/settings/account) page. If access to the other account settings tabs is required e.g. [Roles](https://app.thousandeyes.com/settings/account/?section=roles), [Quotas](https://app.thousandeyes.com/settings/account/?section=quotas) or [Organization](https://app.thousandeyes.com/settings/account/?section=organization) please assign the user the role of **Organization Admin** \(or similar\).
* view sensitive transaction test settings e.g. usernames and passwords in the [test settings](https://app.thousandeyes.com/settings/tests/?tab=settings) or [test view](https://app.thousandeyes.com/view/tests) pages

**Note: The Account Admin role only has permissions to create, edit or delete users within their assigned account group.**

The permissions assigned to a user with a **Regular Users** role \(or similar\) enables them to do the following:

* access all test results and read-only access to test settings
* customize their dashboards
* reset their password
* create and delete their own shares, snapshots
* check their own activity log
* run instant tests but are not able to save/create them

###  Managing Roles

Roles and Permissions settings are all contained under the [Account Settings &gt; Users & Roles &gt; Roles](https://app.thousandeyes.com/account-settings/users-roles/?section=roles) tab. To create a new Role choose the **Add New Role** button or to customize an existing role choose the pencil icon; both options will place you in Role edit mode. Once you are finished editing your Role ensure you use the **Save Changes** button to save your changes. A reminder on editing default built-in Roles: you have to duplicate a built-in Role using the duplicate icon before you can customise it.

IMAGE MISSING

1. Search bar: Allows searching using a string such as "email" or "alert" for matching permissions.  The number in parentheses is the number of Permissions currently displayed.  Additionally, there are two buttons:
   * All - displays the full list of permissions that match the search string
   * Lock icon - displays only Management permissions that match the search string
2. Search filter selection: Filters the permissions column by **All Permissions**, **Management Permissions** or **component.** The component filter options available are: 
   * Admin
   * Alerts
   * API
   * BGP
   * Cloud and Enterprise Agents
   * Dashboard
   * Devices
   * Endpoint Agents
   * Labels
   * Live Shares
   * Saved Events
   * Snapshots
   * Tests
3. Role change icons: Allows creation of new Roles via duplication of an existing Role, or editing or deleting of existing Roles
4. Permission names: Lists the Permissions names which match the current search string
5. Roles: Lists the names of the built-in Roles and any customer-defined roles.  In this example, there is a customer-defined role "Limited Admin 1" in addition to the three built-in roles.  Use the scroll bar at the bottom of the display to move horizontally through the columns if more Roles are present that can be viewed in the current page size.  Use the scroll bar at the right to move vertically through the rows of Permissions.
6. Management permissions: A lock icon next to a Permission name is there to indicate the Permission is a Management Permission. A Management Permission allows a user to change their own or another user's permissions or scope of permissions, view and edit billing information, manage quotas and delete accounts. They are given the special indication of a lock icon to set them apart from other permissions and to ensure they are applied with care.

#### [Example custom Role]()

 The following table is an example of a commonly configured custom Role used by ThousandEyes users.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Table 1: Custom Role example</th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Role Purpose</td>
      <td style="text-align:left">Role Description</td>
      <td style="text-align:left">Example Permissions</td>
    </tr>
    <tr>
      <td style="text-align:left">NOC wallboard monitor for displaying dashboards</td>
      <td style="text-align:left">Enable users to log in, keeps their session alive, view dashboards and
        any report type widgets used within a dashboard.</td>
      <td style="text-align:left">
        <ul>
          <li>View reports (if you have report widgets in your dashboard)</li>
          <li>Login via Single Sign-on/ThousandEyes login page</li>
          <li>Keep session alive on auto-update</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>If there are any custom roles you think would benefit you or other users do [let the Customer Success Team know](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) and we'll consider adding them to the table above.

###  Managing Account Groups

Account Groups settings are all contained under the [Account Settings &gt; Users & Roles &gt; Account Groups](https://app.thousandeyes.com/account-settings/users-roles/?section=accountgroups) tab. 

IMAGE MISSING

1. Add New Account Group button: Click the button to enter **Add New Account Group** mode and display the **Add New Account Group** panel.
2. Search bar: Allows searching the Account Groups for a text string or substring.
3. Account Group column:  Alphabetized list of Account Groups in the organization.  Click the triangle icon to reverse the sort order.  Click the triangle next to an Account Group's name to enter **Add New Account Group** mode for that Account Group.
4. Users column: The number of users in the Account Group.
5. Enterprise Agents column: The number of Enterprise Agents in the Account Group.
6. Delete: Click the trash can icon to delete the Account Group.

### Add new Account Group

To add a new Account Group open the **Add New Account Group** panel located on the [Account Settings &gt; Users & Roles &gt; Account Groups](https://app.thousandeyes.com/account-settings/users-roles/?section=accountgroups) tab, provide an Account Group Name, select any Enterprise Agents you would like to belong to the new group then finally use the Add New Account Group button. 

IMAGE MISSING

1. Account Group Name: The name of the new Account Group.
2. Enterprise Agents: Select Enterprise Agents assigned to this Account Group \(optional\).
3. Add New Account Group/Cancel: Click the **Add New Account Group** button to save the new Account Group or **Cancel** to exit without saving.

### Edit Account Groups

To edit Account Groups, click on the triangle next to an Account Group's name.  The **Edit Account Group** panel will appear:

IMAGE MISSING

1. Account Group Name: The name of the Account Group.
2. Enterprise Agents: Select Enterprise Agents assigned to this Account Group \(optional\).
3. Account Group Token: The token for the Account Group.  Used when installing Enterprise Agents for this Account Group.  Agents can be assigned to multiple Account Groups.
4. Save Changes/Cancel: Click the **Save Changes** button to save the changes or click Cancel to exit without saving. 

###  Managing Users

Add or edit the users and assign to one or more Account Groups.  Users are added or modified under the Users tab.

IMAGE MISSING

1. Mode indicator: Displays the current mode--either Edit Users mode or Add New Users mode.
2. Add New Users button: Click the button to enter **Add New Users** mode and display the **Add New Users** panel.
3. Search bar: Allows searching the User, Email or Account Group columns for a text string or substring.
4. User column: Alphabetized list of users in the organization.  Click the triangle icon to reverse the sort order.  Click the triangle next to a user's name to enter Edit User mode for that user.  A **User** entry will be a dash \( -- \) if the user has not yet performed the registration process per the account registration email, after account creation.
5. Email column: List of user email addresses, which are used as logins to the ThousandEyes platform.
6. Account Groups column: List of the Account Groups to which the user belongs.  "All" indicates membership in the built-in Account Group whose name is "All account groups".
7. Management permissions: The user-and-lock icon indicates that this user possesses Management permissions.
8. Registration pending: A red triangle icon indicates that the user has not yet completed the registration process as provided for in the registration email sent from the ThousandEyes platform. If you haven’t received a registration email within 24 hours and you are getting the notification above, please reach out to Customer Success Team and request their assistance.

### Adding User\(s\)

To add new users, click on the **Add New Users** button.  The **Add New Users** panel will appear:

IMAGE MISSING

1. Emails: Enter one or more email addresses which will be used by the users as logins to the ThousandEyes platform.  Use a comma as a delimiter to add multiple emails addresses \(typically by pasting text from your clipboard\).  An email with instructions to complete registration will be automatically sent to each address.
2. Account Groups: Select the Account Group\(s\) to which the user will belong using the Account Groups pull-down menu. Multiple Account Groups are permitted. The selection affects all users listed in the **Emails** field.
3. Roles: Click within the text field to display and select the Roles that the user\(s\) will have within the scope of the associated Account Group. Multiple Roles are permitted.
4. Add/Remove Account Group: Click the **+** icon to add a new Account Group pull-down and associated Roles field, for multiple Account Group assignment. Click the **-** icon to remove an Account Group pull-down and associated Roles field.
5. Login Account Group: Select the Account Group in which the user starts.  If a user is a member of multiple Account Groups, the user will be able to switch Account Groups using the **Switch Account Groups** link under their username in the upper-right corner of the interface.

**Note:** When creating new users, the name of the user\(s\) are not entered by the administrator.  After the user account is created, the user will receive an email from the ThousandEyes platform requesting that the user complete the registration process.  This permits the user to provide their name string, saving the administrator typing and reducing the risk of errors.  If the administrator wishes to provide the name, the Edit User panel under the Users tab allows for manual entry.  
 

### Edit User

In the Users tab click any user entry in the table to expand all the editable options as per screenshot below.

IMAGE MISSING

1. Registration pending: A red triangle icon indicates that the user has not yet completed the registration process as provided for in the registration email sent from the ThousandEyes platform. Note: One registration email can be sent per 24 hours using the Resend registration email link. If you attempt to send more than one in the 24h period a warning message will appear "A registration email has been sent to this user in the past 24 hours."
2. Name: The name of the user.  This will be blank if the user has not completed registration.
3. Email: The email addresses which will be used as the login to the ThousandEyes platform.
4. Account Groups: The Account Group\(s\) to which the user belongs.  Edit the Account Group\(s\) to which the user belongs with the Account Groups pull-down menu. Multiple Account Groups are permitted.
5. Roles: The Roles which belong to the user, within the associated Account Group.  Click within the text field to edit the Roles that the user has within the scope of the associated Account Group. Multiple Roles are permitted.
6. Add/Remove Account Group: Click the **+** icon to add a new Account Group pull-down and associated Roles field, for multiple Account Group assignment.  Click the **-** icon to remove an Account Group pull-down and associated Roles field.
7. Login Account Group: The Account Group to which the user belongs upon login.  Click the **Login Account Group** pull-down to edit Account Group assignment.
8. Delete: Click the trash can icon to delete the user.

##  Roles and permissions table

| Table 2: Permission titles, |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- |
|   |  |  |  |  |
| descriptions and predefined roles |  |  |  |  |
| Permission Name | Permission Description | Organization Admin | Account Admin | Regular User |
| Accept inbound live shares | Be able to accept a live share of a test  | x  | x  |  |
| API access | Full access to ThousandEyes API  | x  | x  | x  |
| Assign agent to account group | Creating agents in and sharing agents to an account group  | x  |  |  |
| Assign email address of users to alerts | Add subscriber emails to alerts | x | x |  |
| Assign management permissions | Assign management permissions | x |  |  |
| Be able to view my own saved events | Be able to view events saved by me | x | x | x |
| Can add or modify tests to consume over 100% resources | Ability to create and modify tests that would consume more than the purchased resource amount. This permission would only apply if your account has overage enabled. | x | x |  |
| Create live shares for inside the organization | Be able to create live shares to share with other account groups in the organization | x | x |  |
| Create live shares for outside the organization | Be able to share data with other organizations | x | x |  |
| Create saved events | Be able to save an event within views | x | x | x |
| Create snapshot shares | Be able to create and share a snapshot within views | x | x | x |
| Create web transaction tests | Be able to create a web transaction tests that records various transactions during a webpage interaction. The "Edit tests" permission is also required for this permission to work. | x | x |  |
| Delete account | Delete Account Group | x |  |  |
| Download Endpoint Agents | Be able to download a custom endpoint agent installer for the organization to use within different account groups | x | x |  |
| Edit agent notifications | Be able to edit agent notification rules in agent settings | x | x |  |
| Edit agents in account group | Be able to modify enterprise agents and their configurations \(e.g. proxy settings\) in an account group | x | x |  |
| Edit alert rules | Be able to create and edit the alert rules for a test | x | x |  |
| Edit alert suppression windows | Be able to configure and edit an alert suppression window | x | x |  |
| Edit all account groups | Be able to create and edit all account group settings | x |  |  |
| Edit BGP monitors | Be able to create and edit private BGP monitors | x | x |  |
| Edit dashboard templates for all users in account group | Be able to edit dashboard templates for all users within an account group | x | x |  |
| Edit default timezone settings | Be able to edit organization-wide timezone settings | x |  |  |
| Edit device notifications | Be able to edit device notifications in device layer view | x | x |  |
| Edit endpoint agent monitored domain sets | Be able to edit the monitored domain sets by endpoint agents | x | x |  |
| Edit endpoint agent monitored networks | Be able to edit the monitored networks by endpoint agents | x | x |  |
| Edit endpoint agent settings | Be able to modify endpoint agents and their configurations in an account group | x | x |  |
| Edit endpoint tests | Be able to edit endpoint tests | x | x |  |
| Edit Internet Insights - Catalog settings | Be able to modify catalog entries | x | x |  |
| Edit labels | Edit labels | x | x |  |
| Edit live shares sent by all users in account group | Be able to edit the live shares sent by all users in an account group | x | x |  |
| Edit live shares shared by ThousandEyes | Be able to edit the live shares shared by ThousandEyes | x | x |  |
| Edit my domains | Be able to write the domains to be monitored | x | x |  |
| Edit organization and account group quotas | In order to edit quotas, you must also be able to view usage and billing | x |  |  |
| Edit own dashboard templates | Be able to edit your personal dashboard template |  |  | x |
| Edit own live shares | Be able to edit own live shares |  |  | x |
| Edit own report snapshots | Be able to edit report snapshots created by you |  |  | x |
| Edit own reports | Be able to edit your reports created by you |  |  | x |
| Edit own saved events | Be able to edit your own saved events | x |  | x |
| Edit own saved events for all users in account group | Be able to edit all saved events within an account group | x | x |  |
| Edit own snapshots | Be able to edit your own snapshots |  |  | x |
| Edit Path Visualization interface groups | Be able to edit interface groups in test views | x | x |  |
| Edit payment and contact details | Be able to edit the billing information and credit card information | x |  |  |
| Edit reports for all users in account group | Be able to edit all reports in an account group | x | x |  |
| Edit roles | Be able to edit the roles. This is a separate tab that will appear in Account Settings to users with this permission | x |  |  |
| Edit security & authentication settings | Be able to modify security and authentication settings. This is a separate tab that will appear to users with this permission | x |  |  |
| Edit snapshots for all users in account group | Be able to edit all snapshots in an account group | x |  |  |
| Edit snapshots shared by all users in account group | Be able to edit all shared snapshots in an account group | x | x |  |
| Edit tests | Be able to create and edit tests | x | x |  |
| Edit user email addresses | Be able to edit email addresses of all users | x | x |  |
| Edit users | Be able to create and edit users in an account group | x | x |  |
| Edit users in all account groups | Be able to create and edit users in an organization | x |  |  |
| Embed own widgets | Embed your own widgets into other applications |  |  | x |
| Embed widgets for all users in account group | Embed widgets within an account group in other applications | x | x |  |
| Internet Insights - Catalog settings | Be able to view Internet Insights - Catalog set | x | x | x |
| Keep session alive on auto-update | Be able to keep the ThousandEyes session alive during an auto-update | x | x | x |
| Login via Single Sign-On | Be able to login by using SSO | x | x | x |
| Login via ThousandEyes login page | Be able to login by typing username and password interactively into ThousandEyes | x | x | x |
| Set dashboard template as account group default | Be able to set default dashboards for an account group | x | x |  |
| Set report template as account group default | Be able to set default reports for an account group | x | x |  |
| View activity log for all users in account group | Be able to view an account group's activity log. The activity log will appear in a new tab within Account Settings for users with this permission | x | x |  |
| View agent notifications | Be able to receive enterprise agent notifications | x | x |  |
| View agents in account group | Be able to view Enterprise Agents settings and their configurations \(e.g. proxy settings\) in an account group | x | x | x |
| View alert rules | Be able to view alert rules | x | x | x |
| View alert suppression windows | Be able to view alert suppression windows | x | x | x |
| View all account groups settings | Be able to view account group settings | x |  |  |
| View all users | Be able to view all users in an organization | x | x |  |
| View BGP monitors | Be able to view all privately created BGP monitors | x | x | x |
| View billing | Be able to view the billing tab | x |  |  |
| View device notifications | Be able to receive and view device notifications | x | x | x |
| View endpoint agent data | Be able to view endpoint agent data | x | x | x |
| View endpoint agent monitored domain sets | Be able to view endpoint agent monitored domain sets | x | x | x |
| View endpoint agent monitored networks | Be able to view endpoint agent monitored networks | x | x | x |
| View endpoint agent settings | Be able to view endpoint agent settings | x | x | x |
| View endpoint data that identifies users | Be able to view endpoint data that identifies users | x | x | x |
| View endpoint data that identifies network | Be able to view endpoint data that identifies network  | x  | x  | x  |
| View endpoint data that identifies users  | Be able to view endpoint data that identifies users  | x  | x  | x  |
| View endpoint data that identifies visited pages | Be able to view endpoint data that identifies visited pages | x | x | x |
| View endpoint tests | Be able to view endpoint tests | x | x | x |
| View labels | Be able to view labels within an account group | x | x | x |
| View live shares shared by ThousandEyes | Be able to view live shares created by ThousandEyes | x | x | x |
| View live sharings from all users in account group | Be able to view live shares in an account group | x | x |  |
| View my domains | Be able to view my own domains | x | x | x |
| View organization usage | Be able to view my organization's units and licenses consumption | x |  |  |
| View own activity log | Be able to view my own activity log |  |  | x |
| View own live shares | Be able to view my own live shares |  |  | x |
| View own snapshots | Be able to view snapshots saved by me |  |  | x |
| View reports | Be able to view reports and report widgets in dashboards | x | x | x |
| View roles | Be able to view the Roles tab within Account Settings | x |  |  |
| View security & authentication settings | Be able to view the security and authentication settings for an organization within Account Settings | x |  |  |
| View sensitive data in web transaction scripts | Be able to view sensitive data in transactions scripts in a transaction test | x | x |  |
| View snapshots | Be able to view snapshots shared to me in an account group | x | x | x |
| View snapshots shared by all users in account group | Be able to view snapshots shared by all users in an account group | x | x |  |
| View tests | Be able to view the tests created in an account group | x | x | x |
| View user activity in all account groups | Be able to view the activity log for the organization within Account Settings | x |  |  |

## Related Articles

* [What is an account group](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjDCAQ_What-is-an-account-group) explains how to use the Account Group feature
* [Working with Account settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnGKAS_Working-with-Account-settings) explains all the features available under the management interface i.e. Roles, Users, User Profile, Quotas, Billing and Usage
* [API permissions list](https://developer.thousandeyes.com/v6/admin/#/permissions) explains how to obtain a list of all assigned permissions via the API

