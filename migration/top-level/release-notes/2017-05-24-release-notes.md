# Release Notes: 2017-05-24

## Bug fixes & minor features

Here's the bux fixes and minor features in this week's release:

* The API now provides access to the Utilization statistic for Agent Clusters, in addition to Utilization for individual Enterprise Agents.
* An API request to create a Network test previously ignored incorrect "Protocol" field specifications and created a test with default values.  The API now correctly validates the Protocol field.
* Fixed a bug that prevented an Enterprise Agent with high utilization from being removed from an Agent to Agent test.
* Fixed a bug that prevented saving changes to test settings and generated an "Unable to process your request. Please try again later" error message.
* The Reports Snapshots page of an Account Group that has no snapshots displays a link to the Reports view which was pointing to the wrong page.  The link now points to the correct Reports page.
* When using the Duplicate function on a Report, the resulting copy is no longer itself duplicated.
* Fixed a BrowserBot issue that was generating a "Browser didn't initialize correctly" error.
* Fixed an issue with web pages that caused BrowserBot crashes and showed a timeout in waterfall data, but still produced screenshots.

## ​Questions, comments?

What's on your mind? Got comments about the blog articles? Suggestions for features you want to see in a future Release Update? We love hearing from our customers. Feel free to [send us an email](mailto:support@thousandeyes.com?subject=2017-05-24+Release+Update).

