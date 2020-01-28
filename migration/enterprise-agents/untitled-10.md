# Enterprise Agent Utilization - ThousandEyes Customer Success Center

### Enterprise Agent Utilization

For ThousandEyes Enterprise Agents and Agent clusters, the Utilization metric is not a measure related to any system hardware resource, such as random-access memory \(RAM\) use or CPU time consumed.

Enterprise Agent utilization is a measure of time taken to execute tests within a given queue.  Tests in a queue must be completed before the next round of tests must begin. Utilization below 100% represents available time to accommodate more tests or for existing tests to take longer to complete.  Because the majority of time for a test to execute is dependent on network or server response time, adding hardware resources such as RAM, faster or more CPU's or faster I/O hardware to the system running the Enterprise Agent is generally not effective in reducing utilization, assuming the [hardware requirements for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC#Hardware) have been met.

Most queues execute tests with varying degrees of concurrency, but place limits on the number of concurrent tests in order to ensure that customers' networks are not over-utilized and to ensure that tests do not interfere with each other.

## Displaying Agent Utilization

Agent utilization is displayed in both the ThousandEyes application \(web interface\) and is available from the ThousandEyes API. Utilization is calculated at 5-minute intervals.

### Utilization in the ThousandEyes application

The Agents tab of the [Enterprise Agents page](https://app.stg.thousandeyes.com/settings/agents/enterprise/) \(**Settings &gt; Enterprise Agents**\) provides a table with each Enterprise Agent that is visible in the current Account Group context. Each row in the table lists an Enterprise Agent, along with a single percentage in the **Utilization** column. The single percentage displayed is the largest of the percentages from the queues which are used by the Agent.

  
Expanding an Agent row and clicking the Agent Statistics tab will display graphs of all **Agent Utilization** queues used, with data for the past 24 hours.

In the example above, the Enterprise Agent "vm2-xen-stl" has four queues active, of which the **Voice Tests** queue currently has the greatest utilization of 21%, which is shown in the **Utilization** column of the table.

Up to four queues may be displayed:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Queue Name</b>
      </th>
      <th style="text-align:left"><b>Test Types Assigned to Queue</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Browser</td>
      <td style="text-align:left">
        <ul>
          <li>Page Load tests</li>
          <li>Transaction tests</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">General</td>
      <td style="text-align:left">
        <ul>
          <li>All Network Layer tests</li>
          <li>All DNS Layer tests</li>
          <li>HTTP Server tests</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Bandwidth and Throughput</td>
      <td style="text-align:left">
        <ul>
          <li>All tests with Bandwidth metrics</li>
          <li>All tests with Throughput metrics</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Voice</td>
      <td style="text-align:left">
        <ul>
          <li>All Voice Layer tests</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>The **Agent Utilization** section displays only those queues in which the Agent is currently running tests, or has run within the past 24 hours. For example, if the Enterprise Agent is only running Agent to Agent tests with Throughput enabled, then the Bandwidth and Throughput queue is displayed. The other queues are not displayed.

Utilization percentage in a queue is independent of utilization in other queues.  For example, high utilization in the Browser queue will not affect utilization in the other three queues.

### Cluster Utilization

Utilization for an Enterprise Agent cluster is displayed as a percentage on the row of the cluster in the Clusters tab of the Enterprise Agents page.  The utilization of a given queue represents the most heavily used queue of any member in the cluster, for that queue type.

### Utilization in the ThousandEyes API

The ThousandEyes API provides the http://developer.thousandeyes.com/agents endpoint.  When specifying an Agent ID, the output of this endpoint will provide the utilization percentage from the queue with the highest utilization percentage on that Enterprise Agent or cluster.  In the example above, if the Enterprise Agent "vm2-xen-stl" has Agent ID 966, then the following query:

```text
https://api.thousandeyes.com/v6/agents/966.json
```

would produce output that included the "utilization" field and the aforementioned percentage:

`"utilization": 21`

See the ThousandEyes API documentation at [http://developer.thousandeyes.com](http://developer.thousandeyes.com/) for more information on using the API.

Data from polling the API for Enterprise Agent utilization can be used by customers to create alerting mechanisms when Agent utilization reaches a threshold.

## High Utilization

Utilization percentage ranges from 0% \(no tests in a queue\) to 100%.  At 100% utilization, tests may not complete before the next round's tests would normally start.  The typical symptom is missing data in one or more Views within a test, either intermittently or consistently, depending on the severity of the high utilization.  Review the sections below to identify causes of high utilization and the corresponding solutions.

### Identifying the causes

High utilization may be caused by one or a number of long-running tests, or may be due to smaller contributions from a large number of tests, or some combination of the two. Long-running tests are tests which fail to complete before reaching their Timeout value, or tests whose completion time is a significant fraction of the test’s Timeout setting, particularly if the Timeout setting has been increased from the default value. Test targets which fail to respond are a common reason for a test to reach their Timeout time. The larger the amount of time taken by a test, the greater the contribution to the utilization for the test's queue.

Alternatively, high utilization may be caused by large numbers of tests, none of which are long-running. There is no single number of tests in a queue which will cause high utilization - the threshold varies by queue and test characteristics.

To determine the cause\(s\) of high utilization in a queue, perform the steps below:

1. Locate tests belonging to that queue type \(see table above\) which have long run times.  Ways to locate long-running tests include:
   * Check all of the test's Views for missing data, or for long completion times \(metric depends on test type: HTTP Server tests use "Response Time"; Page Load tests use "Page Load time", DNS Server tests use "Resolution Time", etc...\)
   * Determine \(using either the Utilization graph or the API\) the date when utilization increased, then use the Activity Log or a test's **Modified** date to identify tests created or modified around that time.
   * Creating a report under the Reports function to display test completion time, either numerically or graphically.
2. Temporarily disable the test with the longest run time by unchecking the box in the **Enabled** column on the [Test Settings](https://app.thousandeyes.com/settings/tests/) page.
3. Observe the Utilization for the next two rounds of new utilization data.
4. If a test is identified as contributing to high utilization, check for tasks within the test which may be the source of the utilization.
   * If a test includes the **Perform Bandwidth measurements** setting, uncheck this setting and observe two rounds of Utilization data.
   * If a test includes the **Perform Network measurements** setting \(for End to End Metrics and Path Visualization\), uncheck this setting and observe two rounds of Utilization data.
   * If a test includes the **Enable Throughput** setting, uncheck this setting and observe two rounds of Utilization data.
5. If the Utilization does not decrease after completing the previous steps, repeat the steps for another test with a long run time. Do not re-enable any tests that have already been disabled.
6. Continue to disable tests until Utilization drops.
7. If the cause is not identified after these steps, check your organization's tools that may be sending requests to the ThousandEyes API to run Instant Tests, and check your firewall and other logs for api.thousandeyes.com or its IP address.

 Alternatively, the reverse approach can be used: disable a large number of tests and then begin adding tests until you see Utilization increase. This approach may be better if no long-running tests can be identified, per Step 1.

Note that spikes in utilization \(as opposed to prolonged high utilization\) may be caused by Instant Tests which are long running. Instant Tests can be initiated through the web interface or the API.  The [Activity Log](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnNKAS) can be used to check for Instant Test run at the same time as a utilization spike. For the API, check for connections to https://api.thousandeyes.com from your network, or contact the [Customer Success Center](mailto:support@thousandeyes.com) to identify individual users of the API.

### Solutions

 Once a determination has been made as to whether high utilization is caused by a small number of long-running tests or a large number of tests which complete within normal times or a mix of the two conditions, one or more of the following options can be employed:

* Deploy additional Enterprise Agents  If additional Enterprise Agent licenses are available with your ThousandEyes subscription, or your organization has a "pay as you go" subscription, then deploy one or more new Enterprise Agents, preferably in an [Agent cluster](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmngKAC). This is the best solution when a large number of tests are the source of high utilization.
* Reduce the frequency of long-running tests  Changing the test interval from a 2-minute or 5-minute frequency to 10, 15 or 30 minutes can reduce utilization.  Optionally, it may be possible to configure an Alert Rule to notify customers when the root cause is no longer present, and a shorter test interval safe to use.
* Reduce the Timeout setting on tests that often time out, particularly if the test is run at 2- or 5-minute frequency.
* Address the root causes of long-running tests  Using test data and other any other resources available, determine why a test takes significant time to complete. Common root causes include:
  * Targets which are unresponsive
  * Transaction tests which timeout due to missing elements
  * Page Load tests that timeout due to missing objects
  * Excessive Bandwidth testing of the same target or multiple targets
* Disable long-running tests
* Reduce use of Instant Tests via the API
* Remove consistently failing tests, as they constantly take the whole test timeout length to execute.

