# Release Notes: 2016-05-11

We're just over a week from ThousandEyes Connect NYC. Great speakers from AIM Specialty Health, Nasdaq and Verisign are on the agenda! There are only a few seats left, so [register online here](https://www.thousandeyes.com/events/connect/new-york-2016).

IMAGE MISSING

We've seen a few blips in connectivity by Tier 1 providers in the East Coast US in the last couple of weeks. In [this blog post](https://blog.thousandeyes.com/trans-atlantic-issues-level-3-network/), [Young Xu](https://blog.thousandeyes.com/author/young/) discusses the impact of Trans-Atlantic Issues in the Level 3 Network, discussing some interesting findings and inferring root cause of the outage which impacted connectivity between Europe and the US east coast last week. Remember, you can subscribe to the ThousandEyes Blog to stay up to date with what's happening out there in the connected world.

And, without further ado, let's get into the release notes for this week.

## FTP tests \(public beta\)

Listening to the voice of your customers is key to maintaining a relationship with your customer base. Based on popular demand, we've added support for FTP-based testing to the product, and are beginning an open beta beginning this week.

IMAGE MISSING

Test common FTP requests; download or upload a file, verify directory contents, and track metrics across your requests. As with other types of application-layer testing, we're including Network tests along with these tests for free.  This beta for FTP-based tests includes testing and alerting; Reporting and API access will be introduced as the beta progresses, as will support for other FTP-like protocols \(including SFTP and FTPS\).

For more information on working with FTP tests, check out articles on [Using the FTP Server tests view](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmWKAS), and [FTP test settings](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC). 

## Reporting updates

### Test & Agent group filtering and aggregation

As we continue to enhance our reporting capabilities, we've added the ability to filter and aggregate based on test and agent groups.

IMAGE MISSING

Refer to [this article on working with reports](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS) for detailed information on how to use this very powerful feature set to report on your data.

## Internet Explorer compatibility

As [was previously announced](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cml8KAC), we've retired support for Internet Explorer 9 and 10. Users will no longer be able to log in when attempting to access app.thousandeyes.com or a ThousandEyes appliance using these browsers.

If you are using a newer version of IE and are unable to log in, check to ensure that your browser isn't accessing the site using compatibility mode, which sets the browser back to an older version.

## Role permissions for API access

We've added a specific permission to the platform, for access to the ThousandEyes API. All roles have been automatically granted this permission, which preserves the behavior of existing access.

## Bugs fixes and minor enhancements

* Units used to show throughput throughout the product have been normalized to use bps, kbps, and Mbps \(depending on the scale of values shown\). 
* The maximum "number of times in a row" option in alert configuration has been increased from 4 to 10. This allows agents to be in a degraded state for longer before triggering an alert.
* We corrected a display bug which caused users to see only 10 rows in the alert settings page.
* Access to the /accounts endpoint in the ThousandEyes API was unavailable for users in the Regular User role for a short period of time following last week's release. This has been corrected.
* Certain customers running Enterprise agents on CentOS, using an older version of libssh2 experienced agent stability problems last week in light of an undocumented prerequisite change. This has been corrected and our dependency trees have been updated to reflect the changes.
* We've reduced the dashboard refresh interval to 2 minutes in order to ensure that users have more real-time access to test results.
* We'll be pushing a major update to the browserbot component of our agents this week, updating from Chromium version 40 to version 49.  

## Maintenance reminder

[As was previously announced](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmrDKAS), we are performing maintenance to our networking infrastructure as part of a datacenter move this on May 13 beginning at 02:00 UTC.  This maintenance period will last 30 minutes.

## Feedback?

We love hearing from our customers. Whether it's a comment about our recent blog posts, about these product updates, or otherwise - [please reach out](mailto:support@thousandeyes.com?subject=2016-05-11+release+update) and let us know what you think!

