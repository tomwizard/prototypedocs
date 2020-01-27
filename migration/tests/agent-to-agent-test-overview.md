# Agent to Agent Test overview

The Agent to Agent Network test allows users of ThousandEyes to have ThousandEyes Agents at both ends of a monitored path, enabling testing of the path in either or both of two directions: Source to Target or Target to Source.  The Agent to Agent test can have multiple source Agents monitoring the target Agent. Similarly, the target Agent monitors each of the source Agents.  By monitoring in both directions, asymmetrical paths between source and target Agents can be visualized, and data for both paths is available.

The Agent to Agent test produces standard Network metrics: packet loss, latency, jitter, and optionally throughput--an improved form of the bandwidth metric--along with Path Visualization and path MTU. Metrics are produced for either or both directions, depending on test configuration. The Agent to Agent test can be configured to use either TCP or UDP.  Payload size can be specified in bytes, or can be determined automatically, based on path MTU discovery.  
 

## How ThousandEyes Agent to Agent Tests work

Agent to Agent tests improve upon Agent to Server tests by basing metrics on packets traveling in only one direction, rather than needing to send probe packets and obtain responses.  Rather than sending response packets, the receiving ThousandEyes Agent provides the results metrics directly to the ThousandEyes collector, which a non-ThousandEyes receiver cannot do.  One-way metrics that require timing are made possible in part by performing an exchange to determine clock offset between the sending and receiving Agents, prior to sending the actual test packets.  With the clock offset, packets can be timed in one direction.

When calculating End-to-End packet losses, this model results in a true one-way loss, rather than loss being possible in either direction. Metrics for trip time in an Agent to Agent test are one-way timings, rather than round-trip timings.  Time synchronization between sending and receiving Agents is accomplished by sending clock synchronization packets at the beginning of each test round, prior to the actual probe packets.

Similarly, the new throughput metric in Agent to Agent tests measures the one-way data transfer rate between the endpoints. Having ThousandEyes Agents at both ends allows a more accurate measurement compared to the Bandwidth metric of an Agent to Server test, since the Target Agent is measuring incoming byte rate directly, rather than the sending Agent inferring data rate from the target's responses to the incoming bytes.

Throughput test duration can be configured for between 5 seconds \(default is 10 seconds\) up to 30 seconds.  Greater accuracy can be achieved with longer test duration.  TCP-based throughput testing uses payloads sent at the fastest possible rate.  UDP-based throughput testing allows a rate setting, which can simulate Quality of Service \(QoS\) bandwidth shaping policies, for example.

For performing Path Visualization and measuring Forwarding loss, the mechanism is not changed from the Agent-to-Server test.

IMAGE MISSING

In the above picture the upper paths travel from the Agent on the left to the Agent on the right, while the lower paths travel in the opposite direction. The direction is indicated by the arrows connecting the nodes on the paths. Using the Direction selector, you can display only the Source to Target, Target to Source, or both directions.  
 

## Agent to Agent test Targets

When selecting a target Agent and one or more source Agents, there are three possible configurations of the Agent to Agent test:

1. **Enterprise → Cloud:** The source is an Enterprise Agent and the target is a Cloud Agent. The IP address used for the target is the public IP address of the Cloud Agent \(all Cloud Agents have publicly routable IP addresses\).  The Cloud Agent's IP address will be available in the **Target IP** column on the Table tab of the Overview view, and displayed in a tooltip when hovering over the Cloud Agent, in the Path Visualization view.
2. **Enterprise → Enterprise:** The source is an Enterprise Agent and the target is an Enterprise Agent. The IP address used for the target is the value of the Target for Tests **IP Address** setting, under on the Advanced Settings tab of the Agent Settings. The target Enterprise Agent's IP address will be available in the **Target IP** column on the Table tab of the Overview view, and displayed in a tooltip when hovering over the Enterprise Agent, in the Path Visualization view. If the target Agent will be accessed through a NAT IP address that is automatically discovered by checking the **Behind a NAT** box in the Agent Settings, then the NAT IP address will be displayed in the tooltip with the target Agent's IP address.
3. **Cloud → Enterprise:** The source is a Cloud Agent and the target is an Enterprise Agent. The IP address used for the target is the value of the Target for Tests **IP Address** setting, under on the Advanced Settings tab of the Agent Settings. The target Enterprise Agent's IP address will be available in the **Target IP** column on the Table tab of the Overview view, and displayed in a tooltip when hovering over the Enterprise Agent, in the Path Visualization view. If the target Agent will be accessed through a NAT IP address that is automatically discovered by checking the **Behind a NAT** box in the Agent Settings, then the NAT IP address will be displayed in the tooltip with the target Agent's IP address.

A test can have both Cloud and Enterprise Agents as source Agents.

For targeted Agents behind a NAT, consult the ThousandEyes Knowledge Base article [NAT Traversal for Agent to Agent tests](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnWKAS).  In general, for Enterprise Agents in the Agent to Agent test, check your [firewall rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK), NAT and/or port forwarding configuration to ensure that test packets are permitted and that any needed IP address and port translations are performed.

### Agent to Agent test costs

In Agent to Agent tests, the cost of a test round in Cloud Units depends on whether the Cloud Agent is used as as target \(\#1 in the above list\) or used as source \(\#3 in the above list\). Please refer to the ThousandEyes Knowledge Base article [How Cloud Unit consumption works](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmoKAC) for details on the billing of Agent to Agent tests. Enterprise Agents are billed with a flat monthly rate so using them as source and target \(scenario \#2\) does not incur additional cost.

## Agent to Agent test Settings

The Basic Configuration tab for an Agent to Agent test is shown below.

IMAGE MISSING

* **Test Name:** Name of the test
* **Target Agent**: Select the target agent for the test
* **Interval**: Configure the test interval expressed in minutes
* **Agents**: Select the source agents to monitor the target agent
* **Direction**: Select the direction of the monitoring as _Source to Target_, _Target to Source_ or _Both Directions_
* **Protocol**: Select either the TCP or UDP protocol
* **Enable Throughput**: Check this box to perform throughput measurements in the selected direction\(s\)
  * with **TCP**: configure the duration of the throughput measurement
  * with **UDP**: configure the duration of the throughput measurement, along with Maximum Rate or Specified Rate that the Agent will send packets at
    * **WARNING: Enable Throughput with UDP and Maximum Rate settings can be disruptive.** UDP protocol has no congestion control, therefore a UDP agent to agent test performed at Maximum Rate may saturate your Agent's local connection for a set Duration. **If unsure, use TCP.**
* **Alerts**: Check the Enable box to assign Alert Rules and create suppression windows

  
The Advanced Configuration tab for an Agent to Agent test is shown below.

IMAGE MISSING

* **Server Port**: Port number on the target Agent to which a source Agent sends packets.
* **Payload Size**: Size of the payload in the packets sent for measurements.
* **Collect BGP Data**: Check this box to enable the BGP Route Visualization View, and select which BGP monitors to use.
* **DSCP**: Configure the DSCP value for the packets.

## Additional notes

* **Server port:** Setting the **Server Port** only specifies the **target** TCP or UDP port to be used for incoming packets to the target. Value `22` is not allowed. Source ports are numbers above 1024 chosen by the operating system's networking stack.

