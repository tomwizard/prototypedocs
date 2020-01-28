# How Alerts work

The ThousandEyes platform allows customers to configure highly customizable Alert Rules and assign them to tests, in order to highlight or be notified of events of interest.  For customers who want simplicity in alert configuration and management, the ThousandEyes platform ships with default Alert Rules configured and enabled for each test.

## Notifications

Alert notifications are delivered either via email, webhooks or via a third-party integration, such as PagerDuty, Slack, HipChat or ServiceNow. Recipients are configured in the Alert Rule's **Notifications** tab. Alerts will be active in the ThousandEyes platform as long as your Alert Rule conditions are met, but notification of the alert being active will only occur at the start of the active period. Alerts can optionally be configured to perform notification once the alert is no longer active.

For email notifications, when multiple alerts are raised simultaneously, their data will be grouped into a single email notification. 

Webhooks integration permits users to send JSON-formatted alert data to a webhooks-enabled server via HTTP. The information can then be programmatically processed and subsequent actions taken automatically. For more information on configuring ThousandEyes Alert Rules with webhooks, refer to the ThousandEyes Knowledge Base article [Using Webhooks](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmVKAS).

PagerDuty integration allows you to use an Escalation Policy \(which defines rules for notification destinations, repeat notifications and other actions\) in your PagerDuty service to receive notifications from ThousandEyes. For more information on configuring ThousandEyes Alert Rules with PagerDuty, refer to the ThousandEyes Knowledge Base article [PagerDuty Integration](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBsCAK).

The Slack and HipChat integrations allow alert data to be send to a chat/instant message application. Users can send notifications to the Slack channel and/or HipChat room of choice.For more information on configuring ThousandEyes Alert Rules with Slack or HipChat, refer to the ThousandEyes Knowledge Base article [Slack and HipChat Integration](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cn2FCAS_Slack-and-HipChat-Integration) .

ServiceNow integration facilitates delivery of direct notification into a ServiceNow account so it may be processed and acted upon based on workflows defined within that system.  For more information configuring Alert Rules to send notifications directly into the ServiceNow platform, refer to the ThousandEyes Knowledge Base article [ServiceNow Integration](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqJPCA0_ServiceNow-Integration).

## Viewing alerts

Current and past alerts can be viewed on the [Alerts page](https://app.thousandeyes.com/alerts/list/).  The Alerts page has two tabs:

* **Active Alerts:** List of alerts currently active for any test within your Account Group.
* **Alerts History:** List of alerts no longer active from tests in your Account Group, shown chronologically on a timeline, and with a table whose entries contain details on each alert.

### Active Alerts

IMAGE MISSING

The Active Alerts tab shows all alerts currently active in your Account Group. The Active Alerts tab will auto-refresh every two minutes.

1. **Search**:  Search for alerts based on the following criteria: **Alert ID, Alert Rule Name,  Alert Type, Test ID, Test Name, Test Type or Status**. Entering text followed by the return/enter key will execute a search and display results in the table below. To filter events by more than one criteria, click either **All** or **Any** links to specify whether the table rows must match all \(AND\) or any \(OR\) of the selected criteria.  
2. **Alert Status:** 
   * A **red** colored box indicates that the Alert Rule is currently active for that Test. 
   * A **green** colored box indicates that the Alert was recently cleared for the test. A cleared Alert will be shown under Alert History tab.
   * A **grey** colored box indicates that the Alert Rule was disabled for that Test
3. **Alert Rule Name**: Name of the Alert Rule currently active. Expand an Alert Rule for more detailed information by Agent, BGP monitor, Start/End Time, Metrics at Alert Start, Metrics at Alert End and Duration for which the Alert was active.
4. **Test Name**: Name of the Test for which the Alert Rule is currently active
5. **Alert ID**: When gathering details for an Alert via ThousandEyes API, use the Alert ID to reference a particular Alert.

### Alert History

IMAGE MISSING

The Alerts History tab tabulates triggered Alerts which are currently in "cleared" or "inactive" state or are "disabled". To interact with the Alert History page,

1. **Date and Time slider**: Input the date endpoints to view Alerts active during that timespan.  Click and drag on either the start or end bars and drag to the desired date.  Your selection will update the **From** and **To** date and time fields automatically. 
2. **Date and Time selector:** The **From** and **To** fields allow manual input of the date and time endpoints to display Alerts active at that time.  Clicking in the date field will both allow manual entry of dates and display a clickable calendar to select a date. Click on the calendar arrows to navigate in the current view \(default is the month view\). To change to a view of months in a year or a range of years, click the current title \(month, year or year range\) at the top-middle of the calendar.  The view will cycle to the next timeframe: month -&gt; months -&gt; years.
3. **Search for alerts**.  By entering text into the search box, you will search for alerts matching based on the following criteria: **Alert ID, Alert Rule Name,  Alert Type, Test ID, Test Name, Test Type or Status**. Entering text followed by the return/enter key will execute a search and refine the table below. To filter events by more than one criteria, click either **All** or **Any** links to specify whether the table rows must match all \(AND\) or either \(OR\) of the selected criteria.
4. **Alert Rule Name**: Expand an Alert Rule for more detailed information by Agent, BGP monitor, Start/End Time, Metrics at Alert Start, Metrics at Alert End and Duration for which the Alert was active.
5. **Test Name**: Name of the Test for which the Alert Rule was triggered.
6. **Duration**: Length of time for which the Alert Rule was active for that test.
7. **Alert ID:** When gathering details for an Alert via ThousandEyes API, use the Alert ID to reference a particular Alert.

## Assignment to tests

Once you have created an Alert Rule it can be assigned to any test which has the **Enable** box checked, on the test configuration page.  By default, each test has the rule "Default &lt;test type&gt; Rule" assigned to it, with your account's email address configured as the recipient for email notification. To add or remove rules, click the pull-down menu below the Enable box, and select or deselect rules.  To create a new rule, click the Edit Alert Rules link to acces the Add New Alert Rules page, and create your rule.  You will then return to the test configuration page, and use the pull-down menu to assign your new rule to the test.

## Rule configuration

Each rule has a name, a series of tests against which it is enabled, a scope of locations to which the Alert Rule applies, Boolean criteria defining the alert conditions, and the number of locations from which the alert conditions must be met in order to trigger an alert.  The rule also can include a notification mechanism, such as a list of email recipients \(recipients need not be users of ThousandEyes in order to receive email notifications\), a PagerDuty Service or one or more Webhooks.

The image below displays the configuration options of a new Alert Rule.

IMAGE MISSING

1. **Alert Type Layer:** test layers available to your organization.
2. **Alert Type:** available alert types for the selected test layer.
3. **Rule Name:** An alphanumeric string naming this Alert Rule.

#### Settings tab

1. **Tests:** Select tests to which this Alert Rule is assigned.  You may choose to configure no tests with this Alert Rule, and assign it to tests at a later time.
2. **Monitors, Countries, Agents:** This selector will display either "Monitors" for a Routing Layer Alert Rule, "Countries" for a DNS+ Layer Alert Rule or "Agents" for all other Alert Rules.  The selector has one of three values:
   * All: This Alert Rule applies to all Agents or Monitors for a test to which this Alert Rule is assigned. 
   * All except:  This Alert Rule applies to all Agents or Monitors for a test to which this Alert Rule is assigned, except for the Agents specified in the selector that will appear when "All except" value is chosen.
   * Specific: This Alert Rule applies only to specific Agents or Monitors for a test to which this Alert Rule is assigned. The Agents or Monitors are specified in the selector that will appear when "Specific" value is chosen.
3. Specify the number of Agents, **all/any** of the following alerting conditions, and the number of test rounds the conditions must be met before alerting.
4. **Threshold:** Specify the threshold value for locations \(Agents, Monitors or Countries, depending on rule type\) that must meet the alert conditions in order to trigger this Alert Rule. This value will be either a number of Agents/Monitors/Countries, or a percentage of Agents/Monitors/Countries, as specified in the next setting.

    **NOTE:** When a percentage of Agents, Monitors or Countries is used, and the percentage results in a non-whole number threshold value of actual Agents, Monitors or Countries, the fractional part of the value is significant.  For example, when an Alert Rule with a threshold of 25% of all Agents is applied to 13 Agents, the threshold is 3.25 Agents. This threshold will require 4 Agents to meet the alert criteria in order to trigger the Alert Rule.

5. **Threshold units:** Select either Agent, Monitor or Country, or percentage of Agents, Monitors or Countries.
6. **Rounds \(met\):** Select the number of test rounds that the following alert condtion\(s\) must be met out of a total number of rounds in order to trigger the Alert Rule.  See the **Rounds \(total\)** entry below.
7. **Rounds \(total\)**: Select the total number of test rounds in which the **Rounds \(met\)** selection is evaluated.  For example, if Rounds \(met\) = 2 and Rounds \(total\) = 3 then for every three rounds, the Alert Rule will trigger if the condition\(s\) were met twice.
8. **Metric:** Select a test metric for this condition.
9. **Operators:** The following operators are available:

   * **&gt;, &lt;, ≥, ≤ :** Numerical comparisons for greater than, less than, greater than or equal to, less than or equal to. Available for all numerical \(decimal and integer\) metrics, such as packet loss percentage \(decimal\) of Network Layer tests, or Error Count \(integer\) of a Page load test.
   * **is, is not:** Numeric comparison for values which are not continuous ranges \(e.g. HTTP status codes\) or to a fixed string value, such as the Error Type \(e.g. "DNS", "Connect", "SSL"\).
   * **is in, is not in:** Numeric or string comparison to a list of values. For example, a BGP Routing rule compares a test metric's AS number \(integer\) to a list of one or more AS numbers to determine if the test metric is found or not found in the list.
   * **is empty, is not empty:** Determines whether a metric has a value or has no value.
   * **is incomplete:** Determines whether a test completed the operations for a given metric. For example, a Path Trace Alert Rule is used to determine whether the path trace reached its destination, or a Page Load test fully loaded a page.
   * **is present:** Triggered when an error condition is present.
   * **matches, does not match:** Determines whether the [POSIX regular expression](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnCKAS) in the Alert Rule is found within the string produced by the test metric \(i.e. a substring will produce a match\). For example, an Alert Rule for the Error metric of an HTTP Server test with the alert condition:

     will alert when the test's Error Details text is "SSL certificate problem: certificate has expired":

     because the regular expression "certificate\s\*\w\*:" matches the sub-string "certificate problem:".  
     IMAGE MISSING  
     will alert when the test's Error Details text is "SSL certificate problem: certificate has expired":  
     IMAGE MISSING  
     because the regular expression "certificate\s_\w_:" matches the sub-string "certificate problem:".

   The operators available per type of Alert Rule are also shown in the table below.

10. **Threshold:** The value that the Metric setting will be compared against, using the chosen operator.  Note that some operators do not have a Value field.
11. **Add/Delete:** Click the + or - icon to add or delete alert criteria to this Alert Rule.  Criteria can be nested for some types of Alert Rule.
12. **Compatible Test Types:** Test types to which this Alert Rule can be assigned.

DNS Server Alert Rules

DNS Server Tests differ from other ThousandEyes tests in that multiple servers can be explicitly targeted in a single test.  As a result, DNS Server Alert Rules are evaluated on a per-server basis; each server in the **DNS Servers** field of the test configuration will have the Alert Conditions evaluated separately from all other servers in the **DNS Servers** field. For example, consider an Alert Rule that has the following Alert Conditions:

IMAGE MISSING

When assigned to a DNS Server test with two servers configured as the targets, each server will be evaluated separately against the above Alert Condition.  To trigger the Alert Rule, at least four Agents must receive an Error against same DNS server.  The Alert Rule would not be triggered if, for example, three Agents received an Error when testing the first DNS Server and a fourth Agent received an Error when testing the second DNS server.

#### BGP Alert Rules

A BGP Alert Rule can be applied to a Routing Layer BGP test, or to a different Layer type that provides the BGP Route Visualization View. It is important to note that some Alert Rule conditions can be applied differently depending on which type of test the rule is assigned to.  For example, a BGP test has only a single target prefix which will be evaluated against the Alert Conditions.  If the "Covered Prefixes" box is checked, any covered prefixes found are not evaluated against the Alert Conditions except the explicit "Covered Prefix" condition.

In contrast, a non-BGP test type can have one or more targets. DNS Server tests can explicitly test multiple DNS servers.  An Agent to Server target's domain name can resolve to multiple servers IP addresses.  When creating the BGP Path Visualization, the Prefix selector will show these multiple target prefixes, and evaluate each prefix against any BGP Alert Rules assigned to the test.  Thus, prefixes which would be considered covered prefixes under a BGP test and not evaluated by the Alert Rule \(unless by a "Covered Prefix" condition\) are evaluated when assigned to the non-BGP test.  Similarly, the "Covered Prefix" condition does not have any relevance when assigned to a non-BGP test.

The BGP Alert Rules have a parameter named "Prefix Length", which is used to determine the length of prefixes evaluated by the rule. The "Prefix Length" can be individually configured for IPv4 and IPv6 protocols.

#### Notifications tab

In addition to presenting the Alert in the app.thousandeyes.com UI, the ThousandEyes platform can deliver notifications of alerts through a number of services. The image below displays the Notifications configuration options of a new Alert Rule.

IMAGE MISSING

1. **Send emails to:** A list of addresses to which an alert email will be sent when the Alert Rule is first triggered.  Addressees need not be users of the ThousandEyes platform.
2. **Edit emails:** Click this link to add email addresses to the Notifications address book.
3. **Send an email:** Check this box to send an email when the Alert Rule is no longer active.
4. **Add/Remove Message:** Enter text to be added to the body of the Alert Rule's email notification.
5. **Webhooks:** Webhooks-enabled web services that receive the alert notification.
6. **Edit webhooks:** create or edit [webhooks](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmVKAS_Using-Webhooks-server-sample-code-included) which can then be added to the Webhooks **Send Notifications to** field.
7. **Integrations:** integrations that should receive the Alert Notification. 
8. **Edit Integrations:** create or edit an integration which can then be added to the Integrations **Send Notifications to** field. Currently ThousandEyes offer integrations for  [PagerDuty](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBsCAK_PagerDuty-Integration), [HipChat, Slack](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cn2FCAS_Slack-and-HipChat-Integration) and [ServiceNow](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CqJPCA0_ServiceNow-Integration).

**Note:** Alerts will be active as long as your Alert Rule criteria are met, but any configured email notification will only occur at the beginning of the alert.

#### Available Operators, Metrics and units

The following table shows a list of test types which are available in the ThousandEyes platform, and the test metrics and operators.   

| Test Layer | Alert Type | Metric | Operators | Units |
| :--- | :--- | :--- | :--- | :--- |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Packet loss | ≤,≥ | % |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Latency1 | ≤,≥ | ms |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Jitter | ≤,≥ | ms |
| Network | End-to-End \(Server\), End-to-End \(Agent\) | Error | is present, matches, does not match | n/a |
| Network | End-to-End \(Agent\) | Throughput | ≤,≥ | Kbps |
| Network | End-to-End \(Server\) | Available Bandwidth | ≤,≥ | Mbps |
| Network | End-to-End \(Server\) | Capacity | ≤,≥ | Mbps |
| Network | Path Trace | Delay | ≤,≥ | ms |
| Network | Path Trace | IP Address2 | in, not in | IP address or prefix |
| Network | Path Trace | ASN2 | in, not in | List of ASNs |
| Network | Path Trace | rDNS2 | in, not in | exact hostname or wildcard-based match to domain |
| Network | Path Trace | MPLS Label2 | is empty, is not empty |  |
| Network | Path Trace | DSCP2 | is, is not | DSCP value selected from list |
| Network | Path Trace | Server IP | in, not in | IP address, prefix |
| Network | Path Trace | Server MSS | &lt;, &gt; | bytes |
| Network | Path Trace | Path MTU | &lt;, &gt; | bytes |
| Network | Path Trace | Path Length | &lt;, &gt; | hops |
| Network | Path Trace | Trace is incomplete | n/a |  |
| DNS | Server, Trace DNSSEC | Error | is present, matches, does not match | n/a |
| DNS | Server | Resolution time | ≤,≥ | ms |
| DNS | Server, Trace | Mapping | is not in | quoted &lt;comma-separated list of mappings&gt; |
| DNS+ | Server Latency, Domain | Resolution Time | ≤,≥ | ms |
| DNS+ | Domain | Availability | ≤,≥ | % |
| DNS+ | Domain | Mapping | is not in | quoted &lt;comma-separated list of mappings&gt; |
| Web | HTTP Server | Response code | is | any error \(≥ http/400 or no response\)  ok \(http/200\)  redirect \(http/300 |
| Web | HTTP Server | Response Header | matches, does not match | [POSIX Extended Regular Expression Syntax](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnCKAS) |
| Web | HTTP Server | DNS time | ≤,≥ | ms |
| Web | HTTP Server | Connect time | ≤,≥ | ms |
| Web | HTTP Server | SSL negotiation time | ≤,≥ | ms |
| Web | HTTP Server | Wait time | ≤,≥ | ms |
| Web | HTTP Server | Receive time | ≤,≥ | ms |
| Web | HTTP Server | Response time1 | ≤,≥ | ms |
| Web | HTTP Server | Total Fetch Time | ≤,≥ | ms |
| Web | HTTP Server | Throughput | ≤,≥ | kBps |
| Web | HTTP Server | Error | is present, matches, does not match | n/a |
| Web | HTTP Server | Error type | is, is not | DNS, Connect, SSL, Send, Receive, Content, HTTP, Any |
| Web | HTTP Server | Client SSL Alert Code | is, is not | SSL error type.   eg. Unexpected message \( 10 \), Bad Certificate \(42\) |
| Web | HTTP Server | Server SSL Alert Code | is, is not | SSL error type.   eg. Unexpected message \( 10 \), Bad Certificate \(42\) |
| Web | Page Load | Page load | Is incomplete | n/a |
| Web | Page Load | Response time | ≤,≥ | ms |
| Web | Page Load | DOM load time | ≤,≥ | ms |
| Web | Page Load | Page load time1 | ≤,≥ | ms |
| Web | Page Load | Error Count | ≤,≥ | \# |
| Web | Page Load | Domain Name3 | is in, is not in | quoted &lt;comma-separated list of mappings&gt; |
| Web | Page Load | Total Fetch Time3 | ≤,≥ | ms |
| Web | Page Load | Blocked Time3 | ≤,≥ | ms |
| Web | Page Load | DNS Time3 | ≤,≥ | ms |
| Web | Page Load | Connect Time3 | ≤,≥ | ms |
| Web | Page Load | Send Time3 | ≤,≥ | ms |
| Web | Page Load | Wait Time3 | ≤,≥ | ms |
| Web | Page Load | Receive Time3 | ≤,≥ | ms |
| Web | Page Load | SSL Negotiation Time3 | ≤,≥ | ms |
| Web | Page Load | Component Load3 | is incomplete | n/a |
| Web | Transaction \(Classic\) | Error | is present | n/a |
| Web | Transaction \(Classic\) | Transaction Time | ≤,≥ | ms |
| Web | Transaction \(Classic\) | Completion | ≤,≥ | % |
| Web | Transaction \(Classic\) | Steps Completed | ≤, ≥, is | \# |
| Web | Transaction \(Classic\) | Any Steps meets | any, all | of the following conditions: Step Duration |
| Web | Transaction \(Classic\) | Step \# meets | any, all | of the following conditions: Step Duration |
| Web | Transaction \(Classic\) | Any Page meets | any, all | of the following conditions: Page Duration |
| Web | Transaction \(Classic\) | Page \# meets | any, all | of the following conditions: Step Duration |
| Web | Transaction | Marker | is/is not present, duration ≤, ≥ | ms |
| Web | Transaction | Assert Error | does not match, is present, matches | value |
| Routing | BGP | Reachability | &lt;,&gt; | % |
| Routing | BGP | Path Changes | &lt;,&gt; | n/a |
| Routing | BGP | Origin ASN | is in, is not in | comma-separated list of ASNs. |
| Routing | BGP | Next Hop ASN | is in, is not in | comma-separated list of ASNs. |
| Routing | BGP | Prefix | is in, is not in | comma-separated list of covered prefixes |
| Routing | BGP | Covered Prefix4 | exists, is in, is not in | comma-separated list of sub-prefixes |
| Voice | RTP Stream | Error | is present, matches, does not match | n/a |
| Voice | RTP Stream | MOS | ≤,≥ | \# |
| Voice | RTP Stream | Packet loss | ≤,≥ | % |
| Voice | RTP Stream | Discards | ≤,≥ | % |
| Voice | RTP Stream | DSCP | is, is not | DSCP Values.   eg Best Effort \(0\), Expedited Forwarding \(46\) |
| Voice | RTP Stream | Latency | ≤,≥ | ms |
| Voice | RTP Stream | Packet Delay Variation | ≤,≥ | ms |

1. For some metrics, dynamic baselines can be configured. See [Dynamic Baselines]() for more information.
2. These metrics are configurable under the "Any Hop", "Last Hop", or "Hop \#" entries in Path Trace alert rules.  Select "Any or "All" for multiple sub-conditions.
3. These metrics are accessed under the "Any Component" alert condition in Page Load Tests. Select "Any or "All" for multiple sub-conditions.
4. Only BGP Routing tests provide Covered Prefix data.  Do not assign a BGP Alert Rule with a Covered Prefix metric to a non-BGP test type that has BGP Path Visualization measurements enabled.  For non-BGP test types, use an Alert Rule that does not include the Covered Prefix metric, and if needed create a separate BGP test and an a separate Alert Rule with the Covered Prefix metric.

Each metric from the table above is defined in the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmzKAC)

## Default alerting rules

Default Alert Rules are defined according to the following list.  Within the Account Group, Default Alert Rules can be changed by any user having a role with the _View alert rules_ and _Edit alert rules_ permissions, such as the built-in Account Admin or Organization Admin roles.  Default rules can be configured with zero or more alert rules representing the default alert rule for each type.

| Name | Criteria | Minimum Locations |
| :--- | :--- | :--- |
| Default Network Alert Rule | Packet loss ≥ 20% | 2 locations |
| Default DNS Trace Alert Rule | Error is present | 2 locations |
| Default DNS Server Alert Rule | Error is present | 2 locations |
| Default DNSSEC Alert Rule | Error is present | 2 locations |
| Default DNS+ Domain Alert Rule | Availability ≤ 90% and Reference Availability ≥ 90% | 2 countries |
| Default DNS+ Server Alert Rule | Resolution time ≥ 100ms | 1 country |
| Default HTTP Alert Rule | Error type is any | 2 locations |
| Default Page Load Alert Rule | Page load is incomplete | 2 locations |
| Default Transaction Alert Rule | Error is present | 2 locations |
| Default BGP Alert Rule | Reachability &lt; 100% | 2 locations |
| Default Voice Alert Rule | Error is present | 1 location    |

## Dynamic Baselines

 Dynamic baselines allow users to create alerts that more accurately reflect the natural variance in test data. Using standard deviation, percentage change, or absolute values, users can configure alerts that dynamically determine whether to fire or not, based on historical data within a sliding time window.

**Note:** Dynamic baselines are currently only available for Cloud and Enterprise Agent alerts.

Let's imagine a scenario where a HTTP server test runs every fifteen minutes. Over the course of the first hour, four tests are run by an agent in New York. It gathers response times of 510ms, 490ms, 550ms, and 450ms, for an average of 500ms, and so far, the alert has not fired.

The alert uses a dynamic baseline, and has a two-hour window. Based on the four results so far, whether it will fire or not for the next test depends on whether it was configured using standard deviation, percentage change, or an absolute value:

* The standard deviation \(STDEV\) for these results is 36. Using the default multiplier, the alert would fire if the next test returned a response time greater than 500+\(36x2\) = 572ms.
* The percentage change would need to be at least 10% to have avoided firing until now. With an average of 500ms, the alert would now fire if the next test returned a response time greater than 500+10% = 550ms.
* The absolute value needs to be at least 50ms for the alert to have not fired \(the third value, 550, is 50 more than the average of the first two test results\). The alert would therefore only fire if the next test returned a response time of 500+50 = 550ms.

 In this example, alert rules using both the percentage change and absolute values would fire at the same point \(551ms or longer\), while alert rules using standard deviation would not fire until 573ms.

Now let’s add two more results - 482ms and 464ms. All six results are within the two hour window, which changes the average or baseline to 491ms, as well as changing when the alert fires:

* The STDEV for the six results is 32.5, meaning that the alert would fire if the next test response time was greater than 491+\(32.5\*2\) = 556ms.
* The percentage change remains 10%, meaning that the alert would fire if the next test response time was greater than 491+10% = 540ms.
* The absolute value remains 50ms, meaning that the alert would fire if the next test response time was greater than 491+50 = 541ms.

 The different options allow users to adapt their alerting framework to better reflect the fluctuation in test results, and ensure that their system isn’t overwhelmed with alerts because of static metric baselines.

The following metrics currently support dynamic baselines:

* Web / HTTP server / Response Time
* Web / Page Load / Page Load Time
* Network / End to End \(Server\) / Latency

 The image below shows an example alert configuration using a dynamic baseline. The alert condition states that if the response time exceeds two standard deviations above the average value over the last four hours, the alert will fire.

IMAGE MISSING

**Important Note:**

 The time window for the alert must be at least three times the length of the interval of any tests it is attached to, in order to fire. For example, if a test runs every five minutes, the time window for the alert must be at least fifteen minutes in order to gather the three data points required.

## Additional Information

Cloud Agents displaying a _Local Problems_ message on a test results page are excluded from alert calculations:

IMAGE MISSING

This is equivalent of having the Alert Rule's Agents field set to "All agents except" the Cloud Agent with the _Local Problems_ message.

