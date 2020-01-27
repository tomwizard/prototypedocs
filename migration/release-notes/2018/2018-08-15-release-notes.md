# Release Notes: 2018-08-15

Welcome to tonight's release! A big Amazon AWS-related new feature, an important annoucement for some API users, and more...

But first... In ThousandEyes blog articles, Senior Product Marketing Manager Angelique Medina has been busy. Her first post, [One Resolver to Rule Them All: Ranking the Performance of Public DNS Providers](https://blog.thousandeyes.com/ranking-performance-public-dns-providers-2018/), adds to ThousandEyes' history of looking at performance of public DNS services. Also mentioned: improvements to the security and privacy of the Domain Name System \(DNS\) that are being rolled out by some providers. Spoiler alert: no hobbits, elves, dwarves, wizards, rangers, ents, goblins, orcs, trolls, giants, dragons, balrogs, Black Riders or a Dark Lord, here.

In our second new blog post, Angelique recounts ThousandEyes' presentation and related presentations and conversations at the recent Google cloud conference, in [Google Cloud NEXT ‘18: Rainbow Unicorns and Multi-Cloud](https://blog.thousandeyes.com/google-cloud-next-2018-rainbow-unicorns-multi-cloud/). A great article for those interested in the challenges of our new multi-cloud reality. Spoiler alert: there's only one unicorn, and it's in the title.

And now for the details of tonight's release...

## Enterprise Agents

### Enterprise Agents for Amazon Web Services

We're happy to announce the first of our Enterprise Agents deployment options that are native to major infrastructure-as-a-service \(IaaS\) providers. Tonight, it's Amazon Web Services. The **+Add New Agent** form on the Enterprise Agents page includes a new tab, **IaaS Marketplaces**, with a link to a CloudFormation template which creates an Ubuntu AMI \(requires authentication to the user's AWS account\). The CloudFormation template allows users to set their account token, region and VPC.

IMAGE MISSING

Instructions for configuring the AWS Enterprise Agent can be found in the ThousandEyes Knowledge Base article [IaaS Enterprise Agent deployment - Amazon AWS](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009S1nCAE_IaaS-Enterprise-Agent-deployment---Amazon-AWS). The **AWS Deployment Guide** link on the **+Add New Agent** form also links to the article.

### Centralized proxy configuration for tests

Enterprise Agents can now be configured with proxies for tests via the application. Create a proxy configuration on the [Settings &gt; Proxy Settings](https://app.thousandeyes.com/settings/proxy) page. Proxies can be configured statically--specifying the hostname, port number and \(optionally\) a bypass list, or assigned dynamically by loading a PAC file from a URL. HTTP Basic or NTLM authentication types can optionally be selected:

IMAGE MISSING

A specific proxy configuration can be applied to multiple Enterprise Agents or Enterprise Agent Clusters using the Agents selector:

IMAGE MISSING

Settings from the application will override any locally configured proxy settings for tests. Local proxy settings will not be overridden for communication to ThousandEyes' infrastructure or to linux repositories.

## Reports

We've improved the creation of new reports, in conjunction with new sources of data for reports. Users will first select the data source \(Cloud and Enterprise Agents, Endpoint Agents, Alerts, and Routing\). Subsequent selections will be filtered to only the relevant metrics available for the data source. Depending on the selection, further selections may become available.

## API

We've improved the response of the API to certain queries which return large amounts of data, by changing the way pagination is performed. **Note** however that the changes made required us to deprecate the ability to move backward in pages of data using the previous parameter of the pages object. Additionally, the change will require strict adherence to the [pagination rules](http://developer.thousandeyes.com/v6/#/pagination) set forth in the API documentation. Crafting URLs to move forward through multiple pages of data must now be performed using the URL provided by the next parameter of the pages object. Scripts which request pages of data using the page parameter in an API URL or through other means may now break.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release:

* In the Path Visualization view of Agent to Agent tests, the tooltip produced by mousing over a source Agent more clearly indicates the end to end metrics and which direction produced the metrics
* In the Path Visualization view, a group of destination nodes is now shown with a black border, to distinguish the group from intermediate nodes
* Virtual Appliance web administration console now correctly displays the proxy bypass list
* Virtual Appliance web administration console no longer hangs on certain errors when parsing PAC files
* Waterfalls of browser-based tests no longer display too large Wire Size with certain compressed responses
* Waterfalls of browser-based tests now indicate "\(Cached\)" correctly for certain responses taken from the browser's cache
* The Alert Settings page now displays correctly with Internet Explorer
* The calendar widget in the Alert History tab of the Alerts page now advances the month correctly in all cases
* Fixed an issue causing the Deleted Test link not to be displayed
* Fixed an issue causing previously discovered devices without credentials in Device Layer to be hidden in the list of devices

## Questions and comments

Got questions or feedback on the new features? Just want to talk Tolkein? [Send us an email](mailto:support@thousandeyes.com?subject=2018-08-15+Release+Update)!

