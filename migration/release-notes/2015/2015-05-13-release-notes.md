# Release Notes: 2015-05-13

Our teams have been busy over the last little while, working through dotting Is and crossing Ts this week as we worked up our voice testing release.

## Voice Launch

It's official! We've launched our Voice over IP \(VoIP\) testing capability, allowing the feature to shed its beta status. All customers subscribed to our Professional edition can now create and manage VoIP tests in their accounts.

For an overview on working with Voice Tests, see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmlKAC), and for instructions on using the Voice Metrics view, see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmkKAC).

Existing customers interested in a demonstration of our Voice testing capabilities should contact their Account Executive.

## User-Agent selection for web tests

By popular demand, we've added popular User-Agent strings for selection on web tests. To select a User-Agent string, in the HTTP request section of advanced test settings, select a specific user-agent from the list of available options. We've added predefined options for the most popular browsers on Windows, Mac OS X, and Ubuntu Linux.

IMAGE MISSING

In addition to our default and predefined User-Agent strings, users can define their own User-Agent strings as needed, by using the "Custom" option from the dropdown list. The list of predefined options can be found below:

| **Label** | **User-Agent string** |
| :--- | :--- |
| default | Mozilla/5.0 AppleWebKit/999.0 \(KHTML, like Gecko\) Chrome/99.0 Safari/999.0 |
| Chrome 42 for OS X 10.10 | Mozilla/5.0 \(Macintosh; Intel Mac OS X 10\_10\_4\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/42.0.2311.135 Safari/537.36 |
| Chrome 42 for Linux | Mozilla/5.0 \(X11; Linux x86\_64\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/42.0.2311.135 Safari/537.36 |
| Chrome 42 for Windows 8 | Mozilla/5.0 \(Windows NT 6.2; Win64; x64\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/42.0.2311.135 Safari/537.36 |
| Firefox 37 for OS X 10.10 | Mozilla/5.0 \(Macintosh; Intel Mac OS X 10.10; rv:37.0\) Gecko/20100101 Firefox/37.0 |
| Firefox 37 for Linux | Mozilla/5.0 \(X11; Linux x86\_64; rv:37.0\) Gecko/20100101 Firefox/37.0 |
| Firefox 37 for Windows 8 | Mozilla/5.0 \(Windows NT 6.2; rv:37.0\) Gecko/20100101 Firefox/37.0 |
| IE 9 for Windows 8 | Mozilla/5.0 \(compatible; MSIE 9.0; Windows NT 6.2; WOW64; Trident/5.0\) |
| IE 10 for Windows 8 | Mozilla/5.0 \(Windows; U; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0\) |
| IE 11 for Windows 8.1 | Mozilla/5.0 \(Windows NT 6.3; WOW64; Trident/7.0; AS; rv:11.0\) like Gecko |
| Safari 8 for OS X 10.10 | Mozilla/5.0 \(Macintosh; Intel Mac OS X 10104\) AppleWebKit/600.6.2 \(KHTML like Gecko\) Version/8.0.6 Safari/600.6.2 |
| Custom | user-defined |

Users managing web analytics platforms will need to take alternate approaches to filtering ThousandEyes agent traffic; we've published this article on one such method [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnyKAC_Identifying-traffic-from-ThousandEyes-Agents).

## Permission changes

We've simplified role permissions for managing users: now users in the built-in Account Admin role will now be able to modify users in any of their own account groups.  

## Alerting changes

We've added the option to alert based on response headers in HTTP server tests.  Check out this [article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) for details on setting up alert rules to to use regular expression parsing on response headers for alert rules.

## Agent changes

We've made a few changes to our Agent codebase over the last few weeks as well...

### Updated version of Chromium

We've updated the version of Chromium running on the following operating systems:

* Ubuntu 12.04 - 14.04: Chromium version 40
* Debian 7: Chromium version 40
* Red Hat Enterprise Linux / CentOS 7: Chromium version 40

Red Hat Linux-based systems running version 6.x will continue to run Chromium version 26.

### Point-to-Point networks

Prior to this release, agents that required point to point network access in order to connect to the Internet could cause the testing process to hang under certain circumstances when attempting to run network tests.  This release corrects this behavior by supporting the use of point to point networks.

## API

This is another reminder that on June 4, 2015 we will be permanently removing versions 2 and 3 of the ThousandEyes API, and switching our current version \(where the version is not explicitly specified\) from APIv4 to APIv5.  Customers using versions 2 and 3 of the ThousandEyes API have been notified individually.

We've also added a new endpoint to the APIv5 for /agents/{agentId}, which returns a list of all tests and accounts to which the agent is assigned, as well as shows utilization. Check out our [APIv5 change summary](http://developer.thousandeyes.com/v5/#/changesummary) for more information.

## Questions?

We love hearing from our customers.  If you've got a question or a comment, please don't hesitate to make your voice heard!  [Email us anytime](mailto:support@thousandeyes.com?subject=May+13+2015+Release).

