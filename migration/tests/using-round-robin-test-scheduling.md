# Using Round-robin test scheduling

When configuring a ThousandEyes test, the Interval setting controls the time between each test execution. Round-Robin execution is available but limited to certain test types:

* Page Load
* Transactions

With Round-Robin an additional two settings, the **Schedule** mode and the **Subinterval** are available to control the distribution of test execution, typically used when the test is assigned to multiple Cloud or Enterprise Agents.  
  
When the Schedule mode is available, users may select either "Default" or "Round-robin" as the setting. In round-robin scheduling, each Agent will be assigned a subinterval during which it must execute the test. Agents will be assigned to subintervals in a round-robin fashion.

This article explains the two scheduling modes, and provides a guide to using round-robin scheduling.

## Default mode

All ThousandEyes tests can be run in Default mode. The images below show the Basic Settings tabs of a test with the Schedule mode, when set to "Default", and a test without the Schedule mode \(can only be run in Default scheduling mode\).

IMAGE MISSING

IMAGE MISSING

In Default mode, a test can be executed by an Agent at any time within the test's Interval setting. An Agent will sequentially execute tests in a test queue. A given test will run whenever previous tests in the queue have completed. The start time for a given test within the test interval depends on the amount of other tests ahead in the queue, and the time taken by those tests to complete.

## Round-robin mode

Currently, Browser-based tests \(Page Load and Transaction test types\) have a **Schedule** mode setting, and a **Subinterval** setting as shown below.

IMAGE MISSING

In Round-robin mode, a test is executed by an Agent based on the Subinterval setting. The test is assigned to Agents' queues with a time-based offset from the beginning of the test round, to create subintervals. The offset varies by Agent in order to evenly distribute all Agents' test executions into subintervals over the time specified by the Interval setting.

Notes:

* An Agent may execute a test at any time within a subinterval
* The subinterval in which a particular Agent executes a test cannot be configured
* For Page Load tests, the included HTTP Server test will be executed in the same subinterval as the Page Load test

The formulas below determine the number of subintervals and the number of Agents in each subinterval. For the following settings

**I** = test **Interval** setting, in minutes  
**S** = test **Subinterval** setting, in minutes  
**A** = number of **Agents** assigned to the test

then

**N** = I ÷ S the number of subintervals in a test round

and

**X** = ⌈A ÷ N⌉ the maximum number of Agents that will execute the test in a subinterval \(the ⌈ ⌉ symbol indicates rounding up to the next integer\)

If A ÷ N is not an integer, the remainder will be scheduled in a round-robin manner, i.e. one to the first subinterval, then one to the second, and so on, until all remaining Agents are scheduled.

### Round-robin example

 For the following settings:

IMAGE MISSING

| Interval \(I\) | 10 minutes |
| :--- | :--- |
| Subinterval \(S\) | 2 minutes |
| Agents \(A\) | 12 |
| Number of subintervals \(N\) | 5 |
| Maximum number of Agents executing per subinterval \(X\) | 3 |

The execution of the test will be distributed as follows:

IMAGE MISSING

### Round-robin use cases

Round-robin scheduling can be useful when performing the same actions at the same time from multiple Agents is not permitted. For example:

1. Steps in a Transaction test would produce conflicting results
2. Rate limits by a security device or security feature require even spacing of requests
3. Concurrent logins to a web application or proxy are not permitted

 To have exactly one Agent per subinterval execute a test \(**X** =  1\) we can express the above equations as:

IMAGE MISSING

For example, with an interval time \(**I**\) of 15 minutes and a subinterval time \(**S**\) of 5 minutes, the test should have 3 Agents assigned.

If fewer Agents are assigned to the test than the number of subintervals, then for **A** Agents, the test will be assigned to the first **A** subintervals.

