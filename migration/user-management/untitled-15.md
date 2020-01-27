# How to configure Single Sign-On with Active Directory Federation Services \(ADFS\)

For the security of your SaaS-based infrastructure and the convenience of users in your organization, the ThousandEyes service offers login via single sign-on \(SSO\). ThousandEyes supports SAML2-based identity providers for single sign-on. There are two steps to set up single sign-on: the service provider configuration, which is done within ThousandEyes, and the identity provider configuration, done within your SSO system.  In this configuration example, we use [Microsoft Active Directory Federation Services](https://technet.microsoft.com/en-us/library/hh831502.aspx) \(ADFS\) as the identity provider.

## Prerequisites

Configuration is normally simple. Here's what you need:

* ThousandEyes account assigned a role with the _Edit security & authentication settings_ permission
* A SAML2 authentication provider, in this example [ADFS](https://technet.microsoft.com/en-us/library/hh831502.aspx) using the internal web SSO server at URL: **https://sso.les.local**

## ThousandEyes configuration

Follow these steps to configure your ThousandEyes organization to use single sign-on:

1. Log into ThousandEyes using an account with a role that has the _Edit security & authentication settings_ permission
2. Open the [Account Settings](https://app.thousandeyes.com/settings/account/) page and click the **Security & Authentication** tab
3. Check the **Enable Single Sign-On** box
4. Configure the **Setup Single Sign-On** fields according to the following settings and click the **Save** button:

   | **Login Page URL** | https://sso.les.local/adfs/ls/ |
   | :--- | :--- |
   | **Logout Page URL** | Optional; see note below |
   | **Identity Provider Issuer** | https://sso.les.local/adfs/services/trust |
   | **Service Provider Issuer** | http://www.thousandeyes.com |
   | **Verification Certificate** | See the **Download certificate** section below |

IMAGE MISSING

**IMPORTANT:** Ensure that the **Service Provider Issuer** field reflects the value set by the identity provider in the AudienceRestriction element of the SAML response. Any mismatch, including a protocol mismatch \(http:// vs https://\) will cause the request to be rejected.

**NOTE:** The "**Login Page URL**" and "**Identity Provider Issuer**" field values depend on your SSO server URL. The values provided in the table above should be viewed only as examples.

**NOTE:** The **Logout Page URL** is optional. If used, the URL should point to the page you wish your users to see when logging out of ThousandEyes. 

## Identity Provider configuration  

### Download certificate

1. Login into your Windows Server and open the **ADFS Management** console**.**  IMAGE MISSING
2. Go to **ADFS** &gt; **Service** &gt; **Certificates** and then double click on **Token-signing** certificate to open it. Click on **Details** tab of the certificate: IMAGE MISSING
3. Click on **Copy to File**, this will launch the **Certificate Export Wizard.** Save the certificate in **DER encoded binary X.509** format \(file extension **.CER**\): IMAGE MISSING
4. Log in to **ThousandEyes** and go to the **Security & Authentication** tab of the [Account Settings](https://app.thousandeyes.com/settings/account/) page.
5. In the **Setup Single Sign-On** section, click the **Choose File** button to select and upload the certificate file that you saved in Step 3: IMAGE MISSING
6. Click the **Save** button to save the settings.
7. Go back to **ADFS** server and open **ADFS &gt; Trust Relationships**. Right click **Relying Party Trusts** and select **Add Relying Party Trust:** IMAGE MISSING
8. The **Add Relying Party Trust Wizard** should open. Click **Start** on the welcome page: IMAGE MISSING
9. Select **Enter data about the relying party manually**, as and click **Next**: IMAGE MISSING
10. Enter the string "ThousandEyes" as **Display name** and click **Next**. This is the application name that you will see in the combo box on the SSO login page. IMAGE MISSING
11. Select **AD FS profile** to use SAML 2.0, and click **Next:** IMAGE MISSING
12. Do not make any changes in the **Configure Certificate** page, and click **Next:** IMAGE MISSING
13. On the next page select **Enable support for the SAML 2.0 WebSSO Protocol** checkbox and enter the following string as service URL:

    [https://app.thousandeyes.com/login/sso/acs](https://app.thousandeyes.com/login/sso/acs)Then click **Next**:  
    IMAGE MISSING

14. Enter **Relying party trust identifier** as it was entered at step 4 of the previous ThousandEyes Configuration section \(see **Service Provider Issuer** field\). Ensure that the **Service Provider Issuer** field reflects the value set by the identity provider in the AudienceRestriction element of the SAML response. Any mismatch, including a protocol mismatch \(http:// vs https://\) will cause the request to be rejected. In this configuration we are using [http://www.thousandeyes.com](http://www.thousandeyes.com/).  Then click **Next**: IMAGE MISSING
15. The next step allows configuration of multi-factor authentication. In this configuration multi-factor authentication is not used, so select **I do not want to configure multi-factor authentication for this relying party trust at this time** and click **Next**: IMAGE MISSING
16. The next page offers to create authorization rules. In this configuration authorization rules not used, so select **Permit all users to access this relying party** and click **Next**: IMAGE MISSING
17. Review information in the summary page and click **Next**, then **Close** the wizard. IMAGE MISSING
18. The **Edit Claim Rules** dialog opens, allowing you to define how you will map your internal Active Directory users to ThousandEyes users. At ThousandEyes we expect to see an attribute called “Name ID” and it must be equal to an email as registered in ThousandEyes. For the purpose of this configuration we map **User Principal Name** \(UPN\) into **Name ID**. In other scenarios this could also be an email address. Click **OK** to close the window. IMAGE MISSING
19. Click **Add Rule** in **Edit Claim Rules for ThousandEyes SSO test**, select **Send LDAP Attributes as Claims** and click **Next**: IMAGE MISSING
20. Set **Claim rule name** as **UPN as NameID.** Use **Active Directory** as **Attribute Store**, and on the left side of the table select **User-Principal-Name** matching on the right side **Name ID.** Click the **Finish** button to complete the configuration and close the wizard window: IMAGE MISSING

## Logging in using SSO

You need to create a test user in the Active Directory and ThousandEyes. The UPN of the Active Directory user equals to email of ThousandEyes user. From a Windows workstation, open the Web browser and navigate to the SSO server URL, in our scenario located at: [https://sso.les.local/adfs/ls/idpinitiatedsignon.htm](https://sso.les.local/adfs/ls/idpinitiatedsignon.htm) \(this URL can vary depending on the customer configuration, as explained previously\). Now select ThousandEyes from the list of your service provider applications and click **Sign in**: this will sign you into ThousandEyes application using your local Active Directory credentials and SAML.

If everything works as expected then you can login into ThousandEyes and force use of SSO, this will prevent users from using local ThousandEyes accounts and enforce federated identity. Please note, Organization Admins will still be able to login using their ThousandEyes local account.

In everyday use, to login to ThousandEyes using SSO, go to https://[app.thousandeyes.com](https://app.thousandeyes.com/) and click the **SSO** link

IMAGE MISSING

## Connection details for troubleshooting

The URL [https://app.thousandeyes.com/login?breakSso](https://app.thousandeyes.com/login?breakSso) allows users to stop using SSO and to return to use of local ThousandEyes accounts.

To troubleshoot issues you can enable ADFS trace in Windows Server Event Viewer.  If your single sign-on login fails, verify that certain SAML settings are configured as below:

* Request Compression: Yes
* Assertion: Unsigned
* Response: Signed
* Destination: http://www.thousandeyes.com
* AuthnContextClassRef: PasswordProtectedTransport
* AudienceRestriction: http://www.thousandeyes.com

  _Note: The AudienceRestriction element generated by your identity provider's configuration must match exactly_ the value set for the Service Provider Issuer field in ThousandEyes.  Any mismatch, including a protocol mismatch \(http vs https\) will cause the request to be rejected.

* Recipient: [http://www.thousandeyes.com](http://www.thousandeyes.com/)
* NameID Format: emailAddress
* Role: User
* AssertionConsumerServiceURL: https://app.thousandeyes.com/login/sso/acs

