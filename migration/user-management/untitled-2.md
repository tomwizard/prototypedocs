# What is an Account Group?

The Account Group is a feature used to divide an organization into different sections. There are many reasons to divide an organization to reflect the internal structure of an organization and provide different levels of visibility into the account resources such as tests, agents and alerts.

## Where to find the Account Groups

The existing Account Groups are listed under the Account Groups tab of the [Account Settings](https://app.thousandeyes.com/settings/account/?section=accountgroups) page:

IMAGE MISSING

**NOTE**: The **Account Groups** tab is not visible to users without the necessary [permissions](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) - the View all account groups settings permission is required.

Each Account Group in the list can be expanded to view and edit its details, such as name, assigned [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) and Account Group Token. The Enterprise Agents drop-down is used to select or view which Agents are shared with the current Account Group.

During installation of an Enterprise Agent, an Account Group Token needs to be provided. The token binds the new Agent to its default Account Group. The new Agent can then be shared with other Account Groups, which in turn allows it to run tests belonging to those Account Groups.

## User assignment to Account Groups

A user can belong to one or multiple Account Groups, and can be assigned different [Roles](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) in each of them. This is configured by expanding the specific user in the [Users](https://app.thousandeyes.com/settings/account/?section=users) tab:

IMAGE MISSING

**NOTE**: The **Users** tab is not visible to users without the necessary [permissions](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) - the View all users permission is required.

## Switching between Account Groups

When a user belongs to multiple Account Groups, each Account Group can be accessed using the **Current Account Group** selector under the Users icon \(1\):

IMAGE MISSING

The **Current Account Group** drop-down menu lists and provides switching between all Account Groups available to the user.

## Related Information

* [Role-Based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) illustrates the role-based security model used in the ThousandEyes app.
* [Where can I get the Account Group Token?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyjrCAA_Where-can-I-get-the-account-group-token) explains where to retrieve the token used to bind Enterprise Agents to the specific Account Group.

