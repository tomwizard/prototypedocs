# Release Notes: 2018-11-27

Welcome to today's release. For those in the northern hemisphere, winter is almost upon us, and for those in the south, please enjoy summer for the rest of us.

IMAGE MISSING

[Registration is open](http://www.thousandeyes.com/events/connect/chicago-2018) for ThousandEyes Connect in [Chicago](https://www.poetryfoundation.org/poetrymagazine/poems/12840/chicago) on December 5th, 2018! Come meet your fellow ThousandEyes users, and hear a lineup of great speakers discussing the ways that ThousandEyes has been put to work in their environments. And speaking of environments... Yeah, ok... it's Chicago in December. It's freezing. We get it. But if ThousandEyes Connect isn't enough to lure you to the Windy City, consider how much fun you could have on [frozen Lake Michigan](http://www.michiganradio.org/post/watch-speedskater-grab-rare-opportunity-glide-lake-michigan)! \(Note: We're kidding. We don't recommend venturing out on Lake Michigan, no matter [how fun](http://www.youtube.com/watch?v=Og5fFv3ozso) it looks. Go indoors and leave the skating to [the pros](https://www.nhl.com/blackhawks).\)

In ThousandEyes blog news, a long-time ThousandEyes customer from the financial sector declares our tech to be disruptive \(in a good way\). Our VP of Product Marketing, Alex Henthorn-Iwane, gives the disruptive details in his short-but-sweet post, [Why Credit Suisse Says ThousandEyes is Disruptive Tech](https://blog.thousandeyes.com/why-credit-suisse-says-thousandeyes-is-disruptive-tech/).

And now for the details of the release...

## Cloud Agents

We've added an IPv6 Cloud Agent in Austin, Texas. Howdy, partner!

## Enterprise Agents

### Enterprise Agents Settings

The **+ Add New Enterprise Agent** form on the [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) has been replaced with a button which opens a modal dialog, similar to other "Add New..." settings, such as for Alert Rules or Reports. 

IMAGE MISSING

The modal dialog opened is identical to the **+ Add New Enterprise Agent** form, and new Enterprise Agents will appear in the listing once the new Agent checks into the ThousandEyes platform, as before.

### Appliance support for server certificates

In the ThousandEyes Appliance, we've enhanced the interface to configure certificates needed for access to the web interface via https. In the **SSL Settings** section of the web interface, we now provide separate fields for:

* SSL/TLS server certificate \(and any intermediate certificates\)
* private key corresponding to the server certificate
* passphrase for the private key \(if the private key was created with a passphrase\) IMAGE MISSING

The file containing the private key and the file containing the server certificate and any intermediate certificate\(s\) must be in PEM format. If the latter contains multiple certificates then the file must begin with the server certificate, followed by any intermediate certificate\(s\).

Additionally, users can:

* view and delete the installed server certificate
* generate, view and download a certificate signing request \(CSR\) for a server certificate

By default, the Appliance is configured with a self-signed server certificate. If a user uploads their own server certificate, and then deletes their server certificate, the self-signed certificate will be restored.

## Custom Headers in Browser-based Tests

Page Load and Transaction tests \(a.k.a. Browser-based Tests\) now permit custom HTTP headers to be sent in HTTP requests other than the request for the root object.

IMAGE MISSING

Users can specify custom headers on a per-domain basis using the "Specific Domain" option, or send custom headers to "All Domains". Multiple custom header entries are created by clicking the **+** icon. A test may have multiple "Specific Domain" entries; "Root Server" and "All Domains" entries can appear only once.

## Reports

Users can now create Snapshots of multiple reports in a single operation. On the [Reports Settings](https://app.thousandeyes.com/settings/reports?) page, check the boxes of the desired reports, then click the **Snapshot** button at the bottom of the page. Users will select a time range of data to be included in the snapshot, which will applied to all reports in the group.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* The **Grouping** setting in the Path Visualization view now persists the Agent, Interface and Destination selections throughout a user's session
* Agent to Agent tests created with the API now default to port 49153
* Fixed an issue where the /tests API endpoint would repeat some test data
* Fixed an issue where the /audit API endpoint would return data in the user's configured time zone rather than UTC
* Fixed an issue which could prevent enabling Network measurements via the API
* Fixed an issue which could cause red or green arrows to be grey, in a Multi-metric Table widget of a Report
* Fixed an issue causing spurious "Dashboard updated" entries in the Event Log
* Fixed an issue which could cause failed logins when clicking the **Single sign-on** link on the app login page

## Questions and comments

Got feedback for us? Want to suggest a feature that would help us skate circles around the competition? [Send us an email](mailto:support@thousandeyes.com?subject=2018-11-27+Release+Update)!

