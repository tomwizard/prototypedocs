# Release Notes: 2015-02-04

A few pretty significant updates this week, with many more to come in the month of February. Check out the list below, and let us know if you have any questions!

## Advance notice of downtime

As many of you have noticed, we have transitioned to a minimal downtime maintenance schedule. Our next release, scheduled for February 18, 2015 at 2 AM UTC, will have a 90-minute downtime window announced. During this maintenance window, our systems will be unavailable and will respond with a 503/Service Unavailable status code.

We will send out another update on February 13th reminding our customers of this maintenance window.

## Dashboard

We've added the ability to click the sparkline charts in the dashboard. Simply hover over one of the small graphs to the right of each test shown in the dashboard, and click when hovered over the area of interest. This will open the selected test, at the selected time, with the selected metric in context.

IMAGE MISSING

For more information on working with the Dashboard, check out [this article.](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmdKAC)

## DNS override on HTTP server tests

Another oft-requested customer feature, we've added the ability to override DNS resolution of an HTTP server target. To override your target, modify the advanced settings option with the IP address you wish to use.  This option is found in the HTTP Request section of the advanced settings tab for HTTP server tests.

IMAGE MISSING

This option is not available for Page Load or Transaction tests at present.  Check out this link on [working with test settings](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC) for more information on using advanced options.

## Reports changes

A few changes reflected to reporting, reflected in the list below:

* When a report widget is configured with data from a single test, the name of the test is shown in the descriptive text for the widget. Prior to this change, the descriptive text would show the number of tests configured \("1 tests"\). IMAGE MISSING
* The **Schedule Snapshots** and **Edit Scheduled Snapshots** scheduling configuration dialogs have been updated to enhance user experience
* Snapshots of reports can now be shared via a publicly accessible URL, similar to Snapshot sharing of test data.

Check out [this article on Working with Reports](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS) for more information on using reports.

## Enterprise agent utilization

In response to customer feedback, we've added a maximum Enterprise agent utilization threshold at 95% of agent capacity. While an agent is at or above 95% utilization, it will no longer allow new tests to be configured using this agent.

## Nomenclature change for subprefixes

We've renamed the term "subprefixes" to "covered prefixes" throughout the application, in order to standardize nomenclature with our BGP views. This nomenclature change applies to both the BGP test settings page, and to alert rules which include covered prefixes.

## Questions & comments

As always, we're here to help. If you have any questions or comments, either leave a comment on this article, or feel free to [email us.](mailto:support@thousandeyes.com?subject=Feb+4+Release+Comment)

