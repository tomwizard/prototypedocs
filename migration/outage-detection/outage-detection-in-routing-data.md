# Outage Detection in routing data

Routing Outage Detection continuously analyzes the entire ThousandEyes data set of BGP routes from more than 300 route monitors to detect reachability issues across the Internet. When reachability outages associated with your tests are detected, you’ll be able to understand the scope of the outage both in the aggregate and as it relates to you, as well as the most likely location of the root cause.

## Using Routing Outage Detection

For the time periods during which the thresholds for a BGP reachability outage are met, purple indicators \(1\) will appear in the swimlane of the timeline in the Routing test view.

IMAGE MISSING

When an affected time period is selected, a dropdown with the label, ‘Outage Detected,’ will appear at the top left corner of the BGP Route Visualization, along with a link to select all of the affected BGP route monitors.

IMAGE MISSING

The ‘Outage Detected’ dropdown shows the country where the BGP outage is occurring, and also the network that is inferred to be the most likely location of the root cause. The dropdown also provides information both specific to the current account group and also aggregated over the ThousandEyes routing data set:

_Specific to your account group:_

The first tab, ‘Affected Tests,’ shows all of the tests in your account group that have been affected by this BGP outage \(1\), along with the corresponding number of affected prefixes \(2\). Click the test link to view that test.

_Aggregated data:_

The number of affected prefixes \(3\) and affected AS origins \(4\) is the global count of affected items in our entire data set of more than 300 monitors, not just the 45 public monitors shown in your Route Visualization.

In addition, the root cause analysis shown in the second tab is computed in the aggregate, where % Routes is the percentage of all affected routes in our entire data set that traverse a given network \(1\). As the % Routes metric for a specific network increases, the number of affected routes going through that network increases. Affected routes thus have a higher association with that network, and the likelihood that this specific network contains the root cause also increases.

The networks with the highest % Routes are shown in descending order with respect to % Routes \(2\). These are the networks that are inferred to be the most likely sources of routing issues, with the topmost network most likely to be responsible for the routing issues.

IMAGE MISSING

Routing Outage Detection helps diagnose reachability-related BGP outages, understand the scope of the outage both globally and as it relates to you, and determine the network\(s\) most likely to be responsible for the routing issues. Use this information to optimize your mitigation strategy, whether it’s calling your provider when they’ve made a mistake in their routing tables, or proactively routing around issues that arise.

## How Routing Outage Detection Works

The Routing Outage Detection algorithm analyzes a data set of routing tables collected from over 300 public BGP route monitors. The data set considered for Routing Outage Detection only includes the following 50 countries with relatively developed network infrastructures: AE, AR, AT, AU, BR, CA, CH, CL, CN, CZ, DE, DK, ES, FI, FR, GB, GR, HK, HU, ID, IE, IL, IN, IS, IT, JP, KR, MX, MY, NL, NO, NZ, PE, PH, PT, RO, RU, SA, SE, SG, TH, TR, TW, UA, US, VN, ZA.

A BGP routing outage occurs when at least 30 prefixes in a given country each see reachability issues during the same time period, where reachability is defined as the percentage of time that a given prefix can be reached via known routes.

For time periods when the outage threshold is triggered, an ‘Outage Detected’ dropdown will appear with additional information about the scope and likely root cause of the outage.

## More information

Read our [Knowledge Base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC) to learn more about using Outage Detection.

