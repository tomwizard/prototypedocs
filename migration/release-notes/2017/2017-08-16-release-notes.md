# Release Notes: 2017-08-16

Welcome to tonight's release!

Continuing our series of posts from our last ThousandEyes Connect event, we've posted a summary of the presentation by PayPal's Viet Nguyen, Senior Manager of Problem and Change Management \(and formerly Senior Manager of Network Engineering/Security/Operations\). Entitled [How PayPal Benchmarks Their Service Providers for Application Delivery](https://blog.thousandeyes.com/how-paypal-benchmarks-service-providers-application-delivery/), the presentation describes the variety of ways that PayPal uses ThousandEyes to monitor such cloud-based infrastructure services as CDN's and DDoS mitigation providers, as well as monitor internal PayPal resources. Viet's discussion of a major DDoS attack that had repercussions for their DDoS mitigation provider and a CDN provider's performance issue demonstrated graphically the risk posed by using cloud services whose resources are shared by many customers.

In our second new blog post, Young Xu discusses the benefits of [Automatic User Provisioning with SCIM](https://blog.thousandeyes.com/automatic-user-provisioning-scim/)--a mechanism for bulk management of users across platforms, including ThousandEyes. If you need to add users to ThousandEyes in bulk, or manage existing users, this post is for you.

And now for the details of tonight's release.

## Cloud Agents

Welcome to our newest Cloud Agent site, Hamburg, Germany! Both IPv4 and IPv6 versions of our Cloud Agent are available.

### IPv6 Cloud Agents

Our newest IPv6 Cloud Agent presence: Melbourne, Australia, joining our existing IPv4 Melbourne Cloud Agent.

### IPv4 Cloud Agents

Manila, in the Republic of the Philippines is our newest IPv4 Cloud Agent. Three cheers in Tagalog for the new addition!

## Endpoint Agent

In order to make managing large numbers of Endpoint Agents easier, we've added a feature to allow editing of multiple Endpoint Agents' settings. On the [Agents tab of the Endpoint Agents Settings page](https://app.thousandeyes.com/settings/agents/endpoint/?section=agents), each Endpoint Agent now has a checkbox. Selecting a box displays the **Edit Selected Agents** button.

IMAGE MISSING

Click the button to display the menu which allows enabling of disabled Agents, disabling of enabled Agents, and deleting of Agents. Click the "-" to select all Endpoint Agents.

Additionally, we've added DNS Server probes to the Network Topology view of the Endpoint Data:

IMAGE MISSING

Mouse over the DNS Server icon to get a tooltip with information on the DNS Server probe.

## BrowserBot

We've made a change to BrowserBot, the component that runs Page Load and Transaction tests. For customers who run Transaction tests on their Enterprise Agents and have used the /tmp directory, you'll now need to use the /var/lib/te-browserbot/uploads directory. As always, watch your disk usage on your Enterprise Agent if you're using this directory!

## Bug fixes & minor features

* Endpoint Agent could display an incorrect Agent Count in Network Topology. Agent Count is now correct in all cases.
* Fixed an issue with Docker-based Enterprise Agents causing BrowserBot to crash when runit is installed.
* Fixed an issue with URL encoding causing BrowserBot to fail.
* Fixed an issue which caused the waterfall of a BrowserBot test to fail to be displayed correctly.
* Fixed an issue which caused the waterfall of a BrowserBot test to temporarily display "Waterfall view not available".

## ​Questions and comments

Have questions on a topic in a blog post? Need advice on provisioning users? Want a Cloud Agent in your hometown? [Send us an email](mailto:support@thousandeyes.com?subject=2017-08-16+Release+Update) and let us know how we can make you more successful.

