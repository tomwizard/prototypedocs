# Release Notes: 2019-10-29

Welcome to our latest release!

Before the details of the release, a quick plug for...

IMAGE MISSING

The second annual Cloud State Live will be held on November 13th. Join us for an hour [via live stream](https://www.thousandeyes.com/cloud-state-live) \(or if you're in Austin, Texas, in person at [Pershing](https://thepershing.com/)\) for the unveiling of this year's Cloud Performance Benchmark report. In this year's report, we've added Alibaba to last year's cloud provider trio of AWS, GCP and Azure. Plus, hear some other recent big news on the state of ThousandEyes.

Never heard of the Cloud Performance Benchmark report? Have a peek at [last year's report](https://www.thousandeyes.com/resources/2018-public-cloud-performance-benchmark-report) to get your head in the right place.

Also, a new post up on the ThousandEyes blog. Guest blogger Steve Mazzuca, an IT veteran from the government sector brings us the second of his posts, entitled [Agency Modernization of Legacy Systems is Half the Battle](https://blog.thousandeyes.com/agency-modernization-of-legacy-systems-is-half-the-battle/) \(with link to previous post\). A timely subject for those of us in California, where utility black-outs and wildfires led to outages of web sites where citizens sought information, such as [PG&E](https://blog.thousandeyes.com/pge-web-servers-go-dark-amid-looming-power-shutdown/) and [CALFIRE](https://znzzrb.share.thousandeyes.com/view/tests/?roundId=1572277920&metric=availability&scenarioId=httpServer&testId=1137468).

Enough clouds and smoke. Let's see what's in our release...

## Test enhancements

We've added two enhancements to tests, based on popular demand.

### Packet transmission rate

For test types which perform Network measurements \(except RTP Stream tests\) users can choose the rate at which the packets for those measurements are set. Under the test's Advanced Settings tab, look for the **Transmission Rate** checkbox, and move the slider to select a packet-per-second rate between 10 and 100 pps:

IMAGE MISSING

Adjusting transmission rate can be helpful when the default setting \(send as fast as possible\) triggers a network device which enforces rate limits.

### Web Layer header size

In Web Layer tests which use HTTP \(i.e. HTTP Server, Page Load and Transaction tests but not FTP Server tests\) the maximum size of a request header has been increased from 1024 to 4096 bytes to accommodate larger custom headers.

## Bug fixes & minor enhancements

Here are the bug fixes and minor enhancements in this week's release. Version numbers in parentheses indicate when a fix first appears \(when relevant, e.g. Endpoint Agent version\):

* Overage notification emails now calculate an Account Group's projected overage using the number of days based on the actual month in the billing cycle rather than on 31 days
* Users in multiple organizations no longer have their login Account Group reset to one particular group if one of the user's organization is locked or deleted
* Loading the Users tab of the Account Settings page no longer freezes when the list of users is very, very long
* Fixed an issue which could cause DOM load and page load times to be incorrect
* When viewing an Endpoint Agent Saved Event, Filter dropdowns are no longer empty, for certain types of filter
* Endpoint Agent Labels based on IP address family are now correctly applied to Agents matching the filter \(0.177.2\)

## Questions and comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-10-29+Release+Update)!

