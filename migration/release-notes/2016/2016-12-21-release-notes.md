# Release Notes: 2016-12-21

Happy Holidays from the team at ThousandEyes!

In case you missed it, Archana Kesavan published an interesting blog article covering a recap of the top Internet outages of 2016 in today's blog post. In her post, Archana writes about everything from fortune-seeking lottery players crashing the Powerball website to the Mirai Botnet taking down Dyn's massive DNS infrastructure.  Check it out [here](https://blog.thousandeyes.com/top-internet-outages-2016/)!

As we work through the final days before the holidays, here's a quick update on tonight's release.

## Cloud agents

 We've added Cloud Agents in the following cities:

* Nanjing, China
* Wuxi, China
* Jinan, China
* Shijazhuang, China
* Xi'an, China
* Zhuhai, China
* Shenyang, China
* Foshan, China
* Wenzhou, China

## SIP Server test beta

We've announced a private beta for the SIP Server testing capability of our platform.  To register to participate, either contact your sales representative, or [email our support team](mailto:support@thousandeyes.com?subject=SIP+beta+participation) and we'll be happy to pass along the request.

## Agent changes

### Clock offset

 We've changed the behavior for Enterprise Agents which have offset clocks.  Prior to this change, if an Agent's clock is out of sync with ThousandEyes, results collected for a round of data would be committed based on the time of the Agent, potentially resulting in an inconsistency between the data collected by multiple Agents assigned to a test.  With this release, if the Agent's time is out of sync upon check-in with the ThousandEyes collector, the data timestamp will be corrected automatically by the Agent.  This process ensures that data collected during a round is presented consistently, irrespective of the Agent's clock offset.

As an ancillary benefit to this change, new Account Groups configured in ThousandEyes will no longer have a default Agent Notification rule for clock offset.

We still recommend that customers configure Enterprise Agents to synchronize their clocks with an NTP server.

### Xenial-based installation

 We've also made a change to the Enterprise Agent installation script to work around a bug in the latest version of apt \(the package manager which ships with Ubuntu 16.04\).  Customers who previously experienced problems installing the Enterprise Agent with a warning indicating that packages could not be authenticated will now be able to install the Enterprise Agent.

##  Minor features

* We've made some improvements to the rendering of Reports widgets which graphically display data on pages and steps in Transaction tests.  This release changes the order of the data series, such that the first pages/steps start at the bottom of the chart, and adds the step/page numbers to the legend.
* Webhooks sent to Hipchat using our built-in integration will now be displayed in color.  Alert Notifications be displayed in red, and cleared alerts be displayed in green.
* Endpoint Agent wireless metrics have been added to tooltips in Path Visualization.

##  Bug fixes

* We've corrected an issue whereby the second line of an address wasn't properly displayed in the **Billing** tab of the Account Settings page.  
* Permission to edit scheduled reports is now based on the permission Edit reports for all users in account group.  Prior to this change, the ability to edit these report snapshots was based on Edit Dashboard templates for all users in account group.
* We've corrected a problem that incorrectly caused alerts on shared tests to be suppressed.  If the original test was configured with an Alert Suppression window, the window incorrectly applied to recipients of the share.
* Users can now disable tests shared from another Account Group.  Prior to this update, in certain circumstances, a test shared from another Account Group would throw an error upon attempting to disable it.
* We've made a few changes in the area of user management:
  * In certain circumstances, a user could not be added to an Account Group when the user had previously been added as an external email recipient \(for Alerts and/or Reports snapshots\).
  * In the case where a user is assigned to multiple organizations, the **Has management permissions** icon would be displayed in the **Users** tab of the Account Settings page reflecting the permissions assigned to the user's default organization, instead of the current organization.
* We've fixed the "continue" link that is displayed after a password expires and is reset by the user.  Previously, the "continue" link didn't go anywhere.

## Support hours

 Our team will be reducing support hours during the holidays to allow their families to spend some much-needed time with friends and family.  We'll continue to offer best-in class support during this period, however customers should be aware that we will be operating without Live Chat capability on December 26th and January 2nd.  The following hours will be observed:

* December 24-26: Weekend hours \(no chat support\)
* December 27-30: Coverage 24h per day \(24 hours\)
* December 31-January 2: Weekend hours \(no chat support\)

 If you experience an issue during our weekend coverage periods, please email [support@thousandeyes.com](mailto:support@thousandeyes.com) and we'll be in touch quickly.  
 

