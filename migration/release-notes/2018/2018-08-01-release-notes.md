# Release Notes: 2018-08-01

Welcome to tonight's release! New features, bug fixes, some important announcements and more, tonight.

Summer is really flying by, which may be a relief to some after experiencing heat wave upon heat wave. Here in San Francisco, we don't actually get summer, but we're still perspiring away, hard at work to produce four new articles for the ThousandEyes blog.

DevOps Engineer Shashank Sahni has forged an exhaustive history: [Evolution of Infrastructure Monitoring at ThousandEyes Engineering](https://blog.thousandeyes.com/evolution-infrastructure-monitoring-thousandeyes-engineering/) describes the technologies and techniques our Operations team has employed over the years to maintain a high level of availability for the ThousandEyes service. If you've ever been curious how the monitors monitor themselves, this article is for you.

In our second blog post of this release, Senior Product Marketing Manager Angelique Medina sweats the details, strengths and weaknesses of application performance monitoring versus the "network intelligence" approach of ThousandEyes, in her post [APM + ThousandEyes: Better Together](https://blog.thousandeyes.com/apm-thousandeyes-better-together/).

For number three, we go under the sea, where temps are cooler, and content providers the new rulers of capacity. Our Technical Marketing Manager, Ameet Naik, charts the trend in undersea network cable construction, in his article [Content Delivery Networks Under the Sea](https://blog.thousandeyes.com/content-delivery-networks-under-the-sea/). Based on a recent talk at ThousandEyes by APNIC Chief Research Scientist [Geoff Huston](https://www.apnic.net/about-apnic/team/geoff-huston/), Ameet explains why large telecom companies have been supplanted as kings of the sea by Google, Facebook, Microsoft and Amazon.

And for number four, Angelique is back, discussing the storm that stranded Fortnite: Battle Royale islanders, in her post [When the Kill Shot is All of Us: Anatomy of a Fortnite Outage](https://blog.thousandeyes.com/kill-shot-all-of-us-anatomy-fortnite-outage/).

And now, hot off the presses, the details of tonights release...

## Live chat support now 24 x 7

In order to better serve our customers, we're now offering live chat support throughout the weekend, bringing our live support coverage to 24 hours a day, 7 days a week. Official terms of the new support hours are spelled out in the [Support Services and Security Policy](https://app.thousandeyes.com/legal/support-security). We hope our customers don't need it, but we're here, live if you do!

## Cloud Agents

We're pleased to welcome two more broadband ISP Cloud Agents to the family--one in San Jos[é](http://www.sjsu.edu/senate/docs/S70-12.pdf), California on the AT&T network, and one in Los Ángeles on the Comcast network.

Additionally, we've added a multi-provider Cloud Agent in Mexico City, Mexico, a third Tokyo, Japan Cloud Agent \("Tokyo 3", on the KDDI network\) and two more Google Compute Platform Cloud Agents--Los Angeles, California and Hamina, Finland.

Bienvenida a todos!

## Instant Tests via API

We are excited to announce the availability of instant tests for Cloud Agents via the API, starting August 28th, 2018. Previously, API-based instant tests were only available for Enterprise Agents.  Instant tests are useful in a variety of scenarios, such as gathering additional data when alerts occur.

We're announcing the change now because Instant tests will also incur usage costs starting on August 28th. Each Instant Test will incur the same cost in Units as a round of correspondingly configured scheduled test. For more information on how usage is calculated, see the ThousandEyes Knowledge Base article [How Unit consumption works](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmoKAC).

Our team has reviewed the historical usage of instant tests and has determined that customers who maintain their historical levels of instant test usage will not see a material impact on their monthly usage.

## Enterprise Agent Cluster filters

Similar to filters on the Enterprise Agent Settings, we've added filters to the Clusters Settings. Filters include:

* High Utilization
* Cluster Name
* Agents \(Cluster members\)
* IPv6 Policy
* Label
* Location
* Assigned to Account Group

The **Assigned to Account Group** checkbox has been removed, and Assigned to Account Group will be the default filter.

## Path Visualization

Two new additions, in our ongoing work to improve the visualization of Path Visualization.

### Grouping by interface for intermediate nodes

In addition to grouping Agents and destinations, intermediate nodes on the Path Visualization can now be grouped using the **Interfaces by** quick link. Users can create a compact view of the path by grouping interfaces by location, network, network and location or individual device. The example below groups by Network:

IMAGE MISSING

Attributes of grouped nodes such as errors or forwarding loss will be shown on the group and in the quick selection menu, similar to ungrouped nodes \(attributes of grouped links will not be visible in the visualization or in the quick selection unless the relevant nodes are ungrouped\). Clicking a grouped node will ungroup it. 

### Bezier curves for links

We now render links between nodes with bezier curves \(similar to the Topology view of Device Layer\):

IMAGE MISSING

 These new curved links make large topologies that converge on the a single node more readable, particularly if labels are used.

## Device Layer

We've implemented a grouping feature for the Topology view of Device Layer.  Neighboring devices of the same type can now be grouped together. Large networks can be viewed in more compact form, and complex topologies simplified. 

## Deprecated ciphers for Appliance access

 In order to enhance secure access to ThousandEyes Appliances, we are removing older, less secure cryptographic algorithms used by the web administration console. Similarly, we are removing older, less secure cryptographic algorithms for SSH access, and enabling newer, more secure ones.

The following algorithms \([per IANA naming convetions](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-4)\) are now deprecated for TLS \(https\) web access:

TLS\_RSA\_W1TH\_AES\_128\_GCM\_SHA256 \(0x9c\)  
TLS\_RSA\_WlTH\_AES\_256\_GCM\_SHA384 \(0x9d\)  
TLS\_RSA\_W1TH\_AES\_128\_CBC\_SHA256 \(0x3c\)  
TLS\_RSA\_W1TH\_AES\_256\_CBC\_SHA256 \(0x3d\)  
TLS\_RSA\_W1TH\_AES\_128\_CBC\_SHA \(0x2f\)  
TLS\_RSA\_WlTH\_AES\_256\_CBC\_SHA \(0x35\)  
TLS\_DHE\_RSA\_WITH\_CAMELLIA\_256\_CBC\_SHA \(0x88\)  
TLS\_RSA\_W1TH\_CAMELLIA\_256\_C BC\_SH A \(0x84\)  
TLS\_DHE\_RSA\_WITH\_CAMELLIA\_128\_CBC\_SHA \(0x45\)  
TLS\_RSA\_W1TH\_CAMELLIA\_128\_CBC\_SHA \(0x41\)

The following algorithms are now deprecated for SSH access:

CBC-mode ciphers  
MD5-based HMAC algorithms  
All 96-bit HMAC algorithms

and the following algorithms are now enabled:

GCM-based encryption

Users will generally not be affected by these changes if using up-to-date versions of client software.

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* Fixed an issue causing improperly colored Path Visualization nodes in private IP space when path discovery is incomplete
* Fixed an issue causing improperly colored Path Visualization nodes in source or target networks of Agent-to-Agent tests
* Fixed an issue that displayed incorrect values for Throughput in a multi-metric table
* Fixed an issue in Voice Call tests causing improper processing of redirect messages
* Fixed an issue that incorrectly specified Total Alerts in widgets when filtering or grouping using Test labels
* A single sign-on user whose account is locked from repeated incorrect password entry can now unlock the account with correct password entry

## Questions and comments

Got feedback on the hot new features? Just want to say ¡Hola!? [Send us an email](mailto:support@thousandeyes.com?subject=2018-08-01+Release+Update)!

