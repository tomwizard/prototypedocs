# How DNS+ Server Latency tests work

Have you ever wondered why DNS requests for your domain are taking so long from certain parts of the world?  Ever been frustrated by users from Asia complaining about slow requests, and wondered how you might solve the problem?

## Welcome to DNS+

These tests are designed to allow users to monitor the global performance of targeted DNS servers and their underlying network, by targeting a specific server with a request, and running these queries from points of infrastructure around the world.  Creating DNS+ Server Latency tests allows users to identify the specific authoritative nameserver\(s\) for a domain which are responding slowly in certain parts of the world - and then take corrective action.  DNS+ Server Latency tests are complementary to the data gathered by DNS+ Domain tests. DNS+ Domain tests measure response time, mappings and availability for a particular domain, allowing the vantage point to select the authoritative server. DNS+ Server tests measure the response time of a particular authoritative server.

The image below shows a sample DNS+ Server Latency view for a root nameserver which is showing higher response time than expected in certain areas of the world - notably, India, South America, and Australia.  By identifying the areas which are not meeting expectations from a performance perspective, changes can be made in geographical load balancing techniques, as well as augmenting or changing infrastructure. 

IMAGE MISSING

In a DNS+ Server latency test, vantage points will send a query for a random domain name ending in **dnste.net**.  When the server responds, since it is not authoritative for the dnste.net zone, it must respond with a REFUSED, NXDOMAIN, or SERVFAIL response.  The server latency metric represents the round trip time from the vantage point to the authoritative server for this query.  
 

## Error handling and troubleshooting

When attempting to add a DNS+ Server Latency test, the system may report an error.  Some examples of these errors are:

* _You have reached your usage limits_: This may be encountered when your projected utilization exceeds 100%, while in a trial phase. DNS+ tests are resource-intensive and consume units at a higher rate than standard web/dns/network tests. Contact your sales representative for more information on increasing your unit allocation.
* _You may exceed your included monthly usage_: This may be encountered when your projected utilization exceeds 100%. DNS+ tests are resource-intensive and consume units at a higher rate than standard web/dns/network tests. Contact your sales representative for more information on increasing your unit allocation.
* _This name is already being used_: occurs when a test name is already in use. Change the name of the test to bypass this error.
* _Test name is too long_. _Maximum 255 characters allowed_: test names must be less than 256 characters in length. Reduce the length of the test name to bypass this error.
* _Badly formed server name_: if a server specified contains an unprintable or unsupported character for DNS records, this error will be thrown. Validate the domain name you are attempting to test, correct and retry.
* _Server already added_: the server being tested is already being tested in your account. Check your other DNS+ Server Latency tests before adding it again.
* _This server is not compatible with our measurement system_:

   Certain nameservers may report that they are incompatible with our measurement system. This may be due to an incompatibility with the zone in which the domain resides, or with a server problem at the target. DNS Servers must be configured to respond with one of the following responses, for the query {random}.dnste.net

  * NXDOMAIN
  * SERVFAIL
  * REFUSED

 The target nameserver MUST respond with one of the above responses, when queried. Failure to respond will cause this error to be thrown.

