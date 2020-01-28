# Release Notes: 2017-10-25

Welcome to a major new feature release!

Before the big new news, some quick announcements.

## ThousandEyes Connect

IMAGE MISSING

ThousandEyes Connect in New York City is November 9th. [Registration](https://www.thousandeyes.com/events/connect/new-york-2017) is open.

Can't make it to New York? Maybe we'll be at an [event in your area](https://www.thousandeyes.com/events).

On to the big news! We are proud to release our latest new feature: Device Layer. We're digging deeper, down into the protocol stack to layer 2, to get you information and monitoring data from your network's devices. Check out the ThousandEyes blog post [Introducing Device Layer: Diagnose Root Cause from App to Network Device](https://blog.thousandeyes.com/introducing-device-layer-network-device-monitoring/) from Product Manager Gopi Gopalakrishnan for more details on what Device Layer can do for you!

We're also very excited for ThousandEyes' appearance on the [Packet Pushers podcast](http://packetpushers.net/series/weekly-show/) in early November. Tune in for a discussion of Device Layer and VoIP testing, or sign up for our [Device Layer webinar](https://www.thousandeyes.com/webinars/network-device-monitoring?utm_source=Marketo&utm_medium=Email&utm_campaign=NA_Q3FY18_All_All_DeviceLayerLaunch_ProspectEmail&mkt_tok=eyJpIjoiWkRJNU56VXlaamxqTXpZNCIsInQiOiJOTk90VE12WFwvaVwvWnc3Wit6Qk03bnplbUtQOEVMbkF0UzcrWGZscktON09hT2VYUkJcL0xpdnViem9Ma2lsSm1XKzV1c1ZcL1krc3dXKzBlR0NTSGRlTzhYMWtPQVk3a0J0QTVHQzhwdVwvSFJGY0VBSTdWdlpzaFZzZ1FJVUU2anBVIn0%3D).

## Device Layer

Device Layer uses SNMP polling by ThousandEyes Enterprise Agents installed on your network to automatically discover network devices. Provide some basic configuration, and Device Layer will automatically find and monitor whatever SNMPv2c- or SNMPv3-capable device you want--routers, switches, firewalls, load balancers, wireless access points, and more! The data from Device Layer is provided to the Device Layer view, and is added to the Path Visualization view on any test with a Path Visualization that's run from an Enterprise Agent configured for Device Layer monitoring. Switch from the Path Visualization view to Device Layer view with a single click on a device.

IMAGE MISSING

Existing customers will have immediate access to Device Layer, with access from five monitored devices. Contact your ThousandEyes Account Manager for additional capacity.  
  
Documentation for [configuring Device Layer](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpmKAC) and for [interacting with the Device Layer data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpqKAC) can be found in our Knowledge Base.

## Renamed view

More news of views... In order to accommodate future enhancements and maintain accurate nomenclature, the End-to-End Metrics view has been renamed to the Overview. Same great metrics; new view name. API endpoints are not affected by this change.

## New Cloud Agents

We've added a second IPv4 and IPv6 Cloud in Tokyo, Japan. This second Tokyo Cloud Agent, "Tokyo 2", uses NTT as its primary internet service provider.

## Bugs fixes and minor enhancements

* Fixed an issue with Transaction tests causing a "Page load timed out \(interrupted\)" error message.
* Transaction test errors now support UTF-8 characters.
* We’re now forcing timeline alignment on full-width widgets for Reports & Dashboards. 
* Added IPv6 IP address to the tooltip of a Dashboard Enterprise Agent widget.

## Questions or comments?

What's your favorite layer of the OSI model? Drop us a note and let us know the answer, or tell us whatever else is on your mind. [Send us an email](mailto:support@thousandeyes.com?subject=2017-10-25+Release+Update).

