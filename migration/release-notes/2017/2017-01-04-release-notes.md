# Release Notes: 2017-01-04

Happy New Year from the team at ThousandEyes!

A short and sweet release containing a number of bug fixes for the first release of 2017.  Please review the content below, and as always, if you have questions please [drop us a note](mailto:support@thousandeyes.com?subject=Release+Update+2017-01-04).

## Bug fixes

* We've made performance enhancements for user deletion.  Prior to this update, an attempt to delete either a user or an email address in a large ThousandEyes organization could result in an application timeout.
* We've made changes to ensure that Page Load and Web Transaction tests provide a screenshot when a test reaches the test timeout before completion.  Prior to this update, a test could fail to provide a screenshot when a test timed out before completion.
* We've corrected the behavior of alert notifications during alert suppression windows.  Prior to this update, in certain circumstances an alert notification was sent during an alert suppression window.  Note: this fix was deployed prior to this release.
* We've corrected an issue that prevented our API's SCIM-based user provisioning endpoints from working with PingFederate due to HTTP "content-type" headers.
* We've corrected an issue that could cause the legend on a bar chart widget in Reports to be offset by one Agent if an Agent with displayed data was deleted in the reporting period.
* We've published an updated version of the ThousandEyes Recorder Chrome Extension which fixes a number of issues.

 That's all for now!

