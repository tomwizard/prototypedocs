# How does the Endpoint Agent work

Endpoint Agent collects data about web browsing performance and network connectivity. This article describes how the Endpoint Agent communicates with ThousandEyes services when registering, updating or downloading configuration changes. Then, we look into how Endpoint Agent collects data from actual user browsing activity and uploads it back to ThousandEyes services. Lastly, we look how the network configuration setup information is gathered from the client machine.

But first, to understand the way data flows through the Endpoint Agent and into the ThousandEyes service, it helps to understand the components that make up the Endpoint Agent:

| Component | Function |
| :--- | :--- |
| ThousandEyes Endpoint Agent Browser Plugin\(Chrome, Internet Explorer, or both\) | Responsible for gathering performance data from the browser. |
| Endpoint Agent System Service \(te-agent\) | Responsible for performing and uploading  network probes. Also acts as a network test service for the browserhelper. Periodically  checks in with the ThousandEyes backend to retrieve the active monitoring profile. |
| Endpoint Agent Browserhelper \(te-browserhelper\) | Connects with the browser and coordinates data collection from the browser and performing network tests based on the browser activity. It is responsible for uploading the browser data to the backend. |
| Updater service | For Windows there is a te-updater binary running as a scheduled task to update the Endpoint Agent.  On Mac, te-agent checks for updates and uses Squirrel to download and apply the update. |

In general, all data is transmitted and received over HTTPS \(port 443\) to and from the following domains:

* **data.eb.thousandeyes.com**: All performance and network data
* **c1.eb.thousandeyes.com:** Control channel for configuration and client updates

Starting from the initial installation of an Endpoint Agent, through the sending of data, to installing updates and eventual uninstallation, data flows through the system as follows:

## Registration and Configuration

* **Endpoint registration**
  * Once an Endpoint Agent is installed, it will attempt to register with the ThousandEyes service using a secret key associated with your organization and a unique machine ID that allows that particular machine to be uniquely identified \(via c1.eb.thousandeyes.com\).
* **Config is downloaded**
  * Upon successful registration, the Endpoint Agent will download the latest configuration from the ThousandEyes service \(again via c1.eb.thousandeyes.com\).
  * This configuration data is stored within the System Service but is also shared with the Browser Plugins.
* **From this point on, the Endpoint Agent \(via c1.eb.thousandeyes.com\) checks for:**
  * A new configuration every 15 minutes or when the network changes
  * System configurations every 2 hours
  * Client software updates every 3 hours

## Data Collection and Uploading

Now that the Agent has an up-to-date configuration, it is ready to start gathering data. It does this in the following ways:

* **Browser-based data**
  * Trigger: 1\) When the user visits a domain that is set to be monitored for the current active network or 2\) the user starts a manual recording by clicking the Endpoint Agent icon in Chrome or IE
  * When a session is started by the browser this information is sent to the browserhelper. The browserhelper creates a sample which contains:
    * A network profile \(see definition below\)
    * Active tests:
      * ICMP ping to destination or proxy \(10 packets\)
      * ICMP traceroute to destination or proxy \(Paris traceroute\)
      * If there is a VPN: ICMP ping and traceroute to VPN server
      * Gateway ping if proxy or VPN is not in same VLAN as gateway
  * Webpage timing data \(HAR\) is streamed from the browser to the browserhelper and then sent to the ThousandEyes backend via data.eb.thousandeyes.com within a few seconds. The HAR data continues to stream until the tab is closed or the user navigates to a different domain.
  * As the HAR data is streaming, the browserhelper sees all of the data, and when more than 10 minutes has lapsed since the last network sample, another sample is created with the same information as the first one \(see above\) and the samples are linked together with the session. \(Note: In the views, a “Session” is equal to a “Sample” in the system\).
* **Periodic local network probes**

   Every 5 min when on a monitored network with “Collect periodic network statistics” enabled for the Monitoring Profile, the following information is gathered:

  * ICMP ping and traceroute data to any proxies and VPNs observed on the current network over the last 24 hours
  * ICMP ping  data to the system's gateway
  * A Network profile

   The Endpoint Agent runs all probes within a short span of time, rather than distributing probes over the 5-minute interval.

##  Network profile:

The network profile, which is used by both the browserhelper and agent, has the following data:

* **Local IP and DNS configuration**
  * Information about the client’s general network configuration that can be used for troubleshooting, filtering Views and reports, etc.
* **Wired or Wi-Fi connection**
  * Including link speed, signal strength, etc. for understanding the type and quality of the connection the machine uses to access the network.
* **VPN configuration**
  * The System Service looks at the routing table to get the interface \(can be virtual or physical\), then queries the system configuration to find the exact IP address of the VPN server, after which it sends packets to the VPN server and then to the destination to attempt to gather performance information about each.
  * Note that this can fail if unsupported VPN software or configurations are used; in such cases the system might indicate a VPN is present but may not be able to present the actual IP of the VPN server. We will mark this issue in the views but still show that there is a VPN connection.
* **Proxy configuration**
  * The System Service examines the proxy profile from the network config in the system. All the information of .pac file is parsed, and evaluated the target domains in by-pass list, and determine whether to send packets to the proxy or not.

## Updating

Endpoint Agents, like Enterprise Agents, update themselves automatically. ThousandEyes updates Endpoint Agent software bi-weekly. However, unlike Enterprise Agents, the Endpoint Agent update process is gradual; not all of your Endpoint Agents will be updated immediately. Endpoint Agents will be updated over the course of 72 hours.  If any issues are introduced due to Endpoint Agent updates, ThousandEyes can stop subsequent updates across an entire organization until the issue is addressed.

When an update is available, each Endpoint Agent will download the update from **downloads.thousandeyes.com** and store it locally. Once an update is downloaded on the client machine, the Agent will wait for all user browsing activity to stop to apply the update. Either the user must quit all browser windows OR have no browsing of monitored domains for 5 minutes. If these conditions are not met, eventually, an Endpoint Agent will force auto-update.  An out-of-date Endpoint Agent will be marked with an exclamation-point warning triangle icon on the **Settings &gt; Agents &gt; Endpoint Agents** page.

