# Release Notes: 2016-08-17

It's been a pretty busy couple of weeks for the Team at ThousandEyes. First, we launched a preview of the ThousandEyes Endpoint Agent. You can catch the press release [here](https://www.thousandeyes.com/press-releases/network-visibility-with-endpoint-agent), a blog post [here](https://blog.thousandeyes.com/introducing-endpoint-agent-extending-visibility-end-user/), and a testimonial on using the Endpoint Agent from AIM Specialty Health [here](https://blog.thousandeyes.com/monitoring-end-user-experience-endpoint-agents/).

We also presented to the experts at Network Field Day 12 last week, and are excited to see some of the feedback of some of the industry's leaders. Check out a summary from our own Archana Kesavan, along with videos of some of the sessions presented [here](https://blog.thousandeyes.com/networking-field-day-12/).

## Endpoint agent preview

As we mentioned, things are pretty exciting for us right now.

IMAGE MISSING

ThousandEyes Endpoint Agent gives you a new vantage point that runs on employee laptops and desktops. Data from Endpoint Agents provides complete visibility into the performance of your applications, as well as the underlying networks that support application delivery, no matter where or how your users are connecting to the Internet and your corporate network. With islands of your network floating around the globe inside your employees’ laptops, you’ll need to look to the endpoint to have any shot at measuring what you care about. It’s the only way.

If you're a ThousandEyes customer, we're granting access to all customers to try the product during the preview period for free. Reach out to the customer success team, or to your sales representative to obtain access and set up a session to help you understand how to take advantage of the rich data immediately at your fingertips.

## Recent cloud agent changes

* **Melbourne, Australia**: our provider disappeared from the face of the earth, and took our servers. We're looking for a new, more trustworthy, provider.
* **Mumbai, India**: we dropped service due to repeated service delivery complaints. Our team is in the process of evaluating new providers in Mumbai at the moment and service will be restored shortly.
* **Hyderabad, India**: we are evaluating new providers. This provider is the same provider as the one from Mumbai, and showing some of the same tendencies, though service is better.
* **Tel Aviv, Israel**: our datacenter in Tel Aviv was flooded during recent inclement weather, and the provider in this location is in the process of recovering.  
* **Bangkok, Thailand**: we have established service with a new provider in this location. Based on current metrics, it appears that quality of service from this customer is stronger than in previous locations.
* **Kansas City, MO**: after fielding a number of issues reported by customers, our provider has replaced a series of upstream routers in this location, which has improved quality of service.
* **Japan**: we have augmented our service in Japan with a new agent location in Nagoya. We will be replacing our provider in Tokyo in the next two weeks, so please be advised that IP addresses for agents in this location will be subject to change.

##  BGP monitor London-4

This monitor has stopped providing routes to our service. As of this evening, it has been removed from all customer tests.

## HTTP server tests

We've introduced a new option to allow administrators to control redirect behavior of HTTP server tests. Found in the advanced settings tab of the test's settings, users can control whether or not HTTP/301 and HTTP/302 referrals will be followed in order to validate the output of a test.

IMAGE MISSING

## DNS trace tests

We've enhanced how DNS trace tests work in the case of a SERVFAIL response received while looking up DNS records. Prior to this change, in the event that a SERVFAIL response were received by an agent, the test would fail with a "Dead End" error message. With the implementation of this change, upon receipt of a SERVFAIL response from an authoritative nameserver for a record, which has multiple authoritative nameservers, the next nameserver in the list will be tried, until either no remaining servers are available, or until the test timeout has been reached.

## Upcoming maintenance

We'll be running two scheduled maintenance periods next week as we introduce changes to our core network infrastructure. We don't expect customers to experience any issues during the maintenance periods. Watch our announcements forum for updates on these maintenance periods; we will publish additional details before the end of this week.

