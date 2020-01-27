# Release Notes: 2015-08-05

### Release update 2015-08-05

This week we're continuing with our growth: beginning this week, we'll start announcing our own Autonomous System, which means that we'll need to make a pretty major infrastructure change in the next couple of weeks.  
 

## New network, new AS number

On August 18th \(two weeks from today's release\), we'll begin using a different network, changing from 208.185.7.0/24 to 192.150.160.0/24. In the next two weeks we'll be making a DNS change, moving from mappings in 208.185.7.0/24 to mappings in 192.150.160.0/24, and announcing the new prefix in BGP.  ThousandEyes can be found under AS 394101.  Our IPv6 prefix is 2620:C2:4000::/48. 

**Old network: 208.185.7.0/24**  
**New network: 192.150.160.0/24**  
**New IPv6 subnet:  2620:C2:4000::/48**  
**ThousandEyes ASN: 394101**

Customers who have whitelisted ThousandEyes' 208.185.7.0/24 network or individual IP addresses within that network will need to update their whitelists in the next two weeks in order communicate withThousandEyes after the change. We will continue to advertise the 208.185.7.0/24 prefix following the update. [Contact our Customer Success team](mailto:support@thousandeyes.com?subject=New+Prefix+Help) if you have any questions.

## Dashboard and Report widget cloning

We've added the ability to clone Dashboard and Report widgets. Click the  icon while in Add/Remove widgets mode to clone a widget.  After clicking the Clone button, the duplicate widget will appear beneath the source widget. 

IMAGE MISSING

## Test settings

A couple of minor updates to options in test settings.

* We've added a 10-minute option for test interval to all Agent-based tests.
* Transactions can now be added using the ThousandEyes API. Refer to the [ThousandEyes Developer Reference site](http://developer.thousandeyes.com/) for more information.

## Agents

### Removal of Debian support

Due to complications with running Chromium on Debian 7, we are at this time removing support for Debian operating systems, focusing on the Red Hat Enterprise Linux \(6 and 7\) family, and Ubuntu Server LTS 12 and 14. Customers running the ThousandEyes Agent on Debian-based operating systems may wish to consider deployment on a supported operating system, or to use a container-based approach for running Enterprise Agents.  [Contact our Customer Success team](mailto:support@thousandeyes.com?subject=New+Prefix+Help) if you have any questions.

### Virtual Appliance running under NAT

Our release two weeks ago introduced some new components from a security perspective into the ThousandEyes Virtual Appliance, including an updated web server component for the VA configuration interface.  This caused issues connecting to the Virtual Appliance's configuration web server when the VA used port forwarding and network address translation \(NAT\) of the VA's host network adapter.  This affects customers running Virtual Appliance version 0.64, so customers will need to update the version of the Virtual Appliance in order to make this feature work.  Virtual Appliances auto-update every 3 hours, so just leaving a machine running \(assuming it has network connectivity\) will be enough to get the VA to update.

If you are in a situation where your Virtual Appliance configuration interface is unreachable due to this scenario, [contact our Customer Success team](mailto:support@thousandeyes.com?subject=VA+and+NAT) and we'll be happy to provide assistance.

## Scroll with ease

You can now scroll with ease in all views; after releasing an update to the Dashboard four weeks ago, where the map was updated to require focus in order to scroll, we've applied this same treatment elsewhere within the application.  To zoom in on the map with a scroll action, click on the map to focus \(it'll show up bordered in blue\), then scroll to zoom. Click outside the map to release focus.

## Tutorial video refresh

Our product marketing team has been working steadily over the last few weeks to release updates to the ThousandEyes tutorial video series, and the results are our best product demo videos to date.  Check out our all new videos using the links below:

[  
Getting Started with ThousandEyes](https://www.thousandeyes.com/resources/getting-started-tutorial)

Enterprise Agent Deployment

* [Enterprise Agent appliance deployment \(OVA\)](https://www.thousandeyes.com/resources/enterprise-agent-esxi-virtualbox-tutorial)
* [Enterprise Agent appliance deployment \(Hyper-V\)](https://www.thousandeyes.com/resources/enterprise-agent-hyperv-tutorial)

[Working with Web tests](https://www.thousandeyes.com/resources/web-tests-tutorial)

[Working with DNS tests](https://www.thousandeyes.com/resources/dns-tests-tutorial)

[Working with Network tests](https://www.thousandeyes.com/resources/network-tests-tutorial)

[Working with BGP tests](https://www.thousandeyes.com/resources/bgp-tests-tutorial)

[Using Path Visualization](https://www.thousandeyes.com/resources/path-visualization-tutorial)

[Working with Voice tests](https://www.thousandeyes.com/resources/voice-tests-tutorial)

[Working with Alerts](https://www.thousandeyes.com/resources/alerts-tutorial)

[Using Private BGP Peering](https://www.thousandeyes.com/resources/private-bgp-peering-tutorial)

If you have any suggestions on future videos, let us know by dropping us an email.

## Questions, comments?

I never get much love from these release notes, but just in case you feel like sending through a question or comment related to this release update, we really do love hearing from our customers. Drop us a line at [support@thousandeyes.com](mailto:support@thousandeyes.com?subject=2015-08-05+Update) and let us know what you think.

