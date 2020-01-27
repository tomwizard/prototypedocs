# Release Notes: 2015-06-10

Almost every day, we get questions from customers on the subject of alerting; Questions along the lines of alert thresholds, alerting granularity, and how to manage things like latency alerts that vary on a regional basis. This week's release focuses largely on increasing the capabilities of our alerting system, which will allow users to more effectively manage their alerting granularity.  
 

## Alerting

We've made a number of changes to alerting: check out the KB article on [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) for more detail on working with alert rules.

### Path trace alerts

We've added a new category of alert rule based on the results of Path Trace. Users can configure alerts on specific hops from either the source or destination, based on network latency, reverse DNS, AS Name, Prefix, or IP address.  To add a path trace alert, choose the **Network** layer, and alert type **Path Trace**, then add criteria to alert based on specific hops in the path.

IMAGE MISSING

### Agent location filters

Beginning today, users can configure alert rules with Agent location filters; This will allow users to configure alert rules on a regional basis, allowing users to set rules which are region and/or location-specific. In conjunction with the Path Trace alerts above, this can be used to effectively manage alerting on both Anycast and Unicast destinations, as well as handle regional variations in latency for test results coming from Agents located around the world.

IMAGE MISSING

When defining alert rules with location filters, we recommend creating generic alert rules which will apply to a specific country, or region.  Tests leveraging these alerts will self-select based on the intersection of the agents assigned to the test, and on the agents in a specific location.

### Default alert rules

To roll up all of the alerting changes, we've made a change to the rules around assigning default alert rules in the platform. Users can now create multiple alert rule defaults for each type of alert, in order to accommodate the location filter rules. For example, for a service which is located in the United States, a user might configure a network latency-based alert rule for US-based agents, an alert rule for Europe-based agents, and an alert rule for agents based elsewhere in the world.  
 

## New permission: view sensitive transaction information

We've added a new permission, which controls whether or not users have access to view sensitive transaction information \(including values used by the type or typeKeys commands\). Users in a role which includes this permission will have access to view unmasked username/password entries associated with the transaction script. Users in a role which does not include this permission will see masked input.  This permission is automatically assigned to any role which had the Create Transaction Test permission assigned prior to the update.  
 

## Browserbot fixes

We've made a couple of minor corrections to the Browserbot deployment in this week's release.

* In certain circumstances, transaction tests would cause the browserbot to hang following the execution of a transaction test. While this didn't materially affect the performance of the browserbot, it could cause certain tests to incorrectly report an incomplete transaction.
* We've also corrected a memory leak in the version of Chromium that we ship. In certain circumstances, this memory leak could cause the agent's host operating system to become unresponsive until administrative intervention.   

## API

As previously advertised, API versions 2 and 3 have been removed. Any requests made against v2 or v3 will be redirected to the new current version \(v5\). Requests using legacy authentication \(authToken specified on the querystring\) will be rejected with an HTTP/401 response code.

APIv5 is now the default version of the API: requests to https://api.thousandeyes.com will now be directed to v5. To specify version 4, add the version explicitly in the request \(for example, https://api.thousandeyes.com/v4/status\)

Review the ThousandEyes developer reference documentation at [developer.thousandeyes.com](http://developer.thousandeyes.com/)

## Questions, Comments?

As always, we want to hear your feedback! [Send us an email](mailto:support@thousandeyes.com?subject=2015-06-10+Release+Notes) and let us know what you think.

