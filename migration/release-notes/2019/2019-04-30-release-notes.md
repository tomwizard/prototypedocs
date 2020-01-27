# Release Notes: 2019-04-30

Welcome to our most recent release! Here in the US, April 15th was the deadline for paying our taxes. If you're one of those folks who waited in line at the post office to get your returns postmarked before midnight, this release is for you... But before the details of the release, some announcements.

IMAGE MISSING

 Connect New York City is coming! Join us on May 9th at the Dream Midtown Hotel--steps away from Central Park, Carnegie Hall, the Theater district and Times Square. Time for a working vacation, maybe? Write off those show tickets and come on down! Meet fellow ThousandEyes users and learn from our great guest speakers how ThousandEyes is the basis for gains in performance and reductions in costs. Itemize them, you say?

IMAGE MISSING

[Registration](https://www.thousandeyes.com/events/connect/new-york-2019) is free and open now! And if you prefer a ThousandEyes Connect event in an offshore haven, don't miss [Connect London](https://www.thousandeyes.com/events/connect/london-2019), coming in June!

In ThousandEyes blog news, Technical Marketing Manager Ameet Naik gives us the second installment in the discussion of Russia's recent moves to test withdrawing the country's networks from the internet. Ameet discusses recent attacks on Yandex \(the Russian equivalent of Google\) in his article [Yandex Packet Loss: DDoS or Russian Firewall?](https://blog.thousandeyes.com/yandex-packet-loss-ddos-or-russian-firewall/)  Attacks? Scheduled Russian withdrawal? Make your own deduction.

Next item: our Senior Solutions Engineer, Prabhnit Singh, gives us [Operationalizing ThousandEyes Using RingCentral Glip](https://blog.thousandeyes.com/operationalizing-thousandeyes-using-glip/)--an example of how a ThousandEyes customer, RingCentral, integrates alerts from ThousandEyes into their operations. If your organization has to account for every alert, this post is for you.

And finally, if the thought of tax day doesn't scare you, maybe our VP of Product Marketing, Alex Henthorn-Iwane will. His post, [What is 768K Day, and Will It Cause Internet Outages?](https://blog.thousandeyes.com/what-is-768k-day/) describes what might happen to the Internet in the very near future. There's even a video. Chilling!

Ok, no more withholding... Here's the details of the release. Many happy returns.

## Quotas for Organizations and Account Groups

For organizations which need to limit consumption of units by Account Groups, or for setting limits for an entire organization, we have created a new quota feature. The new Quotas tab under the Account Settings page displays the units allotted monthly to an organization under the organization's contractual plan, and permits setting quotas on Account Groups within the organization.

IMAGE MISSING

Review the ThousandEyes Knowledge Base article [Working with Account settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnGKAS_Working-with-Account-settings) for more information on the Quotas tab.

## New Alert List widget

In additon to the Alert Grid widget, users can now get a tabular listing of their Alerts and related information with the new Alert List widget.

IMAGE MISSING

Users can click on the specific test \(alert source\) to quickly navigate to the test and view the collected test data. The list can be filtered by several critieria, including Tests, Agents and status \(active/inactive\). The timespan of the alerts list can also be selected.

## New Test features

This release brings a number of new features and enhancements for Tests, as well as a feature that's being deprecated.

### OAuth support for HTTP Server Tests

 Users can now monitor API's or mobile applications which use OAuth authentication. OAuth authentication is available for HTTP Server tests. The test will make an initial HTTP request to an authentication server in order to obtain an OAuth token, which will then be used to authenticate the request to the HTTP Server test's target.

### Proxy Settings

As part of our ongoing efforts towards implementation of proxy settings on a per-test basis, we have moved the Proxy Settings tab to the Agents Settings of the Cloud And Enterprise Agents, up from its previously nested location.

IMAGE MISSING

Proxy configurations applied to Cloud Agents will be applied on a per-test basis.

### Skype for Business Online

 The SIP Server test type now supports testing the Skype for Business Online service.

IMAGE MISSING

Setting **Server Type** to "Skype for Business Online" will result in additional authentication options being displayed at the bottom of the Basic Configuration tab.

### Test Description field

 Test settings now provide a Test Description field, so that users can provide a short text description associated with the test.

IMAGE MISSING

 The free-form search tool on the Test Settings page allows users to search for tests by Test Description.

### URL validation deprecated

 Previously, when configuring the target of a Web Layer test, the ThousandEyes app performed a check on the target URL. The URL was requested from the ThousandEyes platform's infrastructure, which meant that non-public URLs produced a warning that the URL was unreachable, even if the user intended for the test to be run from an Enterprise Agent which did have access to the URL. To avoid confusion, we've removed the validation check.

## Endpoint Agent

We've made a few of changes to the process of Endpoint Agent configuration, and to the wireless metrics.

### Proxy settings

The Endpoint Agent's Agent Settings page now has its own Proxy Settings tab, similar to the existing tab of the same name under the Agent Settings of the Cloud and Enterprise Agents page.

IMAGE MISSING

### Downloads modal now a side panel

The page for downloading Endpoint Agent installation packages now displays the download as a side panel rather than a modal window.

### Endpoint Agent metrics renamed

 The metric called BSSID Changes is now called Roaming Events, and Channel Changes are now called Channel Swap Events. Roaming Events measures the number of changes in BSSID within the same SSID. Similarly, Channel Changes measures the number of changes of channel within the same SSID. Neither metric tracks a change that accompanies a change of SSID. The new names better reflect the nature of the metrics.

## Bug fixes & minor features

Here are the bug fixes and minor features in this week's release:

* IPv4 and IPv6 Cloud Agents in Osaka, Japan have a new provider. Review the [maintenance announcement](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ZSAS_Cloud-Agent-Maintenance-2019-04-19-Osaka-Japan-Osaka-Japan-IPv6) for more details.
* The API's /usage endpoint now provides the number of purchased and used Endpoint Agents and Device Layer devices in an Account Group
* The API's /agents endpoint now returns similarly named error messages as those in the app, for Enterprise Agents reaching end of lifecycle dates \(end of installation support, end of support, end of life\)
* The count of active Alerts is now displayed next to the Alerts menu.
* When clicking on a video link under the Help & Support menu \(\) users, a new window appears which can be dragged and pinned within the browser window to allow for viewing both the video and the app
* Deleted Endpoint Agents no longer appear within the Labels &gt; Endpoint Agents selector list
* Certain file operations with the box.com service now appear in the Endpoint Agent's waterfall graphs
* The Windows uninstaller for Endpoint Agent now removes the ProgramData\ThousandEyes directory
* Fixed an issue causing no page to load on the Cloud and Enterprise Agents &gt; Views page

## Questions and comments

Got feedback for us? Bad puns taxing your patience? [Send us an email](mailto:support@thousandeyes.com?subject=2019-04-16+Release+Update)!

