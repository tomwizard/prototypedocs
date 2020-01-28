# Endpoint Agent Views - Wireless

All data collected by Endpoint Agents from browsing webpages of domains listed under a monitoring profile from a monitored network is presented under [Endpoint Agents &gt; Views](https://app.thousandeyes.com/view/endpoint-agent/?). This article describes the **Wireless** View under **Network Access**.

IMAGE MISSING

1. **Metric:** Under the Wireless View, measurements for the following categories of metrics are available and metrics are averaged across all agents by default:
   * **Signal Quality:** A percentage value from 0% to 100%. A value of 0% implies an actual RSSI \(Received Signal Strength Indicator\) signal strength of -100 dBm. A value of 100% implies an actual RSSI signal strength of -50 dBm.
   * **Throughput:** Throughput observed by Endpoint Agent.
   * **Retransmission Rate:** Wireless retransmission rate an Endpoint Agent experiences.
   * **Roaming Events:** Number of times the wireless access point serving Endpoint Agent changes, measured from the number of times the BSSID of the connected network changes.
   * **Channel Swap Events:** Number of times the wireless channel changes for connected Access Point.
2. **Timeline:**  Plots a line graph of the selected metric and also a bar chart of the number of Endpoint Agents across all user sessions, over time. You can use the 24h, 7d and 14d links or drag the tabs to show data over a custom range. 
3. **Endpoint Table:** The Endpoint Table contains the following metrics:
   * **Agent:** Endpoint Agent performing measurements.
   * **Location:** Location of Endpoint Agent.
   * **SSID:** Service Set Identifier of wireless access point serving Endpoint Agent.
   * **BSSID:** Base Station ID \(MAC address\) of wireless access point serving Endpoint Agent.
   * **Roaming Events:** Number of times the wireless access point serving Endpoint Agent changes, measured from the number of times the BSSID of the connected network changes.
   * **Phy Mode:** IEEE 802.11 specification for the wireless connection used. Describes which standard is being used related to coverage range and speed optimization.
   * **Channel:** Channel used for wireless connection with access point serving Endpoint Agent.
   * **Channel Swap Events:** Number of times the wireless channel changes for connected Access Point.
   * **Transmit Rate \(Mbps\):** An Endpoint Agent host's transmission rate.
   * **Signal Quality \(%\):** A percentage value from 0% to 100%. A value of 0% implies an actual RSSI \(Received Signal Strength Indicator\) signal strength of -100 dBm. A value of 100% implies an actual RSSI signal strength of -50 dBm.
   * **Throughput:** Throughput measured by Endpoint Agent.
   * **Retr. Rate \(%\):** Wireless retransmission rate an Endpoint Agent experiences.
4. **BSSID Table:** The BSSID table contains the following metrics:
   * **BSSID:** Base Station ID \(MAC address\) of wireless access point serving Endpoint Agent.
   * **SSID:** Service Set Identifier of wireless access point serving Endpoint Agent.
   * **Location:** Location of Endpoint Agent.
   * **Number of Endpoints:** Number of Endpoint Agents being served by the same wireless access point, based on agents with the same **BSSID.**
   * **Phy Mode:** IEEE 802.11 specification for the wireless connection used. Describes which standard is being used related to coverage range and speed optimization.
   * **Channel:** Channel used for wireless connection with access point serving Endpoint Agent.
   * **Throughput:** Throughput measured by Endpoint Agent.
   * **Retr. Rate \(%\):**  Wireless retransmission rate an Endpoint Agent experiences.
   * **Signal Quality \(%\):** A percentage value from 0% to 100%. A value of 0% implies an actual RSSI \(Received Signal Strength Indicator\) signal strength of -100 dBm. A value of 100% implies an actual RSSI signal strength of -50 dBm.
   * **Roaming Events:** Number of times the wireless access point serving Endpoint Agent changes, measured from the number of times the BSSID of the connected network changes.
   * **Channel Swap Events:** Number of times the wireless channel changes for connected Access Point.
5. **Save:** Create a saved event, for more details visit [Retaining data beyond the 90-day limit](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn0KAC_How-long-does-ThousandEyes-retain-customer-data).
6. **Share:** Create a snapshot and share with a public link. More details here: [Sharing Test Data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data).

