# Voice Test overview

VoIP \(Voice over Internet Protocol\) embeds the sound of your voice into data packets, which are sent over the Internet to be converted back into original sound once they reach the destination. Typically, VoIP calls are divided into two phases: Session Connection and Voice Data Transfer. Session Initiation Protocol \(SIP\)  and the Skinny Call Control Protocol \(SCCP, or simply Skinny\) are the widely used VoIP control mechanisms to create, modify, and terminate sessions with the target participant\(s\). SIP signaling messages can be either TCP or UDP based and use Real Time Transport Protocol \(RTP\) for sending voice streams while SCCP uses TCP/IP to connect to the VoIP server and sends traffic as stream of RTP packets using UDP. A Voice test measures network bandwidth, latency, call jitter, packet loss and round trip time.

IMAGE MISSING

## How ThousandEyes Voice tests work

IMAGE MISSING

ThousandEyes has introduced Voice Tests for VoIP network monitoring and optimization capability, analysis of call quality problems, facilitate bandwidth planning and help understand protocol behavior. Running a Voice Test using ThousandEyes is slightly different from placing a VoIP call. Instead of going through the connection phase, ThousandEyes agents establish a direct connection from the source \(VoIP call initiator\) to the target \(VoIP call endpoint\). A stream of UDP encapsulated voice packets are sent between the endpoints  and depending upon the choice of [codec]() and [Differentiated Services Code Point \(DSCP\) values](), the test measures Mean Opinion Score \(MOS\), packet loss, frame discards, latency and Packet Delay Variation \(PDV\). The test also provides a path visualization for the route and can optionally provide routing information showing a map of connections between autonomous systems in the route from each agent to the target.

## Voice Test Target

There are three possible ways to select a Target for a Voice test

1. **Enterprise → Cloud:** A voice test will be sourced from an enterprise agent destined to a cloud agent. Such tests will measure voice call  
     quality sourced from the internal network to the external cloud agent.  
2. **Enterprise → Enterprise:** A voice test will be sourced from an enterprise agent destined to another enterprise agent . Such  
      tests provide an insight view on call quality for the internal network within the same branch offices or between different branch  
      locations.  
3. **Cloud → Enterprise:** A voice test will be sourced from a cloud agent towards an enterprise agent. Such tests will allow you to  
     measure and troubleshoot the quality of voice calls sourced from the Internet to the internal network. Please verify your NAT configuration,  
     [firewall rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) and router port forwarding configuration for a successful run of the test.  
 

**Note: It is not possible to configure a voice test from one cloud agent to another.**

## Advanced Settings fields for a Voice test

Below is a screenshot of the Advanced Settings Tab while adding a Voice test:

IMAGE MISSING

* _**Server Port:**_ The target port to which the client will send the voice packets. Please ensure the target port is configured to accept UDP traffic inbound. Refer to the [firewall requirements article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) for more information.
* _**Codec:**_ Short for “coder-decoder”, codecs convert an analog voice to digitally encoded version for transmission over the network and then back to its original audio form for playback. Selection of a codec is a trade-off between sound quality, bandwidth and computational load. Factors such as compression techniques, sample size used to re-generate the audio signal affect the performance of the codec. Generally, choosing a codec with a higher MOS requires more bandwidth, but also provides better sound quality.Refer the [codec values table]() for more details

   Available codecs while configuring a Voice test

  | Codec and Bit Rate \(Kbps\) | Frame size \(ms\) | Frame length \(bytes\) | Frames per packet | Mean Opinion Score   \(MOS\) | codecId |
  | :--- | :--- | :--- | :--- | :--- | :--- |
  | G.711 \(64Kbps\) | 10 | 80 | 2 | 4.41 | 0 |
  | G.722.1 \(24 Kbps\) | 20 | 60 | 1 | 3.79 | 1 |
  | G.722.1 \(32 Kbps\) | 20 | 80 | 1 | 4.03 | 2 |
  | G.726 \(32 Kbps\) | 5 | 20 | 4 | 4.07 | 3 |
  | G.723 \(6.4 Kbps\) | 30 | 24 | 1 | 3.95 | 4 |
  | G.729a \(8 Kbps\) | 10 | 10 | 2 | 4.10 | 5 |
  | RTAudio \(27.8 Kbps\) | 20 | 69.5 |    1 | 2.95 | 6 |
  | RTAudio \(45 Kbps\) \(WB\) | 20 | 112.5 |    1 | 4.10 | 7 |
  | SILK \(36 Kbps\) \(WB\) | 20 | 90 |     1 | 4.42 | 8 |

* _**DSCP \( Differentiated Services Code Point \):**_ The Differentiated Services \(DiffServ\) is a 8-bit field in the IP header, and further divided into 6 bits for the DS field and 2 bits for ECN. The DS field contains 6 bit DSCP values which are used for network traffic classification and marking to ensure higher routing priority of packets and prevent voice quality degradation due to packet loss or delay. The commonly defined Per-Hop Behaviors \(PHB\) are Default PHB, Expedited PHB, Assured Forwarding \(AF\) and Class Selector \(CS\). DSCP values supported by ThousandEyes are listed [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn1KAC).
* _**De-Jitter Buffer Size:**_ A buffer generally stores packets for a particular time to reduce the effect of packet delay variations. A very small buffer size may cause large number of packets to be discarded, while a very high value of buffer size may add additional delay. As a general rule, a static de-jitter buffer should be between 1-1.5x the Packet Delay Variation \(PDV\) time to avoid frame discards.

  Voice packets are sent as a continuous stream of evenly spaced packets. However, depending on the network path congestion a packet can take any path available which may be different from the other voice packets. As a result, packets may arrive at the destination at variable time and thus out of order. In the screenshot below, packet 3 was delayed at the receiver. In the absence of a buffer, the playback will have a short pause to account for the delayed time of arrival.  
  IMAGE MISSING  
  When a large number of packets are delayed at the destination, the quality of the voice call can degrade significantly. ThousandEyes Voice tests implement a de-jitter buffer to delay playback of packets for a desired time period. As shown in the diagram below, waiting time period equal to the configured de-jitter size allows smooth playback of packets.  
  IMAGE MISSING

* _**Collect BGP Data:**_ ****Check this box to enable BGP data collection for the target prefix. The drop down menu lists the available BGP monitors. Collection of BGP routing information helps detect routing disruptions which can impact the voice call quality.

