# Release Notes: 2016-08-31

Hi everybody!

Lots to announce in this week's release, so will jump into it without further ado.

## FTP server tests GA

With tonight's release, FTP moves into general availability status and out of Beta.  With FTP server tests, users can validate throughput \(both upload and download\), or validate server listings and content, running tests against servers running FTP, FTPS \(FTP over SSL\), and SFTP \(FTP over SSH\).

IMAGE MISSING

We've also added support for FTP server tests in version 6 of the ThousandEyes API. For more information on using the ThousandEyes API, refer to the ThousandEyes developer reference at http://developer.thousandeyes.com.

For more information on configuring FTP Server tests, read [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC).  For more information on results from FTP Server tests, read [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC) and [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmWKAS).

## Crash reporting for Agents

In order to improve diagnosis of problems with Enterprise Agents, we've added an automatic crash reporting feature.  Similar to other systems, which send reports to their parent companies when execution is halted by an error, this feature allows Enterprise Agents to send error data to ThousandEyes when the te-agent process encounters a fatal error.

For more information on the new crash reporting feature, review [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000Cn2HCAS).

## Alerting changes

### Hipchat and Slack integration

We've added direct third-party integrations for Slack and HipChat, to go along with our PagerDuty integrations. These integrations can be used to notify your teams when there's something of interest for your tests.

IMAGE MISSING

You can check out details on how to enable these integrations in your alerts - review the [article here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000Cn2FCAS). 

### Web transaction step names on alerts

For Transaction alerts, we've made the alerts more user-friendly, by displaying the step name where an error was encountered during execution of a transaction.  Prior to this update, we'd show the step number alone.

## Endpoint Agent

We've made a number of enhancements to the Endpoint Agent, currently in preview mode.  

### New permissions

We've added the following assignable permissions to ThousandEyes:

| Permission name | What it controls | Assigned to these Roles by default |
| :--- | :--- | :--- |
| View endpoint agent settings | Access to the Settings &gt; Agents &gt; Endpoint Agent menu | All roles with _View agents in account group_ permission |
| Edit endpoint agent settings | Access to make changes in the Settings &gt; Agents &gt; Endpoint Agent menu | All roles with _Edit agents in account group_ permission |
| View endpoint agent monitored networks | Access to see the Monitored Networks tab, found in the Endpoint Agent settings menu | All roles with _View agents in account group_ permission |
| Edit endpoint agent monitored networks | Access to create and make changes to monitored networks, found in the Endpoint Agent settings menu | All roles with _Edit agents in account grou_p permission |
| View endpoint agent monitoring profiles | Access to see the Monitoring Profiles tab, found in the Endpoint Agent settings menu | All roles with _View agents in account group_ permission |
| Edit endpoint agent monitoring profiles | Access to create and make changes to monitoring profiles, found in the Endpoint Agent settings menu | All roles with _Edit agents in account group_ permission |
| View endpoint agent data | Access to the Endpoint agent views \(Found under the Views &gt; Endpoint Data\) menu | All roles with _View agents in account group_ permission |

### IE compatibility mode

* A warning has been added to the waterfall section of the session details view, when a user with the endpoint agent is accessing a site in a monitored domain with IE compatibility mode enabled.  Users will now see an informational icon \(instead of an error\) indicating that no waterfall is available.

## General enhancements & fixes

* We've added a navigator property called 'thousandeyes' to Page Load and Web Transaction tests. This can be used as part of a general filtering strategy to prevent ThousandEyes testing from showing up on website analytics platforms.
* The title information for share links which would theoretically include content from the future have been updated to reflect the last available round of data at the time the snapshot is created.
* We've corrected a bug that caused path trace alerts to be missing from the filter selector in reports.
* We've adjusted the clearing behavior of path trace alerts. Prior to this change, if a specific network attribute was expected in a specific hop from the destination, and response from a path trace came back with a star \(\*\) response, it was possible for an alert to trigger which would never clear. We've adjusted this behavior such that a star response is acceptable in the clearing of the alert.
* Waterfall information available via the ThousandEyes API has been adjusted to correctly calculate the size of headers. Prior to this change, it was possible for the results to show a negative size for headers.
* The label on the timeline for DNS server tests when no server is selected has been adjusted to read "Average Minimum Resolution Time", as opposed to minimum resolution time. 
* We've added redirect behavior control to HTTP Server tests. As of this release, it is now possible to configure a test that would normally receive an HTTP/301 or HTTP/302 response to end before following redirects.

