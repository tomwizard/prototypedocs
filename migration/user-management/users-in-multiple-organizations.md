# Users in multiple organizations

Previously, the ThousandEyes platform required that a username \(email address\) be unique within the platform.  Now that constraint has been lifted, and a single username may be used in multiple organizations.  This article describes the functionality and user interface applicable to a user account in multiple organizations.

## Adding a user to an additional organization

Existing users may be added to additional organizations in exactly the same way that a new user is added to an organization.  Another user having a role with the appropriate permissions navigates to the **Users** tab of the [Account Settings](https://app.thousandeyes.com/settings/account/) page, then clicks the **Add New Users** button. Provide the email address of the existing user, and select the Account Group\(s\) and Role\(s\) that the user will have.  Select the Account Group into which the user will be placed at login time with the Account Login Group menu, or use the default of the current Account Group.  Then click the **Add New Users** button again to add the user.

 The image below shows an existing user whose username \(email address\) is "myexistinguser@thousandeyes.com" being added to a new organization in the Account Group "InfoSec" with a Role of "Account Admin":

IMAGE MISSING

The user will be added immediately to the new organization, no additional steps are required by the user to confirm the addition. The user will receive a notification email similar to the one pictured below, indicating that they have been added to an additional organization within the platform:

IMAGE MISSING

## Menus reflecting new organizations and Account Groups

The user's entry in the listing under the **User** tab will only show the Account Group\(s\) for the current organization.  However, the **Profile** tab of the user's own account will display an "Organization" column if the user is in multiple organizations, and list the Account Groups to which the user belongs in each organization, along with the Role\(s\) assigned.  Below we see the listing from the **Profile** tab of a user in two organizations: "ThousandEyes Internal" and "ThousandEyes Staging".

IMAGE MISSING

Additionally, other menus now display Account Groups for each organization in which the user belongs, separated by organization name.  For example, the Login Account Group menu on the **Profile** tab will now permit selection of the Account Group in which the user is logged into from the additional organization\(s\):

IMAGE MISSING

## Behaviors of multi-organization accounts

The following rules and restrictions apply to user accounts assigned to multiple organizations:

* Users may only be added to additional organizations if their first organization and any additional organizations have paid subscription accounts. Trial accounts do not support multi-organization users.
* Security policies as configured under the Security & Authentication tab \(authentication method, password expiry\) will be applied at the time the user switches between organizations, in addition to the initial login, provided the switch is to an organization with method higher "priority". Single sign-on is considered higher in priority than the native password-based authentication.  Some examples are provided below, based on the following organizations with the following authentication mechanisms:

  | **Organization Name** | **Authentication Method** |
  | :--- | :--- |
  | Org1 | password |
  | Org2 | password with expiry |
  | Org3 | single sign-on \(provider A\) |
  | Org4 | single sign-on \(provider A\) |
  | Org5 | single sign-on \(provider B\) |

* * Scenario 1: User in Org1 and Org2; Login Account Group in Org2  User logs in by providing their password in Org1. When the user switches from an Account Group in Org1 \(such as their Login Account Group\) to an Account Group in Org2, they are not required to provide credentials unless the password expiry is in effect, in which case they must provide their new password for Org2, as password expiry is considered higher priority.
  * Scenario 2: User in Org2 and Org3; Login Account Group in Org2  User logs in by providing their password in Org2. When the user switches from an Account Group in Org2 to an Account Group in Org3, they are redirected to the single sign-on page of provider A and must provide their credentials for Org3.
  * Scenario 3: User in Org3 and Org2; Login Account Group in Org3  User logs in by providing their credentials in Org3 to the single sign-on page of provider A. When the user switches from an Account Group in Org3 to an Account Group in Org2, they are not required to re-authenticate, as password authentication is considered lower in priority to single sign-on.
  * Scenario 4: User in Org3 and Org4; Login Account Group in Org4  User logs in by providing their credentials in Org3 to the single sign-on page of provider A. When the user switches from an Account Group in Org3 to an Account Group in Org4, they are not required to re-authenticate, as authentication to the same single sign-on provider is considered equal in priority.
  * Scenario 5: User in Org4 and Org5; Login Account Group in Org5  User logs in by providing their credentials in Org4 to the single sign-on page of provider A. When the user switches from an Account Group in Org4 to an Account Group in Org5, they are  required to re-authenticate, as authentication to a different single sign-on provider is considered higher in priority. 
* For users in multiple organizations, only the user can modify their Login Account Group.
* Enterprise Agents are available to users in multiple organizations. The Account Groups menu from the [Enterprise Agents page](https://app.stg.thousandeyes.com/settings/agents/enterprise/) will display Account Groups broken out by organization: IMAGE MISSING
*  Multiple tabs open in a browser will all be switched from one organization to another, but only the tab in which the switch is effected will display the new organization context.  Other tabs will indicate that the context has been switched if the user attempts operations in them.

## ThousandEyes API

The accounts endpoint \(https://api.thousandeyes.com/accounts\) shows all of the Account Groups in all organizations to which the user belongs, and should additionally show the "organizationName" for each account.  "organizationName" is not shown for users that are in only one organization.

