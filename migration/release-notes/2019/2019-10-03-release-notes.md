# Release Notes: 2019-10-03

Welcome to our latest release!

Before the details of the release, a couple quick notes.

In case you missed the ThousandEyes Connect event in New York City earlier this year, Sean Coombs, our Content Marketing Manager summarizes one of the presentations--given by the VP of Advanced Technical Services for a major financial institution--in his most recent blog post, [Gaining End-to-End Application Visibility at a Top 10 Financial Institution](https://blog.thousandeyes.com/gaining-end-to-end-application-visibility-at-a-top-10-financial-institution/).

If you'd prefer the live experience to reading a summary, October is a great month for conferences. Multiple opportunities from all corners of the US await you. There's still time to sign up for ONUG Fall 2019 in New York City; Gartner IT Symposium/Xpo 2019 in Orlando; Florida, WAN Summit London; NANOG 77 and more! Check out our [events page](http://www.thousandeyes.com/events) for details. If you're headed to any of these events, stop by our booth and see what we're up to. There might be a [ThousandEyes t-shirt](https://www.thousandeyes.com/tshirt) in it for you!

And now for the details of our release...

## China Cloud Agents

We've added a dozen new Cloud Agents across multiple providers in China. Here's the list of Agent names/locations, as they appear in the app \(provider name in parenthesis, as usual\):

* Beijing, China \(China Telecom\)
* Beijing, China \(China Mobile\)
* Changsha, China \(China Mobile\)
* Dalian, China \(China Unicom\)
* Chongqing, China \(China Mobile\)
* Guangzhou, China \(China Unicom\)
* Ningbo, China \(China Mobile\)
* Shanghai, China \(China Unicom\)
* Shenzhen, China \(China Unicom\)
* Shenzhen, China \(China Mobile\)
* Tianjin, China \(China Mobile\)
* Zhengzhou, China \(China Mobile\)

Welcome to the Cloud Agent family. 你好 \(Ni how\)!

## Path Visualization improvements

A couple improvements in the way Path Visualizations are drawn for Enterprise and Endpoint Agents. First, we are using more information from neighbor nodes to determine whether a private \(RFC 1918\) IP address that appears in multiple Agent's traces is a single node common to multiple paths, or the same IP address used by multiple distinct nodes \(i.e. paths with no common node\).

IMAGE MISSING  
IMAGE MISSING

Also, we've improved the rendering of nodes near the target when forwarding loss is occurring. In the following image, the white nodes before the target will now be correctly rendered as forwarding loss on a single 10.12.16.86 node:

IMAGE MISSING

## Endpoint Agent permissions

To proive administrators with more granular control over displaying information which could identify an end-user or resource, the permission View endpoint data that identifies the user has been split into the following three permissions:

* View endpoint data that identifies Endpoint Agents  
   Allows users to see the names of Endpoint agents in the views. Users without this permission will see a numeric ID instead of the Agent name.

   Note that by default Agent names are taken from the name of the computer. Often, the computer name contains the name of the computer's primary user. In this scenario, to avoid identifying an end-user through the Agent name, administrators can either remove this permission or change the Agent name in the Endpoint Agent &gt; Agent Settings page.

* View endpoint data that identifies users  Allow users to view the name of the user on a computer where the Endpoint agent is installed. Users without this permission will see a numeric ID instead of the name of the user on the computer with the Endpoint Agent. The "Users" option will not be available as a Filter.
* View endpoint data that identifies network  Allow users to view the names of the IP networks being monitored as well as SSIDs and names and addresses of network devices such as routers, firewalls and proxies. Users without this permission will see a numeric ID instead of the network or device name or address.

By default, all existing Roles will have all of these permissions enabled.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release. Version numbers in parentheses indicate when a fix first appears \(when relevant, e.g. Endpoint Agent version\):

* Improved warning messages on the Endpoint Agents Settings page to better describe plug-in issues, and added the ability to filter on Agents with error messages
* Improved the aesthetics of the Overview tab of the Endpoint Agent's Browser Sessions
* Fixed an issue which could display "No Data" for the location in the tooltip of an Endpoint Agent on the Map widget
* Fixed an issue which could report the Current Location of an Endpoint Agent as "\(Unknown\)"
* Fixed an issue which could display an extraneous VPN server icon with address 0.0.0.0 for Endpoint Agents using Cisco AnyConnect VPN client
* Fixed an issue which displayed visited pages in the Endpoint Agent's Browser Sessions without first having configured Monitored Domains
* In the Endpoint Agent's Overview, Experience Score now displays correctly when filtering by User
* The Scale setting of a Number widget is now applied when Metric setting is Throughput
* In Path Visualization, clicking on the "Show in Device Layer" link in a device's tooltip now displays the device properly

## Questions and comments

Got feedback for us? Want to tell us about your mean boss who won't let you go to a conference? [Send us an email](mailto:support@thousandeyes.com?subject=2019-10-02+Release+Update)!

