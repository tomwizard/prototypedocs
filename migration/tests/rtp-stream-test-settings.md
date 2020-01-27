# RTP Stream test settings

An RTP Stream test creates a simulated voice data stream between two ThousandEyes Agents acting as the VoIP user agents. RTP packets are sent between one or more Agents and a target Agent, using UDP as the transport protocol, to obtain Mean Opinion Score \(MOS\), packet loss, discards, latency and Packet Delay Variation \(PDV\) metrics. Metrics produced are one-way metrics \(source to target\). The RTP Stream test provides server port, call duration, de-jitter buffer size and codec configuration options.

Additionally, the Path Visualization and BGP Route Visualization Views can be configured.

## Basic Configuration

 When creating a new test, the RTP Stream test configuration is available under the Voice Layer of the Test Settings page.

IMAGE MISSING

* **Test Layer:** Voice
* **Test Type:** RTP Stream
* **Test Name:** __The test's name.  When no name is configured, the name in the **Target Agent** field is used.
* **Target:** An Enterprise Agent or Cloud Agent which will be the sole user agent \(endpoint\) on one side of the RTP stream.
* **Interval:** How frequently the test will be run.
* **Agents:** ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account.  Select one or more Agents to assign them to this test. These Agents initiate the RTP stream to the **Target Agent**.
* **Alerts:** When the **Enable** box is checked, the Alert Rules selected in drop-down list will be active for the test. You can select Alert Rules with the drop-down list, and create, modify and delete Alert Rules with the **Edit Alert Rules** link.  Additionally, Alert Suppression windows can be selected through the second drop-down list.

Advanced Settings

IMAGE MISSING

### Voice

* **Server Port:** The port number that the server uses for incoming RTP sessions.
* **Codec:** The codec name and associated bit rate used for the RTP session.
* **Duration:** The length of time the test will run, in seconds.
* **De-jitter Buffer Size:** The size of the de-jitter buffer, in milliseconds. A de-jitter buffer stores voice data packets in order to eliminate the effects of delay variations. Having too small or too large a buffer size relative to network conditions can result in poor call quality \(reduced MOS score\).

### Network

* **Data Collection:** Checking this box performs the network measurements that produce the BGP Route Visualization View.
* **BGP Monitors:** Select the BGP monitors used to produce the BGP Route Visualization View.
* **DSCP:** The Differentiated Services Code Point \(DSCP\) value for the IP packet headers of the RTP session.  DSCP allows for prioritization of voice traffic in a network. Depending on the goal of the test, customers may need to match this setting to the DSCP value used on their network.

