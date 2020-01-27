# Release Notes: 2017-11-08

Welcome to the first ThousandEyes release night after the clocks turned back an hour \(unless you live in one of the locations around the world [without daylight savings](https://en.wikipedia.org/wiki/Daylight_saving_time_by_country) time\). We hope your time disorientation was minimal.

Speaking of things which cause disorientation... If you're in the USA and a user of internet service provider Comcast, you might have been disoriented yesterday. Our Senior Product Marketing Manager, Archana Kesavan, has a [blog post](https://blog.thousandeyes.com/comcast-outage-level-3-route-leak/) documenting yesterday's outage with backbone provider Level 3 which affected users across the nation.

And if you want to have a fun time connecting...

IMAGE MISSING

If you're in the New York City metro area, there's still time to sign up and come on down to ThousandEyes Connect on Thursday, November 9th! Great speakers, great t-shirts and great \(human\) networking await you. [Registration](https://www.thousandeyes.com/events/connect/new-york-2017) is still open.

And now, on to tonight's release!

## Current trial customers

If you're currently signed up for a trial account of ThousandEyes, a quick heads-up that this release will see the end of self-conversion of trials to paid accounts using a credit card. Going forward, you'll need to speak with your ThousandEyes Account Manager to convert your trial to a paid account. But don't worry, our Account Managers are all very friendly.

## New Reports snapshots scheduling interface

We're updating the interface for scheduling snapshots of Reports. Here's the new look and feel:

IMAGE MISSING 

No radical changes, but a bit more flexibility of configuration options, better organization and clarity. For example, we're now displaying the date and time of the next scheduled snapshot, based on the user's selections.

## Endpoint Agent

We've added the hop slider to the Network Topology view:

IMAGE MISSING

We've also applied the hop slider setting to all the elements that can appear in a path, such as VPN and DNS servers.

## Bugs fixes and minor enhancements

* Fixed an issue which prevented an Enterprise Agent installed on Ubuntu Xenial \(16.04 LTS\) from using configured NTP servers.
* Fixed an issue causing Enterprise Agents installed on Ubuntu to crash when checking for updates.
* Fixed an issue causing incorrect display of some Cloud Unit usage in the Usage tab. This issue was strictly display-related, and did not affect any actual billing.
* Fixed an issue causing some Instant Tests to fail to run.
* Added more specific text in the Device Manager's **Settings &gt; Device Settings** page when no unclustered Enterprise Agents were available. Previously the page displayed "No enterprise agents owned by this account group".
* Added the date range of a report snapshot to the /report-snapshots endpoint of the API, to allow for easier identification of specific snapshots.

## Questions or comments?

Like the new Reports Snapshot scheduling interface? Want to see some UI improvements elsewhere in the product? [Send us an email](mailto:support@thousandeyes.com?subject=2017-11-08+Release+Update) and let us know.

