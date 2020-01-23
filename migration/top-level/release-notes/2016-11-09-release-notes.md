# Release Notes: 2016-11-09

Tonight's release night comes on election day, here in the US of A.  Bear with us while we get the bugs out of the system.

Political jokes aside, we've got some promises to deliver on, so without further speeches...

## New Cloud Agent Locations

We're proud to welcome new a Cloud Agent location in the USA in Austin, Texas, two Canadian locations in Winnipeg, Manitoba and Edmonton, Alberta, and an Australian addition in Perth, Western Australia.  A kiss to the new babies.

## ​Tests

Back by popular demand: we're reverting our recent color scheme changes to the timeline, with some minor tweaks.  Seems the one-color-fits-all-test-metrics was not polling well with the electorate.

FTP Server tests have had the Target field separated into two fields, one for the server name, and one for path.  This will provide some clarity via differentiation and on-screen help text as to whether to specify an absolute or relative path for your chosen protocol \(FTP, SFTP, FTPS\).  Consult the [Working with Test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn7KAC) article in the ThousandEyes Knowledge Base for more information.

## Single Sign-On

Single sign-on \(SSO\) metadata can now be downloaded from your identity provider and uploaded into ThousandEyes to configure SSO.  As with voting, we strive for maintaining your privacy and data integrity while improving convenience.

## Alert Rule Notifications

Alert Rule notifications sent to the Slack messaging application can now use the @user syntax to call a user's attention to the message.  Simply use the "@user" syntax in the **Channel** field of your Slack Alert Notification, just as you would use "\#channel"  Get your Slack [@users](https://get.slack.help/hc/en-us/articles/201259356-Slash-commands) out to vote at a Slack [/poll](https://get.slack.help/hc/en-us/articles/229002507-Polls-in-Slack).

## Minor features & bug fixes

 The down-ballot winning candidates...

### API

* Ping payload settings are now available via the API.
* An issue which omitted the Duration attribute of a Voice layer test in API results is now fixed.

### Enterprise Agents

* Improved the Install Type descriptions of Enterprise Agents to include physical appliances and Docker containers.
* Fixed an issue in the Linux package installation script that prevented the Agent process from starting on systems running systemd to manage services.

### Endpoint Agent

* Added the ability to filter by Location in the Network Topology View of the **Views &gt; Endpoint Data** page.
* Added a Quick Link to Session details inside the Agent tooltip in the Network View of the **Endpoint Data** page.
* Improved the user experience for indicators of success or failure to visit sites in the expanded rows of the Endpoint Agent's Session Details View.
* Fixed an Endpoint Agent Network Topology bug where the **Network** filter displayed network names incorrectly in the link's drop-down menu.

### Tests

* Fixed an issue in which Agent to Agent tests which would report the private IP address of a target
* Content verification settings for the HTTP Server portion of a Page Load test are correctly preserved in all circumstances.

### Miscellany

* Fixed a bug with Dashboard widgets that caused failure to load under certain conditions.

## Questions or comments?

 It's your right as our valued customer to petition us at ThousandEyes and give us your feedback.  Send that [mail-in ballot to us](mailto:support@thousandeyes.com) and tell us what you vote for. Or against.  We'll be sure your vote is counted.

