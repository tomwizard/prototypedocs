# Release Notes: 2019-09-03

Welcome to our latest release!

Before the new blog and feature fun, a quick reminder about the next ThousandEyes Connect event:

IMAGE MISSING

Our next Connect will be held in Seattle on October 3rd, 2019 at the world-famous Space Needle! [Registration](https://www.thousandeyes.com/events/connect/seattle-2019) is open and free! Come rub elbows with your fellow ThousandEyes users and hear presentations on how ThousandEyes provides them with peace of mind. And if that's not enough reason to come to Seattle, then don't forget the spectacular views of [Mount Rainier](https://www.nps.gov/mora/planyourvisit/images/mountseries2rainierlentics-1-26-2011sdredmaneatvilwa_web.jpeg?maxwidth=1200&maxheight=1200&autorotate=false) from many locations in the city, a [museum](https://en.wikipedia.org/wiki/List_of_museums_in_Seattle) for almost any interest, an amazing [art scene](https://en.wikipedia.org/wiki/Arts_in_Seattle) \(Seattle is the [glass arts](https://www.seattlemag.com/article/how-seattle-became-epicenter-glass-art) epicenter of the US, dontcha know\) and one of the most wonderful [used bookstores](http://www.twicesoldtales.com/) in the world \(trust me, it's awesome; warning: NSF those with certain allergies\).

And speaking of Connect presentations, our Content Marketing Director Sean Coombs brings us the second post in his recap of Viacom's presentation at ThousandEyes Connect Chicago: [How Viacom Brings Reliable Real-Time Video to Millions of Customers](https://blog.thousandeyes.com/how-viacom-brings-reliable-real-time-video-to-millions-of-customers/). Have a peek at how Viacom uses ThousandEyes to instrument its massive video streaming infrastructure.

And now the details of tonight's release...

## Path Visualization enhancement for non-announced IP addresses

When a node in a Path Visualization is not part of any BGP-announced network prefix, we can now look for the network and autonomous system \(AS\) information for the node using whois. Routers in transit networks may use IP addresses which are not within a BGP-announced prefix, but those IP addresses will still appear when tracing paths. By using whois data, we can now provide the metadata.

## Kerberos proxy authentication for Appliances

The ThousandEyes Appliance's web administration now provides a configuration setting for authenticating with Kerberos to a proxy server, under the Network section of the web admin's UI:

IMAGE MISSING

Kerberos authentication can be used with either the Static or PAC proxy types.

## Dashboard/Report concurrent editing warning

In addition to warning a user when a Dashboard/Report is being concurrently modified by a different user, we now provide a warning when a Dashboard/Report is being concurrently modified by one user in multiple browser tabs.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release:

* A Report/Dashboard widget's color scale will now correctly handle two decimal places in the Scale setting,
* The /users and /groups API endpoints now contain all necessary meta attributes to be SCIM RFC-compliant.
* A change to the port number of a scheduled Endpoint Agent test is now correctly saved.
* Fixed an issue in the Endpoint Agent's Proxy Configurations which could permit a proxy without a name, preventing the configuration page from subsequently loading.
* Fixed an issue with Endpoint Agent snapshots replacing the scheduled test name with the snapshot name
* Fixed an issue with Endpoint Agent Network Topology which could display a DNS server address as 0.0.0.0.
* Fixed an Endpoint Agent issue causing missing Path Visualization for scheduled tests while Network Topology is displayed.
* Fixed an Endpoint Agent issue where a scheduled test configured for success on 300-level HTTP status codes had results colored in red instead of green when 300-level responses were received.

## Questions and comments

Got feedback for us? Want to tell us your favorite used bookstore story? [Send us an email](mailto:support@thousandeyes.com?subject=2019-09-03+Release+Update)!

