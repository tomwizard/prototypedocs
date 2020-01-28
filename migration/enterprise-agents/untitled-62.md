# Working with Enterprise Agent Clusters

In environments where there are more than one enterprise agent running in a single location, administrators may want to simplify the Agent selection process for their end users, by abstracting the number of Enterprise Agents running from a single location into an Agent cluster.  Additionally, clustering provides the benefit of assigning new tests to the least utilized member of a cluster, for the given test type.

ThousandEyes Cloud Agents operate using the same concept as Enterprise Agent clusters: there are multiple independent servers operating together to run tests from a single location.

## Creating a cluster

To create a cluster, click the **Add to Cluster** link shown at the bottom of an Enterprise Agent's Settings.  A dialog will open; choose to either add to a new cluster, or add to an existing cluster, and give the cluster a name.  By default, the cluster will inherit the name of the first cluster member.

IMAGE MISSING

When the new cluster is created, all Agent settings will be automatically mapped to the new cluster. This includes:

* Inherit all tests assigned to the standalone Agent
* All accounts which had access to the standalone Agent
* Agent groups where the standalone Agent was a member
* Agent settings:
  * Verify SSL certificates setting
  * Keep browser cache between tests setting
  * Agent notification rules selections
* For customers using the API, the cluster retains the agentId of the first agent added to the cluster

## Adding capacity to a cluster

Once a cluster is created, more agents can be added to the cluster, by running through the same process and clicking the add to existing cluster, then selecting the cluster.

When adding a new agent to an existing cluster, the cluster will:

* Inherit all tests assigned to the agent
* Ignore all groups assigned to the newly assigned agent
* Enforce the cluster settings for:
  * Verify SSL certificates setting
  * Keep browser cache between tests setting
* For customers using the API, the newly assigned agent's agentID will no longer exist

If a test on an inbound Agent is already assigned to the cluster, then one Agent will appear as removed from the test.

## Deleting a cluster

To delete an Enterprise Agent cluster, under the Settings menu select Enterprise Agents, and choose the Cluster tab.  Expand the Enterprise Agent cluster's row, then click the trash icon in the lower left corner.  Note that deleting a cluster with existing Enterprise Agent cluster members will also delete the Enterprise Agents.  To preserve the Enterprise Agents, remove them from the cluster before deleting the cluster.  See the section below for instructions on removing an Agent from a cluster.

## Removing an Agent from a cluster

In certain cases, an Administrator may want to remove an Agent from a cluster.  To accomplish this, under the Settings menu, select Enterprise Agents, and choose the Cluster tab.  Expand the Enterprise Agent cluster's row, then click the **x** icon next to the cluster member.  You'll be shown a confirmation dialog:

IMAGE MISSING

Click the **Remove** button to remove the Agent from the cluster and return the Agent to a standalone status.  This operation removes the Agent, and recreates it in the context of the user's current Account Group, so be aware of your current Account Group, in the event that your user has management permissions across multiple Account Groups.  The Agent is created fresh, inheriting default Agent Notification rules, and without any tests assigned.

## Agent management

In the Enterprise agents page, you'll be able to tell which agent is a cluster member by looking at the expanded agent details of an agent, or the cluster icon.  Click the cluster hyperlink to open the cluster settings, and view other cluster members.

IMAGE MISSING

Utilization details for the Agent are shown at the cluster member level, as well as on an overall basis at the cluster level.

It's important to note that Enterprise Agent clusters are not meant for high availability of agents. If a cluster member is shut down or becomes unreachable via the network while tests are assigned to it, those tests will remain assigned to that same agent \(cluster member\).  Removing the agent from a cluster will force redistribution of those tests to other cluster members.

## Test management and utilization

New tests assigned to the cluster are distributed to each cluster member, based on each agent's utilization. As a new agent is assigned, the tests assigned to that agent are distributed amongst the cluster members.

If a cluster member agent is deleted, the tests assigned to the agent are redistributed amongst the remaining cluster members.

Utilization is shown for each agent in the agent settings page, and the overall cluster utilization shows the average value across all cluster members.

## Views and results

Views will show the name of the agent as the cluster name, but show the individual IP address of the cluster member. This may include private and/or public IP information, so to troubleshoot individual cluster members having problems resolving data on a test, you'll have to identify the cluster member assigned to the test, and diagnose from that specific agent.  To view the information for a specific test, hover over the agent icon.

IMAGE MISSING

## Agent to agent tests

Using a cluster as a target for Agent to Agent tests \(such as Voice\) will work fine, unless all agents are behind the same NAT. In this scenario, you'll need to create a firewall rule for the target, which would point to a specific agent in the cluster. While all results will behave as planned, the agent targeted will absorb all Agent to Agent tests targeted at that specific port on the cluster. To target different agents, change the port of the target, which is set under the Advanced Settings tab of the test's configuration.

## API support

Versions 5 and later of the ThousandEyes API have support for Enterprise Agent clusters.  See http://developer.thousandeyes.com for information on Enterprise Agent clusters in the context of our API.

## Restrictions

* All Agents must be owned by the same Account Group \(i.e. use the same account token\)
* All Agents must be using the same address family \(no mixing of IPv4 Agents with IPv6 Agents\)

## Recommendations

* Agents should be running the same version of both operating system and agent software
* Agents should have similar hardware configuration
* Agents should be in the same physical location
* Agents should be running the same components \(ie, all agents run both agent and BrowserBot, or just agent\)

