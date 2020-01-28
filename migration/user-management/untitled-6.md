# How to configure Single Sign-On with PingOne

For the security of your SaaS-based infrastructure and the convenience of users in your organisation, the ThousandEyes service offers login via single sign-on \(SSO\). ThousandEyes supports SAML2-based identity providers for single sign-on. There are **two steps** to set up single sign-on:

1. [Identity Provider configuration](), done within your SSO system \(in this article we use [PingOne](https://www.pingidentity.com/en/products/pingone.html)\)
2. Service Provider configuration, which is done within ThousandEyes using one of the following options \(the last two are normally easier and quicker to use\):
   * [Static Configuration](): requires manual settings of the parameters.
   * [Imported Metadata Configuration](): a metadata file is used to configure the parameters.
   * [Dynamic Configuration](): a URL is used to configure the parameters.

## Prerequisites

Configuration is normally simple. Here's what you need:

* ThousandEyes account assigned a role with the _Edit security & authentication settings_ permission
* A SAML2 authentication provider \(in this example, [PingOne](https://www.pingidentity.com/en/products/pingone.html)\)

## Identity Provider configuration 

1. Log in to the PingOne [Admin Console](https://admin.pingone.com/web-portal/), and go to the **Application Catalog** tab of the **Applications** page.
2. Search for "**Thousand Eyes**" and click on the logo to expand the details. IMAGE MISSING
3. Click the **Setup** button to open the configuration panel.
4. If you want to use ThousandEyes [Static Configuration](), click on the **Download** button to save the **Signing Certificate** on your local drive. IMAGE MISSING
5. Again, only in case of ThousandEyes [Static Configuration](), copy the value of the **idpid** field of the query string, found at the end of the **Initiate Single Sign-On \(SSO\) URL**. Copy the string starting after the '=' character \(see image below as example\)

    **NOTE**: the **idpid** is a unique identifier generated when the ThousandEyes application is added.  If the ThousandEyes application is removed from the PingOne and re-added, the **idpid** will change, and require you to reconfigure per these steps\). Append the **idpid** string to this URL: **https://sso.connect.pingidentity.com/sso/idp/SSO.saml2?idpid=**

   An example of a complete URL:  
    _https://sso.connect.pingidentity.com/sso/idp/SSO.saml2?idpid=de8e56ff-fdb1-4a22-8963-fbcff6952a89_    
    IMAGE MISSING

6. At the bottom of the page click on **Continue to Next Step** to display the connection details: IMAGE MISSING
7. Click the **Continue to Next Step** button to display the attribute mapping. IMAGE MISSING
8. Click the **Continue to Next Step** button to display the application customization: IMAGE MISSING
9. Click the **Save & Publish** button ****to review the configuration: if you are using the [Imported Metadata Configuration](), then download the **SAML Metadata** file. IMAGE MISSING
10. Click the **Finish** button to complete the application setup.
11. Go to the **Users &gt; User Groups** tab and click on the **Edit** button of the **Users@directory** group name. IMAGE MISSING
12. Check the **ThousandEyes \(SSO\)** check-box and click the **Save** button.
13. Go to **Dashboard** and click the **Your PingOne dock URL** link. IMAGE MISSING
14. The ThousandEyes application should be available in the dashboard when you go to your PingOne dock URL page: IMAGE MISSING
15. To add new users to the Signgle Sign-On, go to the **Users** page in PingIdentity and click the **Add Users** button. The new user can be "**created**" filling all the information or "**invited**" just providing the email address.  IMAGE MISSING

##  ThousandEyes static configuration

Follow these steps to configure your ThousandEyes organisation to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
2. Open the [**Account Settings**](https://app.thousandeyes.com/settings/account/) page and click the **Security & Authentication** tab.
3. In the **Setup Single Sign-On** section, check the **Enable Single Sign-On** box.
4. Click the **Static Configuration** button.
5. Configure the **Setup Single Sign-On** fields according to the following settings and click the **Save** button.
6. To test the configuration use the instructions provided [here.]()

| **Login Page URL** | Use the URL created at **Step-5** of the Identity Provider configuration section. |
| :--- | :--- |
| **Logout Page URL** | https://app.thousandeyes.com/login/sso |
| **Identity Provider Issuer** | https://pingone.com/idp/thousandeyes |
| **Service Provider Issuer** | https://www.thousandeyes.com |
| **Verification Certificate** | Use the certificate file downloaded at **Step-4** of the Identity Provider configuration section. |

IMAGE MISSING

**IMPORTANT:** Ensure that the **Service Provider Issuer** field matches the "service provider entityId" provided by PingOne. Any mismatch, including a protocol mismatch \(http vs https\) will cause the request to be rejected.

**NOTE:** The **Logout Page URL** is optional. If used, the URL should point to the page you wish your users to see when logging out of ThousandEyes.   

## ThousandEyes Imported Metadata Configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
2. Open the [**Account Settings**](https://app.thousandeyes.com/settings/account/) page and click the **Security & Authentication** tab.
3. Check the **Enable Single Sign-On** box.
4. Click the **Imported Metadata Configuration** button.
5. Click the **Import File** button and upload the **Metadata XML File** downloaded at Step-9 of the **Identity Provider configuration** section. The configuration section should populate with the SSO parameters \(see screenshot below\).
6. Click the **Save** button.
7. To test the configuration use the instructions provided [here.]() IMAGE MISSING

## ThousandEyes Dynamic Configuration

 At the moment PingOne does not support dynamic configuration, so the most automated way to configure SSO is using the [Imported Metadata Configuration]() option.

## Test the configuration in PingIdentity

1. Log out of ThousandEyes.
2. Go to **Dashboard** and click the **Your PingOne dock URL:** IMAGE MISSING
3. Click the **ThousandEyes** logo, you should automatically login into ThousandEyes. IMAGE MISSING

## Test the configuration in ThousandEyes

1. In the ThousandEyes **Security & Authentication** tab, click the **Run Single Sign-On Test** button. This button is present in all the configuration types \(Static, Imported Metadata and Dynamic\), but it only needs to be checked once for the selected configuration. IMAGE MISSING
2. If the SSO is configured properly, you should get a message indicating success, as shown in this screenshot:  IMAGE MISSING

##  Logging in using SSO

1. To log in to ThousandEyes, go to [https://](https://app.thousandeyes.com/)[app.thousandeyes.com](https://app.thousandeyes.com/)[ ](https://app.thousandeyes.com/)and click the **Single Sign-On** link. IMAGE MISSING
2. Input the SSO-enabled email address, and click the **Log In** button.
3. When the PingOne authorization page appears, enter your email and password, and press the  **Sign On** button, you should automatically log into ThousandEyes. IMAGE MISSING
4. Alternatively, users can access the ThousandEyes application through the user's PingOne dashboard. Please refer to the "**Test the configuration in PingIdentity"** section presented above.

## Metadata details for troubleshooting

If your single sign-on login fails, verify that certain SAML settings are configured as below:

* Request Compression: Yes
* Assertion: Unsigned
* Response: Signed
* Destination: https://www.thousandeyes.com
* AuthnContextClassRef: PasswordProtectedTransport
* AudienceRestriction: [https://www.thousandeyes.com](http://www.thousandeyes.com/)

   _Note: The AudienceRestriction element generated by your identity provider's configuration must match exactly_ the value set for the Service Provider Issuer field in ThousandEyes.  Any mismatch, including a protocol mismatch \(http vs https\) will cause the request to be rejected.

* Recipient: [https://www.thousandeyes.com](http://www.thousandeyes.com/)
* NameID Format: emailAddress
* Role: User
* AssertionConsumerServiceURL: [https://app.thousandeyes.com/login/sso/acs](https://app.thousandeyes.com/login/sso/acs)

