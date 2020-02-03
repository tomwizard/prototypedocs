# Using the DNS Server view



When you create any DNS Server test, you get access to the DNS Server Metrics view.  The DNS Server Metrics view leverages the ThousandEyes [standard layout](https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC). 

This article highlights specifics shown in the DNS Server view.

## Example

The example below shows the result of a globally distributed DNS Server test, requesting the A record for cn.vpn.wework.com from nameservers authoritative for that domain:

![DNS-Server-View](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNWP)

## View Specifics

When you run a DNS Server test, you specify a domain name and record type, and also specify the nameserver\(s\) to which the queries for the target record that will be sent. The DNS Server view provides the following Selectors:

1. **Metric:** For the Server Metrics view, select either Availability or Resolution Time as metrics.  
2. **Server:** Select the DNS server to use for the Timeline as well as the Map, Servers and Agents tabs.
3. **Agent:** Select the Agent to use for the Timeline as well as the Map, Servers and Agents tabs.
4. **Views:** The Views menu provides access to Network and BGP views.

The DNS Server View can be configured in the following ways for any given Metric.  In the example below we use Availability as the Metric.

1. Globally, without either a nameserver or an Agent selected:  ![all-servers-all-agents-overview](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNV7)  
   * **Map**: shows average availability and resolution time from every nameserver and Agent location.  ![map-all](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVC)  
   * **Servers**: Tabulates for each nameserver configured the date, number of errors, and average resolution time for the target domain name.  ![server-all](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVH)  
   * **Agents**: Tabulates for each Agent the Date, minimum resolution time across all servers, availability percentage of all servers and any error details target domain name.  ![Agents-tab-all](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVM)
2. Globally, looking at a specific nameserver:  ![Overview-Server-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVR)  
   * **Map**: shows availability and resolution time against the selected nameserver, calculated by averaging results from all Agents.  ![Map-tab-server-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVW)  
   * **Server**: Tabulates for each server the date, number of errors, and average resolution time for each location, with the selected server's row highlighted.  ![Server-tab-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVb)  
   * **Agents**: Tabulates for each Agent the date, record mapping, any error details and resolution time for each Agent.  ![Agents-tab-server-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVg)   
3. From a specific Agent, looking at all nameservers.  ![overview-agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVl)  
   * **Map**: shows average availability and resolution time across all servers from the selected Agent, calculated by averaging results from all nameservers.   ![Map-tab-agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVq)  
   * **Servers:** Tabulates for each nameserver the date, record mapping, any error details and resolution time for each Agent.  ![Server-tab-agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVw)  
   * **Agents:** Tabulates for each Agent the date, resolution time, availability percentage and any error details and resolution time for each Agent, with the selected Agent's row highlighted.  ![Agents-tab-agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNW0)
4. From a specific Agent, looking at a specific nameserver.  ![Overview-tab-Server&amp;Agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNW5) 
   * **Map**: shows the status \(availability, where the only values for availability are 100% or 0%\) for the selected nameserver, from the selected Agent location, as well as resolution time.  ![Map-tab-Server&amp;Agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNVm)
   * **Servers**: Tabulates for each nameserver the date, record mapping, any error details and resolution time for each server, with the selected Server's row highlighted.  ![Servers-tab-Server&amp;Agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNWA)  
   * **Agents**: Tabulates for each Agent the date, record mapping, any error details and resolution time for each Agent, with the selected Agent's row highlighted.  ![Agents-tab-Server&amp;Agent-selected](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQl4&feoid=00NE0000006OT0r&refid=0EM2R000000CNWF)

