# Release Notes: 2017-02-16

For those of you traveling to [Cisco Live Berlin](https://www.ciscolive.com/emea.html) next week \(Feb 21 - Feb 23\), come by the ThousandEyes booth E55 \(Hall 3.2 - World of Solutions\), chat with the product team and grab yourself one of our new “go ahead, blame the network” t-shirts.  

Also, check out [Archana Kesavan's](https://blog.thousandeyes.com/author/archana/) latest blog post analyzing the implications of VPN performance on end-user experience, and how to monitor VPN-oriented networks using ThousandEyes Endpoint Agents.  You can read more on the ThousandEyes blog, [here](https://blog.thousandeyes.com/how-virtual-private-networks-impact-performance/).

This week we deviated from our regular Tuesday night release schedule in order to allow our engineers to spend Valentine's Day with their loved ones.  That said, there's a lot packed into this small release, so check out the updates below.

## Cloud Agent changes

 First, we've changed our provider in San Francisco in order to allow elastic expansion in this location.    
Second, in keeping with our recent IPv6 deployment trend, we've added IPv6 locations in the following locations:

* San Jose, Costa Rica
* Johannesburg, South Africa

For a full list of our agent locations, [check out our website.](https://www.thousandeyes.com/product/cloud-agents)

## Enterprise Agent changes

 We've made a number of updates in this release regarding Enterprise Agents.

### Browser version upgrade

BrowserBot, the component of Cloud and Enterprise Agents that runs Page Load and Transaction tests, is getting a major upgrade.  BrowserBot runs the Chromium browser, which is being upgraded to version 55, except for Enterprise Agents running on Red Hat 6 and CentOS 6.  Enterprise Agents running on Red Hat Enterprise Linux and CentOS 6 will remain on Chromium 40.

### Adobe Flash support

 We've updated the package used to provide Flash support to Enterprise Agents that run BrowserBot.  While Flash is not a requirement of the enterprise agent, we make the option available for customers to deploy as needed.  Flash is now added to new installations of the Enterprise Agent Appliances and Docker container.

### Dual-stack networking support

We've added support for dual-stack \(IPv6 and IPv4 address families\) Agents in this release.  With this update, users will be able to assign an Agent that has addresses in both families to tests that have IPv6 or IPv4 targets. The behavior of a test assigned to the Agent is based on the **IPV6 SETTING** option in the Agent Settings.  An image of the option from the Advanced Settings tab of the Agent Settings page is shown below:

IMAGE MISSING

The policy option allows the user to select one of three options:

* **IPv4 only**: The Agent will use an A record in DNS resolution of the test target's name to an IPv4 address
* **Prefer IPv6**: If an AAAA record is available in DNS, the Agent use it for DNS resolution of the test target's name to an IPv6 address.  If no AAAA record is available, the Agent will use A records and IPv4 addresses.
* **Force IPv6**: The Agent will only use an AAAA record.  This is the behavior of legacy IPv6 Agents.

For an IPv6 Enterprise Agent being upgraded, the **IPV6 SETTING** will be set to "Force IPv6" in order to maintain the same behavior before and after the upgrade.

**Note**: all browser-based tests \(Page Load and Transaction tests\) will prefer IPv6, regardless of the policy chosen in the Agent Settings page.

### Linux package installation script

 The agent installation script has been updated to remove the -i option \(interface selection\) and add the -F option \(add support for Adobe Flash in BrowserBot\).  For help with the Linux package installation script, run the script with the -? argument.  Information on installing the Linux package can be found in [this KB article.](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS)

### Appliance unlock

 With this release, users can now unlock the ThousandEyes Appliance.  Unlocking an Appliance will allow users to install packages and otherwise make changes to the system configuration.

**Warning**: customers who unlock ThousandEyes appliances should be aware that if issues are encountered with an unlocked appliance, the ThousandEyes team will provide support to those appliances on a best-effort basis.  If those efforts are unable to find a suitable solution to the issue, our recommendation to resolve the issue may be to re-deploy the appliance in a factory state.

To unlock a ThousandEyes appliance, [install the te-va-unlock package](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvrCAC).  Installing the package will unlock the appliance, allowing authorized users who ssh into the appliance to install packages and make system configuration changes.

###  Dependency updates

As a result of these changes, we've updated our dependency tree documents.  Check out that article [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnSKAS).

## Endpoint Agent

 A few updates in the area of the Endpoint Agent this week:

* Introduced detection support for Palo Alto Networks and Cisco AnyConnect VPN clients.  When connected to a VPN using these clients, network adapters will now show based on the appropriate connection type, rather than via ethernet.
* Improved location detection, specifically for cases where computers are connected behind a VPN.
* Improved the stability of the Internet Explorer plugin
* Added support for installation of the Endpoint Agent on Windows Server 2012 without the Windows Wireless LAN Service feature installed.  Prior to this update, the installer would crash if the feature was not installed.
* We've added a filter for monitored networks into the views, and changed grouping options to include location.and private network. 

## Upcoming planned maintenance \(2/23/2017\)

We're announcing 2 hours of planned maintenance on February 23, 2017 beginning at 03:00 UTC.  During this update, we will be applying software updates to devices on our edge.  Users may experience minor disruptions in service during failover to secondary devices while the update is in progress.  Customers who are running BGP peering sessions with ThousandEyes may experience flaps during this maintenance.

Updates for this maintenance announcement are tracked in [this KB article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cnu0CAC).

## Reduced support hours 2/27/2017 through 3/3/2017

 We'll be reducing our support hours between February 27 and March 3rd.  Instead of our normal 24x5 chat support, we'll be offering support this week between the hours of 6am and 8pm Pacific Standard Time.  This is to allow us to bring all resources into a single location and plan the upcoming year.  We'll revert to normal support hours beginning on Monday March 5th.

If you have any urgent requests during normal service hours \(8pm to 6am\), please feel free to email our team and we'll be happy to respond as soon as we can.

## Questions and comments?

 As always, we'd love to hear from you.  [Drop us a note](mailto:support@thousandeyes.com?subject=Release+Notes+2017-02-16), and we'll be sure to get you a response posthaste.  
 

