# Replacing an Enterprise Agent using the agent clustering method

For a variety of reasons, customers may need to replace an Enterprise Agent which is currently operational.  When replacement is required, customers may want to preserve the Agent's configuration \(such as the Agent's name, or settings from the Advanced Settings tab of the Agent's entry on the [Enterprise Agent page](https://app.thousandeyes.com/settings/agents/enterprise/)\) and the tests and Account Groups to which the Enterprise Agent has been assigned. The information below provides a process to quickly substitute the new Enterprise Agent for the old, using the ThousandEyes Enterprise Agent cluster feature.

Replacement using the process below not only makes replacement faster and simpler than manual reconfiguration of an Agent, but ensures that organizations which have limits or which are billed for overages to their contracted number of concurrently active Enterprise Agents do not encounter problems due to those limits.

**NOTICE:** Customers with accounts using metered billing model are advised against using this method.

For more information and alternative upgrading methods, head over to the [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades) article.

## Overview

The replacement process consists principally of the following steps:

1. Create a new cluster using the Agent requiring replacement
2. Disable the new cluster
3. Create the new Agent
4. Add the new Agent to the cluster
5. Delete the old Agent
6. Enable the new cluster or remove the cluster and enable the Agent

For more detailed instructions, refer to the section below.

## Detailed Instructions

1. Create a new cluster using the Agent requiring replacement

   Navigate to the [Enterprise Agents page](https://app.thousandeyes.com/settings/agents/enterprise/?), expand the row of the Agent requiring replacement, and click the Add agent to cluster button.  
    More info about clusters can be found in the Knowledge Base article [Working with Enterprise Agent Clusters](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmngKAC).  
   IMAGE MISSING

2. Name the new cluster IMAGE MISSING
3. Disable the new cluster

   Disabling the cluster will prevent overages for additional Agents or errors for exceeding your contracted number of concurrent Agents.  
   IMAGE MISSING

4. Create the new Agent

   Links to our most common deployment options are below.

   * [Re-initializing an Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmniKAC) \(This will wipe an existing Agents settings and cause it to appear as a new Agent\)
   * [How to set up the Virtual Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC)
   * [Enterprise Agent deployment using Linux Package method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS)
   * [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS)

5. Add the new Agent to the cluster

   Expand the row belonging to the new Agent and click the **Add agent to cluster** link.  
   IMAGE MISSING

6. When the **Add Agent to Cluster** window appears, click the **Add to existing cluster** radio button, then select the name of the cluster in the drop-down box IMAGE MISSING
7. Delete the old Agent IMAGE MISSING
8. Confirm deletion  IMAGE MISSING
9. Enable the new cluster \(1\) or convert the Cluster back into an Agent \(2\) IMAGE MISSING

## Related information

Consult the [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades) article for more information regarding Enterprise Agent upgrades and available upgrading options.

If you have any questions, [reach out to ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

