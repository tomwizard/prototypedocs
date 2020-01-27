# Release Notes: 2016-06-22

### Release update 2016-06-22

Almost halfway through the year, we're finally into summer!  Bring out the shorts, and welcome, event season!

IMAGE MISSING

We'll be at Velocity Santa Clara on June 22nd.  Be sure to stop by our booth \#707 and say hello!

IMAGE MISSING

We'll also be attending Cisco Live in Las Vegas!  Booth \#2244 is where it's at! \(and as usual, we'll have a fresh batch of t-shirts\)

From a blog perspective, be sure to take time to read our own [Primož Sečnik Kolman's post](https://blog.thousandeyes.com/reporting-noc-box-whiskers-widget-carousel/) on creating a lightweight framework for shuffling through embedded report widgets in a NOC environment \(complete with a link to shared source on github\), as well as our [Chief Information Security Officer Alexander Anoufriev's post](https://blog.thousandeyes.com/secure-dns-management-best-practices/) on attacks, mitigation and monitoring techniques to use when hosting domain name services in your environment.

And, without further ado, our release updates for this week.

## Reports

### Limits

We've added the ability to limit the number of rows for widgets which support sorting of results based on value.  This applies to bar chart \(both stacked and grouped versions\), table, and multi-metric table widgets.

IMAGE MISSING

### Widget size configuration

We've made it easier to configure a widget as half-size by adding a control to the right hand side of the widget when viewing in Add/Remove Widgets mode.  Click the &gt; to expand a widget to full width, and &lt; to collapse a widget to half-size.

IMAGE MISSING

See [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS) for more information on working with reports.

## Test settings changes

### User-Agent option changes

We've updated the list of pre-filled User-Agent values found in the Advanced settings of Web tests to reflect current versions of each of the 4 mainstream browsers on each available operating system.  The following options are available:

|  | Chrome | Firefox | Internet Explorer | Safari |
| :--- | :--- | :--- | :--- | :--- |
| Mac OS X 10.10 | 51 | 47 | n/a | 9 |
| Linux | 51 | 47 | n/a | n/a |
| Windows 8 | 51 | 47 | 9, 10, 11 | n/a |

Existing tests will not be changed, so if you had previously configured a test to use Chrome 47 for Mac OS X, the test's settings will be unchanged.

###  SSL version changes

We've changed our options for SSL versions on HTTP server tests.  Effective today, the following versions are available:

* **Auto**: the agent will negotiate with the target server and negotiate the highest supported level of encryption available.  If both the agent and server support TLS 1.2, then it will negotiate at this level.  If not, the agent will fall back to 1.1, 1.0.  
* **SSLv3**: When connecting, the agent will explicitly request SSLv3 be used.  If this fails, the connection will fail.  If your server uses SSLv3, this option must be explicitly set.
* **TLSv1.0**: When connecting, the agent will explicitly request TLS 1.0 be used.  If this fails, the connection will fail.
* **TLSv1.1**: When connecting, the agent will explicitly request TLS 1.1 be used.  If this fails, the connection will fail.
* **TLSv1.2**: When connecting, the agent will explicitly request TLS 1.2 be used.  If this fails, the connection will fail.

Any tests which had previously selected the "default" or "TLSv1" options will be automatically changed to use the "auto" option.

See [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC) for more information on working with test settings

## Other changes

* We've renamed the "Total Fetch Time" metric found in the HTTP Server view to "Total Time" to make the metric more consistent across views.
* The sliders which control loss and latency thresholds in path visualization have been relabeled as "Forwarding Loss" and "Link Delay", respectively.
* We've introduced Dashboard support for FTP tests

## Bugs squashed

* We've corrected a problem that caused some report snapshots to be generated with incorrect formatting.
* Corrected an issue which prevented ThousandEyes Virtual Appliance installs running using Ubuntu 12.04 from updating to the most recent version.
* Users can now rename saved events.
* Corrected a problem that caused agent installation to fail due to a missing account token.
* Fixed an issue which prevented the option to enable password expiration from saving.

