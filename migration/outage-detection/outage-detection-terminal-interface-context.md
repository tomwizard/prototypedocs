# Outage Detection - Terminal Interface Context

## Terminal Interface Context

ThousandEyes aggregates data from all users to provide additional information on terminal interfaces that appear in the Path Visualization view. This can be useful in understanding the impact of a single affected interface - both across your tests and in the aggregate.

### What is a Terminal Interface?

Within the ThousandEyes Path Visualization view, a node circled in red indicates that forwarding loss is occurring at that point in the path, meeting the loss threshold specified by the loss slider found above.

A terminal interface is likely what you’d expect: an interface where at least one path trace has terminated, meaning that for that specific trace it was the last known interface to have replied to our probes. A terminal interface is roughly equivalent to seeing asterisks in the output of a traceroute. Below is a traceroute-style output from the Tokyo Cloud Agent with a terminal interface at hop 16.

IMAGE MISSING

See the older style of mouseover in which we showed information for a terminal interface:

IMAGE MISSING

There are various reasons for the appearance of terminal interfaces, including unexpected issues like routing changes, network congestion, and hardware failures, or for reasons of design due to router or firewall configurations.

When terminal interfaces are observed together with associated application-level issues, causation can typically be inferred at the network level, indicating a serious network-level issue that likely requires immediate attention.

### Using the Terminal Interface Context

To help you evaluate the scope and mitigation plan for such a scenario, we’ve expanded the context to include more information about a given terminal interface.

IMAGE MISSING

The terminal interface context includes the following information:

* Pie chart \(1\):
  * Percentage of tests across all ThousandEyes users that are affected by this terminal interface.
  * Number of affected tests both across all users and in your current account group that observe at least one path trace terminating at this interface during the selected time period. Click the ‘N in this account group’ link to open the list of affected tests and their respective test types and links \(see image below\).
  * Percentage of tests across all ThousandEyes users that are NOT affected at this terminal interface.
* Loss Frequency \(2\) is a low, medium or high value that indicates how “noisy” an interface is in terms of loss. For example, if an interface’s loss frequency is low, that means that the interface is typically very stable and generally doesn’t see much loss. In this case you’ll want to pay close attention when you do see paths terminating at that interface, because it’s an infrequent condition. If an interface has a high loss frequency, any loss you’re seeing may need to be taken with a grain of salt.
* You may also see a ‘Part of Outage’ line item \(3\), which will only be present if the loss you’re observing on that interface has been deemed to be part of a [larger outage in an Internet service provider](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC). In this case, you can look to the top left corner of the Path Visualization window and click the ‘Outage Detected’ dropdown to get more information about the outage.

IMAGE MISSING

There are a couple of key points to consider when looking at the Terminal Interface Context:

* The pie chart indicates two key pieces of information related to the severity and scope of the issue at this interface:
  * Percentage of traffic affected: If some traffic is not affected and still getting through, the outage likely isn’t as severe as if 100% of traffic is terminating at that interface.
  * Number of affected tests in total and in your account group: As the number of total affected tests increases, so does the likelihood that this outage is having a significant global impact. Compare the total number with the number of affected tests in your account group to assess whether the issue is occurring on a more localized or a more global scale.
* If the terminal interface is within your own infrastructure, then the problem is likely to be isolated to your network and not part of a broader outage—you may need to address the problem yourself.
* If the terminal interface is within another Internet service provider, you may be seeing a partial or full outage within that provider. Look for the ‘Part of Outage’ line item to see if it’s an outage that ThousandEyes has detected, and if so, click on the ‘Outage Detected’ dropdown in the top left corner of the Path Visualization window for additional details. For more information, see the related [Knowledge Base article on Outage Detection](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC).

For a summary on interpreting the terminal interface context, see the table below.

|  | Noise Level |  |  |  |
| :--- | :--- | :--- | :--- | :--- |
| Low | Medium | High |  |  |
| % Tests Affected | 0-30% | Of interest | Look for more info | Non-critical |
| 30-60% | Critical | Of interest | Look for more info |  |
| 60-100% | Critical | Critical | Of interest |  |

### How the Terminal Interface Context Works

Any interface at which at least one path trace is terminating will be evaluated as a terminal interface, so that when you mouse over that node, you will be presented with the popover window containing the above-mentioned information.

Loss frequency is calculated based on the amount of loss this interface generally sees on an ongoing basis. ThousandEyes generates a baseline for all interfaces that are regularly used to transit test traffic, and scores loss frequency into “Low,” “Medium,” “High” or “Noisy” depending on how often that interface is seen as terminal. A “Noisy” interface is frequently seen as terminal whereas a “Low” loss interface is rarely seen as terminal.

Any terminal interface that is not “Noisy” will be considered by our algorithms for ThousandEyes [Outage Detection](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC), assuming it satisfies other filtering criteria.

### Outage Association

In cases where a node in your Path Visualization is a transit for more than just your organization’s tests and appears as a terminal interface in at least one of those cases, it might be part of a broader network outage attributed to an Internet service provider.

In those cases, ThousandEyes detects and presents context about such outages with [Outage Detection](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC). When outages are detected, you’ll not only get context about the scope of tests affected at this interface, but you’ll also see information about the specific outage that this terminal interface is associated with:

IMAGE MISSING

If you see the ‘Part of Outage’ line \(1\), it’s very likely that the issue you’re experiencing is having impacts beyond your network. Investigate the breadth of the detected outage by exploring the ‘Outage Detected’ dropdown \(2\) near the top left corner of the Path Visualization.

## More Information

Read our [Knowledge Base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmskKAC) to learn more about using Outage Detection.

