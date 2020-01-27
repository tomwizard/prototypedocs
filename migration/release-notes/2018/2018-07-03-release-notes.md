# Release Notes: 2018-07-03

Welcome to tonight's release!

Ten days 'til ThousandEyes Connect in Silicon Valley, on July 12th!

IMAGE MISSING

Check out the [schedule of events](https://www.thousandeyes.com/events/connect/santa-clara-2018) and sign up today--registration is free. Nothing like a cool conference to beat the summer heat!

The new crop of ThousandEyes blog posts discusses two significant recent outages. On Friday, Senior Marketing Manager Angelique Medina posted about that day's fiber optic cable cuts in two providers' networks which affected many subscribers of Comcast's Xfinity service, in locations across the nation. Read about the rip and the ripple in her article [Comcast Fiber Outage Rips the Internet](https://blog.thousandeyes.com/comcast-fiber-outage-rips-the-internet/).

From ISP outages to IoT outages... In the beginning of June, Philips introduced Hue, a smart home service for lighting. The API-based service experienced rollout issues with its API service. Two weeks prior, Nest experienced similar issues with its home monitoring offering. Our VP of Product Marketing, Alex Henthorn-Iwane, asks "How many API calls does it take to turn on a light bulb?" in his post [Smart API Monitoring for Smart Light Bulbs](https://blog.thousandeyes.com/smart-api-monitoring-for-smart-light-bulbs/).

On a lighter note, ThousandEyes employees had a Hack Day last week, and some of the results can be seen in Archana Kesavan's post, [ThousandEyes Hackday: Where Innovation Meets Fun](https://blog.thousandeyes.com/hackday-innovation-fun-june-2018/).

And now for the details of tonight's release...

## Appliance web interface

We've revamped the web-based administrative interface of our Appliances to correspond to the app's look and feel, and to prepare for future new features.

IMAGE MISSING

The Diagnostics have been moved under the Status menu. You'll also now see the details of the web server's SSL certificate, under the Appliance Access menu. Stay tuned for more improvements!

## Reports

We've added a new Settings menu item for Reports. The Reports Settings page lists the current Account Group's reports, and permits management of individual reports or multiple reports \(bulk actions\). Bulk actions are duplicate, delete and add a label.

IMAGE MISSING

Users can view the list by filtering on Snapshots of reports, email recipients of a Snapshot, or labels.

Single report actions include setting a report as the default report, adding labels, duplicating and deleting. A report can also be renamed, and given a description.

IMAGE MISSING

## Path Visualization grouping

In a [previous release](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q0noCAC_Release-Update-2018-06-06#pv_group), we added new groupings for Agents on the Path Visualization. This release adds the sameNetwork

,Location

 andNetwork & Location

 options for the Destinations and the Interfaces quick links.

An example of grouping destinations by Location:

IMAGE MISSING

Each destination grouping node displays the number of targets in the group. In the example above, the location of Sunnyvale contains two targets.

## Device Layer filters

​We've added filters to the Search bar on the [**Devices &gt; Device Settings**](https://app.thousandeyes.com/settings/devices/?tab=credentials) page. Devices can now be displayed by Device Type or Monitoring Agent.

IMAGE MISSING

## ServiceNow Alerts

Notifications in Alert Rules can now be sent to ServiceNow, natively. When creating an Alert Rule, click **Edit Integrations** in the Integrations section of the Notifications tab, and select ServiceNow as the **Type**:

IMAGE MISSING

A Notification is sent to ServiceNow when a condition triggers an Alert Rule, and when the condition that triggered the Alert Rule is no longer in effect.

## API

To provide more direct access to Agent data, users can now select ‘CLOUD’, ‘ENTERPRISE’ or ‘ENTERPRISE\_CLUSTER’ as the **agentTypes** parameter in the API request. For example, the request:

```text
https://api.thousandeyes.com/v6/agents.json?aid=1234&agentTypes=ENTERPRISE_CLUSTER 
```

will list only Enterprise Agent clusters in the Account Group with ID 1234.

## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* If a Path Trace from an Endpoint Agent does not reach the target, a message is now displayed indicating that the trace was incomplete.
* Fixed an issue preventing users from resetting their passwords.
* Fixed an issue with the Alert History's time selection which could display incorrect dates/time using the arrow selectors.
* Fixed an issue which caused the Account Groups listed for a user under the Account Settings' Users tab not to be correct.
* Fixed a Device Discovery issue preventing devices with a generic engineID from being discovered.
* Fixed an issue preventing the Bandwidth test portion of Network metrics from functioning when the Protocol setting is ICMP.

## Independence Day holiday support and release

July 4th is the Independence Day holiday in the US. Support on July 4th will be by email for the following hours:

| UTC/GMT | US EDT | US PDT |
| :--- | :--- | :--- |
| 13:00 to 1:00 on July 5th | 9:00 to 21:00 | 6:00 to 18:00 |

## Questions and comments

Got feedback on the new features? Got an idea for our next Hack Day? [Send us an email](mailto:support@thousandeyes.com?subject=2018-07-03+Release+Update)!

