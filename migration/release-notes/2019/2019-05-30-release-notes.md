# Release Notes: 2019-05-30

Welcome to our latest release! A light release--mostly bug fixes and some minor upgrades to our Enterprise Agents. But there's news of events, some new blog posts to tout, and as well as an important reminder about Enterprise Agents at the end of life.

The events: Looking to meet other ThousandEyes users and hear great presentations? Come join us for Connect London on Thursday, June 13th, 2019. [Registration](https://www.thousandeyes.com/events/connect/london-2019) is open and free! And if London's not your thing, you can come swing by our booth at Cisco Live! in San Diego, from June 9th to the 13th. [Sign up](https://www.thousandeyes.com/cisco-live-us-2019) and get a free web site diagnosis, using ThousandEyes!

The blog posts: First, what everyone loves to read--internet outage post-mortems! This one's from our Director of Product Marketing, Angelique Medina, who looks at the recent China Telecom outage, in her article entitled [Internet Outage Reveals Reach of China’s Connectivity](https://blog.thousandeyes.com/internet-outage-reveals-reach-of-chinas-connectivity/).

Second, our VP Product Marketing, Alex Henthorn-Iwane, gives us [Measuring Web Performance and Digital Experience](https://blog.thousandeyes.com/measuring-web-performance-digital-experience/), in which he announces our latest performance benchmark report, the Digital Experience Performance Benchmark Report. See how the 20 top U.S. consumer websites in each of the retail, media & entertainment and travel & hospitality industries perform. Compare. Contrast.

Last but not least, get your C++ geek on! Senior Software Engineer Giannis Georgalis' post, [A Futures Library for Asynchronous Programming in C++](https://blog.thousandeyes.com/futures-library-asynchronous-programing-cplusplus/) introduces the [thousandeyes::futures](https://github.com/thousandeyes/thousandeyes-futures) library which extends the functionality of the std::future class in ways that consume fewer threads than other, contemporary mechanisms. If that's your bag, then Giannis gives you all the gory details.

And now for the details of tonight's release!

## Enterprise Agent End of Life

A more-or-less final warning: Enterprise Agents running on Ubuntu 14.04 LTS \(a.k.a. “Trusty”\) and on Red Hat/CentOS/Oracle Linux 7.3 and earlier versions will cease to operate as of July 1st, 2019. The Agent process will shut itself off, preventing tests from running. No data will be collected, nor will the Agent receive updates to the ThousandEyes software packages. Customers will need to upgrade to a [supported operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC) to continue to use the Agent and receive software updates.

So, check your [Enterprise Agents Settings page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents), and look for a red triangle warning icon \(\) in an Agent row. Hovering over the icon produces an **Agent OS is Unsupported** warning. Also, the General Info panel for the Agent will display additional details:

IMAGE MISSING

If any of your Enterprise Agents are in this state, review the ThousandEyes Knowledge Base article [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades). Feel free to contact the Customer Success team for further advice.

## Enterprise Agent targets using privileged ports

Bi-directional \(Agent to Agent\) tests and RTP Stream tests can now target Enterprise Agents on privileged ports \(port numbers less than 1024\). This provides testing capability with UDP for services that normally use privileged port numbers, for example the IKE service \(UDP port 500\) of an IPSec VPN. Note that port 22 is excluded from use.

## Bug fixes & minor feature enhancements

Here are the bug fixes and minor features in this week's release:

* Minor improvements in the UI for Kerberos Settings tab for Agent Settings
* For bar charts with very thin bars, a bar's tooltip can now be displayed by hovering over the chart axis adjoining the bar
* Voice Layer tests no longer sending multiple REGISTER and INVITE messages
* Kerberos settings no longer display Agents for which the user lacks permission to edit settings
* On the Get Started with Endpoint Agents page, the Create New Test button for Endpoint Scheduled Tests now allows test creation
* When validating email addresses for Notifications, we now use the most up-to-date list of top-level domains
* Fixed an API issue that could return a 500 HTTP error code for the /usage endpoint when a test changed Account Group during the billing period

Got feedback for us? Want to reminisce about the days of Red Hat 4.0? [Send us an email](mailto:support@thousandeyes.com?subject=2019-05-14+Release+Update)!

