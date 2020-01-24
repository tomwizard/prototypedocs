# HTTP Server test fails with SSL Error

An HTTP Server test or the HTTP Server view of a Page Load test may display the following error message:

```text
SSL certificate problem: unable to get local issuer certificate
```

in the **Error Details** column of the test's Table tab, as shown below.

IMAGE MISSING

If the error occurs when the test is run from either ThousandEyes Cloud Agents or Enterprise Agents, the cause of the error is typically a misconfigured web server which fails to send all required intermediate digital certificates in the certificate chain.

Alternatively, if the web server's SSL server certificate was issued by a non-trusted certification authority \(such as with private/internal PKI\) then the error is due to the Agents missing the certification authority's root certificate.

If the error occurs only from Enterprise Agents which use an SSL-decrypting proxy, the error is due to the Agents missing the proxy's signing certificate.

This article describes the concept of a certificate chain, lists the scenarios which lead to this error and provides instructions to fix the source of the error. Note that more than one of the aforementioned scenarios may be present for a given ThousandEyes Agent. Additionally, a work-around is provided for customers who cannot implement the solution for their scenario.

This error has no relation to errors which can occur in an HTTP Server test when using client certificates for authentication and/or authorization.

## [Certificate chain basics]()

Web servers which provide content through https URLs must use an SSL server certificate in order to demonstrate to the client that the server is the legitimate provider of the content at the requested URL. SSL server certificates are issued by certification authorities \(CAs\) using the the CA's own certificates, and use a cryptographic technique called a digital signature.  Each SSL server certificate is digitally signed by the CA.

SSL server certificates issued by public certification authorities \(such as DigiCert, Comodo or Let's Encrypt\) are typically signed by intermediate certificates, which may themselves be issued and signed by other intermediate certificates belonging to the CA. At the end of a chain of certificates is a root certificate \(also called a root CA certificate\). The root certificate is signed by itself \(unless cross-signed\).

IMAGE MISSING

An example, taken from the Firefox browser's Certificate Viewer, displays the certificate chain associated with the website www.thousandeyes.com:

IMAGE MISSING

This certificate chain is comprised of:

| Root certificate | DigiCert High assurance EV Root CA |
| :--- | :--- |
| Intermediate certificate | DigiCert SHA2 Extended Validation Server CA, issued and signed by the root certificate |
| Server certificate | www.thousandeyes.com, issued and signed by the intermediate certificate |

 The Certificate Viewer also displays the fields in the www.thousandeyes.com certificate. The **Issuer** field is highlighted, showing the common name \(CN\), organizational unit \(OU\), organization \(O\) and country \(C\) values of certificate 2.

Root certificates of public certification authorities are distributed with clients such as web browsers, and are trusted based on the processes which certify the CA's and the security of the client software installation process. Root certificates are stored on each client system in a certificate store.

All other certificates in the chain are normally sent to the client by the server.  With the entire chain of certificates--server, intermediate\(s\) and root--a client computes each of the non-root certificates' digital signatures using the public key contained in the previous \(issuing\) certificate in the hierarchy.  The computed signature is compared to the signature in the certificate.  Matching signatures indicates the certificate was issued by the issuing certificate and has not been altered.

The process is repeated for each certificate, until the computation uses a trusted root's public key for verification. In this way, a chain of trusted certificates can be constructed from the server certificate back to the trusted root certificate, confirming authenticity of the server.

### [Displaying certificate chains]()

A number of ways are available to display the certificates in a chain:

1. Use an online SSL server test tool, for example Qualys' [SSL Server Test](https://www.ssllabs.com/ssltest/). The tool's diagnostics offer confirmation of the diagnosis taken from this article. However, this method will only work with publicly accessible sites.
2. Use the [openssl](https://wiki.openssl.org/index.php/Command_Line_Utilities#s_client) utility or a similar command-line utility \(e.g. [curl](https://curl.haxx.se/)\) which can display a certificate chain. The following command:

   openssl s\_client -connect google.com:443 -servername google.com will display the following certificate chain: 

   ```text
   0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=*.google.com

     i:/C=US/O=Google Inc/CN=Google Internet Authority G2

   1 s:/C=US/O=Google Inc/CN=Google Internet Authority G2

     i:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA

   2 s:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA

    i:/C=US/O=Equifax/OU=Equifax Secure Certificate Authority
   ```

   In the openssl output, the numbered lines start with the server certificate \(\#0\) followed by the intermediate \(\#1\) and the root \(\#2\). The s: indicates the certificate subject, and i: indicates the issuing certificate's subject.

3. Browse to the web server and use the browser's certificate display function. In the browser's address bar, click the lock icon next to the URL, and then navigate to the option to view the certificate.

    The example above used the Certificate Viewer of Firefox. The Chrome and Chromium browsers will produce results most similar to ThousandEyes Page Load and Transaction tests.

## [Chain validation failure scenarios]()

 When some or all of the ThousandEyes Agents assigned to a test display the "SSL certificate problem: unable to get local issuer certificate" error, review the three scenarios below to determine which scenario is present, and the solution or work-around. Note that more than one scenario may be present for a given Agent.

### [Scenario \#1: Web server failing to send intermediate certificate\(s\)]()

The most common cause of the "unable to get local issuer certificate" error is a misconfigured web server which fails to send all of the intermediate certificates with the server certificate, when the client and server perform the SSL/TLS negotiation. The certificate chain cannot be verified back to an "issuer certificate" that is local \(i.e. in the client's certificate store\). A properly configured web server will send all intermediate certificates to the client.

#### Steps to fix

1. Display the certificate chain using one of the methods listed in the [Displaying Certificate Chains](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBCLCA4_Test-fails-with-SSL-Error-SSL-certificate-problem-unable-to-get-local-issuer-certificate#display_chain) section above.  Method 1 is preferable, and can confirm the diagnosis of a missing intermediate certificate\(s\). Use method 2 if the server is not accessible from the internet. Method 3 may obscure the missing certificates due to AIA fetching, as described in the section [No errors with browsers or other ThousandEyes Web Layer tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBCLCA4_Test-fails-with-SSL-Error-SSL-certificate-problem-unable-to-get-local-issuer-certificate#no_errors).
2. Identify which intermediate certificates are not sent by the server. The issuer of the last certificate in the chain is the first missing certificate. Check the issuer of each missing certificate until a root certificate is reached. You may be able to compare the output of Method 1 or 2 with Method 3 to identify the missing intermediate certificates.
3. Download the missing intermediate certificate\(s\) from the issuing CA using the table below or your CA's support site:

   | CA Name | URL for Certificate Downloads |
   | :--- | :--- |
   | Comodo | [https://support.comodo.com/index.php?/Knowledgebase/List/Index/71/](https://support.comodo.com/index.php?/Knowledgebase/List/Index/71/root--intermediates) |
   | DigiCert | [https://www.digicert.com/digicert-root-certificates.htm](https://www.digicert.com/digicert-root-certificates.htm) |
   | GoDaddy | [https://certs.godaddy.com/repository/](https://certs.godaddy.com/repository/) |
   | GlobalSign | [https://support.globalsign.com/customer/en/portal/topics/538410](https://support.globalsign.com/customer/en/portal/topics/538410-root-certificates/articles) |
   | Let's Encrypt | [https://letsencrypt.org/2015/06/04/isrg-ca-certs.html](https://letsencrypt.org/2015/06/04/isrg-ca-certs.html) |
   | Symantec | [https://knowledge.digicert.com/generalinformation/INFO4033.html](https://knowledge.digicert.com/generalinformation/INFO4033.html) |
   | Verisign | [https://www.websecurity.symantec.com/theme/roots](https://www.websecurity.symantec.com/theme/roots) |

4. Install the certificate\(s\) on the web server or SSL termination device, in accordance with the documentation

### [Scenario \#2: Server Certificate issued by non-trusted CA]()

If the web server's certificate is issued by a certification authority that is not one of the publicly trusted CAs, such as an organization's own internal certification authority, then the appropriate root certificate must be added to the Enterprise Agent's certificate store. Root certificates cannot be installed on Cloud Agents.

#### Steps to fix

1. Obtain the root certificate. The root certificate may be obtained in one of a few ways:
   * Request the certificate from the CA administrator, network administrator or similar support group in the organization which owns the CA
   * Export the certificate from a browser or operating system which has the root certificate installed. Consult the documentation for your browser or operating system for instructions on exporting certificates to a file.
   * Check the server certificate's **CA Issuers** field of the Authority Information Access extension for a URL which can be used to download the root certificate. A browser or a command-line utility such as openssl can be used to view the fields of a certificate, as described in the [Displaying certificate chains]() section.
2. Once a file with the root certificate has been created, install the certificate in the Enterprise Agent's certificate store.  Review the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG) for more information on installing a CA's root certificate in an Enterprise Agent.

### [Scenario \#3: Enterprise Agent missing proxy certificate]()

 If the error comes from an Enterprise Agent which uses an SSL-decrypting proxy, then the proxy's signing certificate \(typically a root certificate but can be an intermediate certificate in organizations which have their own CA\) must be added to the Enterprise Agent's certificate store. Proxy signing certificates cannot be installed on Cloud Agents.

Normally, if a proxy's signing certificate is not installed in an Enterprise Agent, the Agent will fail to contact the ThousandEyes collector, which would prevent the Agent from obtaining test configuration information. However, if the proxy and/or other network equipment permit a direct connection between the Agent and ThousandEyes collector, but test traffic must go through the proxy, then this error can be seen.

#### Steps to fix

1. Obtain the proxy signing certificate. The certificate may be obtained in one of a few ways:
   * Request the certificate from the proxy administrator, network administrator or similar support group in the organization which owns the proxy
   * Export the certificate from a browser or operating system which has the proxy certificate installed. Consult the documentation for your browser or operating system for instructions on exporting certificates to a file.
   * Check the server certificate's **CA Issuers** field of the Authority Information Access extension for a URL which can be used to download the proxy certificate. A browser or a command-line utility such as openssl can be used to view the fields of a certificate, as described in the [Displaying certificate chains]() section.
2. Once a file with the proxy certificate has been created, install the certificate in the Enterprise Agent's certificate store.  Review the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG) for more information on installing a proxy signing certificate in an Enterprise Agent.

## [Work-arounds]()

If the steps to correct any of the scenarios cannot be implemented, such as a web server configuration cannot be corrected because the web server is not maintained by your organization, then the verification check can be turned off for an HTTP Server test.  In the Test Settings page, select the HTTP Server test or Page Load test, and uncheck the **Verify SSL certificate** box under the test’s Advanced Settings tab.

IMAGE MISSING

Unchecking the **Verify SSL certificate** box will prevent the Agents assigned to the test from performing verification of the server certificate.

A work-around for missing intermediate certificates is to configure an Enterprise Agent with the intermediate certificate, using the same instructions as for configuring the Agent with a root certificate. However, the drawback to this approach is that the verification can fail if either the intermediate or server certificate is changed, rendering the copy on the Agent invalid.

## [No errors with browsers or other ThousandEyes Web Layer tests]()

If the target web server does not send one or more intermediate certificates, then a ThousandEyes HTTP Server test will fail with the "unable to get local issuer certificate" error but a Page Load or Transaction test may show no error message. Additionally, the site may be accessed using a web browser without error.

Most modern browsers can retrieve a missing intermediate certificate \(but never a root certificate\) using information contained in the previous certificate of the chain \(server certificate or previous intermediate certificate\).  Specifically, the TLS extension "Authority Information Access" \(AIA\) provides browsers with a URL to download the missing certificate from a server belonging to the certificate authority. This retrieval is called AIA fetching. Because ThousandEyes Page Load and Transaction tests emulate browser behavior, these tests will perform AIA fetching. While AIA fetching of certificates allows for avoiding the error, performance is degraded due to the additional request\(s\) for certificate data, which occur prior to loading the actual web site content.

Similarly, if the cause is a ThousandEyes Agent missing a non-public root CA certificate or proxy signing certificate \(scenarios \#2 or \#3, above\) then a ThousandEyes HTTP Server test will fail with the "unable to get local issuer certificate" error but the site may be accessible via web browser without error. The reason is likely that the certificate store of the user's browser or operating system has been configured with the necessary root or signing certificate.

Another reason for differing results may be that the web server is configured to provide different certificate chains based on  cryptographic cyphers negotiated with the client. The server may respond with one chain of certificates to an HTTP Server test, and a different chain for Page Load and Transaction tests because the clients are different.

