# Release Notes: 2018-04-25

Welcome to tonight's release!

We will be at [Interop ITX](https://www.interop.com/) in Las Vegas, from May 1st to the 3rd. Stop by the Exhibit Hall and say hello!

On to the latest additions to the ThousandEyes blog. Our Technical Marketing Manager, Ameet Naik, has released an [article](https://blog.thousandeyes.com/amazon-route-53-dns-and-bgp-hijack/) explaining how ThousandEyes detected the recent BGP hijack affecting Amazon's DNS service, Route 53.

Ian Waters, Solutions Marketing Director here in ThousandEyes, has written an [article](https://blog.thousandeyes.com/thousandeyes-helps-sidn-migrate-to-anycast-dns/) describing how SIDN \(Stichting Internet Domeinregistratie Nederland\) used ThousandEyes to assess the performance benefits of moving their DNS servers to anycast IP routing.

Additionally, our Vice President of Product Marketing, Alex Henthorn-Iwane, [published an example](https://blog.thousandeyes.com/monitoring-open-banking-apis/) of how users can leverage HTTP Server tests to monitor the availability of APIs mandated by the Open Banking Standard.

Without further ado, here are the the details of tonight’s release:

## API

A few additions and changes to the API: 

* Added Voice Call and SIP Server tests to the  "/tests" endpoint, as well as a “/voice/sip-server” endpoint
* The /voice/metrics endpoint has been renamed to /voice/rtp-stream, all requests to the old endpoint will be redirected with HTTP/301 response. 
* /voice/rtp-stream endpoint now provides RTP stream layer test data for both RTP Stream and Voice Call tests.

Be sure to check the [developer reference](http://developer.thousandeyes.com/v6/tests/) for more specifics on these changes.

## BGP

We now support BGP Alert Rules evaluating covered prefixes. Check the **Alert on covered prefix data** box on the Alert Rule’s settings.

IMAGE MISSING

## Cloud Agents

Three new broadband ISP locations have been added to our Cloud Agent portfolio:

* San Jose \(Charter Communications\)
* Ashburn \(Charter Communications\)
* Dallas \(Comcast\)

## User management

Basic Authentication and OAuth bearer token information has been moved back to the [Profile](https://app.thousandeyes.com/settings/account/?section=profile) tab under Account Settings.

IMAGE MISSING

## Bug fixes & minor features

* Waterfall Views for Page Load and Transaction Tests now include request timings for failed initial HTTP requests.
* The default monitoring profile for Endpoint Agents now features an expanded list of suggested SaaS domains. This change is only visible on accounts where no Endpoint Agents have been deployed.
* Fixed a bug where some monitored domains reported data for the Web View but no data for network traces.
* Fixed a bug on the Device Layer timeline where, in some cases, a previous round of data was incorrectly shown in place of rounds with no data.
* In the Topology view of Device Layer, the **Hide unknown devices** selection is now persistent across navigation between test and Device Layer views.
* Added support for extracting Device Layer topology information from certain Meraki switch models.
* Made improvements for time selectors on the Dashboard.
* Voice Call tests configured with a non-standard port no longer revert to the default port.
* Fixed an issue where SIP tests were sending path trace probes despite Network Measurements being disabled.
* Fixed an issue where incorrect information was returned from the /alert-rules API endpoint for alerts with no tests assigned.
* Added te-curl option to the te-agent-utils package

## Questions and comments

Comments or questions about tonight's release? [Send us an email](mailto:support@thousandeyes.com?subject=2018-04-25+Release+Update)!

