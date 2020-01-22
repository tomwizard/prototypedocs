# Release Notes: 2016-09-14

Welcome to Fall!

Ok, technically the equinox is next week.  But the weather's turned cooler, people are headed back to school, and our staff's finishing up the last of the family vacations, so close enough...  This week's release is light on major new features, since we're still suffering from summer vacation hangover. But we're back at our desks, diligently doing our homework, and we've got some good stuff on the horizon that we think you'll like better than a refrigerator magnet from a tourist trap gift shop.  Until then, we've got lots of bug fixes.

## Endpoint Agent

For the Network View, we've added MPLS information in the Path Visualization. Sorry Windows fans--that data's not available to us at present!

## General enhancements & fixes

* Added the ability to edit disabled tests. Previously, tests had to be enabled in order to edit and save the changes.
* The Docker-based Enterprise Agent installation now allows specifying a proxy bypass list for the Agent configuration.
* Now showing Agent-to-Agent test utilization and using the information in assignment of tests to Enterprise Agents in an Enterprise cluster.
* Fixed an issue which caused HTTP Basic Authentication data to appear \(in standard base64 encoding\) in the Request Headers page of a Web Layer test.  We have now removed from the Request Headers both HTTP Basic Authentication-related headers and also removed NTLM-related \(Integrated Windows Authentication\) headers for consistency.
* Changed the behavior of rounding time to the nearest minute in the Alerts History page. Previously, we would always round down; now we round to the nearest minute for time of alert duration.  Concomitantly, the display format now shows hours, minutes and seconds instead of hours and minutes.
* Fixed a bug in the Virtual Appliance Web Admin page's Advanced Settings tab which prevented viewing the BrowserBot log.
* Leading/trailing whitespace in an email address is now properly scrubbed when creating users via the API.
* Fixed an issue with the SFTP test when the Limit Download Size option is selected.
* Fixed an issue in Reports that could cause incorrect data under certain conditions.  See our [Knowledge Base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000Cn2ECAS) for more information.

## Questions or comments?

If you're not too busy getting yourself or your offspring back to school, we would love to hear from you! [Send a note](mailto:support@thousandeyes.com) home to tell us if we've been behaving especially well or particularly naughty.  We promise not to turn D's into B's, forge signatures or otherwise alter report cards \(unless said report cards use [SHA-1 hashes](https://en.wikipedia.org/wiki/SHA-1)\).

