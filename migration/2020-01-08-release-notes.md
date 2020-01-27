# Changelog

## 2020-01-22

### New Features and Enhancements

The following new features and enhancements are included in this release:

* Device data can now be snapshotted and shared publicly.
* Device views now include an Interface Type filter.
* Internet Insights outage snapshots can now include snapshots of affected tests.
* Improved the speed in which monitored domains are pushed to Endpoint Agents.
* Adjusted Dashboard Number widget sizing to improve usability.
* Dynamic baselines are now available for some metrics, replacing the “auto” baselines functionality previously available. See the [Dynamic Baselines](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work#dynamic-baselines) documentation for more information.

### Bug Fixes

The following issues have been fixed in this release:

* Fixed an issue where tests were not removed from the UI when updating a suppression window.
* Fixed an issue in the notification UI to distinguish between an organization’s internal and external email recipients.
* Fixed an issue where some older Auto metric rules did not trigger once they were converted to the new dynamic baseline functionality.
* Fixed an issue with dynamic percentage calculation.
* Fixed an issue where the browser extension was disabled in Endpoint Agent trial accounts.
* Fixed a widget label issue in Agent to Server tests for Endpoint Agents.
* Fixed a permissions issue when downloading Endpoint Agents.
* Fixed an issue where the latest geodata was not displaying correctly.
* Fixed an issue that prevented the test table widget from filtering by all label IDs.
* Fixed an issue with the Agent Status widget that, in some circumstances, resulted in configuration changes to Endpoint Agents not saving.

### Questions and Comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2020-01-22+Release+Update)!

## 2020-01-08

### ThousandEyes Blog

 There is new activity on the ThousandEyes blog:

* The speed, scale, and complexity of digital environments is increasing exponentially every year, making monitoring those environments an increasingly difficult task. But not an impossible one. There are several myths about monitoring the Internet, and Tris Clark \(Sr. Analyst Relations Manager at ThousandEyes\) aims to debunk them in their new post, [Top 4 Monitoring Myths: Debunked](https://blog.thousandeyes.com/top-4-monitoring-myths-debunked/).
* ThousandEyes’ Customer Success Engineer Kemal Sanjta asks the question [Do We Need to Rethink Network Monitoring?](https://blog.thousandeyes.com/do-we-need-to-rethink-network-monitoring/) Their presentation and blog post examine the challenges faced by monitoring a modern network and how we need to evolve.
* Angelique Medina, Director of Product Marketing at ThousandEyes, reviews the most disruptive Internet outages of 2019, outlines what you can learn from them, and explains how Internet Insights can help in the future, with their newest blog post, [Looking Back at the Biggest Internet Outages of 2019](https://blog.thousandeyes.com/looking-back-biggest-internet-outages-2019/).
* In their post, [Monitoring Application Performance with Elastic APM](https://blog.thousandeyes.com/monitoring-application-performance-elastic-apm/), Sergio Freitas \(Engineering Manager at ThousandEyes\) dives into the reasons behind adopting an Application Performance Management \(APM\) tool, why we chose Elastic APM, and how it was deployed and integrated with the rest of our infrastructure.

And now for the release details.

### New Features and Enhancements

 The following new features and enhancements are included in this release:

#### Cloud and Enterprise Agents

* DNS Server and DNS Trace tests now support TCP as the transport layer protocol. This is configurable in Advanced Settings, and is also available in the API as dnsTransportProtocol.  IMAGE MISSING
* Tests can now override the Enterprise Agent’s IP policy. This is also available in the API as ipv6Policy. IMAGE MISSING
* SSO audience restriction logic now allows arbitrary restriction URLs, for customers with a large number of organizations. This enables an organization to specify a unique suffix that identifies one organization from another.
* Granular information has been added to the usage API to improve parity between metered \(Enterprise Agent\) information and current Unit usage.
* Device layer functionality is now included as a feature of the Enterprise Agent. **Note:** Device licenses are no longer required. The ThousandEyes account management team will be reaching out to existing customers with device layer licenses to determine next steps.
* Virtual interfaces are now visible in Devices views.
* Interface type column added to Devices table views.

#### Internet Insights

* Added an Internet Insights knowledge-base link to terminal node tool tips.
* Error notifications are now displayed if adding / removing Internet Insights packages using the buttons in the package and catalog entry tables fails.

#### Synthetic Transactions

* The Transaction Recorder now supports pausing / resuming script playback. The Recorder also displays the line number the script reached when playback was paused.
* Synthetic Transactions now supports Multi-Factor Authentication \(MFA\) via an API that generates a Time-Based One-Time Password \(TOTP\) token that is given the authentication secret.

### Bug Fixes

 The following issues have been fixed in this release:

* Fixed an issue causing duplicate entries in waterfall views.
* Fixed an issue where widgets could not be renamed when configuring a scheduled snapshot.
* Fixed an issue in some Endpoint Agent environments where waterfall views were not generated.

### Questions and Comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2020-01-08+Release+Update)!

