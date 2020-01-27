# Release Notes: 2019-06-11

Welcome to today's release! Our last spring bloom, as it were.

Before we get to the details... June is a time for much of the world to start contemplating vacation and travel. If you need a last-minute destination, we have a few excuses to get away:

IMAGE MISSING

If San Diego, Washington DC, or London sound appealing, there's still time to sign up and come on down to say hi at our booths. Head on over to our [events page](https://www.thousandeyes.com/events) for details, if you fancy a spur-of-the-moment get-way that can be written off to a business trip! Or check out the upcoming events that are not so last-minute.

In ThousandEyes blog news, we got what everyone loves to read about--outages! Angelique Medina has analysis of the Google Cloud Platform outage in her appropriately entitled post, [Google Cloud Platform Outage Analysis](https://blog.thousandeyes.com/google-cloud-platform-outage-analysis/). Archana Kesavan covers the disruption of WhatsApp's service in [WhatsApp Disruption: Just One Symptom of Broader Route Leak](https://blog.thousandeyes.com/whatsapp-disruption-just-one-symptom-of-broader-route-leak/). Have at 'em.

And now, the details of our release.

## Enterprise Agent End of Life

Enterprise Agents running on Ubuntu 14.04 LTS \(a.k.a. “Trusty”\) and on Red Hat/CentOS/Oracle Linux 7.3 and earlier versions will cease to operate as of July 1st, 2019. The Agent process will self-terminate. No data will be collected, nor will the Agent receive updates to the ThousandEyes software packages, including security updates. Customers will need to upgrade to a [supported operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC) to continue to use the Agent and receive updates.

So, check your [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents), and look for a red triangle warning icon \(\) in an Agent row. If hovering over the icon produces an **Agent OS is Unsupported** warning, or the General Info panel for the Agent displays:

IMAGE MISSING

then review the ThousandEyes Knowledge Base article [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades). Feel free to contact the Customer Success team for further advice.

## Proxy improvements

A couple of additions in our ongoing process of improving both the proxy capabilities of tests, and the user interface in general. The Proxy Settings tab of the Agent Settings page now uses slide-out panels to display the details of the proxy configurations. Click on a row to display the panel:

IMAGE MISSING

Additionally, the Bypass List settings are now consulted for all proxy configurations of a test to determine whether to run included Network metrics \(Overview and Path Visualization\). If a test has a **Proxy Configuration** setting which instructs the test to use a proxy, then the test target must be in the bypass list to run included Network metrics \(Overview and Path Visualization\).

IMAGE MISSING  
IMAGE MISSING

In the above example, the test is using a **Proxy Configuration** of "Orange" \(first image\). The test must have a target matching the configuration's **Bypass List** contents \( \*.mysite.com\) in order to run included Network metrics, which will be run directly to the target.

If the test target is not in the **Bypass List** field, then the test will display the message "Agent is proxied and test is not on the bypass list".

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release:

* Endpoint Agent installed on Internet Explorer 11 no longer interferes with CGI-based web forms
* Activity Log now provides  Device Layer events when a device is archived and when monitoring resumes on an archived device
* Embedded Color Grid Widgets now show the same data as when the widget is displayed in the Dashboard
* Fixed an issue with Agent-to-Agent tests which caused the test to incorrectly report 100% packet loss
* Fixed an issue which could cause the Proxy Authentication scheme to switch from NTLM to Basic in the Appliance's web admin interface
* Fixed an issue which could cause HTTP Server tests using HTTP/2 to fail to display error conditions on the timeline
* Fixed an issue which could cause inconsistent projected unit usages in different locations of the app
* Fixed an issue which could cause test creation on capped Enterprise Agents to fail due to incorrect units overage
* Share Links and Saved Events for tests whose targets have been modified no longer show "No Data"
* Path trace node names from reverse DNS lookups that contained the string "LAG" now are not geolocated to New York/La Guardia
* Sped up the "Lookup Servers" feature of a DNS Server test
* Duplicating an Alert Rule will now retain the Test **Type** setting

## Questions and comments

Got feedback for us? Want to send us a "postcard" from your vacation spot? [Send us an email](mailto:support@thousandeyes.com?subject=2019-06-11+Release+Update)!

