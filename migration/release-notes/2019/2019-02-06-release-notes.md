# Release Notes: 2019-02-06

Welcome to today's release!

Some quick notes before we get to tonight's new features. First, a net-nerd news flash:

IMAGE MISSING

 Judging from the weather reports, we've hit the depths of winter in the northern hemisphere. If you need a break from frigid temperatures, or if you're in the southern hemisphere and laboring under heatwaves, then consider a quick trip to a place that has the same weather, year-round: San Francisco! NANOG 75 runs from February 17th to the 20th, and is happening in the home of ThousandEyes' HQ, a short walk from the site of NANOG. Hope to see you there!

In ThousandEyes blog news, we are very pleased to have a pair of great guest bloggers. First up: John Todd, the Executive Director of public DNS service Quad9. John favors us with his experience using ThousandEyes, in [Discovering Latent DNS Issues: A Quad9 Case Study](https://blog.thousandeyes.com/discovering-latent-dns-issues-quad-9-case-study/). And joining John is Jonathan Lewis, the VP of Product Marketing at cloud service provider NS1. His post, [Modern DNS and the Value of One Second](https://blog.thousandeyes.com/modern-dns-and-the-value-of-one-second/), dovetails nicely with John's, and provides a great overview of the advanced capabilities of DNS which enable a fast online experience. Thanks, guys!

Continuing with the DNS theme, our Senior Product Marketing Manager, Angelique Medina, gave us one post for [Surviving DNS Flag Day](https://blog.thousandeyes.com/surviving-dns-flag-day/), and a second to look forward to trends in IT infrastructure for the coming year, in [Five Infrastructure Trends to Watch for in 2019](https://blog.thousandeyes.com/five-infrastructure-trends-to-watch-for-2019/). Spoiler weather report: clouds get bigger, clouds get cloudier.

And now for the news of features...

## Cloud Agents

Welcome to a new IPv6 Cloud Agent in Strasbourg, France. Bienvenue!

## Mandatory TLS access for Appliances

Web access for management of Virtual Appliances and Physical Appliances now require a secure SSL/TLS browser connection \(i.e. encrypted connection on port 443/TCP using an https:// URL\). Connections to the unencrypted http:// URL will now be redirected to the https:// URL.

Note that by default the secure connection uses a self-signed certificate, which will cause standard browsers to display security warnings. To prevent warnings and ensure secure access, customers can upload a valid server certificate via the **SSL Settings** tab of the web management interface. The interface also allows users to create a certificate signing request. For more information, check out the ThousandEyes Knowledge Base article [Secure access to ThousandEyes Appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000XofqCAC_Secure-access-to-ThousandEyes-Appliances).

## Test filters

The Test Settings page now has display filters, similar to other settings pages.

IMAGE MISSING

Available filters include Name, Type, Target, Test Label and Enabled.

## Endpoint Agents in the Agent Status widget

 In Dashboards, the Agent Status widget can now display Endpoint Agents, using similar iconography to Enterprise Agents.

IMAGE MISSING

The widget can be configured to display Endpoint Agents individually or grouped by one or more Endpoint Agent Labels, and can be configured to filter similarly.

IMAGE MISSING

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Added the .pdf extension to Reports which are downloaded as PDF files
* Added support for unicode characters in Reports which are downloaded as PDF files

## Support coverage change

 From February 22nd to March 3rd, ThousandEyes will have a minor reduction from 24 x 7 support coverage, in conjunction with our annual all-company event. Check the [announcement of reduced support coverage](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFZUCA4_Reduced-Support-Coverage-Feb-22-March-3) for full details.

## Questions and comments

 Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-02-05+Release+Update)!

