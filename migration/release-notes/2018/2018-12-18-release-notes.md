# Release Notes: 2018-12-18

Welcome to today's release! The holiday season is upon us. Time to gather together, light candles, eat, drink, sing or do whatever brings you joy. Whether or whatever you're celebrating, we hope our last release of 2018 will provide you with something to bring you good cheer.

IMAGE MISSING

[Registration is now open](https://www.thousandeyes.com/events/connect/atlanta-2019) for the next ThousandEyes Connect in Atlanta on January 15th! We've got great guest speakers lined up to tell us how their companies use ThousandEyes. If you're in the Atlanta area, or need a break from the cold weather, come connect with us!

Before we get to open the shiny new features, some ThousandEyes blog news. The elves in the blog workshop have been busy, these past few weeks... 

For starters, we're fortunate to have a guest author this week, IT Operations & Reliability Consultant [Tony Davis](https://www.linkedin.com/in/tonydaviscambridge/), who will be doing a three-part series for us. Tony shares his experiences using Business Service Reliability methodology to spin mountains of raw monitoring data into something of value, in his post [Turning Monitoring into Measurable Business Value is Imperative](https://blog.thousandeyes.com/turning-monitoring-into-measurable-business-value-is-imperative/). If you've got lots of monitoring data but feel like you didn't get what you wanted, this series is for you.

Speaking of series... Our Senior Product Marketing Manager, Archana Kesavan, graces us with two new articles in a series based on her research into [benchmarking cloud provider performance](https://www.thousandeyes.com/resources/2018-public-cloud-performance-benchmark-report?utm_source=blog). In the series' second article, she discusses some interesting results from the research, in the post [How Cloud Network Architectures Impact Performance](https://blog.thousandeyes.com/how-cloud-network-architectures-impact-performance/). And in the final article of the series, Archana discusses a new offering related to the previous post, in [AWS Addresses Performance Instability with AWS Global Accelerator](https://blog.thousandeyes.com/aws-addresses-performance-instability-with-aws-global-accelerator/). A set worth collecting.

The Internet is always improving, sometimes in small steps, sometimes large ones. ThousandEyes Senior Solutions Engineer Prabhnit Singh has crafted an excellent overview of an important recent development: the TLS 1.3 standard. Prabhnit provides the technical details and explains why the new standard matters, in his post [Optimizing Web Performance with TLS 1.3](https://blog.thousandeyes.com/optimizing-web-performance-tls-1-3/). TLS 1.3: a gift you won't want to return.

To wrap up our blog gifts, Product Manager Janani Ramakrishnan reviews all of the major new ThousandEyes features released this past quarter, in [What’s New in Fall 2018](https://blog.thousandeyes.com/whats-new-fall-2018/).

And now for the release details...

## Enterprise Agents

### Support for Ubuntu 18.04

We now support installing Enterprise Agents on Ubuntu 18.04 LTS \(code name "Bionic Beaver", or just "Bionic"\) via the Linux package installation method.

### End of support for Red Hat/CentOS/Oracle Linux 6.7, 7.2 and 7.3

Per our [announcement on October 23rd, 2018](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CplcCAC_Release-Update-2018-10-23), we are ending support for Enterprise Agents installed on versions 6.7, 7.2 and 7.3 of Red Hat, CentOS, and Oracle Linux. Support for Enterprise Agents running on these operating systems ends on January 1st, 2019. After that date, no new Agent installations will be permitted on these operating systems, and existing installations will not be supported. Please contact the [ThousandEyes Customer Success team](mailto:support@thousandeyes.com?subject=End+of+support+for+RH) if you need assistance migrating to a supported operating system.

## Tests

### Path Visualization pagination

The Path Visualization for Cloud and Enterprise Agent tests will now be paginated, similar to the Endpoint Agent's Path Visualization and the BGP Route Visualization. A maximum of 45 Agent or Agent groups can be shown per page.

IMAGE MISSING

Users will now see a "Next Nodes" icon when pagination occurs. The icon displays the number of nodes not shown in the current page.

### Historical test configurations in views

Test views will now show the configuration in effect at the time of the currently selected test round, rather than always showing the current configuration. This includes configurations that affect views \(e.g. enabling or disabling **Perform network measurements**\), metrics \(e.g. enabling or disabling **Perform bandwidth measurements**\), targets \(e.g. target URL, DNS servers\), and directionality \(both directions, source to target, or target to source\). We do not yet support historical configs for Agent-to-Agent test targets.

## Reports

We've added an option in the Multi-Metric widget to allow the number of rows of cards to be capped. Check the **Limit To** box and set the maximum number of rows. The cards which are shown are determined by the **Sort by** setting.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Users can now directly delete the last Enterprise Agent assigned to a cluster. Previously, the cluster needed to be converted to a stand-alone Agent before deleting.
* Fixed an issue that reported incorrect timezones in the PDF versions of reports
* Fixed an issue that flipped the colors of objects in the bar chart widget based on metric value

## Questions and comments

Got feedback for us? Didn't get the feature you wanted? [Send us an email](mailto:support@thousandeyes.com?subject=2018-12-18+Release+Update) \(if you're nice; naughty emails not needed!\)

