# Secure access to ThousandEyes Appliances

Management of ThousandEyes' Virtual Appliance and Physical Appliance is done using a web-based management interface. Connections to the management interface are secured with the Transport Layer Security \(TLS\) protocol, as indicated by the https in the URL used to access the interface. HTTPS/TLS encrypts the network connection between browser and Appliance, guaranteeing data privacy and data integrity. Additionally, TLS provides a mechanism for the user to verify the identity of the server. Many organizations' security policies require that web-based management be done using a TLS connection.

In order to access an Appliance using TLS, configuration of the Appliance, the user's browser, or both is required, depending on the level of security required. This article explains how to access the Appliance in the default configuration, how to replace the default configuration by configuring the Appliance's web server with a digital certificate, and lists steps which may be required after configuring the Appliance with a digital certificate.

## [Accessing the Appliance with the default configuration]()

 The web management interface of the ThousandEyes Virtual Appliance or Physical Appliance are accessed by an https URL. Access via http URL will be redirected to the HTTPS. For initial configuration, the HTTPS connection to the web interface is done using the Appliance's IP address, for example, https://192.168.1.100

IMAGE MISSING

Normally, accessing the Appliance web interface with the IP address will cause most browsers to generate a security warning because the pre-installed digital certificate used by the Appliance's web server is a self-signed certificate. Chrome, for example, displays the message **NET::ERR\_CERT\_AUTHORITY\_INVALID**, indicating that the certificate authority \(itself\) is not acceptable as an issuer of trusted root certificates:

IMAGE MISSING

Other browsers will display similar warnings.

For the first connection to the Appliance, users must allow the browser to continue to the site. In the example above using Chrome, clicking the **Advanced** button will display a link which allows the user to proceed to the site. Other browsers may display similar buttons, or request explicit exemption be made for the site.

For customers planning to add a valid server certificate, temporarily bypassing the warning will suffice. For customers who wish to use the self-signed certificate indefinitely, configuring the user's browser with a permanent exemption may be desirable. Consult your organization's security polices, and browser's documentation or contact ThousandEyes Customer Success if needed, to allow the browser to proceed to the Appliance login page.

Once the browser has permitted a connection to the site, the login page for the web management will appear, likely with the browser displaying additional warnings, such as Chrome, below, displaying Not Secure in the address bar:

IMAGE MISSING

Users may now log in to the Appliance's web management with the default username \("admin"\) and password \("welcome"\). Depending on the type of browser and configuration settings, the warnings may or may not reappear upon subsequent connections, while the Appliance uses its default self-signed certificate. Additionally, users should remove any browser exceptions for bypassing certificate warnings once they are not needed.

**IMPORTANT:** Because the initial connection will be made in a way which does not utilize the HTTPS ability to verify the server identity, initial configuration should be done in a secure environment. The Appliance should not be accessible from the public Internet for initial configuration. Organizations with stringent security requirements may wish to perform initial configuration in an isolated network, such as a virtual network or "host-only" network created within a hypervisor or similar virtualization software.

**NOTE:** The username will always be "admin" but the Appliance will require a password change when the initial configuration of the Appliance is done.

## [Configuring the Appliance with a valid server certificate]()

 Valid server certificates are those issued \(or "signed"\) by certificate authorities \(CAs\) which browsers trust. To obtain a valid server certificate from a CA, a certificate signing request \(CSR\) must be created then submitted to the CA. Upon receiving a CSR, a CA will determine whether to issue a certificate based on the requestor providing proof of identity and other factors. Once the CA creates and signs the certificate, the certificate is issued to the requestor. Many [public certificate authorities](https://ccadb-public.secure.force.com/mozilla/CACertificatesInFirefoxReport) provide this service for a fee or for free. Additionally, some organizations run their own certificate authority for private use. Consult your network or security administrator for your organization's policies on TLS certificate issuance for web servers.

The ThousandEyes Appliance provides two methods for configuring a server certificate, both of which require an external \(public or private\) certificate authority:

1. [Uploading a certificate and private key created without using the Appliance web interface]()
2. [Creating and downloading a CSR using the web interface, then uploading the certificate via the web interface]()

 The Appliance does not currently support creation of a CSR by uploading a public and private key pair generated independently from the web interface.

### [Uploading a certificate and private key]()

If users wish to perform all tasks in the certificate issuance process without using the Appliance's web interface, then users can simply upload the certificate and its associated private key via the web interface. The certificate and private key must be in separate files, in [PEM format](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG_Installing-CA-Certificates-on-Enterprise-Agents#converting). If the server certificate requires one or more intermediate certificates to be bundled, then concatenate all certificates in PEM format into a single file, with the server certificate first, followed by the intermediate certificate that issued the server certificate. If more than one intermediate certificate is present in the chain of trust, place the first intermediate certificate \(the intermediate that issued the server certificate\) after the server certificate, then the second intermediate after the first.

To upload the file with the certificate\(s\) and the associated private key, use the following procedure:

1. Log into the Appliance web interface  Use https://&lt;IP\_address\_of\_Appliance&gt; in a web browser, and continue through any security warnings, as described in the section [Accessing the Appliance with the default configuration]().   
2. Click **SSL Settings** in the menu at left   
3. Click the **Import Private** Key button   
4. Navigate to the private key file on the local computer using the file browser, and select the file   
5. If the certificate is protected with a passphase, enter the phrase in the **Passphrase** field; otherwise leave the field blank   
6. Click the **Import Certificate** button   
7. Navigate to the certificate file on the local computer using the file browser, and select the file   
8. Click the **Submit SSL Certificate** button

 Installing the certificate requires rebooting the Appliance. A modal will appear, asking whether the user wants to reboot the appliance now. After rebooting, the **Installed SSL Certificate** section now displays information about the installed server certificate.

### [Creating a CSR in the web interface]()

In the Appliance web interface, users can create and download a CSR and then use that CSR to obtain the server certificate, and then upload the certificate. If the server certificate requires one or more intermediate certificates to be bundled, then concatenate all certificates in PEM format into a single file, with the server certificate first, followed by the intermediate certificate that issued the previous certificate.

The Appliance generates and retains the corresponding private key as long as the CSR that generated the private key is active in the web interface.

Consult your network or CA administrator for more information on the values needed for generating a CSR.

To create a CSR in the Appliance's web interface, use the following procedure:

1. Log into the Appliance web interface  Use https://&lt;IP\_address\_of\_Appliance&gt; in a web browser, and continue through any security warnings, as described in the section [Accessing the Appliance with the default configuration]().   
2. Click **SSL Settings** in the menu at left   
3. Fill out the fields in **Generate CSR** form  
    Fields with a red \* are required.

   **NOTE:** Subject Alternative Names is not a required field, but if left blank be certain that:

   * The Common Name field contains a domain name, if required for access AND
   * Your CA will populate the SAN field with the value of the Common Name OR
   * Your certificate issuance process includes adding SAN values \(domain names, hostnames and/or IP addresses\) subsequent to the CSR generation, via CSR request attributes

4. Click the **Create CSR** button

 The SSL Settings page will now display the CSR's configuration in the **Outstanding CSR** field. A private key associated with this CSR has been generated and will be stored until either a certificate with the associated public key is uploaded, or the pending CSR is deleted.

Once the certificate is created, place the certificate file in [PEM format](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG_Installing-CA-Certificates-on-Enterprise-Agents#converting) on the local computer, then upload the certificate to the Appliance using the following procedure:

1. Log into the Appliance web interface
2. Click the SSL Settings section in the menu at left
3. Click the **Import Certificate** button
4. Navigate to the certificate file on the local computer using the file browser, and select the file
5. Click the **Submit SSL Certificate** button

Installing the certificate requires rebooting the Appliance. A modal will appear, asking whether the user wants to reboot the appliance now. After rebooting, the **Installed SSL Certificate** section now displays information about the installed server certificate.

## [Accessing the Appliance with a valid certificate]()

 Once a valid server certificate has been Installed, the Appliance can be accessed with an https:// URL using any of the names \(or IP addresses\) in the Subject Alternative Names field. For example, if the CSR form in the Appliance contained:

IMAGE MISSING

then a browser could use the following URLs securely:  
 

https://test.stg.thousandeyes.com  
https://test-teva.stg.thousandeyes.com  
https://10.1.1.100  
https://192.167.150.100

**NOTE:** To use names such as test.stg.thousandeyes.com in URLs, the browser must be able to resolve the name to an IP address through DNS, local host files or some other name resolution service. Consult your network administrator to ensure that names chose for your certificate have the necessary configuration in your organization's name service.

## [Deleting a certificate or CSR]()

Once a certificate is uploaded, the certificate and its associated private key can be removed by clicking the **Remove Certificate** button.

IMAGE MISSING

Removing the certificate requires rebooting the Appliance. A modal will appear, asking whether the user wants to reboot the appliance now. Upon rebooting, the Appliance will automatically re-install the original, self-signed certificate.

Additionally, a new certificate can be uploaded to replace a previously uploaded certificate. The Appliance will always retain the original, self-signed certificate regardless of the number of user-uploaded certificates.

Once a CSR is created, removing the current CSR can be done by clicking the red X in the Outstanding CSR field. The associated private key is also removed.

