# How to configure Single Sign-On with Okta

ThousandEyes supports use of any SAML2-based identity provider for single-sign on.  There are two parts to an SSO configuration - the service provider configuration, which is what you set inside ThousandEyes, and the Identity Provider configuration, which you set in your SSO system.  In this configuration example, we use Okta as the Identity provider.

## How to Configure ThousandEyes for SSO

Configuration is fairly simple, but can come with a few gotchas.  Here's what you need:

* User in a role with the **Edit security & authentication settings** permission in ThousandEyes
* An authentication provider which provides SAML authentication
* From the SAML provider \(in this case, [Okta](http://www.okta.com/)\):
  * Login URL for your SAML provider
  * Logout URL for your SAML provider \(not required\)
  * Identity Provider issuer
  * Service provider Issuer
  * Validation certificate
* A post-back URL from ThousandEyes: **https://app.thousandeyes.com/login/sso/acs**
* Connection details:
  * Request Compression: Yes
  * Assertion: Unsigned
  * Response: Signed
  * Destination: http://www.thousandeyes.com
  * **autnContextClassRef: PasswordProtectedTransport**
  * Audience Restriction: http://www.thousandeyes.com

    _Note: it is very important that the Audience Restriction configured in your Identity Provider's configuration exactly match the value set for the Service Provider Issuer field in ThousandEyes.  Any mismatch, including a protocol mismatch \(http:// vs https://\) will cause the request to be rejected._

  * Recipient: http://www.thousandeyes.com
  * Name ID Format: Email Address
  * Role: User

To configure the system for Single Sign-on, configuration must be done on both the SAML provider site, and on ThousandEyes.

### In the Identity Provider's site \(Okta\), follow these steps:

1. Log in
2. Open Administration
3. Select the **Applications** tab
4. Locate the ThousandEyes app using the search or scrolling through the list of apps
5. Click the **Add** button
6. Accept the defaults on the **General Settings** or select values appropriate for your environment ****
7. Click **Next**
8. Click the **View Setup Instructions** to open ThousandEyes-specific configuration information in a new page.

   You will need the information on this page for the single sign-on configuration in the ThousandEyes app.  If you close this page and need to re-open, you can use the URL http://saml-doc.okta.com/SAML\_Docs/How-to-Configure-SAML-2.0-for-ThousandEyes.html but you must be logged into your Okta Administrator account to be able to access the ThousandEyes-specific configuration information for your organization.

9. Click **Next**
10. Assign the app to people in your SAML organization using the checkbox next to a user's name
11. Click **Next**
12. Modify as needed any user logins \(email addresses\) for ThousandEyes for your users.  The username here must match the username configured in ThousandEyes for this user.
13. Click **Done**

### In ThousandEyes, follow these steps:

1. Log in.
2. Click on the user menu \(top right\) and select Account Settings &gt; Security & Authentication tab.
3. Check the box to _Enable Single Sign-On_
4. Copy the value found in the **Redirect Login URL** field of the ThousandEyes-specific configuration page \(from step 8 above\) into the **Login Page URL** field on the Security & Authentication tab
5. The **Logout Page URL** is optional, but should point to the page you wish your users to see when logging out of ThousandEyes.  

   Recommended: https://app.thousandeyes.com/login/sso

6. Copy the value found in the **Identity Provider Issuer** field of the ThousandEyes-specific configuration page into the Identity Provider Issuer field on the Security & Authentication tab.  This should be http://www.okta.com/{externalKey}.
7. Enter http://app.thousandeyes.com in the **Service Provider Issuer** field.  

   _NOTE: It is extremely important to make sure that the Service Provider Issuer field in ThousandEyes reflects the value set by the Identity provider's response in the audienceRestriction field.  Any mismatch, including a protocol mismatch \(http:// vs https://\) will cause the request to be rejected._

8. For the **Verification certificate** option, upload the file downloaded from the ThousandEyes-specific configuration page \(from step 8 above\).
9. Click **Save**.

## Logging in using SSO

When you visit ThousandEyes for the first time on your computer, enter your username into the Email Address field, and click the SSO link, indicated with the number \(1\) in the image below:

IMAGE MISSING

This will redirect to your SAML provider's login page, and validate the login, then will redirect back to ThousandEyes, and your user will be logged in.  After logging in for the first time successfully, a cookie is written to your system, indicating that you are an SSO user - and in the future, you will be taken to a special SSO-only login page, shown below.

IMAGE MISSING

## To return to the normal login page

If your organization discontinues use of SSO at any time, you can return to the login page, by using this special login URL: https://app.thousandeyes.com/login?breakSso

This will return you to the normal, non-SSO login page.

## Required Permissions

The following permissions are required in ThousandEyes in order to configure and use SSO.  For more information on configuring roles, see our [Role Based Access Control explained document](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnLKAS).

### Configuration

In order to configure SSO, a user in a role with the **Edit security & authentication settings** permission needs to configure the settings identified above.

### User permissions

For a user to login using SSO, they must be in a role with the **Login via Single Sign-On** permission.  To restrict users to login via SSO, modify the role of these users to remove the **Login via ThousandEyes login page** permission.  It is important to note that for users with management permissions, it is not possible to remove the Login via ThousandEyes login page permission, in order to prevent lockout when having issues with your Identity Provider.

## Further questions

Contact ThousandEyes Customer Success, should you have further questions on configuration of SSO with ThousandEyes.

