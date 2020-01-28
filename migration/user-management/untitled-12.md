# How to configure Single Sign-On with Bitium

For the security of your SaaS-based infrastructure and the convenience of users in your organization, the ThousandEyes service offers login via single sign-on \(SSO\). ThousandEyes supports SAML2-based identity providers for single sign-on. There are **two steps** to set up single sign-on:

1. [Identity provider configuration](), done within your SSO system \(in this article we use [Bitium](https://www.bitium.com/)\)
2. Service provider configuration, which is done within ThousandEyes using one of the following options:

* [Static Configuration]() : requires manual settings of the parameters.
* [Imported Metadata Configuration]() : a metadata file is used to configure the parameters.
* [Dynamic Configuration]() : a URL is used to configure the parameters.

## Prerequisites

Configuration is normally simple. Here's what you need:

* ThousandEyes account assigned a role with the _Edit security & authentication settings_ permission
* A SAML2 identity provider \(in this example, [Bitium](https://www.bitium.com/)\)

## Identity provider configuration  

1. Log in to the Bitium Admin Console, and go to **Manage ThousandEyes &gt; Manage Apps**  IMAGE MISSING
2. If the ThousandEyes app is not installed, click the **Add an App** button, search for **ThousandEyes** and click the **ThousandEyes app** to get it installed. If prompted, select **Single Sign-On with SAML Authentication**. IMAGE MISSING
3. From the **Manage ThousandEyes &gt; Manage Apps** page, select ThousandEyes from the list of installed apps, then click on the **Single Sign-On** tab and select **SAML Authentication** from the drop-down menu. IMAGE MISSING
4. The following screenshot highlights the values which will be used in the ThousandEyes **Security & Authentication** tab, as explained in the following sections. Copy these values. IMAGE MISSING
5. Depending on the type of single sign-on configuration that you would like to use, download the related file:

* for [ThousandEyes Static Configuration](): download the **X.509 Certificate** file.
* for [ThousandEyes Imported Metadata Configuration](): download the **Metadata XML** file.
* for [ThousandEyes Dynamic Configuration]() : annotate the **Metadata URL.**

## ThousandEyes \(service provider\) configuration

### Static Configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
2. Open the [**Account Settings**](https://app.thousandeyes.com/settings/account/) page and select the **Security & Authentication** tab.
3. Check the **Enable Single Sign-On** box.
4. Click the **Static Configuration** button.
5. Configure the **Setup Single Sign-On** fields according to the following settings and click the **Save** button.  
  

   | **Login Page URL** | The **Login URL** from Step 4 in the **Identity Provider configuration** section above |
   | :--- | :--- |
   | **Logout Page URL** | The **Logout URL** from Step 4 in the **Identity Provider configuration** section above |
   | **Identity Provider Issuer** | The **Entity ID** from Step 4 in the **Identity Provider configuration** section above |
   | **Service Provider Issuer** | https://app.thousandeyes.com |
   | **Verification Certificate** | The X.509 certificate downloaded at Step 5 in the **Identity Provider configuration** section above |

6. To test the configuration use the instructions provided [here](). IMAGE MISSING

**IMPORTANT:** Ensure that the **Service Provider Issuer** field reflects the value set by the identity provider in the AudienceRestriction element of the SAML response. Any mismatch, including a protocol mismatch \(http vs https\) will cause the request to be rejected.

**NOTE:** The **Logout Page URL** is optional. If used, the URL should point to the page you wish your users to see when logging out of ThousandEyes.

### Imported Metadata Configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
2. Open the [**Account Settings**](https://app.thousandeyes.com/settings/account/) page and click the **Security & Authentication** tab.
3. Check the **Enable Single Sign-On** box.
4. Click the **Imported Metadata Configuration** button.
5. Click the **Import File** button and upload the **Metadata XML File** downloaded at Step-5 of the **Identity Provider configuration** section. The configuration section should populate with the SSO parameters \(see screenshot below\).
6. Click the **Save** button.
7. To test the configuration use the instructions provided [here](). IMAGE MISSING

### Dynamic Configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission.
2. Open the [**Account Settings**](https://app.thousandeyes.com/settings/account/) page and click the **Security & Authentication** tab.
3. Check the **Enable Single Sign-On** box.
4. Click the **Dynamic Configuration** button.
5. In the **IdP Metadata URL** box paste the **Metadata URL** obtained at Step-5 of the **Identity Provider configuration** section. The configuration section should populate with the SSO parameters \(see screenshot below\).
6. Click the **Save** button.
7. To test the configuration use the instructions provided [here](). IMAGE MISSING

### Test the configuration

1. In the ThousandEyes **Security & Authentication** tab, click the **Run Single Sign-On Test** button: IMAGE MISSING
2. If the SSO is configured properly, you should get a message indicating success, as shown in this screenshot: IMAGE MISSING

### Logging in using SSO

1. To log in to ThousandEyes, go to [https://app.thousandeyes.com](https://app.thousandeyes.com/) and click the **SSO** link.
2. Input the SSO-enabled email address, and click the **Log In** link.
3. When the Bitium authorization page appears, enter your email and password, and press the **Sign On** button.
4. You should automatically logging into ThousandEyes.

**NOTE:** You can also log in to ThousandEyes using the App Dashboard provided in the Bitium Admin Console.

### Connection details for troubleshooting

If your single sign-on login fails, verify that certain SAML settings are configured as below:

* Request Compression: Yes
* Assertion: Unsigned
* Response: Signed
* Destination: http://www.thousandeyes.com
* AuthnContextClassRef: PasswordProtectedTransport
* AudienceRestriction: https://app.thousandeyes.com 

   _Note: The AudienceRestriction element generated by your identity provider's configuration must match exactly_ the value set for the Service Provider Issuer field in ThousandEyes.  Any mismatch, including a protocol mismatch \(http vs https\) will cause the request to be rejected.

* Recipient: http://www.thousandeyes.com
* NameID Format: emailAddress
* Role: User
* AssertionConsumerServiceURL: https://app.thousandeyes.com/login/sso/acs

