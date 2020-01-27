# Release Notes: 2017-08-30

Welcome to tonight's release!

In new blog articles, Young Xu's article [Automatic User Provisioning with SCIM](https://blog.thousandeyes.com/automatic-user-provisioning-scim/) describes the benefits of using SCIM to provision users in ThousandEyes. If you've got large numbers of users to add to ThousandEyes, this article is for you.

And now without further ado...

## Update your whitelists!

Starting on September 12, 2017, we will be bringing online a new and improved system to which Enterprise Agents will upload data. The new system’s domain name is data1.agt.thousandeyes.com and its IP address is 192.150.160.203. This change will affect customers who have security devices with configurations \(firewall rules, web proxy rules, router ACL’s\) which explicitly permit \("whitelist"\) Enterprise Agent connections to ThousandEyes. Currently the connections go to c1.thousandeyes.com, at IP address 192.150.160.17. Customers with whitelists should add the new information to the existing configurations \(or if possible whitelist the entire ThousandEyes network, 192.150.160.0/24\).

At some later date following the next release on 9/14, we will push changes to the Enterprise Agents to use both c1.thousandeyes.com/192.150.160.17 and data1.agt.thousandeyes.com/192.150.160.203. If customers do not update their whitelists, Enterprise Agents will appear as online, but the Agents will not be able to upload test data.

## IPv6 Cloud Agents

Our newest IPv6 Cloud Agent is Helsinki, Finland. Raise your glass of glögi in a toast!

## Agent to Agent tests

In a bidirectional Agent to Agent test \(**Direction** setting is "Both Directions\) where an Enterprise Agent is NAT'ed, it is possible that the source IP address in the outbound direction is not the same as the destination IP address in the inbound direction. Previously we only displayed the Enterprise Agent's icon with the source IP address. Now we display two Enterprise Agent icons to indicate different IP addresses, as in the example below, with the Enterprise Agent "Dallas, TX NAT":

IMAGE MISSING

## Bug fixes & minor features

* Added units of Mbps and Gbps for Throughput metric in Views and widgets.
* Fixed an Endpoint Agent issue which occurred when exiting Internet Explorer 9.
* Fixed an issue preventing selection of a test when creating an Alert Rule.
* Corrected issues which could occur when setting an Alert Rule as a default.
* Clicking the Settings icon of an embedded widget no longer returns a "Dud Link" page \(HTTP status code 404\).
* Configuring the Custom Headers field in a Page Load test no longer results in merging of the text if multiple headers are specified.
* Updated the number of projected cloud units shown in the Usage tab of the Account Settings Page to be consistent with numbers shown in the API.
* Fixed an issue which caused import of a SAML Metadata XML file to not parse the SingleSignOnService correctly.
* Fixed an issue which caused SCIM v2 API endpoint to incorrectly parse names during user creation.

## ​Questions and comments

Talk to the 'Eyes! [Send us an email](mailto:support@thousandeyes.com?subject=2017-08-30+Release+Update) and let us know how we can make you more successful.

