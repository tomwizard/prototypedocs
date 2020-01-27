# Voice Call test settings

A Voice Call test simulates a full Voice over IP \(VoIP\) call sequence: first the session initiation using the Session Initiation Protocol \(SIP\) and then voice data transmission using the Real-time Transport Protocol \(RTP\) between one or more ThousandEyes Agents and a target Agent, acting as the VoIP user agents \(call endpoints\). Call registration with SIP servers is performed for both user agents using credentials specific to each user agent. Separate SIP proxies can be configured for one or both user agents.  Simulated voice data is then sent via RTP between one or more Agents and a target Agent, using UDP or TCP as the transport protocol.  Metrics produced are one-way metrics \(source to target\).

Additionally, the Path Visualization and BGP Route Visualization Views can be configured.

## Basic Configuration

When creating a new test, the Voice Call test configuration is available under the Voice Layer of the Test Settings page.

IMAGE MISSING

* **Test Layer:** Voice
* **Test Type:** Voice Call
* **Test Name:** __The test's name. When no name is configured, the name in the **Target Agent** field is used.
* **Target:** An Enterprise Agent or Cloud Agent which will be the sole user agent \(endpoint\) on one side of the call.
* **Interval:** How frequently the test will be run.
* **Agents:** ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account. Select one or more Agents to assign them to this test. These Agents are the source Agents which initiate the call to the **Target Agent**.

**IMPORTANT:** In order to simulate a call between unique user agents, each ThousandEyes Cloud and/or Enterprise Agent must perform the test on its own. Therefore, the number of Cloud and Enterprise Agents that can be assigned to the test is limited by the **Interval** setting in the Basic Configuration tab and by the **SIP Server Timeout** and **RTP Duration** settings in the Advanced Settings tab, in order to ensure enough time in each round for each agent to complete the test. To assign more agents to a test, either increase the test **Interval** or reduce the **SIP Server Timeout** and/or **RTP Duration** values.

The actual formula used to calculate the maximum number of agents for a Voice Call test:

```text
maxAgents = floor[ test-interval-in-seconds / (sip-timeout-in-seconds + rtp-duration-in-seconds + 1) ]
```

* **Alerts:** When the **Enable** box is checked, the Alert Rules selected in drop-down list will be active for the test. You can select Alert Rules with the drop-down list, and create, modify and delete Alert Rules with the **Edit Alert Rules** link.  Additionally, Alert Suppression windows can be selected through the second drop-down list.

### SIP Credentials for Target and Source Agent

Settings for the Target Agent and the Source Agent or Agents are configured in separate sections, but contain the same configuration parameters.  Below is the **SIP credentials for Target Agent**.  These sections contain the configuration for each Agent to perform registration with a SIP server, and optionally to use a SIP proxy to route the SIP communication to the other Agent or to that Agent's proxy.

Note that the SIP credentials \(username and password\) for both target and source of the call should be unique within a ThousandEyes Account Group.

IMAGE MISSING

* **SIP User:** Name used to register with the SIP server. The username should be unique within a ThousandEyes Account Group.
* **SIP Server:** SIP server used by the agent for registration, specified as a domain name or IP address.
* **SIP Proxy:** \(Optional\) A SIP proxy that is distinct from the SIP server, specified as a domain name or IP address. Check the **Enable** box if a SIP proxy will be used to send SIP communication to the target, and configure the SIP proxy's domain name or IP address in the field below.  The proxy port will be the same as the value in the **Port** field.  Loose routing is used in the SIP messages.
* **Protocol:** Either the TCP or UDP protocol may be used as the transport layer for the SIP communication. Choosing TCP will result in the Path Visualization using TCP. Choosing UDP will result in the Path Visualization using ICMP.
* **Port:** The TCP or UDP port number for the protocol chosen in the **Protocol** field.
* **Auth User:** \(Optional\) If the SIP User field is not identical to the authentication username, check the **Custom Auth User** box and specify a custom authentication username in the field below.
* **Password:** Password to be used when authenticating with the SIP server.

 Once the target Agent's SIP settings have been configured, configure the **SIP Credentials for Target and Source Agent** section. All source Agents will use these settings.

### Advanced Settings

IMAGE MISSING

### SIP Timing

* **SIP Server Timeout:** Timeout for SIP INVITE command to establish communication between source Agents and target Agent.
* **Target Time for View:**  Sets the scale of the color legend \(green to yellow to red\) for metrics on the world map.

### SIP

* **Desired Status Code:** For the SIP Server View, the SIP status code returned by the target for which the test is considered successful. By default, 200- and 300-level status codes are considered success. Uncheck the box and enter a status code in the field below to set a different status code.

**RTP**

* **Server Port:** The port number that the server uses for incoming RTP sessions.
* **Codec:** The codec name and associated bit rate used for the RTP session.
* **Duration:** The length of time the RTP stream will run, in seconds.
* **De-jitter Buffer Size:** The size of the de-jitter buffer, in milliseconds. A de-jitter buffer stores voice data packets in order to eliminate the effects of delay variations. Having too small or too large a buffer size relative to network conditions can result in poor call quality \(reduced MOS score\).

### Network

* **Data Collection:** Check the **Collect BGP data** box to produce the BGP Route Visualization View.
* **BGP Monitors:** Select the BGP monitors used to produce the BGP Route Visualization View.
* **DSCP:** The Differentiated Services Code Point \(DSCP\) value for the IP packet headers of the RTP session.  DSCP allows for prioritization of voice traffic in a network. Depending on the goal of the test, customers may need to match this setting to the DSCP value used on their network.

