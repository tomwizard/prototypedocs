# How to configure Single Sign-On \(SSO\): Metadata

For the security of your SaaS-based infrastructure and the convenience of users in your organization, ThousandEyes offers login via single sign-on \(SSO\). ThousandEyes supports [SAML 2.0](https://en.wikipedia.org/wiki/SAML_2.0)-based SSO. 

##  **ThousandEyes' side configuration:**

Within ThousandEyes, SSO configuration is done in the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) section under the [Organization tab](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnGKAS_Working-with-Account-settings#organization-tab) of Account Settings. The following information from your Identity Provider \(IdP\) must be supplied to ThousandEyes in order to get SSO working:

* Login URL for your SAML provider
* Logout URL for your SAML provider \(optional\)
* Identity Provider Issuer
* Service Provider Issuer
* Verification certificate\(s\).

 There are three methods to set these options:

* **Static Configuration**
  * Each parameter needs to be supplied manually, including verification certificate\(s\). 
* **Imported Metadata Configuration**
  * ThousandEyes will parse a user-supplied metadata XML file and load the parameters.
* **Dynamic Configuration**
  * ThousandEyes will parse a metadata file from a provided URL on demand \(for each user login\).  

##  **Identity Provider's side configuration:**

 If XML metadata loading is supported by your Identity Provider, you can use our Service Provider \(SP\) metadata file available at the following URL:  
[https://app.thousandeyes.com/saml-metadata](https://app.thousandeyes.com/saml-metadata)

Alternatively, manual configuration of your Identity Provider can be performed. The following information lists the characteristics of ThousandEyes as a SAML Service Provider:

* ThousandEyes supports both Service-Provider-initiated \(i.e. ThousandEyes login page initiated\) and Identity-Provider-Initiated \(i.e. clicking a link from inside the customer portal\) based logins
* ThousandEyes post-back URL: [https://app.thousandeyes.com/login/sso/acs](https://app.thousandeyes.com/login/sso/acs)
* SAML Assertion NameID \(unspecified or emailAddress format\): Email address of user to be authenticated \(must be already registered in ThousandEyes\). 
  * If a valid email address \(as registered in ThousandEyes\) is not found in the NameID field, the assertion will be parsed for additional name claims.
* Connection details:
  * Request Compression: Yes
  * Assertion: Unsigned
  * Response: Signed
  * Destination: https://app.thousandeyes.com
  * **AuthnContextClassRef: PasswordProtectedTransport**
  * Audience Restriction: https://app.thousandeyes.com

     _Note: When using static configuration, the Audience Restriction configured in your Identity Provider's configuration **must** **exactly** **match** the value set for the Service Provider Issuer field in ThousandEyes.  Any mismatch, including a protocol mismatch \(http:// vs https://\) and trailing slashes will cause the request to be rejected._  
     _When using dynamic or imported metadata configurations, make sure you configure your IdP to use **https://app.thousandeyes.com** as the Audience Restriction._

  * Recipient: https://app.thousandeyes.com
  * AssertionConsumerService URL: [https://app.thousandeyes.com/login/sso/acs](https://app.thousandeyes.com/login/sso/acs)

##  **Key points in ThousandEyes assertion validation:**

* ThousandEyes parses the email \(our primary identifier of users\) on the SamlResponse created by your Identity Provider. We require that you configure your IdP to supply a registered user's email address in one of the following attributes of the assertion \(failure to find a registered email address in any of these attributes will break the SSO process\):  
  * NameID in the format "urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified”
  * NameID in the format "urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress"
  * Attribute "emailaddress" \(http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress\)
  * Attribute "name" \(http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name\)
  * Attribute "Email"
* Make sure that at least one of the uploaded verification certificates is an **exact match** of what is being used to sign the SamlResponse assertion. 
* Verify that the AudienceRestriction configured in your IDP is an **exact match** of the service provider issuer string within ThousandEyes SSO configuration.

##  Vendor Specific Configurations

ThousandEyes supports use of any SAML 2.0-based identity provider for single-sign on. Vendor-specific configuration examples can be found in the following articles: 

* [**How to configure Single Sign-On with Okta**](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnKKAS)
* [**How to configure Single Sign-On with miniOrange**](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnMKAS)
* [**How to configure Single Sign-On with PingOne**](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnJKAS)
* [**How to configure Single Sign-On with OneLogin**](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnHKAS)

