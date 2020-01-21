# Disabling the web server of a Virtual Appliance

ThousandEyes’ Virtual Appliance is normally managed remotely via a web-based administration tool served from the Virtual Appliance, and accessed with a URL of http://&lt;IP\_address\_of\_the\_appliance&gt;. If an organization’s security policy or other factors require that the Virtual Appliance not run its web server, then the web server can be disabled, and the Virtual Appliance managed remotely via SSH using the VA’s command line interface \(CLI\).

## Prerequisites

SSH access to the Virtual Appliance is required both to disable the web server and to manage the Virtual Appliance after the web server is disabled. To configure SSH access to the Virtual Appliance, consult the following ThousandEyes Knowledge Base Articles:

* [Connecting to the ThousandEyes Virtual Appliance using SSH \(Windows\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC)
* [Connecting to the ThousandEyes Virtual Appliance using SSH \(Mac/Linux\)](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC)

**NOTE:** After disabling the web server, the only method for management of most settings on the Virtual Appliance is through SSH access, which requires that at least one public key be uploaded to the Virtual Appliance.  If the private key corresponding to the SSH public key on the Virtual Appliance is lost, access \(and the ability to configure the Virtual Appliance\) is lost.  ThousandEyes recommends the following, prior to disabling the web server:

1. Multiple SSH public keys be loaded on the Virtual Appliance
2. Access is verified using each of the private-public key pairs
3. The private keys are stored in a secure location which will not be forgotten or lost

## Disabling the web server

To disable the web interface in the Virtual Appliance:

1. Access the Virtual Appliance CLI through SSH
2. Execute the command sudo te-va-disable-webserver

## Enabling the web server

To enable the web interface in the Virtual Appliance:

1. Access the Virtual Appliance CLI through SSH
2. Execute the command sudo te-va-enable-webserver

