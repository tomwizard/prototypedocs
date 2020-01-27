# Release Notes: 2017-04-12

Don't forget...

IMAGE MISSING

The next ThousandEyes Connect event will be held in Bellevue, Washington, on April 20th, 2017.  A great time to be in Seattle, with Earth Week festivities starting the day after ThousandEyes Connect.  [Save your spot](http://www.thousandeyes.com/events/connect) for Connect.  And after Connecting, head outdoors to enjoy the festivities and the great Northwest, perhaps sporting your new [ThousandEyes t-shirt](https://www.thousandeyes.com/tshirt).

Thinking of employing DNSSEC to protect your organization's DNS resource records?  Curious to know what DNSSEC does or how it works? Check out this week's entry on the ThousandEyes Blog is Archana Kesavan's [Introduction to DNSSEC Monitoring](https://blog.thousandeyes.com/introduction-dnssec-monitoring/).

## Cloud Agents

We've added a new Cloud Agent location in Hong Kong.  Since this is the second site in Hong Kong, we'll be changing the name of the existing Hong Kong Cloud Agent to "San Po Kong, Hong Kong", and adding the second Cloud Agent location, "Wan Chai, Hong Kong".

## Enterprise Agents

A quick reminder for those customers still running Virtual Appliances installed prior to 2016... As noted in our [March 2 release update](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnwuCAC), we are ending support this month for Virtual Appliances running on Ubuntu 12.04 LTS \(“Precise”\), in conjunction with the April 28th [End of Life](https://wiki.ubuntu.com/Releases) for Precise by the Canonical corporation. For more information, see our [end-of-life announcement](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnyqCAC).

ThousandEyes Customer Success has reached out via email to customers with these Virtual Appliances.  If you haven't yet updated your Virtual Appliances, we strongly encourage you to do so, as soon as possible.  The process is straightforward and documented in our Knowledge Base article [Replacing an Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0).

## Enhancements

### Tests

We're changing the behavior of navigating to the Test Settings page from the test's Views page. Previously, clicking the Settings \(gear\) icon on the Test Views page would take you to the Test Settings page and expand the test's row to display the settings of the test. The new behavior adds the test name to the Search box, thus allowing the chosen test to be displayed more clearly when a customer has more than a small number of tests.

We've changed the behavior of name resolution in tests which have an included Network test, such as HTTP Server tests, FTP Server tests, etc...  Previously, the test's nominal View and the included Network metrics view could resolve a target to different IP addresses, if the domain name of the target mapped in DNS to multiple IP addresses.  We've now changed the test behavior to have the same IP address across the Views.

## Bug fixes and minor enhancements

* Fixed an issue with the password expiration feature that caused users to have to repeatedly reset their passwords before login. Users will need one more reset after this release with the fix.
* On the Enterprise Agents page, searching by primary Account Group in the Clusters tab is now available. Previously, only the Agents tab allowed searching by primary Account Group.
* Fixed issues with the app's interface when using Internet Explorer 11.
* Selecting "Transaction Time" for a Reports widget previously did not restrict the list of tests in the Filter to Transaction tests. Now the test list displays only Transaction tests. 
* Pie Chart widgets no longer show a "Widget not fully configured" warning unless the "Group by" selector was explicitly set.
* Fixed an issue in Reports when a change to a widget's "Nth Percentile" setting was not saved correctly.
* Fixed an issue with stopping the te-browserbot service via systemd/systemctl under CentOS 7 that could cause annoying subsequent failure messages.
* Fixed an issue with removing Endpoint Agent on Mac OS X via dragging to the trash.
* Fixed an issue in Endpoint Data that could cause non-zero millisecond histogram bars in a waterfall graph to be rendered as 0 ms bars.
* Fixed an issue in Endpoint Agent Data's User Sessions view which caused multiple objects loaded not to be displayed on a single page.

## Questions or comments?

 As always, we'd love to hear from you.  Just [drop us a note](mailto:support@thousandeyes.com?subject=Release+Notes+2017-04-12).

