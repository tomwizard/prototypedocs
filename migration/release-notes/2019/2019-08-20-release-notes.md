# Release Notes: 2019-08-20

Welcome to our latest release!

What's new this week? Our latest blog post by Director of Product Marketing, Archana Kesavan, which brings us the story behind our recent announcement of Cloud Agents in Alibaba. Steal a peek at her article [Alibaba Cloud Vantage Points for Monitoring in Asia-Pacific](https://blog.thousandeyes.com/alibaba-cloud-vantage-points-monitoring-asia-pacific/). A blog-tale to reveal the hidden treasures in cloud performance monitoring's dark cave \(China\). Learn the secrets of the lambda wave. Just say "Open sesame," and... Well, maybe just read the article and see how you can get a better understanding of cloud performance in Asia.

Our other new blog post tells a tale of the tale-tellers. Content Marketing Director Sean Coombs brings us the first installment of a two-part story, [How Viacom Improves Employee Digital Experience and Productivity](https://blog.thousandeyes.com/how-viacom-improves-employee-digital-experience-and-productivity/), recapping the presentation by Viacom’s IT infrastructure team at our last ThousandEyes Connect event. Learn how this entertainment giant uses ThousandEyes to ensure that their cloud-based infrastructure never disappoints an audience, whether they be customers, or employees gathered 'round their browsers to stream a CEO town hall event.

And speaking of ThousandEyes Connect...

IMAGE MISSING

 If you're located in the Great Northwest of the US, or fancy a visit, come to the city that has the computers and the coffee and [Connect Seattle](https://www.thousandeyes.com/events/connect/seattle-2019)! Join ThousandEyes at the world-famous Space Needle \(no joke!\) on October 3rd, see Seattle from on high, and hear some great speakers \(TBD\). [Registration](http://www.thousandeyes.com/events/connect/seattle-2019) is free and open now!

IMAGE MISSING

Pass your camel through that, get a free ThousandEyes t-shirt! 

And now to unveil the details of our release...

## Account Group custom Labels

We've removed the limit on the number of custom Labels that can be assigned to an Account Group. Go crazy. You know who you are.

## Kerberos rDNS configuration

Some customers who use Kerberos authentication do not control the reverse-lookup zones for the IP addresses of hostnames in their Service Principal Names \(SPN\). An organization which has cloud-based services that use the organization's Kerberos authentication is a common example.

When Kerberos is configured to perform reverse DNS lookups, an SPN hostname is resolved to an IP address, then the IP address is used to perform a reverse DNS lookup \(PTR record query\). Authentication can fail if the result of the lookup fails to match the SPN hostname.

To prevent these authentication failures, we have added the ability to disable Kerberos reverse lookups. For Agent configuration in the app, under the Advanced Kerberos Options section, check the **Disable reverse DNS lookup** box to prevent the reverse lookup check.

IMAGE MISSING

For customers managing Agent configuration locally, set kerberos-rdns=1 in the /etc/te-agent.cfg file. Don't forget to restart the Agent process or reboot the Agent after making the change.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release:

* Fixed an issue which could prevent a user from logging in, if the user's role in their login Account Group was removed using the API.
* The API's /alert-rules endpoint now provides the minimumSources field for the minimum percentage of sources meeting an Alert Rule's conditions in order to trigger the rule.
* When displayed in a Dashboard or Reports widget, the Device Througput metric is now colored on a "neutral" scale of blue to green rather than red to green.
* The Endpoint Agent Waterfall incorrectly displayed "Object Incomplete" when receiving a response with a "Transfer-Encoding: chunked" header. We now provide an accurate description.
* When viewing the details of a page visit in the Visited Pages view of Endpoint Agent, we now display the Response Time metric next to the VISITED SITE icon: IMAGE MISSING
* Fixed an issue in the Endpoint Agent's Overview which caused a null Experience Score to be displayed as 0%.
* Increased timeout threshholds for Endpoint Agent Scheduled Tests.
* Endpoint Agents now can check in with the ThousandEyes platform after receiving 302 status code responses from Microsoft IWA proxies.
* Endpoint Agent Scheduled Tests no longer attempt to perform Path Visualization to the target when the Agent is configured to use a proxy.  

## Questions and comments

Got feedback for us? Want to tell ThousandEyes your one favorite Arabian nights tale? [Send us an email](mailto:support@thousandeyes.com?subject=2019-08-20+Release+Update)!

