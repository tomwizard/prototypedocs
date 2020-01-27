# Release Notes: 2017-02-01

## Meet us in Washington, DC for NANOG 69!

Here in most of the U.S. the dark, cold depths of winter are upon us.  If you're feeling the need to get away, these days there's no place more interesting than our nation's capital. Meet us in Washington, DC for [NANOG 69](https://archive.nanog.org/meetings/nanog69/home)! Come by the ThousandEyes table at lunch on Tuesday and grab one of our new t-shirts.

## Recent ThousandEyes blog posts

Archana Kesavan's new blog post, [Tune Your Network Monitoring with Instant Tests](https://blog.thousandeyes.com/tune-network-monitoring-instant-tests/) offers tips for using our recent improvements to the Instant Test feature. Validate your test configuration and preview network monitoring data more easily than ever.

Young Xu's new post, [Best Practices to Combat Route Leaks and Hijacks](https://blog.thousandeyes.com/best-practices-combat-route-leaks-hijacks/) discusses best practices to help mitigate route leaks and hijacks, as well as longer-term solutions to prevent the propagation of bad routes.  

## Cloud Agent changes

### Added

As part of a major IPv6 expansion initiative, we've added IPv6 service in Sydney, Australia, Berlin, Germany, and Ashburn, Virginia.

### Removed

We've removed our Cloud Agent in Tunis, Tunisia due to unreliable service by our provider.  Our Operations team will continue to search for a replacement service provider in that location.  

## Instant tests

Access to the legacy Instant Tests pages has been removed.  This completes the update to this feature, initially announced last release, and documented [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnaUCAS).  Customers who have bookmarked the legacy page will now see an error when using the old URL.

## Notice of update to BrowserBot

We will be releasing a major update to the BrowserBot component of the Enterprise Agent in 2 weeks \(BrowserBot runs Page Load and Transaction tests using the Chromium browser, and is available to "Pro" level subscriptions\).  This update will include upgrades to Chromium version 55 and Java 7.  The update is available for Enteprise Agents on all supported operating systems other than Red Hat Enterprise Linux 6 and CentOS 6, which will continue to use Chromium 42 and Java 6.

## Bug fixes & Minor Enhancements

* Test ownership change now includes an option to not retain a share to the test in the source Account Group. To suppress creation of a Live Share in the source Account Group, uncheck this option during the transfer of ownership. For more information on changing ownership of tests, review the ThousandEyes Knowledge Base article [Changing ownership of a test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWcCAK).
* Customers can now configure BGP Private Peering with our services by using a private ASN.  Prior to this update, only valid, non-private ASNs could be used with our BGP Private Peering feature.
* Test Settings will now correctly reflect the test editor.  Prior to this update, Last Modified stamps would incorrectly indicate the editor as the original creator.
* When clicking the Export Data option in the Share dialog of a test, users will no longer be presented with a pop-up requesting credentials.  Prior to this update, the user was prompted for API credentials prior to displaying information.
* We've fixed Transaction test step time charts. Prior to this update, transactions were stacked top-down in ascending order of steps/pages.  Following this update, layers will be stacked from the bottom up in ascending order of steps/pages.  This more accurately reflects the order of execution on a timing scale.

## API fixes

We've also made a few fixes to the API:

* Disabled tests queried via the /tests endpoint or /tests/testId endpoint will now show the list of Agents assigned to the test.  Prior to this update, a test which was disabled would not show the list of Agents.
* API reference links presented in the /alerts endpoint will reflect the queried version number of the API
* DNS+ alerts will now show metrics.  Prior to this update, metrics were not shown for DNS+ alerts when querying via the API.

## Questions or comments?

Got a bug? Got a question? Got feedback?  [Send us](mailto:support@thousandeyes.com) whatever you got. The next Release Update awaits your input!

