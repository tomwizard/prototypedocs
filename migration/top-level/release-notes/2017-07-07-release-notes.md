# Release Notes: 2017-07-07

### Release Update 2017-07-07

Welcome to our non-Tuesday release!  This past Tuesday our staff was enjoying the Fourth of July holiday, so we're doing our release on a Thursday.

Two great new posts in the ThousandEyes blog. Young Xu continues her theme of reprising articles on public DNS server performance: this week, she revisits [performance of root name servers](https://blog.thousandeyes.com/2017-update-comparing-root-server-performance-globally/), comparing numbers from 2015 with current data. And Archana Kesavan discusses [use cases for the new VoIP test features](https://blog.thousandeyes.com/complete-voip-visibility-sip-rtp/) from our last release.

Our team at [Cisco Live!](https://www.ciscolive.com/us.html) in Las Vegas tells us they had a great time meeting all of you.  They won't tell us what else they did, but they came back without a [ThousandEyes t-shirt](https://www.thousandeyes.com/tshirt) to their names.  If you didn't make it to Cisco Live! this time, you can still grab a t-shirt online, and come see us at another event in the future.

And now for the details of the release...

## Cloud Agents

 Continuing our efforts enhance our IPv6 fleet, we've added the following locations to our IPv6 Cloud Agents:

* Munich, Germany
* Singapore, Singapore \(a second Singapore location\)

## Agent operating system end of life

Per our [Release Update of April 26th](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoAXCA0), we are discontinuing support for Enterprise Agents running on older, unsupported versions of Linux.

### Ubuntu Precise-based Agents and Virtual Appliances

We've reached the release following the 60-day period from the end of life announcement for Ubuntu Precise. After tonight, all existing Precise-based Enterprise Agents \(both Virtual Appliances and Linux package-based\) will automatically be disabled. Notifications have been sent to affected customers via email. Customers who need further assistance can contact the Customer Success team for assistance in replacing Precise-based Enterprise Agents. The procedure for replacement is documented in the ThousandEyes Knowledge Base article [Replacing an Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0).  Additionally, new installations will fail on these unsupported operating systems.

### Red Hat, CentOS and Oracle Linux based Agents

The end of life announcements from their vendors for Red Hat, CentOS and Oracle Linux versions 6.6 and earlier and 7.1 and earlier have been in effect for some time.  After tonight, new installations on these operating systems will fail on these unsupported operating systems.

For more information on Enterprise Agent End of Life announcements, consult the following Knowledge Base articles:

* [End-of-Life announcement for Precise-based Virtual Appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnyqCAC)
* [End-of-Life announcement for Ubuntu Precise Linux package Enterprise-Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB1rCAG)
* [End-of-Life announcement for Red Hat Linux package Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CoB6CAK)

## API

We are adding an endpoint for user-based events in the Activity Log. Query https://api.thousandeyes.com/v6/audit/user-events/search to see what your users are up to.

## Voice Layer tests

Based on feedback and data, we are removing Voice Layer test automatic proxy detection based on a packet's IP ID field.  As a result, proxies will no longer be displayed using small proxy \(shield\) icons on the links between nodes, in the Path Visualization.  Proxies that are explicitly configured in test settings will be displayed as full nodes, similar to the iconography used for Endpoint Agent.

## Bug fixes & minor features

 Here's the bug fixes and minor features in this week's release:

* Fixed an issue with the NTP configuration file on Xenial-based Virtual Appliances.
* Fixed an issue with the Virtual Appliance Diagnostics for the APT repository checking a custom repository setting.
* Snapshots now display Outage Detection swimlanes.
* SIP Server view no longer erroneously detects multiple proxies in a single Path Visualization link.

  
Have comments? Want to tell us what you did on the Fourth of July? [Send us an email](mailto:support@thousandeyes.com?subject=2017-07-07+Release+Update)!

