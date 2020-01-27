# Release Notes: 2016-04-13

A quick plug before our standard Release Note content: our marketing team has been busy putting things together for our next major event, ThousandEyes Connect NYC. Join us and hear what our panel of customers has to say! The event will occur on May 19, 2016 in Bryant Park in New York, and we're excited to announce presenters from Nasdaq, AIM Specialty Health and VeriSign.

IMAGE MISSING

Registration is free; click [this link](https://www.thousandeyes.com/events/connect/new-york-2016) to register.

Now back to your regular Release Notes.

## Agent-to-Agent Tests

We've improved Agent-to-Agent tests by adding support for network address translation \(NAT\) traversal. This will allow Agents running Network/Agent-to-Agent tests to initiate connections to Enterprise Agents behind a NAT'ing firewall without the need for port forwarding rules on the NAT'ing firewall.

To enable NAT traversal for a target Enterprise Agent, click the **Behind a NAT** checkbox on the Agent's settings.  Agents with this setting will run a NAT traversal compatibility check.  If your environment is not compatible with NAT traversal, a warning will be displayed for the Agent on the Enterprise Agents page and under the Agent Status in the [Navigation Bar](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).

## Support for Internet Explorer 9 and 10

Since Microsoft has moved Internet Explorer 9 and 10 into "end of support" status \([see this link](https://www.microsoft.com/en-us/WindowsForBusiness/End-of-IE-support)\), we are ending support for Internet Explorer versions 9 and 10 in ThousandEyes. Beginning today, if you're using Internet Explorer 9 or 10, you will see a warning when you log in. In a month's time, we will remove the ability to log in using these versions of Internet Explorer.

##  Bugs squashed

The following bugs have been corrected in this week's release

* Customers using authenticated web proxies with the ThousandEyes Virtual Appliance to connect to the Internet were unable to use passwords which included certain special characters. 
* We've added support for both comma \(,\) and semicolon \(;\) as delimiters in the Add User form of the Users tab, on the Account Settings page.

## Questions?

We love hearing from our users!  [Send us a note](mailto:support@thousandeyes.com?subject=2016-04-13+release+update) and we'll be happy to answer any questions you have!

