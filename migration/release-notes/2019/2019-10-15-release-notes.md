# Release Notes: 2019-10-15

Welcome to our latest release!

Before we get to what's new in the product, some news of upcoming events and new articles from the ThousandEyes blog...

Fancy an early vacation to a warm location? Want to learn how earn how ThousandEyes helps 70 of the Fortune 500 and 20 of the top 25 SaaS companies plan, build and run their cloud-centric IT? ThousandEyes will be at the [Gartner IT Symposium/Xpo 2019](https://www.gartner.com/en/conferences/na/symposium-us) in Orlando, Florida from October 20th to the 24th. [Sign up to meet with us](https://www.thousandeyes.com/gartner-symposium-orlando-2019) and discuss your cloud-centric challenges. Attend our presentation How to Avoid the Hybrid IT Visibility Gap with Credit Suisse's regional CTO. And there's probably other stuff to do in Orlando as well...

For the netheads, we'll be boothing at [NANOG 77](https://www.nanog.org/meetings/nanog-77/) in Austin, Texas from October 28 - 30.

And as an Austin encore... We're very excited to present Cloud State Live, 2019! [Come to Austin](http://www.thousandeyes.com/cloud-state-live/attend) or [live stream](http://www.thousandeyes.com/cloud-state-live) the event from your location, but don't miss the unveiling of ThousandEyes' latest Cloud Performance Benchmark report--this year with 33% more clouds \(we've added Alibaba to last year's contestants: AWS, Microsoft Azure and Google Cloud\). Find out who wins Best Cloud!  Registration is free. Sign up today!

In blog news... The past week in the San Francisco Bay Area saw ~800,000 customers of our local utility, Pacific Gas & Electric, experience deliberate power blackouts \(intended to lower the risk of wildfires in dry rural areas of California, which have occurred in recent years when high winds damaged the aging transmission infrastructure\). PG&E relied on its web site to provide customers with information on who would be affected and when. Unfortunately, PG&E website wasn't up to the task, either. Our Director of Technical Marketing, Hans Ashlock, provides the details of the outage, in his blog post [PG&E Web Servers Go Dark Amid Looming Power Shutdown](https://blog.thousandeyes.com/pge-web-servers-go-dark-amid-looming-power-shutdown/).

On a brighter note... Is your organization's increasing demand for cloud-based computing got you looking to power down your MPLS backbone and switch to SD-WAN? Our VP of Product Marketing, Alex Henthorn-Iwane, has penned an illuminating article entitled [Visibility for SD-WAN Deployment Best Practices](https://blog.thousandeyes.com/visibility-drives-sd-wan-deployment-best-practices/), which will give you the power to ensure your transition to a cloud-centric network with SD-WAN goes right as rain.

And now for the details of our release...

## Cloud Agent addition

We've added an IPv6 Cloud Agent in our Luxembourg, Luxembourg location. Welcome, welcome!

## Kerberos configuration for Appliances

In our [release of 2019-08-20](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000UH1vSAG_Release-Update-2019-08-20), we added the **Disable reverse DNS lookup** setting. This setting gives users the choice of whether an Enterprise Agent uses reverse DNS lookups in the Kerberos authentication process. The setting was available from the app, and could also be configured by editing an Enterprise Agent's configuration file. In this release, we've added the setting to the web admin interface of ThousandEyes Appliances.

## Reports API v7

We've added new functionality for the [/reports endpoint](https://developer.thousandeyes.com/v7/reports/) in version 7 of our API to create or update a Report or a Report Snapshot. This is a great way to recreate an existing report in a different Account Group or Organization, or use an existing report as a template on which to create further reports. Just don't forget to add the /v7 to the URL of your API call, as the default API version [is still version 6](https://developer.thousandeyes.com/v7/#/versioning).

## Endpoint Agent HTTP Server tests & system proxy

When configuring the **Proxy Options** setting of an Endpoint Agent's HTTP Server test, the proxy configured for the system on which the Agent runs will now always be used if configured for the test. Previously, if an Agent-level proxy had been assigned via the Agent Settings page, the system proxy was not used even if selected in Proxy Options. To implement this, we've added a fourth menu choice: "Endpoint Agent's proxy configuration" which will allow for Agent-level proxies to be selected from the Proxy Options. The "System Proxy" setting will now always allow the test to use the system's proxy setting.

IMAGE MISSING

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release. Version numbers in parentheses indicate when a fix first appears \(when relevant, e.g. Endpoint Agent version\):

* Targets in the RTP Stream and Voice Call test types can now be edited via the app's UI and the API
* In the Alerts and Alert History, Internet Insights Alerts now are only displayed in the Account Group in which the Alert Rule is configured, not in all Account Groups in the Organization
* Fixed an issue with an attribute preventing SSO logout
* Fixed a race condition that could cause a newly activated user account to be treated as deleted
* Fixed an issue which could cause "Internal Server Error" or partial data when downloading the Activity Log in CSV format
* Fixed an issue which could display projected usage as "∞%" when creating a new test
* Fixed an issue which could cause Endpoint Agent to report incorrect object size if the response does not contain a "Content-Length" header

## Questions and comments

Got feedback for us? Want to tell us about the time your favorite website went dark? [Send us an email](mailto:support@thousandeyes.com?subject=2019-10-15+Release+Update)!

