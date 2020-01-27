# Release Notes: 2017-07-19

Welcome to our midsummer night's release!

No new posts this release for the ThousandEyes blog. Even our dedicated bloggers get to take summer vacations. But if you miss reading the usual blog post or two with your Release Update, consider a trip to the ThousandEyes Knowledge base, instead? Check out a new article, such as [HTTP Server test fails with SSL Error: SSL certificate problem: unable to get local issuer certificate](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBCLCA4). We in Customer Success are often asked about this error, and the article explains the resolution while providing some of the theory behind digital certificate use on the Internet. Let us know what you think of the article!

And now for the details of the release...

## Cloud Agents and BGP Monitors

### IPv6 Cloud Agents

First... Another new member of our IPv6 family! Welcome, Perth, Australia!

### IPv4 Cloud Agents

In IPv4 Cloud Agent news, in our [Release Update 2017-06-21](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB7pCAG), we announced that we were withdrawing a Cloud Agent location in Jakarta, Indonesia due to quality issues with the provider. We have now brought that Jakarta location back online with another provider. If you’ve had IP address-based whitelists in the past for Jakarta Cloud Agents, be sure to update your whitelist. The ThousandEyes Knowledge Base has the following articles describing how to obtain Cloud Agent IP addresses:

[Obtaining a list of ThousandEyes Agent IP Addresses](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnuKAC) \(for users of our API\)

[Obtaining a list of ThousandEyes Agent IP Addresses with te-iplist](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cn2GCAS) \(for those wanting a tool to do the API query\)

Spoiler: an API query using the curl command is:

curl [https://api.thousandeyes.com/v6/agents.json](https://api.thousandeyes.com/v6/agents.json) -u noreply@thousandeyes.com:g351mw5xqhvkmh1vq6zfm51c62wyzib2

and the information is \(for the moment\) in the last line. The usual caveat: these addresses are relatively stable but \(as this example demonstrates\) subject to change at any time.

### BGP Monitors

Lastly... BGP Monitor [San Jose-3](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmo2KAC#route_collectors) of the [Route Views](http://www.routeviews.org/) project has been failing for the past few weeks, so we've removed the monitor from BGP tests and tests with the BGP Route Visualization view.

## System maintenance

In case you're not subscribed to the Maintenance Announcements forum...

Per our [Planned Maintenance 2017-07-22](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBEvCAO) announcement, it is possible there may be platform interruptions this coming weekend due to provider maintenance in our main data center.

Additionally, per our [Planned Maintenance 2017-07-25](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBG8CAO) announcement, we will be performing maintenance on the infrastructure for our DNS+ feature. For those customers who are DNS+ users, check the announcement for more details. Customer who do not use DNS+ tests will not be affected.

## Bug fixes & minor features

Here's the scoop on bug fixes and minor features in this week's release:

* In the listing of Alerts, tests which can alert on individual target servers \(e.g. DNS Server tests\) now display information on the server triggering the alert.
* Endpoint Agent now provides more data when ICMP probes are blocked.
* Added support to Endpoint Data's Path Visualization to filter on VPN servers whose IP addresses cannot be detected.
* Fixed an Endpoint Data issue causing the Path Visualization to render nodes in different networks with the same IP address as the same node.
* Fixed an Endpoint Data issue causing tooltips not to appear in waterfall charts from the Session Details view.
* Fixed an Endpoint Data filter issue when clicking on "Show only agents using this node" when an intermediate node in the Path Visualization was selected.
* Fixed an Endpoint Data filter issue when the filter expression contained certain special characters.
* Fixed a Reports issue with Endpoint Agent data which showed 'no data' when the Location filter was applied.
* Fixed a Reports issue with Endpoint Agent data which caused Transaction test steps to be displayed in ASCII collating \(alphabetical\) order rather than numeric order.
* Fixed an issue with missing BGP data in Snapshots, which includes existing Snapshots that were affected.
* The number of BGP Monitors in the BGP Route Visualization's "Showing:" quick link now differentiates between IPv4 and IPv6 Monitors, and reflects the number displayed in the Route Visualization's graph.
* Fixed an issue causing BrowserBot \(Page Load and Transaction tests\) not sending HTTP Basic Authentication credentials through proxies consistently.
* Fixed an issue with the Appliance's web administration interface that failed to highlight a required field \(primary DNS server\) upon changing network configuration.
* The /v6/account-groups.json endpoint now returns all expected fields.

Have comments on our Knowledge Base articles or maintenance announcements? [Send us an email](mailto:support@thousandeyes.com?subject=2017-07-19+Release+Update) and let us know how we can make you more successful.

