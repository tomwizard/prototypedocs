# Release Notes: 2013-05-21

We delayed our release last week to bring some very new and cool features to the product, updating usability, increasing performance, and making your virtual infrastructure easier to manage!  Changes are detailed below.

## New Features

### Previous and Next round buttons on timeline

We have added buttons to the timeline to allow navigation between rounds of testing. These buttons will take the currently selected round of testing, and navigate one step backward or forward, using the previous \(&lt;\) and next \(&gt;\) buttons, respectively. This is particularly useful when looking at the Path Visualization and BGP Route Visualization views, in order to understand changes captured at the network level for each test.  In the image below, each of the timeline zoom and navigation controls has been identified:

IMAGE MISSING

1. Context selection - choose either to show 14 days or 24 hours of context in the timeline.  This selection controls the behavior of the Zoom Out button \(\#2 below\)
2. Zoom out - click here to zoom out to the level of context selected in \#1 above.  For example, if 14d is selected, clicking Zoom Out will show the entire 14 days of data in the timeilne.
3. Previous button - click here to step back one testing interval on the timeline.  For example, if your test runs every 15 minutes, clicking the previous button will jump back on the timeline by 15 minutes.
4. Next button - click here to step forward one testing interval on the timeline.  For example, if your test runs every 15 minutes, clicking the next button will jump ahead on the timeline by 15 minutes.
5. Latest - takes you to the latest data available.

### Live sharing

Sharing your test results has never been easier: we've renamed the classic share link feature to shared snapshots. This feature is the same as it was under the share link nomenclature, and is now accessible by navigating to the new top navigation menu \(Sharing\), and drilling down to snapshots. We've also added a new feature, called _**Live Sharing,**_ which allows you to share a live view of your test with another ThousandEyes customer. When the recipient of the live sharing link receives the authorization link, the test will be added to that user's account, and will be represented in the dashboard and other areas of the application with a paperclip.  This is particularly useful when working with an external vendor, but you are unable to provide that vendor with access to your own virtual agents.

IMAGE MISSING

1. When looking at the dashboard as the recipient of a Live Share, a paperclip icon denotes a shared test.

To create a live share, click the "Share this Screen" link in the upper right corner of the test view, and click the "Live Sharing" tab, and enter the recipient's email address.  Clicking the share button will send an email to the user with a one-time authorization code, to enable the test to be shown within their list of tests.  Once the recipient has clicked on the authorization link, the test will be added to their account as a shared test.

IMAGE MISSING

If at any time you wish to revoke access to the share link, simply browse to Sharing &gt; Live, and click the Shared by me tab. The status of each share link will be shown, and the live share can be revoked by clicking the trash can icon.

IMAGE MISSING

1. Each share is shown in a table; the account name of the recipient of the share will be shown, as well as the user who initiated the live share, and how long the share has been active.
2. When _pending_ is shown under the test name, this is an indication that the recipient of the Live Share has not yet clicked on the authorization link.
3. Click the trash can icon to remove the share link.  This will remove the live share from the recipient's dashboard and list of tests.

Note: Live sharing is active until the share has been cancelled, and recipients of live shares cannot create a snapshot link, view alerts, or generate reports based on the content of a live share.

### Mini-dashboard widget

When you log in, you'll notice a new pop-out menu on the left hand side of the page. This is known as the mini dashboard. We've relocated the messages icon from just above the timeline, as well as pulled in agent alert information and monthly account utilization.

To activate the mini-dashboard, click one of the icons on the left hand side of the page. The dashboard will pop out, and you will be able to view any relevant alerts, Enterprise Agent problems, and activity on your account. The number of alerts for the messages and Enterprise Agent components will be shown in an orange badge to the upper right corner of the icon.  Below, a sample of each expanded section is shown.

IMAGE MISSING

### Locations are now known as Agents

Since the 'location' nomenclature didn't aptly describe a Enterprise Agent, we've switched the name location to "Agent". Agents still have location identification \(based on geolocated IP addresses, by default\), but servers acting as ThousandEyes will henceforth be known as agents, rather than locations.

### Instant tests get richer!

Many of you have used the instant test capability of the platform to run traceroutes from a specific location to your target, which was extremely useful. With this release, we have improved on the instant traceroute test, by adding Path Visualization to the results of the test. Below, an example is shown, running an instant traceroute test to www.reuters.com:80:

IMAGE MISSING

### Bandwidth Estimation \(Beta\)

We're beginning a private beta beginning with this release, for a new type of network test, which measures estimated bandwidth between sites. As such, certain customers may notice new options available under any test which includes network measurements, to estimate the bandwidth between the agent performing the test and the test target.  Bandwidth estimation user interface elements will be found for certain customers in the following areas:

* Network test view, metric option for Bandwidth
* New test page, when enabling network measurements, a sub-option to 'Enable Bandwidth Measurements'
* Instant test &gt; Network &gt; Bandwidth

More information will be made available on the Bandwidth Estimation feature in a subsequent release.

## API Changes

Continuing along the path of making the ThousandEyes API bigger, stronger and faster, we have completed work on the following API changes:

### Rate Limiting

We have introduced rate limiting into the ThousandEyes API with this release. Following this update, each account will be limited to 2 API calls per second, or 600 calls every 5 minutes.  If an organization exceeds 600 API calls in a 5 minute period, the API will return an HTTP/429 "Too many requests" error.  After the 5 minute period from the first call has elapsed, the counter will be reset and API calls will continue.

Note: we are cognizant of the fact that many organizations are leveraging the ThousandEyes API in monitoring solutions;  We are actively monitoring the level of usage of the API and may make adjustments to the rate limit as required.

### Result paging

In order to handle large queries, we have introduced result set paging into the API. Beginning with this release, queries which target results in a window larger than 60 minutes will be limited to 100 records per page. The teResults object now contains a new child object called pages, containing the following elements:

* current \(integer\), designates the page number of current results
* first \(URL\), designates the first page of results for the current query. Note: this element is not present on the first page of results.
* previous \(URL\), designates the URL of the previous page of results for the current query. Note: this element is not present where there is no previous page of results.
* next \(URL\), designates the next page of results for the current query. Note: this element is not present where there is no next page of results.
* last \(URL\), designates the last page of results for the current query. Note: this element is not present on the last page of results.
* total \(integer\), designates the total number of pages of results.

If your query was based on a window of time \(example: window=4h\), then the first, previous, next and last links will be translated to include from and to parameters. This will avoid time drift in your results while the data is being processed.

Sample output can be found below for both XML and JSON versions of the endpoint:

XML representation:

```text
<pages>
<current>2</current>
<first>https://api.thousandeyes.com/web/page-load/1158.xml?authToken={token}&amp;from=2013-05-21+15%3A00%3A00&amp;to=2013-05-22+01%3A15%3A00&amp;page=1</first>
<previous>https://api.thousandeyes.com/web/page-load/1158.xml?authToken={token}&amp;from=2013-05-21+15%3A00%3A00&amp;to=2013-05-22+01%3A15%3A00&amp;page=1</previous> 
<next>https://api.thousandeyes.com/web/page-load/1158.xml?authToken={token}&amp;from=2013-05-21+15%3A00%3A00&amp;to=2013-05-22+01%3A15%3A00&amp;page=3</next>
<last>https://api.thousandeyes.com/web/page-load/1158.xml?authToken={token}&amp;from=2013-05-21+15%3A00%3A00&amp;to=2013-05-22+01%3A15%3A00&amp;page=11</last>
<total>11</total>
</pages>
```

JSON representation:

```text
"pages": {
 "first": "https://api.thousandeyes.com/web/page-load/1158.json?authToken={token}&page=1&from=2013-05-21+15%3A00%3A00&to=2013-05-22+01%3A15%3A00",
 "next": "https://api.thousandeyes.com/web/page-load/1158.json?authToken={token}&page=3&from=2013-05-21+15%3A00%3A00&to=2013-05-22+01%3A15%3A00",
 "previous": "https://api.thousandeyes.com/web/page-load/1158.json?authToken={token}&page=1&from=2013-05-21+15%3A00%3A00&to=2013-05-22+01%3A15%3A00",
 "last": "https://api.thousandeyes.com/web/page-load/1158.json?authToken={token}&page=11&from=2013-05-21+15%3A00%3A00&to=2013-05-22+01%3A15%3A00",
 "current": 2,
 "total": 11
 }
```

### New Endpoints added

The following endpoints have been added to the ThousandEyes API for DNS+ queries.

```text
/dnsp/availability/{testId}/{countryId}/network
/dnsp/mappings/{testId}/{countryId}/network
/dnsp/resolution-time/{testId}/{countryId}/network
```

The /dnsp/.../{testId}/{countryId}/network endpoint will return a list of all networks for which we are aggregating information, and will show the appropriate metric for each specific network.

```text
/dnsp/availability/{testId}/{countryId}/network/{asn}
/dnsp/mappings/{testId}/{countryId}/network/{asn}
/dnsp/resolution-time/{testId}/{countryId}/network/{asn}
```

The /dnsp/.../{testId}/{countryId}/network/{asn} call returns the list of the selected metric, for the specific provider specified in the {asn} field.

### Two API bugs fixed

* Duplicated BGP data was being returned in certain circumstances via the /net/bgp-metrics/{testId}/{prefixId} endpoint.
* The /net/bgp-metrics/{testId}/{prefixId} endpoint has been adjusted to always return data in 15 minute intervals, since BGP data is aggregated from various monitors on a different schedule than typical tests.

## Virtual appliance updates

The ThousandEyes virtual appliance has been updated. First, we've added a setup wizard to the virtual appliance configuration webpage. This wizard will take you through initial configuration of the virtual appliance, making sure to verify the various settings along the way.

The steps in the virtual appliance configuration run through the steps to get your Virtual Appliance configured, including Network Configuration, Time Server configuration, hooking the agent up to your account, and then verifies your settings to ensure optimal operation.  An image is shown below of the ThousandEyes virtual appliance configuration wizard.  The configuration wizard is the first page opened on the virtual appliance after authentication.

IMAGE MISSING

We've also added IPv6 support to the ThousandEyes Virtual Appliance, which can be configured using the Network tab of the configuration page.

## Enterprise Agent updates

We have resolved an issue which could occur when the IP address of a Enterprise Agent was changed, but the agent had not been restarted.  Prior to this release, if this scenario occurred, the Enterprise Agent would be unable to gather network measurements while a mismatch between the IP address of the appliance and the IP address of the appliance, as known by the agent collector.  Beginning with this release, the agent code will validate the IP address during check-in with the Agent collector.

