# Release Notes: 2019-03-06

Welcome to our latest release!

Two new yet related blog articles to plug from our VP of Product Marketing, Alex Henthorne-Iwane. Alex dives into the DevOps world to demystify the latest buzzword: AIOps. In [What is the Point of AIOps?](https://blog.thousandeyes.com/what-is-the-point-of-aiops/) and [Solving the Visibility Gaps AIOps Leaves](https://blog.thousandeyes.com/solving-the-visibility-gaps-aiops-leaves/), Alex provide framework for discussing DEM in today's cloud-centric world.

And without further delay, the details of today's release!

## Enterprise Agents

### Support for Cisco 9000 series switches

The ThousandEyes Appliance is now available for Cisco 9000 series switches. Installation instructions are available in the ThousandEyes Knowledge Base article [Enterprise Agent Installation for Cisco Catalyst 9000 series switches](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqCOCA0_Enterprise-Agent-Installation-for-Cisco-Cat9K-IOS-XE).

### Warnings for unsupported Agents

In keeping with our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy), Enterprise Agents will now display warnings on the Enterprise Agents Settings page when an Agent has reached End of Installation Support, End of Support or End of Life. Note that the next lifecycle date for Agent support is the end of support for Trusty-based Agents, on April 30th, 2019. For a full list of lifecycle dates, consult the ThousandEyes knowledge base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems). 

## Reports and Dashboards

When a Report or a Dashboard is edited concurrently by more than one user, we now provide warnings and block saving edits to out-of-date widgets. When a user makes an edit to a widget, the application will display a warning to any other user who has the same Report or Dashboard open, and provide an option to refresh the page.

## Device Layer

We've improved the user experience for Device Layer setup. Users who have yet to configure any Device Layer monitoring will now see a "Get Started With Devices" wizard on the Device Settings page, which will walk users through the configuration to monitor devices.

IMAGE MISSING

Also, we've modified the modal which appears when clicking the **Find New Devices** button on the Device Settings page. The new modal is a slide-out, and provides some additional options and instructions, when discovering new devices.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* References in the app UI to the email address sales@thousandeyes.com now display the address sales-inquiry@thousandeyes.com
* In the BGP Monitors Settings page, the Juniper IPv4 configuration now explicitly sets the family parameter
* The diagnostics tab of the Appliance no longer shows an incorrect "Agent is running with errors" message
* Fixed issues which could produce "Browser didn't initialize correctly\* errors in browser-based tests
* Fixed an issue causing RTP Stream test data not to be displayed

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-03-05+Release+Update)!

