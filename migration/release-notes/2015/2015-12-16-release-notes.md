# Release Notes: 2015-12-16

HO HO HO! Happy holidays from the team at ThousandEyes!  Yep, the holidays are upon us, but we'll spare you the wassailing in this week's update. Instead, Santa's loaded up his sleigh early this year, in order to bring the gift of several new features - some of which have been in development for quite some time. Check out the list below, and let us know if you have any questions.  
 

## New cloud agent locations

We've recently added cloud agent locations in the following cities:

* San Francisco, California
* Glasgow, Scotland
* Athens, Greece

These agents are immediately available to paying customers. Please note that access to these agents is not included in trial subscriptions.  View our entire cloud agent map [on our website](http://www.thousandeyes.com/product/agent-locations).

## New features

### Agent-to-Agent tests \(BETA\)

On November 11th, we updated some of our test names. Network tests became "Agent to Server" tests - and there may have been some foreshadowing at play, but today we're announcing an open Beta of the new Agent-to-Agent tests feature.

With this feature, we're enabling the ability for users to visualize both directions of a communication flow between agents, using either TCP or UDP. Set DSCP and payload values, and show the throughput of your network connections by modifying advanced settings of the test.

IMAGE MISSING

Throughout the beta phase, this feature will be available free of charge to customers running tests between enterprise agents. The feature is restricted to enterprise agents on both ends - this is to ensure that customers do not incur usage costs for using the beta.  Access to use this feature with cloud agents will be introduced once we move this feature into general availability.

We've introduced new alert rule types which can be applied to these tests as well: check out [this Knowledge Base article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) for more details.

#### Known issues

With any completely new feature, we're bound to have some loose ends to tie up.  See the following list for items that will come during the beta phase, prior to general availability.

* API access for Agent-to-Agent tests is unavailable.
* Reporting for metrics gathered by Agent-to-Agent tests are unavailable.
* Only Agent-to-Agent alert rules are assignable to Agent-to-Agent tests.
* When reviewing an Agent-to-Agent test using Internet Explorer 11, the arrows will be... pretty big.  We're working on a way to work around this issue, but are hampered by a bug in Internet Explorer at the moment \(https://connect.microsoft.com/IE/feedback/details/781964/\).

### Alerts list update

We've rewritten the alerts list page to improve performance and optimize user experience. Beginning in tonight's release, when either clicking through an alert notification users will be directed to a multi-tabbed page showing a list of currently active alerts. Click through to a second tab to show the alert history over the prior 90 days, and use our new search widget to find alerts by rule name, alert ID, name, type, affected test, or status.  Check out [this Knowledge Base Article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) for more information on the alerts list.

IMAGE MISSING

### Multi-organization login

With this release, we've introduced the ability to users to belong to multiple organizations - this will be a useful feature for customers using ThousandEyes across multiple business units.  Prior to this release, users have been restricted based on unique email address. Each unique email address could be assigned to a single organization. We've extended the major security overhaul we effected earlier this year to allow user portability between assigned organizations.  

A number of very useful features come along with this update, including:

* Share your enterprise agents with other business units
* Grant access to team members who are already members of other ThousandEyes organizations

Please note that this feature is restricted to paying organizations: users assigned to Trial and/or Lite organizations cannot be linked to paid organizations.

#### API change

With this feature's introduction, we've added an additional field, _OrganizationName_ to the /accounts endpoint of the API, which will show the Organization Name \(as displayed in ThousandEyes\) for any user for whom multiple organization login is enabled. A documentation update will follow to update this on the [ThousandEyes developer reference](http://developer.thousandeyes.com/) site.

There are a number of important changes that affect how security works in the context of a user assigned to Multiple organizations.  Please review t[his Knowledge Base Article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnDKAS) for more details on the feature.

### Updated usage tab

We've also rewritten the usage tab \(found in account settings for users with permissions to view organization usage\), taking into account user feedback received.  We've simplified the interface to show more clearly the cloud units and enterprise agents allocated to the organization on a month-to-month basis, as well as the breakdowns shown for each of the sections.  Check out this Knowledge Base article for more information on [Displaying and Alerting for Cloud Unit consumption](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn9KAC).

IMAGE MISSING

##  Holiday support hours

In order to give our staff a well-needed break and time with their families, our offices will be closed on Christmas Eve, Christmas Day, and New Year's day. For those of you who need support on these days, fret not: our Customer Success team will be actively monitoring email and ready to engage on any urgent issues that come through while our offices are closed.  Non-urgent emails will be addressed upon our return to the office.  
 

## Feedback

We really do love hearing from our customers: in case you have questions or comments around these release updates, or want to send us either a virtual lump of coal or some holiday cheer, feel free to [drop us a note](mailto:support@thousandeyes.com?subject=2015-12-16+Release+Notes+Feedback).

