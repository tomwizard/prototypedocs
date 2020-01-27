# Release Notes: 2019-03-19

Welcome to today's release! The equinox is nearly upon us; a time of transitions from old to new, and tonight's release will have a bit of each.

But first... There's always something new springing up at the ThousandEyes blog.

Whether you're starting a company and need to nail down the digital side of business, or you're in charge of your enterprise's cloud adoption efforts, ask how will you maintain operational visibility in your new, cloud-y environment? With some help from David Mann, Senior Director of Global Network Services at McGraw-Hill, our Senior Product Marketing Manager Archana Kesavan gives you answers in her post  [How Operational Visibility Can De-Risk Your Cloud Strategy](https://blog.thousandeyes.com/how-operational-visibility-can-de-risk-your-cloud-strategy/). Betcha didn't know "de-risk" was a word. Me neither.

For you Game of Thrones fans, our Lead Software Engineer, Adam Blank, gets to talk about what he engineers here, in his post [Alerting at ThousandEyes: The Watchers on the Walls](https://blog.thousandeyes.com/alerting-at-thousandeyes-the-watchers-on-the-walls/). Get a behind-the-scenes look at the workflow and technologies used to send you emails, webhooks, PagerDuty and Slack notifications when something's about to go wrong. Don't let a digital White Walker get the jump on you!

Lastly, our Technical Marketing Manager Ameet Naik has a great post discussing Russia's plans to temporarily disconnect the country from the Internet, in [Does the Internet Have an Off Switch?](https://blog.thousandeyes.com/does-the-internet-have-an-off-switch/) Can it be done, and if so, how? And what consequences of cutting the cord? We're all waiting with bated breath for the answers.

But no more waiting for the details of tonight's release!

## Enterprise Agents

A number of announcements regarding old and new Enterprise Agents...

### End of Support and End of Life

Important news regarding the various Linux operating systems on which Enterprise Agents are supported, and the notification mechanisms for Agents running on older versions of these operating systems.

#### Red Hat Enterprise Linux, CentOS and Oracle Linux

As we have [announced previously](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CplcCAC_Release-Update-2018-10-23), we have ended support for Enterprise Agents running on all versions of Red Hat 6 \(RH 6.7 was the last supported minor version\) and Red Hat variants \(CentOS and Oracle Linux\), as well as versions 7.1, 7.2 and 7.3 of those operating systems. Until this release, we have not enforced this policy with hard limits on the Agent software--a "grace period" for customers to make the transition to newer releases. Existing systems can be either be upgraded using the supported methods from Red Hat, or by installing a new operating system and Agent.

As of now, we are setting dates for those hard limits. The end of support for software updates will be April 30th, 2019. Updated Agent software packages for these operating system versions will no longer be published after this date. The end of life for these Agents will follow two months later on June 30th, 2019, per our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy). Existing Agent software on these operating systems will no longer run after this date.

#### Ubuntu Linux

As we have [announced previously](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqLfCAK_Release-Update-2019-01-08), we are approaching the end of support and end of life for all Agents \(including Virtual and Physical Appliances\) running on Ubuntu 14.04 LTS \(a.k.a. "Trusty Tahr" or just "Trusty"\). Existing Appliance based systems will be upgradeable using a ThousandEyes-supplied mechanism \(stay tuned for details\). Non-Appliance based systems can be upgraded using the supported methods from Ubuntu, or by installing a new operating system and Agent.

The end of support for software updates will be April 30th, 2019. Updated Agent software packages for these operating system versions will no longer be published after this date. The end of life for these Agents will follow two months later on June 30th, 2019, per our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy). Existing Agent software on these operating systems will no longer run after this date.

#### Agent operating system warnings

To ensure that customers are aware of Enterprise Agents running on operating systems approaching an end of support or end of life date, the Enterprise Agent Settings page will now display warnings for these conditions when an Agent is:

* approaching end of support
* reached end of support and is approaching end of life
* reached the end of life

The red triangle warning icon will contain a warning with a link to the relevant documentation. The General Info panel will display a brief text message with the relevant date:

IMAGE MISSING

### Docker image updated

The Docker image for Enterprise Agent installation we provide is now based on Ubuntu 18.04 LTS \(a.k.a. "Bionic Beaver" or just "Bionic"\).

## New, optimized Menu Panel

 As the ThousandEyes application has grown in functionality, we've been planning to redo the menus and optimize navigation within the app. Starting in today's release, we begin unveiling a revamped set of menus and a reorganization of the pages for data and configuration settings. 

We will be making the transition to the new menus starting in this release, in which we have relocated just the Cloud and Enterprise Agent Labels tab, previously under the Labels menu. This tab will now be found under the Agents menu, and will be called Agent Labels. The tab will contain the same data and configuration options.

The upcoming release on April 2nd will see the full transition to the new menus. Here's a sneak preview, comparing the classic Menu Panel to the new Menu Panel.

IMAGE MISSING

We'll also be publishing an article in our Knowledge Base in the next release to help users navigate the new menus.

## Number widget improvements

We've made a number of improvements to Number widgets in Dashboards and Reports. Each card in a widget now can be colorized from red to green based on the data in the card. Users can set their own ranges for the color spectrum, or allow the widget to automatically calculate ranges.

IMAGE MISSING

Additionally, we've made the card's title and description more prominent, and added more detailed error messages when a widget is unable to populate with data.

## Waterfall search

For browser-based tests \(Page Load and Transaction\) the Waterfall tab now includes a search box to find objects in the waterfall listing.

IMAGE MISSING 

Search by object name, domain name or any other portion of the object's URL.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Bi-directional tests \(Agent to Agent, RTP Stream and Voice Call\) can now be run via the API
* Improved some visual elements and error handling on the Quotas tab of the Account Settings
* Fixed an issue which could cause failure to load a valid SSL server certificate for an Appliance's SSL Settings
* Fixed an issue which could cause an erroneous "You have reached your usage limit" message when creating a test
* The API now sends an HTTP 409 status code instead of 400 when writing to an endpoint results in a conflict due to an existing resource

## Questions and comments

 Got feedback for us? Have a suggestion for a Game of Thrones-themed blog post? [Send us an email](mailto:support@thousandeyes.com?subject=2019-03-19+Release+Update)!

