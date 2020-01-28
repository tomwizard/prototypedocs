# Release Notes: 2017-11-29

Welcome to tonight's release. Those of us working at ThousandEyes offices in the US are coming back from the US holiday of Thanksgiving. We at ThousandEyes have much to be thankful for--most notably our great customers and our wonderful co-workers from around the world.

In the ThousandEyes blogosphere... Our new VP of Product Marketing, Alex Henthorn-Iwane, has hit the ground running with his first blog post. Entitled [Gartner’s Take on Unified Communications Monitoring](https://blog.thousandeyes.com/gartner-unified-communications-monitoring-market-guide/), Alex expounds upon Gartner's discussion of needs, pitfalls, and planning assumptions when implementing UC and an accompanying monitoring solution \(like ThousandEyes\).

Also, Senior Product Manager Gopi Gopalakrishnan has the latest quarterly review of newly released features and services.  Check out [what was new](https://blog.thousandeyes.com/whats-new-q3-2017-product-updates/) in Q3!

And now, what's new in this release...

## Cloud Agents

 After much hard work by our Operations team, we're finally welcoming a new IPv6 Cloud Agent in Los Angeles.

## Endpoint Agent

 Endpoint Agents on Mac OS X can now connect to ThousandEyes via an SSL decrypting proxy \(a.k.a. man-in-the-middle proxy\) which does not use cipher suites that support perfect forward secrecy \(PFS\). Previously, if an organization's proxy did not support PFS cipher suites, the Endpoint Agent would not be able to communicate with the ThousandEyes platform.

For more information on perfect forward secrecy, check out Scott Helme's article "[Perfect Forward Secrecy - An Introduction](https://scotthelme.co.uk/perfect-forward-secrecy/)".

## Bug fixes & minor features

Here's the list of bug fixes and minor features in this week's release:

* For a BGP-enabled test, the "Showing: X of Y monitors" now reflects the actual number of BGP monitors shown in all cases.
* Increased the resolution of the Endpoint Agent icon for better appearance in Retina displays.
* Fixed a bug causing the names in an Endpoint Agent's Filters selector to be missing, when using the Path Visualization view.
* Fixed a bug that prevented a single Endpoint Agent session from being displayed in the timeline of the Session Details view.
* Fixed a bug that could prevent generation of a Reports snapshot with Endpoint Agent data.
* Fixed a bug that caused the Duration field to be missing when configuring an Alert Suppression Window.
* Images in emailed Report snapshots are no longer cached when viewed using Apple Mail.
* Fixed an issue on the Account Settings' Usage tab to display "0 of X agents used" on the first day of the billing cycle \(note that this issue did not affect actual billing data\).
* The /update endpoint in the API now behaves in a consistent manner with the app for target Agents of an Agent to Agent test.

## ​Questions, comments?

 Got a question or a comment? Want to tell us what feature of ThousandEyes you're thankful for \(or one you'd be thankful for if we added it\)? [Send us an email](mailto:support@thousandeyes.com?subject=2017-11-29+Release+Update). Thanks in advance! 

