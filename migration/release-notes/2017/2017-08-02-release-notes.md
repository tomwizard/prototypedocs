# Release Notes: 2017-08-02

Welcome to tonight's release!

Normally, in this portion of the Release Update, we provide you with information and links to our latest ThousandEyes blog posts. In our previous release, we had none to give--a consequence of summer vacations and other factors. Tonight, we're making up for that shortfall with four terrific new blog posts.

First up: Product Manager Gopi Gopalakrishnan's [What’s New in Q2?](https://blog.thousandeyes.com/whats-new-q2-2017-product-updates/), which reviews the new features introduced in the past three months, highlighted by "The Sight of Sound" review of our new Voice-over-IP tests. If you missed the first the quarterly feature round-up, check out the Q1 installment [here](https://blog.thousandeyes.com/new-may-2017-dashboard-widgets-api/).

Next, for those who weren't able to attend our last ThousandEyes Connect event, or if you attended and wanted to review some of the great presentations from ThousandEyes customers, here's your chance. Our Marketing team's Archana Kesavan has a nicely summarized and illustrated \(presentation slides included\) post on the presentation by Daniel Shanahan, Staff Network Performance Engineer at Intuit, entitled [How Intuit Monitors Connectivity to AWS](https://blog.thousandeyes.com/how-intuit-monitors-connectivity-aws/). From the tax software company that processes more returns in the cloud every April than anyone else, some great and practical architecture and implementation info from Daniel, describing how ThousandEyes helps keep those returns flowing between the AWS cloud and Intuit's infrastructure.

And still more stories of real-world experience... If your company uses Marketo, the marketing automation software product, then your marketing department probably noticed that Marketo's online resources were unavailable for a time last week. What caused it? Young Xu's [blog post](https://blog.thousandeyes.com/what-happened-when-marketos-domain-name-expired/) will tell you, ThousandEyes-style \(meaning, we got data and pretty graphs covering the period of the outage for you to explore, interactively\).

But wait, there's more. ThousandEyes' Chief Information Security Officer, Alexander Anoufriev, has a blog post for those of you interested in certification and compliance. Entitled [Five Reasons Why ISO 27001 Certification Matters](https://blog.thousandeyes.com/five-reasons-why-iso-27001-certification-matters/), the post describes the drivers behind ThousandEyes' push for ISO 27001 certification.

And now, the details of tonights release.

## Cloud Agents

### IPv6 Cloud Agents

Continuing to grow our IPv6 Cloud Agent presence internationally, we've added Bucharest, Romania this week to the list of available IPv6 locations.

### IPv4 Cloud Agents

Another addition to the US-based IPv4 Cloud Agents: Baltimore, Maryland. Crab cakes and Cloud Agents for all!

## Dashboards

Similar to the Reports widgets, you can now embed Dashboard widgets in your web portals. Click the **Add/Manage Widgets** button in the Dashboard containing the widget you wish to embed, and select Embed Widget from the **More Actions** menu:

IMAGE MISSING

Click the **Allow anyone to embed this widget onto external sites** box. The window expands to display the embed's HTML code snippet, which uses an &lt;iframe&gt; tag. The window also displays a preview of the widget.

IMAGE MISSING

A role with one of the Edit Dashboards... permissions is required to access the Embedded Widget feature.

## Bug fixes & minor features

* Fixed an issue with Reports snapshots which could add an extra day if the timespan included a 30-day month.
* Corrected an issue which could prevent re-enabling certain tests after an organization's account is locked after a credit card expiration.
* Improved the appearance of the horizontal axis in Dashboard widgets with many data points.
* Fixed an issue which caused the "active alerts" count of an Alert Grid widget in the Dashboard to be incorrect.
* Fixed an issue which could cause unwanted Activity Log entries when ThousandEyes support personnel browse Dashboards or Reports in customer accounts.
* Fixed an edge case that caused slow loading of the Test Settings page for a limited number of users.
* The APT diagnostic under the Diagnostics tab of the Appliance's web console no longer displays SSL errors for the ThousandEyes APT repository on Ubuntu Trusty-based Virtual Appliances.
* The APT diagnostic under the Diagnostics tab of the Appliance's web console will now correctly test a custom APT repository.
* Fixed an edge case causing Red Hat 7.3-based Enterprise Agents to crash when configured with a proxy and running certain Web Layer tests with client certificate authentication.
* Fixed an issue with Reports for Endpoint Agent data that displayed duplicate locations when the Group By filter was set to Location.
* Fixed an issue with the Path Visualization in Endpoint Data that would cause some Agents to be grouped as "Unknown Network"
* Fixed an issue with the Path Visualization in Endpoint Data that would incorrectly display a link as having a loop.
* Fixed Instant Test issue which caused errors when attempting to run valid Web Layer tests that have username and password configured.
* We've added an option to the Instant Test's Run Now button in Test views to optimize clicks and make clearer that users can choose whether to modify the configuration before running the Instant Test: IMAGE MISSING
* We've changed the orientation and wording of the active and cleared or disabled alerts indicators on Alert Grid widgets in the Dashboard to better reflect what these two categories represent: IMAGE MISSING IMAGE MISSING

## ​Questions and comments

Have comments on our blog articles? Something you'd like us to write about? [Send us an email](mailto:support@thousandeyes.com?subject=2017-08-02+Release+Update) and let us know how we can make you more successful.

