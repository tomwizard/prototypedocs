# Release Notes: 2014-07-23

Wow, end of July already! During tonight's maintenance window, we cut our datacenter over to a new power system, in order to avoid a prolonged outage later this month - as a result, our maintenance ran a little longer than expected.  Check out some of the recent updates and see what's important to you.  

## Browser compatibility

We've updated the platform to prevent access to incompatible browsers, and display an appropriate warning message. Users using versions of Internet Explorer prior to version 9 \(or those using the compatibility mode option\) will now see the following page when attempting to authenticate into the platform. Our supported browser list includes current versions of Google Chrome, Safari, FireFox and Internet Explorer 9+.

IMAGE MISSING

## ThousandEyes Recorder 

We've deprecated the legacy version of the ThousandEyes recorder.  For versions that were not sourced from the Chrome store, users will begin seeing an icon atop the recorder icon in the toolbar, similar to the one below:

IMAGE MISSING

When clicking the link, users will see the recorder open, with a warning shown at the top of the window that there is an upgrade available.  Click the Install Now link to download the latest version of the ThousandEyes Recorder from the Chrome Store.  

IMAGE MISSING

Note for users with saved tests: your test data will be retained when upgrading to the new version of the ThousandEyes recorder.  Once you've installed the latest version of the recorder, it will self-update from the Chrome Store as we publish updates.

## BGP tests in Calculator

Beginning with tonight's release, a BGP test option will be available in the [Pricing Calculator.](https://app.thousandeyes.com/calculator)  Unit cost for BGP tests run at 8 units per 15-minute increment, regardless of how many monitors are used.

## API Changes

We've added a mappings field to the output of an API-based instant DNS trace test.  This is documented at the [ThousandEyes Developer reference site.](http://developer.thousandeyes.com/#/changesummary)

## Bugs squashed

### Agent Settings

We've resolved an issue that occurred during Agent settings modification for organizations with large numbers of Enterprise Agents and Tests. Prior to this fix, users would occasionally see service unavailable messages when attempting to modify sharing settings for, or delete an Enterprise Agent.

### Built-in groups for Enterprise Agents

We've added the IPv4 and IPv6 built-in groups to Enterprise Agents.  Prior to this update, these built-in groups were only being populated with Cloud agents.

### Charts in PDF-based reports

We've corrected an issue that occasionally occurred on large PDF-based reports, whereby certain charts were missing.

### BytesToDownload update

For HTTP server tests which included a bytesToDownload directive value exceeding 1000kB, this value was not being shown when viewing the test's settings. This has been corrected.

