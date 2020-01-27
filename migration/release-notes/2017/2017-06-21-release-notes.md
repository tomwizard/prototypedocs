# Release Notes: 2017-06-21

Welcome to tonight's release! We've got some long-awaited features that are making their debut, but first...

Thanks to all who made [ThousandEyes Connect in Silicon Valley](https://www.thousandeyes.com/events/connect/santa-clara-2017) a great success! We had outstanding presentations and the turnout was equally outstanding. If you missed the fun, keep an eye on the [ThousandEyes Blog](https://blog.thousandeyes.com/) for posts on the presentations and more.

And if you're attending [Cisco Live](https://www.ciscolive.com/us.html) in Las Vegas, Nevada next week anytime from 6/26 to 6/29, drop by our booth and say hello. You might get a ThousandEyes t-shirt for introducing yourself.

Now, on to the new features...

## Voice Layer Tests

We're adding to our Voice over IP With tonight's release, two Voice Layer test types that have been in beta testing are moving into general availability, to join the existing RTP Stream test type. The SIP Server test allows customers to verify functionality and performance of a SIP server on the local network or in the cloud. This test type performs either a "SIP ping" \(issue the OPTIONS command from the SIP protocol\) and \(optionally\) performs registration with the target SIP server. The Voice Call test combines the functionality of the SIP Server and the RTP Stream tests to simulate a full voice call between two ThousandEyes Agents. As with other ThousandEyes tests, the new Voice Layer tests also provide a Network View for troubleshooting issues below the application layer.

Configuration of Voice Layer tests requires a subscription to the ThousandEyes "Pro" plan.

Documentation on Voice Layer configuration and test metrics are available in the ThousandEyes Knowledge Base.

Configuration:  
[SIP Server test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB68CAG)  
[RTP Stream test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB7QCAW)  
[Voice Call test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB63CAG)

Test Metrics  
[Using the SIP Server view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnW8CAK)  
[Using the RTP Stream view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmkKAC)  
[Using the Voice Call view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoAICA0)

## Groups/Labels

We've redone our Groups interface for grouping ThousandEyes Agents, which will now be called Labels. We've replaced the drag and drop-based configuration with a new interface which is consistent with the look and feel of the rest of the app, and which simplifies configuration and management of multiple Agents or multiple tests.

IMAGE MISSING

Access to the Labels from the Tests page or Enterprise Agents page is unchanged, beyond renaming the "Groups" to "Labels":

IMAGE MISSING

## Cloud Agents

Continuing our efforts enhance our IPv6 fleet, we've added the following locations to our IPv6 Cloud Agents:

* Dusseldorf, Germany
* Frankfurt, Germany
* Maidstone, UK
* Manchester, UK
* Singapore 2, Singapore \(just to be confusing, we're doing the "Singapore 2" location before "Singapore"\)

  Due to provider reliability issues, we've removed IPv4 Cloud Agents in:

* Jakarta, Indonesia
* Winnipeg, Canada
* Kitchener, Canada

  We were able to quickly replace the Kitchener Agent. Stay tuned for news on the other two locations.

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* For an Enterprise Agent which has both IPv4 and IPv6 addresses, we now display the IPv6 address in addition to the IPv4 address in the General Info section of the Enterprise Agents page.
* For an Enterprise Agents which has both IPv4 and IPv6 addresses, the API will now provide the IPv6 address in addition to the IPv4 address.
* Fixed an issue preventing access to the **Add message** box under the Notifications tab of an Alert Rule.
* Addressed an issue with our provider for the Indore, India Cloud Agent which was causing elevated levels of packet loss.
* Fixed an issue with Reports which caused FTP tests not to be displayed in the Tests filter of a widget. 

Want to comment on the new features? We'd love to know what's on your mind. [Send us an email](mailto:support@thousandeyes.com?subject=2017-06-21+Release+Update).

