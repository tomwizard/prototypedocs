# Release Notes: 2017-03-02

Welcome to March!  February said goodbye in spectacular fashion, with a major Amazon Web Services \(AWS\) outage of their Simple Storage Service \(S3\), this past Tuesday.  The outage caused many cloud-based applications built on S3 to come crashing to earth, and left users of those apps searching for an explanation that did not involve supernatural evil forces.

Fortunately, ThousandEyes was not one of those affected cloud-based applications.  So while we here in the ThousandEyes office couldn’t swap photos of each other \(taken at our week-long company kick-off meeting\) via Slack, we could still use our own product to figure out why almost everything we use was having issues.

If you’ve recovered sufficiently from the trauma of the cloud that burst, Young Xu has a [blog post](https://blog.thousandeyes.com/aws-s3-outage-likely-caused-by-internal-network-issue/) that shows what broke. Don’t ask us what the silver lining of this tale is, though, unless it’s getting to read two of Young’s posts in one week.  The blog post she planned for this week is [Benchmarking Network Performance in China](https://blog.thousandeyes.com/benchmarking-network-performance-china/)—the first in a series that focuses on using ThousandEyes to peer into China’s corner of the Internet…  Bad week for the Internet leads to bad networking puns.

This week’s release is a modest one, due to the aforementioned annual festivities here at ThousandEyes.  But we’ve all had enough excitement for one week…

## Cloud Agents

We’ve added IPv6 cloud agents in Oakland and New York City, bringing us up to 30 IPv6 locations.  We’ll be regularly adding more locations, so stay tuned to this channel for more updates.

## Enhancements

### Test Views

The world map on the Map tab of test Views now displays Agents which failed to collect data distinctly from Agents that collect data which represent error conditions. A red dot will indicate error conditions: 

IMAGE MISSING

Also, we've introduced a new filter for the Endpoint Data. The "Network" filter allows users to select Endpoint Agents by the network owner, as determined by Whois. As an example, you can quickly view Endpoint Agents using a particular Internet Service Provider when trying to determine if Endpoint Agents with bad metrics have a common ISP:

IMAGE MISSING

IMAGE MISSING

The Network filter is also available in the list of filters for Reports widgets, so that you can filter by service provider when creating reports.

### Test creation

Ever begin to create a test, then realize you forgot to choose the correct test type?  Already typed the test name, the URL for the target, added 43 Agents and 5 Alert Rules, and now realize that you wanted a Page Load test instead of an HTTP Server test?  Well, suffer no more.  We can change the test type, and the configuration information that is already entered will be preserved, assuming it’s relevant to the new test type.

## Pre-2016 Virtual Appliances

Our original Virtual Appliance was built on Ubuntu Precise 12.04 LTS, with a 32-bit operating system.  Precise 12.04 LTS reaches [End of Life by Canonical](https://wiki.ubuntu.com/Releases) in April of this year, so they’ll no longer be publishing security updates.  We’ll be working with customers over the coming weeks to replace these Virtual Appliances with more recent versions, which will be supported by Canonical far into the future.  We’ve also begun developing release upgrade processes on Virtual Appliances, so that this issue won’t rear its head again.

If you have questions on the status of any deployed Virtual Appliances in your organization, please contact our Customer Success team.

## Bug fixes

### Alerting

* Fixed an issue which prevented Path Trace Alert Rules from being triggered on Agent to Agent tests when the Alert Rule contained an "X of Y rounds" criterion, combined with the “Both Directions” option of the Alert Rule.  Users should keep in mind that “Both Directions” in the context of an Agent to Agent test's Path Trace alert means **either** direction**.**  We’ll be correcting this label in the near future to be clearer.

### User Management

* Deleting users via the SCIM endpoint of the API when using the HTTP DELETE method now works.
* Deleting users via any method now removes the user’s email address from the Notifications address book.
* Fixed a bug that caused the **Cancel** and **Save** buttons to change position on the Test Settings page when the **Save & Enable** button is clicked.

### Enterprise Agent/ThousandEyes Appliance

* Fixed an issue with ThousandEyes Appliances which caused failure to install the most recent update due to an unmet BrowserBot package dependency.
* Fixed an issue that allowed Enterprise Agents added to a cluster to exceed the organization’s limit on the number of deployed Enterprise Agents, if an organization is configured not to allow overages.

### Endpoint Agent

* Fixed an Endpoint Agent issue that incorrectly displayed proxy info when a proxy's domain name resolved to multiple IP addresses.
* Fixed an issue that caused deployed Endpoint Agents not to be disabled when the organization’s limit on Endpoint Agents is decreased below the currently active number of Endpoint Agents.  
* Added detection support for Cisco AnyConnect VPN connections to the Endpoint Agent.  With this new information, we’ll be able to display the VPN server's IP address in the path trace.

## Support hours reminder for this week

Due to the aforementioned company kickoff, \(and as mentioned in our February 16 Release Update\) our entire team is at HQ, and working daytime hours in order to allow the team to participate in planning sessions.  Our support coverage hours this week are from 6 AM to 8 PM Pacific Standard Time.  We’ll return to 24 x 5 coverage beginning on Monday, March 6th.

## Questions or comments?

Got questions about the product?  About something you read in Young’s blog posts?  About life in general?  Send ‘em [to the Customer Success team](mailto:support@thousandeyes.com), if you dare.  Who knows what kind of excitement awaits?

