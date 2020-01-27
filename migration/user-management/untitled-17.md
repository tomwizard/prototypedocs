# How to configure Single Sign-On with Google G Suite

For the security of your SaaS-based infrastructure and the convenience of users in your organization, the ThousandEyes service offers login via single sign-on \(SSO\). ThousandEyes supports SAML2-based identity providers \(IdPs\) for single sign-on.  In this configuration example, we use Google's G Suite \(formerly Google Apps\) as the identity provider.

There are **two steps** to set up single sign-on:

1. Identity provider configuration, which is done within your identity provider's system \(in this case, Google\)
2. Service provider configuration, which is done within ThousandEyes using one of the following options:

* [Static Configuration]() : requires manual settings of the parameters.
* [Imported Metadata Configuration]() : a metadata file is used to configure the parameters \(recommended method\).
* [Dynamic Configuration]() : a URL is used to configure the parameters \(not yet supported by G Suite SAML\)

## Prerequisites 

Here's what you need to configure single sign-on:

* User in a role with the Edit security & authentication settings permission in ThousandEyes.
* A G Suite administrator account.

## Identity provider \(Google\) configuration  

1. Log in to G Suite using an administrator account
2. Open the Admin Console \([https://admin.google.com](https://admin.google.com/)\)
3. Click on the **Apps \(Manage apps and their settings\)** item 
4. Click on the **SAML apps**
5. Click on the **+** icon to configure a new SAML application IMAGE MISSING
6. Click on **SETUP MY OWN CUSTOM APP** IMAGE MISSING
7. Obtain the Google identity provider information for configuration in ThousandEyes.

    "**Option 1**" is used for [Static Configuration]() of the Service Provider. Copy and paste the SSO URL and IdP Entity ID values into a separate document, and download the certificate. Then click **Next.** Or...

    "**Option 2**" is used for [Imported Metadata Configuration]() of the Service Provider. Download the IDP Metadata file. Then click **Next.**  
   IMAGE MISSING

Enable the ThousandEyes application for all users by clicking on the More Options menu \(three vertical dots\) and selecting **ON for everyone**  
IMAGE MISSING

## Service provider configuration

### Static Configuration

1. Log in to ThousandEyes as a user having a role with the Edit security & authentication settings permission
2. Navigate the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) tab of the Account Settings page
3. In the **Setup Single Sign-On** section:  IMAGE MISSING
   * Check the Enable Single Sign-On box
   * Enter the **Login Page URL** \(SSO URL from previous section - step 7\)
   * Enter a **Logout Page URL** \(Optional\)
   * Enter the **Identity Provider Issuer** \(Entity ID from the previous section - step 7\)
   * Enter the Service Provider Issuer \(SP Entity ID from previous section - step 9; do **not** use the Entity ID from step 7\)
   * Click the **Choose File** button to upload the verification certificate \(certificate downloaded from the previous section - step 
4. Click **Save**
5. Click **Run Single Sign-On Test** to verify the single sign-on works as expected.

### Imported Metadata Configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

* Enter the ThousandEyes application information that will be visible with the user's Google environment.

   **Description** and **Upload logo** are both optional. The ThousandEyes [Media Kit](https://www.thousandeyes.com/media-kit) provides a variety of ThousandEyes logos, which can be scaled down to fit within the required dimensions, if needed. A pre-sized logo is available below the screenshot.  
  IMAGE MISSING

   A ThousandEyes logo, sized to fit with Google Apps:  
  IMAGE MISSING

   Right-click on the image above to save it to your local storage, then upload to Google Apps with the **Choose File** button.

* Enter required ThousandEyes Service Provider details: IMAGE MISSING
* Skip the optional **Attribute Mapping**, and click **Finish:** IMAGE MISSING
  1. Log in to ThousandEyes as a user with a role that has the Edit security & authentication settings permission.
  2. Navigate to the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) tab of the Account Settings page
  3. In the **Setup Single Sign-On** section:
     * Check the **Enable Single Sign-On** box
     * Enter the **Login Page URL** \(SSO URL from previous section - step 7\)
     * Enter a **Logout Page URL** \(Optional\)
     * Enter the **Identity Provider Issuer** \(Entity ID from the previous section - step 7\)
     * Enter the Service Provider Issuer \(SP Entity ID from previous section - step 9; do **not** use the Entity ID from step 7\)
     * Click the **Choose File** button to upload the verification certificate \(certificate downloaded from the previous section - step 7\) IMAGE MISSING   
  4. Click **Save**
  5. Click **Run Single Sign-On Test** to verify the single sign-on works as expected.
  6. Log in to ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
  7. Navigate to the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) tab of the Account Settings page
  8. Check the **Enable Single Sign-On** box.
  9. Click the **Imported Metadata Configuration** button.
  10. Click the **Import File** button and upload the **IDP Metadata File** downloaded at Step 7 of the **Identity Provider configuration** section. The configuration section should populate with the SSO parameters \(see screenshot below\).
  11. Click the **Save** button.
  12. Click **Run Single Sign-On Test** to verify the single sign-on works as expected. IMAGE MISSING IMAGE MISSING

## Logging in using SSO

1. To log in to ThousandEyes, go to [https://app.thousandeyes.com](https://app.thousandeyes.com/) and click the **SSO** link.
2. Input the SSO-enabled email address, and click the **Log In** link.
3. When the Google authorization page appears, enter your email and password, and press the **Sign On** button.
4. You should automatically login to ThousandEyes.

## Returing to standard \(non-SSO\) login page

If your organization discontinues use of SSO at any time, you can return to the login page, by using this special login:

[https://app.thousandeyes.com/login?breakSso](https://app.thousandeyes.com/login?breakSso)

This will return you to the normal, non-SSO login page.  
 

## Required Permissions

The following information describes the permissions required in ThousandEyes in order to configure or use single sign-on.  For more information on configuring roles and permissions, see the ThousandEyes Knowledge Base article [Role-Based Access Control explained](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnLKAS).

### Configuration

In order to configure single sign-on in ThousandEyes, a user in a role with the Edit security & authentication settings permission is required, as described above.

### User permissions

For a user to login using single sign-on, they must be assigned a role with the Login via Single Sign-On permission.  To restrict users to login only via SSO, remove the Login via ThousandEyes login page permission. Note that for users with management permissions, it is not possible to remove the Login via ThousandEyes login page permission. This feature ensures administrators cannot be prevented from logging in when having issues with an identity provider.

