# Release Notes: 2019-09-17

Welcome to our latest release!

Before the news of the release, a quick spur to register for the next ThousandEyes Connect event:

IMAGE MISSING

The ThousandEyes user community will flock like cattle to Seattle on October 3rd, 2019 and round-up at the iconic Space Needle! So plan a trek to the Great Northwest. Your bonanza at the end of the trail includes a trio of big-brand hometown speakers from Microsoft, Alaska Airlines and Hewlett-Packard. These top dogies will tell you how their respective teams drive reliability, results and revenue using ThousandEyes. And of course, there will be ThousandEyes t-shirts waiting for you. Something to wear on the ride back to your ranch. This is gonna be wild as the Old West, so don't miss out! Registration is open now and totally free, so [go sign up](http://www.thousandeyes.com/events/connect/seattle-2019)!

In other news, our VP of Product Marketing, Alex Henthorn-Iwane, brings us a big bad blog post recounting [the DDoS attack](http://blog.thousandeyes.com/analyzing-the-wikipedia-ddos-attack/) on Wikipedia, this past week. See the story of the bad guys' attack unfold, ThousandEyes-style, and learn how Wikipedia circled their wagons to chase away the black hats.

And speaking of big announcements riding into town, our Director of Product Marketing, Archana Kesavan, brings news of a big new feature on the horizon, in her post: [Introducing Internet-Aware Synthetic Transaction Monitoring](https://blog.thousandeyes.com/introducing-internet-aware-synthetic-transaction-monitoring/). With words and video, Archana introduces this major upgrade in ThousandEyes' ability to monitor your web applications, just the way your real users use 'em. Whoopee ti yi yo!

Lastly, Alex is back with a blog post entitled [Agency Modernization Begins and Ends with Network Visibility](https://blog.thousandeyes.com/agency-modernization-begins-and-ends-with-network-visibility/). Honestly... I am at a loss make any relevant western-themed puns about this article. If you run an agency, are an agent of some type...? Maybe just go read it.

And now for the details of our release...

## Enterprise Agents

Back by popular demand! The Enterprise Agent page once again displays a colored \(green/yellow/red\) dot in the Status/Last Contact column.

IMAGE MISSING

Also, we've finished the UI improvements, with the Agent modals' drop-down selectors for Country and Region/City now having search boxes.

IMAGE MISSING

Makes it easy to adjust the location of your Agent from Boston to Cambridge \(or San Francisco to Berkeley if you prefer a West Coast analog\).

## Round-robin test scheduling

Browser-based tests \(Page Load and Transaction tests\) now have a new way to be scheduled. Previously, tests assigned to multiple Agents would all be scheduled to run on each Agent as soon as possible in each test round, typically resulting in tests running largely at the beginning of rounds. Using the new "Round-robin" option for the **Schedule** setting and the **Subinterval** setting, the test will be run at times spaced across the test **Interval** setting.

IMAGE MISSING

For more information on the behavior of these settings, check out our Knowledge Base article [Using Round-robin test scheduling](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000UHOuSAO_Using-Round-robin-test-scheduling).

## ServiceNow Notifications integration

Our ServiceNow integration for Notifications now supports the Madrid and New York releases of ServiceNow.

## Path Visualization enhancement for non-announced IP addresses

When a node in a Path Visualization is not part of any BGP-announced network prefix, we can now obtain network and autonomous system \(AS\) information using whois. For example, routers in transit networks may use IP addresses which are not within an announced prefix, but their IP addresses still appear in Path Visualizations.

IMAGE MISSING

We erroneously announced the release of this feature in the previous Release Notes. Our apologies.

## Usage and Quotas

 Weekly summary emails for quota-configured organizations and Account Groups have been updated to show the 31-day projection. This aligns with the Quota configuration page that displays configuration in _usage rate_ rather than consumption within the current billing period.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release, with a new twist--we're adding information on software versions in which a fix first appears \(when relevant, e.g. Endpoint Agent version\):

* Improved the appearance and usability of the Overview tab for Endpoint's Browser Sessions/Visited Pages View
* Fixed an Endpoint Agent Network Access view issue which could cause the Network Topology view's Wireless Signal Quality metric to be different from the Wireless view's Signal Quality metric
* Fixed an Endpoint Agent Label issue that could fail to update the name of a renamed Agent in the Matching Agents graph
* Fixed an Endpoint Agent Scheduled Test issue on Windows systems to support web pages encoded with gzip \(0.168.0\)
* Fixed an Endpoint Agent Scheduled Test issue which caused an Agent without access to its proxy server to attempt DNS resolution of the target rather than indicating no access to the proxy  \(0.170.0\)
* Fixed an Endpoint Agent issue displaying Visited Pages from unmonitored domains  \(0.172.0\)

## Questions and comments

Got feedback for us? Want to tell us your favorite [Zane Grey](https://en.wikipedia.org/wiki/Zane_Grey) story or [Tex Ritter](https://www.nytimes.com/1970/07/12/archives/from-grand-ole-opry-to-us-senate-high-noon-for-tex-ritter-high-noon.html) song? [Send us an email](mailto:support@thousandeyes.com?subject=2019-09-17+Release+Update)!

