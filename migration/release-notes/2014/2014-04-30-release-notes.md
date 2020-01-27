# Release Notes: 2014-04-30

Well, it's the end of April.  As the old saying goes, April showers bring May flowers - so keep an eye on this space for more updates in the coming month.  We've had a few projects gestating over the last few months, and they're starting to bear fruit.  Mixed bag of metaphors aside, here's a list of fun stuff we've been working on over the last few weeks.  Don't hesitate to [let us know](mailto:support@thousandeyes.com), if you have any questions, comments or concerns with the release. 

## Agent proxy bypass list

We've updated our agent code to allow a proxy server to be bypassed for tests run from a Enterprise Agent. In situations where the agent requires proxy configuration in order to access the Internet, and users wish to test internal targets \(which do not require use of a proxy server\), the agent can be configured with a list of hostnames, IP addresses, domain name suffixes, and network prefixes, which will be used when running a test against the target.

_VERY IMPORTANT_: test targets are matched literally against the proxy bypass list - so you can't rely on name resolution in order to resolve a name to a network block.  Take www.company.com as an example, which in my example resolves to 10.1.1.1.  The only way that a test for the target will successfully bypass the proxy is to enter www.company.com \(or \*.company.com\) to the proxy bypass list.  Entering 10.1.1.1 or 10.0.0.0/8 will fail to match the URL - and the request will be routed through the proxy, resulting in missing network data.

In order to specify this setting, the agent must be configured to use a proxy.   In the Agent tab of the Virtual Appliance configuration page, under the "use proxy" option, specify proxy details - including proxy bypass list, if applicable:

IMAGE MISSING

Each entry must be added individually, in the form:

| **Rule** | **Example** |
| :--- | :--- |
| Exact IP | _10.0.0.1_ |
| Exact Hostname | _www.myserver.com_ |
| Network Prefix | _192.168.0.0/16_ |
| Wildcard Suffix | _\*.company.com_ |

If you are using the Linux package version of agents, you can manually edit the agent configuration file, found in /etc/te-agent.cfg.  The configuration file entry is a semicolon-delimited list of rules, with the name "proxy-bypass-list"; an example is shown below.

```text
proxy-bypass-list=10.0.0.0/8;192.168.1.1;*.mycompany.com;www.myserver.com
```

Note - on Linux package installations, the te-agent process must be restarted in order for any change made to the configuration file to take effect. This does not apply to the virtual appliance, as it is handled automatically.

Once the agent checks in, the proxy bypass list can be found under the "Advanced Options" for the agent, using the Agent Settings page.

IMAGE MISSING

### Updating multiple agents

If you have multiple Enterprise Agents which require configuration simultaneously, a utility is available for this - contact the ThousandEyes Customer Success team for instructions on making widespread changes.

## Network tests for proxied agents

Enterprise Agents running behind a proxy will no longer run network tests for targets whose connections traverse a proxy server.  Prior to this release, in most circumstances, Enterprise Agents would show 100% packet loss, and no path visualization information for network tests which were targeted on resources traversing the proxy.

If the test target is found in the proxy bypass list, then network tests will run as they previously did \(and return valid data\) otherwise, the test will return "no data", thus preventing the agent from being considered during validation against alert rules.

## BGP subprefix alert rules

We've updated our alert rules for the "Subprefix Exists" rule: Prior to today's change, users could alert when a subprefix is detected on a monitored prefix, by using the 'Include Subprefixes' option on the test settings.  Effective today, users can now choose to suppress alerts when a specific subprefix is advertised, by changing their alert rule to be based on 'Subprefix not in \(w.x.y.0/z\)'.

Note: Prefix must be entered using CIDR notation \(ie, 172.16.1.0/24\)

To retain the legacy behavior, configure an alert rule for Subprefix not in \(&lt;empty input&gt;\).  Existing rules will be configured using the Subprefix exists criteria will be shown as "Subprefix not in \(\)", as the "Subprefix exists" option is no longer available.

## API updates

We've updated the methodology for updating tests. Prior to this change, in order to update a test, all required fields of a test needed to be submitted. After today's release, only the fields requiring modification need to be updated as a part of the data posted in the request. Check out the [developer reference site](http://developer.thousandeyes.com/) for more information.

