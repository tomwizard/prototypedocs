# Release Notes: 2016-07-20

Some great stuff coming your way in this release, but first a quick recap of last week's big conference.

IMAGE MISSING 

Thanks to everyone who came to visit the ThousandEyes booth at Cisco Live!  We hope you said hi, picked up a tee shirt or maybe took in a presentation on the new features of the product.  Cisco was very gracious in lending us the services of Project Manager Andrea Di Lecce to help us roll out the new ThousandEyes Enterprise Agent for their **Cisco IOS XE** platform.  We're very proud to be the first 3rd-party application for the Cisco ISR-series and ASR-series routers!  For those of you unable to make it to the conference, you can read about this new Enterprise Agent platform on the [Cisco Communities blog](https://community.cisco.com/t5/network-architecture-blogs/first-3rd-party-application-running-on-an-isr/ba-p/3659062).

## Cloud Agents

Our list of worldwide locations for Cloud Agents keeps growing. We've added a new Cloud Agent location in Panama City, Panama.  This Cloud Agent is available to customers with a paid subscription.  The full [list of Cloud Agent locations](https://www.thousandeyes.com/product/cloud-agents) is available on our website.

## Outage Detection

We’re also very excited to announce Outage Detection, a new set of features that helps you determine when performance or availability issues are due to an outage somewhere in the Internet, in networks other than last-hop networks \(transit networks\). Outage Detection uses generic data from all of ThousandEyes’ customers tests to locate outages and display the information in the tests you’re running.

Outage Detection is free of charge for all users.  To help you learn more about Outage Detection, we have new articles in the ThousandEyes Knowledge Base.  Start your introduction with the [Outage Detection Overview](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC), and then get into the specifics of the [routing plane](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmsmKAC) and the [data plane](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmsjKAC).

## Report Widgets

To facilitate creating presentations and similar tasks, we've added the ability to export a widget \(for example, a table, bar chart or time series\) as an image file in PNG or JPG format.  Click the More Options icon on the widget to display the "Save As Image" option. 

## Path Visualization

We've updated the styling of Path Visualization's tooltips to make them clearer and easier to use.  For example, we include a legend at the top to identify what type of object is being displayed and the object's state--no more needing to remember the meaning of node colors! When you mouse over a node or a link, you'll see the new tooltip:

IMAGE MISSING

We've also changed the behavior of the slider which displays the number of nodes \(hops\) in the path from the Agent and from the target. Previously, the slider settings were not retained when refreshing the page or logging out. Now the settings are retained, even across browsing sessions.

## API

For the currently supported versions of the API \(version 5 and version 6\) we have added the following:

* Some settings not previously available on the Advanced Features tab of HTTP Server tests \(for example, the **User-Agent** or **Override DNS** settings\) are now available
* API responses now contain a "Cache-Control: no-cache" HTTP header to ensure certain proxies do not cache API responses   

## Bugs squashed

* We've corrected an issue which caused certain Alert Rules to trigger sooner than their configuration of "x of y" rounds of data.
* When an Enterprise Agent Cluster member was removed, Agent-to-Agent tests whose target was the removed cluster member were not updated. This has been fixed.
* We've corrected an issue which caused the Duplicate Test button to fail to include the User-Agent setting in a Web Layer test.   

## Questions or comments?

We would love to hear from you! Send us your questions or comments and we'll be happy to answer them. Send us[ an email!](mailto:support@thousandeyes.com?subject=2016-05-25+release+update)

