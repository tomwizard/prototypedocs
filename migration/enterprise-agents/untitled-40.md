# Installing CA Certificates on Enterprise Agents

Enterprise Agents which perform Web Layer tests to targets protected by SSL/TLS \(a target URL beginning with https://, ftps://, or ftp:// when using implicit-mode SSL/TLS\) must validate the SSL server digital certificate and any intermediate certificates returned by the server or fetched by the client. Additionally, Enterprise Agents perform configuration download and data upload to ThousandEyes servers using TLS.  Certificate validation requires that the sequence of certificates “chain” via digital signature back to the trusted root certification authority \(CA\) certificate that signed the previous certificate in the chain. As with most browsers and operating systems, ThousandEyes Enterprise Agents are pre-loaded with the standard X.509 CA certificate store of root CA certificates, which is provided by the [Mozilla NSS project](https://www.mozilla.org/en-US/about/governance/policies/security-group/certs/).

In some environments, the certificate\(s\) returned by the server do not chain back to a CA certificate in the standard certificate store, causing Web Layer tests to produce certificate errors and/or the administrative communication to ThousandEyes to fail. To avoid the errors, customers can add any needed certificates to an Enterprise Agent’s certificate store. The steps to add certificates vary, depending on the type of Enterprise Agent.

Adding root CA certificates cannot be performed on Cloud Agents, due to the shared nature of Cloud Agents. Endpoint Agents are installed on standard operating systems which the customer controls, including control of the certificate stores.

## When to add certificates to an Enterprise Agent

When any Web Layer test \(HTTP Server test, Page Load test, Transaction test or FTP Server test\) or administrative communication from the Agent to ThousandEyes produces a certificate error, review the following scenarios to determine whether a root CA certificate must be added to the Enterprise Agent’s certificate store.

* **Certificates are issued by a private root CA certificate \(internal PKI\)**

   Organizations which run their own public key infrastructure \(PKI\) will issue their own SSL server certificates, intermediate certificates \(if any\), and root CA certificate\(s\) which will not be included in the standard Mozilla root certificate store. The root CA certificate that issued certificates on servers that are the targets of ThousandEyes tests must be added to the Enterprise Agent.

* **Decrypting proxy server**

   If an Enterprise Agent is explicitly configured to use a proxy or if an Agent's web traffic is captured by a transparent proxy \(a proxy that does not require configuration of the client\) and the proxy performs SSL/TLS decryption, then the proxy's signing certificate\(s\) must be added to the Enterprise Agent. Proxy servers which decrypt and inspect data carried by SSL/TLS use a signing certificate to rewrite server certificates. Typically, the proxy signing certificate is not issued by one of the certificates in the standard certificate store. Often, the proxy software generates this certificate.  The decrypting proxy scenario affects both ThousandEyes Web Layer tests and Agent communication to ThousandEyes.

* **Self-signed SSL server certificate**

   A self-signed SSL server certificate will not chain back to a root CA certificate in the Enterprise Agent's standard certificate store. If correctly created, a self-signed certificate can be added to the Enterprise Agent's certificate store to eliminate certificate errors when the Agent performs tests to the server with the self-signed certificate.

 Additionally, if the target of the test does have certificates issued by a Certificate Authority whose root certificate is in the Agent's certificate store, but the target server does not return all needed intermediate certificates, and the customer cannot add the missing certificates on the server, then the intermediate certificate\(s\) can be added to the Enterprise Agent’s certificate store to create the “trust anchor” other than the root CA certificate. However, the customer should take great care in ensuring the veracity of any intermediate certificates, and understand and accept the impact the new trust anchor could have on other tests or aspects of the Agent operation, either in the present or in the future. ThousandEyes does not recommend adding intermediate certificates to an Enterprise Agent's certificate store.

## Converting certificates into PEM format

 To add a CA certificate to an Enterprise Agent, the certificate file must be in [PEM format](https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions). This format can easily be recognized by viewing the file:

```text
-----BEGIN CERTIFICATE-----
...
... (certificate content, base64 encoded)
...
-----END CERTIFICATE-----
```

If your CA certificate is in a format other than PEM format, either use one of the free online certificate converters \([link \#1](https://www.sslshopper.com/ssl-converter.html), [link \#2](https://www.sslchecker.com/ssl_converter) or [link \#3](https://www.thesslstore.com/ssltools/ssl-converter.php)\), or use the commands below to convert your CA certificate into PEM format with the `openssl` command line utility.

Convert a DER file \(.crt, .cer or .der\) to PEM format:

```text
openssl x509 -inform der -in infile -out outfile.pem
```

Convert a PKCS\#12 file \(.pfx or .p12\) to PEM format:

```text
openssl pkcs12 -in infile -out outfile.pem -nodes
```

## Installing on Virtual Appliances

 Log into the Virtual Appliance's web management console, and click on the Network tab:

IMAGE MISSING

In the CA Certificate section, either paste the CA certificate into the **Add CA Certificate** field or browse to your PEM-formatted certificate file:

IMAGE MISSING

If pasting, ensure that whole certificate is pasted into the field, including the "-----BEGIN CERTIFICATE-----" and "-----END CERTIFICATE-----" markers at the beginning and end of the certificate.

Multiple CA certificates may be installed by copying and pasting each certificate, concatenating the certificates in the **Add CA Certificate** field:

IMAGE MISSING

Click the **Save** button at the bottom of the page to complete the operation.  


## Installing on supported Linux Distributions

When installing CA certificates on supported Linux distributions with the Enterprise Agent, CA certificates must be installed in two locations:

1. The system's CA certificate store
2. The NSSDB certificate store in the .pki/nssdb sub-directory of BrowserBot's home directory /var/lib/te-browserbot

 All commands should be executed as root. If logging into the system as a non-privileged user, begin each command with sudo.

The instructions below are provided in two sections for the two sets of supported Linux distributions: 1\) Ubuntu and 2\) Red Hat Enterprise Linux, CentOS and Oracle Linux.

### Ubuntu

 Install the required packages for managing CA certificates:

```text
apt-get install ca-certificates libnss3-tools
```

Copy the certfile file \(in PEM format; see above for conversion information\) onto the system. Then copy it into the /usr/share/ca-certificates directory:

```text
cp MY-CA-CERT.pem /usr/share/ca-certificates/
```

Edit the /etc/ca-certificates.conf file:

```text
nano /etc/ca-certificates.conf
```

Append a line containing only the certfile filename to the end of the file:

```text
#...
#...(existing certificates here)
#...
certfile
```

 Multiple certificate files can be added using multiple lines.

Update the system certificate store using the `update-ca-certificates` command, as shown below, with successful output:

```text
root@my-ubuntu-agent:~# update-ca-certificates
Updating certificates in /etc/ssl/certs... 1 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...

Adding debian:certfile

done.
done.
root@my-ubuntu-agent:~#
```

The system CA certificate store now contains your CA certificate\(s\).

For BrowserBot, first create the directory that will contain the certificate store:

```text
mkdir -p /var/lib/te-browserbot/.pki/nssdb
```

Initialize the certificate store in directory created above:

```text
certutil -N --empty-password -d sql:/var/lib/te-browserbot/.pki/nssdb
```

Add the CA certificate into the newly created certificate store:

```text
certutil \
  -d sql:/var/lib/te-browserbot/.pki/nssdb/ \
  -A \
  -t "C" \
  -n "MY-CA-CERT" \
  -i /usr/share/ca-certificates/MY-CA-CERT.pem
```

Change both the owner and the group of all newly created files and directories to browserbot:

```text
chown -R browserbot.browserbot /var/lib/te-browserbot/.pki
```

Restart the te-browserbot service:

```text
systemctl restart te-browserbot   # Ubuntu 16.04
restart te-browserbot             # Ubuntu 14.04
service te-browserbot restart     # Ubuntu 16.04 and/or 14.04
```

### Red Hat Enterprise Linux, CentOS and Oracle Linux

 Install the required packages for managing CA certificates:

```text
yum install ca-certificates nss-tools
```

Copy the certfile file \(in PEM format; see above for conversion information\) onto the system. Then copy it into /etc/pki/ca-trust/source/anchors/ directory:

```text
cp certfile /etc/pki/ca-trust/source/anchors/
```

Update the system certificate store using the update-ca-trust command:

```text
update-ca-trust extract
```

The system CA certificate store now contains your the CA certificate.

For BrowserBot, first create the directory that will contain the certificate store:

```text
mkdir -p /var/lib/te-browserbot/.pki/nssdb
```

Initialize the certificate store in the directory:

```text
certutil -N --empty-password -d sql:/var/lib/te-browserbot/.pki/nssdb
```

Add the CA certificate to the newly created certificate store:

```text
certutil \
  -d sql:/var/lib/te-browserbot/.pki/nssdb/ \
  -A \
  -t "C" \
  -n "certificate name" \
  -i /etc/pki/ca-trust/source/anchors/certfile
```

On RHEL/CentOS 7 only, change both the owner and the group of all newly created files and directories to browserbot. On RHEL/CentOS 6 this step must be skipped:

```text
chown -R browserbot.browserbot /var/lib/te-browserbot/.pki   # RHEL / CentOS 7 only!
```

Restart the te-browserbot service:

```text
systemctl restart te-browserbot   # RHEL / CentOS 7
restart te-browserbot             # RHEL / CentOS 6
```

## Installing on Docker

The Enterprise Agent Docker image is based on Ubuntu. To install CA certificates on a Docker Enterprise Agent, follow the instructions for [Installing on Ubuntu]().

**IMPORTANT: If you replace the Enterprise Agent container, CA certificates will need to be reinstalled in the system store.**

Docker-based Enterprise Agents can be quickly reinstalled by removing the existing container with the `docker rm` command and redeploying the container by running the same `docker run` command that was used for initial container creation. Provided that the directories on the host created with the `-v` or `--volume` flag from the `docker run` command are not removed after `docker rm` is executed, and that those state directories are reused during the second `docker run` command execution, the replacement Enterprise Agent will retain the identity and general configuration of the previous container. However, replacing the container in this manner will not retain your CA certificates in the system store. The certificates will need to be reinstalled for the system store using the process described in the [Installing on Ubuntu]() section. The certificates installed for the NSSDB/BrowserBot store will be retained, so customers do not need to re-add the certificate\(s\) to the NSSDB certificate store.

