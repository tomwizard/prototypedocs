# Release Notes: 2018-03-07

Welcome to last night's release. Apologies for the delay in getting out the Release Update. We had a technical glitch affecting email distribution; one that we can't check for with the ThousandEyes app.

IMAGE MISSING

## ThousandEyes Connect

If you reside in the vicinity of England or will be visiting later this month, consider a visit to [ThousandEyes Connect London](https://www.thousandeyes.com/events/connect/london-2018) on March 21st, along with the trip to Buckingham Palace and the Tower of London. ThousandEyes Connect is a great opportunity to meet with the ThousandEyes team and the community of ThousandEyes users, and attend presentations by ThousandEyes customers. This ThousandEyes Connect will feature presentations by Kristof Heselmans, IT Architect & Compliance Specialist  
from Atlas Copco, and David Parker, Senior Solutions Architect at Linklaters. ThousandEyes CEO Mohit Lad will also be a speaker. [Registration](https://www.thousandeyes.com/events/connect/london-2018) is free and open now.

A busy week of blogging for our Marketing team, thanks to some historic Internet incidents.

The good news: DDoS attacks on GitHub were handled well, limiting the inconvenience to users, despite massive volume of malicious traffic. Our Senior Product Marketing Manager, Archana Kesavan has the details, ThousandEyes-style, in her post, [How GitHub Successfully Mitigated a DDoS Attack](https://blog.thousandeyes.com/how-github-successfully-mitigated-ddos-attack/).

The bad news: Amazon Web Services suffered an outage which affected many popular AWS-based services. Archana covers the gory details in her second post of the week, [Amazon AWS Outage a Lesson in Managing Cloud First Risks](https://blog.thousandeyes.com/amazon-aws-outage-lesson-managing-cloud-first-risks/).

And now for the details of the release.

## Cloud Agents

More new additions to our Cloud Agent family, plus some improvements in location information.

### New broadband provider Cloud Agents

Our [last release](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SYoCAM_Release-Update-2018-02-14) contained the first batch of Cloud Agents connected exclusively to networks of US consumer broadband providers. This week, we're adding a new location: Los Angeles, California. Providers at this location are CenturyLink, Cox and Charter. In the app, you'll see these Cloud Agents listed as:

* Los Angeles \(CenturyLink\)
* Los Angeles \(Cox\)
* Los Angeles \(Charter\)

### Cloud Agent name changes

Continuing with our improvements to the naming of Cloud Agents, we are changing the names of single-homed Cloud Agents to the nomenclature used for the new broadband provider Cloud Agents. Provider name \(in parentheses\) now follows location:  

| Original Name | New Name with Provider |
| :--- | :--- |
| Berlin, Germany | Berlin, Germany \(Telia\) |
| Berlin, Germany IPv6 | Berlin, Germany IPv6 \(Telia\) |
| Oakland, CA | Oakland, CA \(Cogent\) |
| Oakland, CA IPv6 | Oakland, CA IPv6 \(Cogent\) |
| Denver, CO | Denver, CO \(Cogent\) |
| New York, NY | New York, NY \(Cogent\) |
| New York, NY IPv6 | New York, NY IPv6 \(Cogent\) |
| New York, NY 2 | New York, NY 2 \(Cogent\) |
| Frankfurt, Germany | Frankfurt, Germany \(Cogent\) |
| Frankfurt, Germany IPv6 | Frankfurt, Germany IPv6 \(Cogent\) |
| Tokyo, Japan | Tokyo, Japan IPv6 \(KDDI\) |
| Wuhan, China | Wuhan, China \(China Telecom\) |
| Wenzhou, China | Wenzhou, China \(China Telecom\) |
| Shanghai, China | Shanghai, China \(China Telecom\) |
| Xi'an, China | Xi'an, China \(China Telecom\) |
| Shijiazhuang, China | Shijiazhuang, China \(China Unicom\) |
| Shenyang, China | Shenyang, China \(China Unicom\) |
| Jinan, China | Jinan, China \(China Unicom\) |
| Beijing, China | Beijing, China \(China Unicom\) |

###  Enterprise Agent locations

We've also improved our algorithm for automatically determining the location of an Enterprise Agent. As a result, Enterprise Agents which were not manually configured with a location may have had their locations updated to better reflect their actual geographic location.

## Endpoint Agent

The Endpoint Agent's .msi installer for Windows now includes an option to choose which features to install, including whether or not to install the Internet Explorer add-on or the Chrome extension. Existing installations can remove an unneeded add-on or extension. The operations are performed in a command window using the **msiexec** command. For example, the Internet Explorer add-on can be removed using the command:

```text
msiexec /quiet /qn /i Path-To-Msi-File.msi ADDLOCAL=ALL REMOVE=IeExtension
```

To remove the Chrome extension, use ChromeExtensionSupport instead of IeExtension.

## Minor features and bug fixes

* Improved the layout of nodes and arrows in the Topology View of Device Layer to avoid overlapping with large numbers of devices.
* Enterprise Agents now correctly parse PAC files which use multiple proxy servers in the RETURN statement \(the Agents will only use the first proxy, currently\).
* Endpoint Agent no longer produces the following errors for proxy servers in the Session Details view:

  Network Connection Error  
   The IP address or port number is invalid \(e.g., cannot connect to the IP address 0 or the port 0

* The **Sort By** field of a Multi-Metric Table widget in a report no longer reverts to the default setting after configuring a non-default value.
* A Bar Chart widget in a report no longer omits the names of the bar legends in some situations.

## Questions and comments

Got a Share Link of a major outage that you'd like to discuss with us? Just want to chat about the Internet weather?  [Send us an email](mailto:support@thousandeyes.com?subject=2018-03-07+Release+Update)!

