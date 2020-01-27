# Release Notes: 2013-11-27

### Release update 2013-11-27

In keeping with the Thanksgiving tradition, we'll all be thankful that this week's release notes are brief.

On an administrative note, please note that ThousandEyes offices will be closed on Thursday, November 28th and Friday, November 29th, in observance of the US Thanksgiving holiday. 

## Feature changes

### BGP Route Visualization changes

Beginning with today's release, targets which route to Content Delivery Networks \(CDNs\) will no longer show BGP information.  This was done primarily to eliminate confusion related to the potentially large number of networks returned in BGP feeds to a target, since BGP information was being shown for each network in which the final data resided.  Beginning with today's release, if a target was to a CDN-based domain, the BGP Route Visualization entry will no longer be shown for these tests, and the test will no longer be listed in the test selector, when using the BGP Route Visualization view independently.  

Please note: in some circumstances, the detection of a CDN-based target may be delayed.  If the BGP Route Visualization menu item is missing from your jump to menu, it is likely because the target domain was detected as a CDN-based domain.

BGP tests can still be manually created for CDN target networks; however, they will not be accessible to tests by using the Jump To menu.

### Instant Bandwidth Tests now support ICMP

Beginning with today's release, our instant Bandwidth Tests now support the use of the ICMP protocol.   To run a bandwidth test using ICMP, select an agent, enter your target and choose ICMP as the query type.  A port number is not required when running a test using ICMP.

IMAGE MISSING

