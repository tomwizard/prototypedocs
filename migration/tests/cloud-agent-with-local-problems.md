# Cloud Agent with Local Problems

When a Cloud Agent experiences full or partial loss of network connectivity or other problems affecting the Agent's ability to perform tests, the Agent is marked with a "Local Problems" error message on the test results page. Typically, such problems occur due to provider issues, such as server or network hardware failures, or network errors such as routing or other configuration errors.

On the Timeline, a grey bar indicates the rounds when the test used one or more Cloud Agents with a local problem \(see the red box in the screenshot below\). Hovering over the bar will display a tooltip, indicating which Agent\(s\) are affected. Additionally, the "Local Problems" error message appears in tooltips when hovering over the Agent name in the Tables tab or hovering over the Agent icon in the Path Visualization.

IMAGE MISSING

The ThousandEyes Operations team runs Agent to Agent tests to all Cloud Agent sites to determine Agent reachability. The "Local Problems" error indicates that at least 80% of the testing Agents received unsatisfactory results from the Agent to Agent tests for at least two consecutive rounds of testing.

Agents marked with the "Local Problems" error message may continue to provide data. Any data will be shown in the test results and will contribute to metrics which are averages across all Agents. Similarly, the data will be used in Alerts and Reports.

However, an Agent displaying the "Local Problems" error will not be counted in the Alert Conditions calculations of an Alert Rule. For example, consider an HTTP Server test run by two Agents, with an Alert Rule having the Alert Condition of "All conditions are met by at least 2 Agents" for Response Time:

IMAGE MISSING

If one or both Agents are marked with the "Local Problems" error then this condition will never be met because the total number of Agents used in the calculation will be fewer than two, even if the Agent\(s\) marked with local problems can provide Response Time data and the Response Time from both Agents is greater than 100 ms.

Generally, tests with fewer Agents will be more likely to miss an Alert Rule condition when an Agent has local problems. Consider using multiple Alert Rules that are met by different Agent values in the conditions \(perhaps with different Notifications characteristics\) for tests run by small numbers of Cloud Agents.

