# How DNS+ Domain tests work

## What is DNS+?

DNS+ tests use public DNS infrastructure to gather Domain Name System \(DNS\) records and performance metrics.  The two principal use cases for DNS+ involve measuring DNS for cache poisoning attempts, and for gaining insight into tier-2 and tier-3 networks, which are otherwise difficult to get infrastructure into.  

Access to DNS+ is restricted to premium ThousandEyes customers.

## How does it work?

In a nutshell, ThousandEyes leverages a series of open DNS resolvers \(known as vantage points\) to gather DNS record availability information, and nameserver performance. In order to ensure accuracy of measurements, our system validates each vantage point on a regular basis to ensure accuracy and consistency of results. The list of open resolvers is dynamic, and as a result, the list of vantage points from which we gather information is not guaranteed to be constant.

Please note: In order to protect the availability of this public infrastructure, ThousandEyes does not disclose the IP addresses of these vantage points, or the method of validation used by our platform.

ThousandEyes only displays countries and networks with enough validated vantage points to return a statistically significant response.  ThousandEyes measures reference statistics, to allow organizations with access to DNS+ to compare their tested domains against the general availability of the most-accessed Internet sites. In order to be considered for the reference list, each of the sites must be available from all countries in which vantage points are present.

## Test types & measurements

ThousandEyes runs two measurements against each tested record, to gather DNS+ Domain data:

### Mappings

For mappings, each vantage point returns the mapping\(s\) of the requested record, measured from its perspective. When requesting an A record, the record will be followed to its ultimate A record, even if there are CNAMEs present in the resolution chain. Each mapping is then added to the list of country and global mappings, and the number of resolvers returning this mapping are calculated based on the overall number of vantage points tested.  For content delivery network-hosted and -owned domains, please refer to the special note below.

This information is obtained and used to calculate the availability measurement, found below:

### Availability

For availability, each vantage point returns either an affirmative response, or an error code.  Where an error is returned, or no mapping comes back in response to the query, we categorize the response into one of the following categories:

* No Mapping: a non-error response was received from the vantage point, but the response was empty.
* NXDOMAIN: An NXDOMAIN \(non-existent domain\) response was returned from the server.
* SERVFAIL: returned when the vantage point is unable to resolve the domain, which could include any of the following:
  * it received a SERVFAIL response from all authoritative servers
  * it could not reach any authoritative server
  * there was a problem in the domain configuration
  * the vantage point had some internal error
* Truncated: when a DNS response exceeds 512 bytes, the response will be truncated when querying over UDP.  When this happens, and a server returns a Truncated response, the response will be categorized as Truncated.

The availability is tabulated on a country-by-country basis by calculating the number of affirmative responses divided by the number of vantage points tested.

### Resolution Time

Resolution time is captured independently from the mappings and availability measurement data.  For resolution time, each vantage point will query the zone in which the domain resides for a record that is a randomly generated and thus guaranteed not to exist. This forces the vantage point to contact the authoritative server each time, avoiding cached records the vantage point may have, making for a consistent performance measurement. Note: random requests are generated and sent to the servers at the ZONE level, and not the DOMAIN level, since the resolution time test is a performance test for the nameservers serving a domain. Since nameservers exist at the zone level \(which can host multiple domains\), we only run this test once per measurement interval, per zone, per account.

## Error handling and troubleshooting

When attempting to add a DNS+ Domain test, the system may report errors while adding the test. Some examples of these errors are:

* _You have reached your usage limits_:  This may be encountered when your projected utilization exceeds 100%, while in a trial phase.  DNS+ tests are resource-intensive and consume units at a higher rate than standard web/dns/network tests.  Contact your sales representative for more information on increasing your unit allocation.
* _You may exceed your included monthly usage_: This may be encountered when your projected utilization exceeds 100%.  DNS+ tests are resource-intensive and consume units at a higher rate than standard web/dns/network tests.  Contact your sales representative for more information on increasing your unit allocation.
* _This name is already being used_: occurs when a test name is already in use.  Change the name of the test to bypass this error.
* _Test name is too long. Maximum 255 characters allowed:_ test names must be less than 256 characters in length.  Reduce the length of the test name to bypass this error.
* _Invalid domain_: Domains without a valid top level domain will respond with this error.  Check your domain and retry.
* _Badly formed domain name_: if a domain specified contains an unprintable or unsupported character for DNS record, this error will be thrown.  Validate the domain name you are attempting to test, correct and retry.
* _There was an error resolving the domain: &lt;error&gt;_: This is a generic error message which will bubble up the response obtained when attempting to resolve the domain. 
* _Mappings will not be collected for CDN-owned domains_: for domains owned by a content delivery network \(CDN\) provider \(such as Akamai\), mappings data are not returned, due to the large amount of data and relative uselessness of the mappings data, when the list of mappings changes \(in many cases\) more frequently than the test runs.  By acknowledging the warning, your test will be created, but mappings data will not be collected.  Refer to special handling of CDN domains, below.
* _Domain already added_: the domain being tested is already being tested in your account.  Check your other DNS+ Domain tests before adding a new domain.
* _This domain is not compatible with our resolution time measurements. It will appear in the DNS+ Availability and Mappings views, but not in the Resolution Time view_:

  Certain domains may report that they are incompatible with response time testing. This may be due to an incompatibility with the zone in which the domain resides, or with a server problem at the target. DNS Servers must be configured to respond with one of the following responses, for the query {random}.zone

  * NXDOMAIN
  * A Record of a wildcarded entry for the zone.

 Servers responding with SERVFAIL for {random}.zone cannot be tested, since a SERVFAIL indicates an internal error, which could occur on either the target endpoint, or the resolver being used to run the test - and would be impossible to differentiate between the two servfail sources.

##  Special handling of CDN domains

We make two differentiations between CDN domains.  Taking the following example, where we query for _store.apple.com_ A, we note that _store.apple.com_ is a CNAME record for _store.apple.com.edgekey.net_, which forwards to _store.apple.com.edgekey.net.globalredir.akadns.net_ which forwards to _e2850.b.akamaiedge.net_, and then from there to a geo-load balanced IP.

```text
;; QUESTION SECTION:
;store.apple.com.		IN	A

;; ANSWER SECTION:
store.apple.com.	266	IN	CNAME	store.apple.com.edgekey.net.
store.apple.com.edgekey.net. 14951 IN	CNAME	store.apple.com.edgekey.net.globalredir.akadns.net.
store.apple.com.edgekey.net.globalredir.akadns.net. 553	IN CNAME e2850.b.akamaiedge.net.
e2850.b.akamaiedge.net.	13	IN	A	23.42.91.171
```

### CDN-hosted domain

In this example, if we were to query for foo.company.com A, the mappings data would return the final CNAME record in the chain, since this is typically the last record of significance to target providers.  The A record data will vary widely based on source of the query.  Rather than adding hundreds \(if not thousands\) of mappings, the final data returned to the mappings interface will be the final CNAME in the chain, or in this case, _e2850.b.akamaiedge.net_

### CDN-owned domain

Using the same example above, an attempt to test _e2850.b.akamaiedge.net_ would trigger a warning when attempting to save the test, and would not collect data for mappings. This is due to the fact that the _akamaiedge.net_ domain is marked as a known CDN domain in our system.  Note the very low TTL values for each A record associated with the final CNAME; given the frequency of DNS+ queries, in most cases, values would _already be stale_ before collection and aggregation across thousands of vantage points is complete.

