# ThousandEyes user session timeouts and terminations

ThousandEyes application can be accessed by navigating to [https://app.thousandeyes.com/](https://app.thousandeyes.com/) URL using your preferred web browser. To enter the application, authentication is required and a successful login event creates an active browser session. For security reasons, active browser sessions are automatically terminated after a period of **inactivity** or due to certain administrative events. This article explains various scenarios that lead to the termination of the browser session.

### How many concurrent browser sessions can a user have?

There is no limit on the number of concurrent browser sessions.

### When does a user's browser session timeout?

The browser session times out after **30 minutes** of inactivity.

However, there is an exception. The 30-minute session timeout does not apply when the user has any of the following views open in their browser:

* [Dashboard](https://app.thousandeyes.com/dashboard) view
* [Alert list](https://app.thousandeyes.com/alerts/list/active) view
* [Settings &gt; Agents &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/) view

The views listed above implement automatic content refreshing that happens every **5 minutes**. These content refresh events also reset the session timeout timer, preventing an inactive user's browser session from timing out.

**NOTE:** The automatic session prolongation described above requires the "Keep session alive on auto-update" permission enabled for the user. See the [Role-Based Access Control article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) for more details about user roles and permissions.

### What are the scenarios for immediate termination of active user session?

An active user session is immediately terminated in the following cases:

* The user has two \(or more\) browser sessions active and they reset their password in one of the sessions. The session in which password reset event occurred is unaffected, but all other user's active sessions are terminated.
* Changes get applied to user's permissions/roles \(by an admin user\) or account's contract while the user is actively using the application.
* User's organization becomes locked while the user is actively using the application.

### What does the “Keep me logged in” login option do?

At login time, checking the “Keep me logged in” option allows the user to be taken back to where he/she was when the automatic logout is enforced.

IMAGE MISSING

## Related information

 The following ThousandEyes Knowledge Base articles provide related information:

* [Role-Based Access Control Explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) provides details about the ThousandEyes application permission system.
* [ThousandEyes view layouts](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC_ThousandEyes-view-layouts) article describes general user-facing functionality and pinpoints where particular views can be found.

