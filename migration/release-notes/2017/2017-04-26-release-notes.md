# Release Notes: 2017-04-26

Hello, ThousandEyes community!

This past week, we held our first ThousandEyes Connect event in Bellevue, Washington, and were treated to some great talks by Tim Franklin at Columbia Sportswear, and Scott Hinckley at Microsoft. Be sure to keep an eye on our [blog](http://blog.thousandeyes.com/) over the coming week as we publish summaries of their presentations!

In addition, are you curious about [Net Neutrality](https://blog.thousandeyes.com/what-is-net-neutrality/)? If so, our own [Nick Kephart](https://blog.thousandeyes.com/author/nick/) published a post last week describing Net Neutrality - what it means, and more importantly, what the current administration's prospective changes mean to you!

Without further ado, on to the release update!

## Reports & Dashboards

If you've been around ThousandEyes for a while, you'll have noticed a gradual stream of releases over the last 18 months or so on our reporting module - and a number of customers have requested that we make the Reports & Dashboards feature sets interchangeable. This release extends some of the key features available for widgets in the Reports interface to the Dashboards interface.

We've added support for \(among other features\):

* Reports widgets in the Dashboards interface
* half-width widget support

IMAGE MISSING

Why is this helpful? The simple concept here is to allow users to aggregate their data as they see fit. If you have 10 tests targeting various servers which make up a single customer-facing service, why not aggregate them to show the service availability as a whole, without taking up a ton of space on the dashboard?

More information on Dashboards and Reports can be found in the ThousandEyes Knowledge Base articles [Working with the Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmdKAC) and [Customizing your Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmcKAC).

## BrowserBot stability updates

We've spent the last month working on optimizing the BrowserBot component for ThousandEyes Agents. Our overall goal in this area is reduction of error incidence, but we've managed to squeeze a few other benefits from the activity. In addition to being more stable, our new BrowserBot implementation will run faster, and provide more information to members of the ThousandEyes Customer Success team when it experiences a problem during test execution, to help in problem diagnosis.

## ThousandEyes Appliance changes

We've updated the underlying operating system used for the ThousandEyes Appliance to run on Ubuntu Xenial \(16.04\). This applies across all Appliance types.

We've also added support for multiple signing/CA certificates on the ThousandEyes Virtual Appliance, for cases where organizations leverage multiple SSL-decrypting proxy servers with unique signing certificates, or other scenarios that require a multiple-certificate chain installed.

## Agent operating system end of life policy

As a reminder, we have amended our support policy for ThousandEyes Enterprise Agents running on end of life operating systems. The current minimum supported operating systems can be found in the ThousandEyes Knowledge Base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC).

Our supported release stream is following announced dates for the following operating systems:

* Red Hat Enterprise Linux \(including derivatives\): ThousandEyes support for Red Hat Enterprise Linux ends when [Red Hat's Extended Update Support](https://access.redhat.com/support/policy/updates/errata#Extended_Life_Cycle_Phase) period ends.  For more information on ThousandEyes' support for Enterprise Agents on Red Hat-based systems, see the ThousandEyes Knowledge Base article [End-of-Life announcement for Red Hat Linux package Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK).
* Ubuntu LTS: ThousandEyes support for Ubuntu LTS versions ends when [Ubuntu's Maintenance Updates](https://www.ubuntu.com/info/release-end-of-life) period ends. For more information on ThousandEyes' support for Enterprise Agents on Ubuntu systems, see the ThousandEyes Knowledge Base article [End-of-Life announcement for Ubuntu Linux package Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB1rCAG).

With the ThousandEyes release immediately following 60 days past the end of support, ThousandEyes will automatically disable Agents running the underlying operating system. Upcoming dates for end of life:

| Operating System | End of Life Date | EoL + 60 days |
| :--- | :--- | :--- |
| Ubuntu Precise \(12.04 LTS\) | April 28, 2017 | June 27, 2017 |
| Red Hat Enterprise Linux/CentOS/Oracle Linux 7.2 | November 30, 2017 | January 29, 2018 |
| Red Hat Enterprise Linux/CentOS/Oracle Linux 6.7 | July 31, 2018 | September 29, 2018 |

We've also added an "Agents with Problems" notice to the platform to let you know that we've identified an Agent running on an end of life operating system. Users will see this in the Agent Settings page, as well as when clicking the Agent icon in the top navigation bar.

Please [contact ThousandEyes Customer Success](mailto:support@thousandeyes.com?subject=Out+of+date+agents) if you need advice on managing the replacement of your agents.

## API Changes

Be sure to follow our API updates; In the last 2 weeks, we've added a series of additional API endpoints, including methods to pull data for the Endpoint Agent. This week, we've added Alert Suppression Window and Agent Notification Rules endpoints. Check out more [on our developer reference site](http://developer.thousandeyes.com/v6/#/changesummary).

On May 24, 2017 we will be promoting API version 6 to be the "current" version.

## Bug fixes & minor features

We've discovered and resolved a number of bugs, and added some minor features in this week's release as well. A quick list can be found below:

* We've adjusted the default duration of an RTP Stream test from 10 seconds to 5.
* We've added region and country information to BGP outage context data.
* We've corrected a problem which prevented certain reports from being deleted, returning an HTTP 414 "Request Too Large" status code.
* We've fixed the Report Snapshots scheduler interface.  Prior to this update, if the snapshot was scheduled to have its first run in the past, the schedule would have been silently dropped.
* When reviewing the test \(or alert rule\) settings interface, if the last modifier of a test was a user who had been subsequently deleted, the user interface would show "Last Modified by \(Deleted user\)", instead of the user's name.  We've changed this to show the deleted user's name.
* We've corrected a bug introduced by our current support chat provider \(Olark\) in a release this week, which caused inadvertent focus to the chat window when undesired.
* We've also corrected an issue where a UDP-based Agent-to-Agent test using the maximum throughput option would report lower maximum throughput than expected.

## ​Questions, comments?

We love hearing from our customers - please [drop us a note](mailto:support@thousandeyes.com?subject=2017-04-26+Release+Update) if you have any questions, and we'll be happy to respond!

