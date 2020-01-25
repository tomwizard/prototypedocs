# Discovering Device Layer Devices

### Discovering Device Layer Devices

ThousandEyes' Device Layer monitoring utilizes Enterprise Agents to poll your network devices using the Simple Network Management Protocol \(SNMP\). The Enterprise Agents must complete an initial device discovery process prior to monitoring the desired devices. Credentials for one or more devices must first be configured before the discovery of devices.

IMAGE MISSING  
 

## [Prerequisites]()

ThousandEyes Device Layer requires either SNMP version 2c or SNMP version 3. Device Layer retrieves the same data regardless of version SNMPv2c or SNMPv3, so you can configure either of the two versions. SNMPv3 provides better authentication, and data encryption in transfer.

Device Layer requires read-only access to the SNMP information. We recommend creating new read-only credentials for the Enterprise Agents, but existing read-only credentials can also be used.

Before the initial device discovery, perform the following steps:

1. Verify that each device will answer SNMP queries.
2. Obtain from each device:
   * the version of SNMP enabled
   * community string \(SNMPv2c\) or authentication & privacy settings
3. Ensure SNMP queries are allowed from the Enterprise Agent IP addresses to each device.

    Your target or other network devices \(firewalls and other security devices\) may restrict SNMP queries from Enterprise Agents to your target network devices using access control lists \(ACLs\). If so, add the Enterprise Agents' IP addresses to the ACLs. Allow SNMP queries destined to port 161/UDP.

## [Configuring device credentials]()

Device Layer requires your devices' SNMP credentials to discover the devices. Navigate to the Device Settings page and select the Device Credentials tab. Click the **Add New Credentials** button to add a new set of credentials.  
 IMAGE MISSING

Give the credentials a meaningful name and select the SNMP version.

IMAGE MISSING

SNMPv2 credentials consist of a single community string, which serves as a plain-text password.

IMAGE MISSING

SNMPv3 requires:

* Security Name
* Context Name \(optional\)
* Authentication Protocol and Key \(optional\)
* Privacy Protocol and Key \(optional; only if using an Authentication Protocol\)

Click the **Add New Credentials** button to save the changes. If you have gathered different sets of credentials for different network devices, repeat the process for each set of credentials you have gathered.

## [Device discovery]()

With at least one Device Credential configured you can configure one or more Device Discoveries. Device discovery can be performed manually, or can be scheduled at regular intervals ranging from 5 minutes to 24 hours.

Device discovery will poll targets specified in the discovery configuration. Polled devices may report interfaces on additional networks not specified in the targets. The Enterprise Agent can perform discovery on any additional networks, and polls discovered devices for further additional networks. This recursive process will continue until no new networks are found. In this way, the maximum number of pollable devices across all networks can be discovered without needing to manually configure polling for all devices. The depth of the recursion can be controlled in order to reduce the time or network traffic levels of the discovery process.

Additionally, discovery of devices can be controlled through the use of whitelists and blacklists, which apply to the configured targets and to any networks discovered. Blacklists take priority over whitelists if the lists overlap.

### One-time discovery

To start a one-time device discovery, select the Devices tab and click the **Find New Devices** button. A discovery configuration form will appear.

#### Basic Configuration

On the Basic Configuration tab of the form, configure the following settings:

IMAGE MISSING

* **Targets:** Specify which devices the Enterprise Agent should attempt to discover. Enter the hostname, IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\).
* **Monitoring Agent:** Select an Enterprise Agent or an Enterprise Agent cluster to perform the discovery. Note the following:
  * When selecting an Enterprise Agent cluster as the **Monitoring Agent**, as with all other testing performed by clusters, Device Layer testing will be performed by a single member of the cluster. The member is selected by the cluster load balancing algorithm. If the Agent performing the Device Layer testing is removed from a cluster, the Device Layer testing is reassigned to another cluster member.
  * If an individual Enterprise Agent which is already performing Device Layer testing is moved into an existing cluster, the Device Layer view data collected prior to joining the cluster will be no longer available. Device Layer data found on the Path Visualization view will continue to be available.
* **Credentials:** From the configuring device credentials step, select all the Credentials used by devices in the **Targets** field.
* **Save as scheduled discovery:** If checked, the following additional fields appear to allow saving the discovery for automatic running: IMAGE MISSING
* **Discovery Name:** The name of the saved Discovery, which will appear in the listing of the Device Discoveries tab.
* **Interval:** The time interval between automatic runs of the Discovery.
* **Notification Rules:** The names of Device Notifications assigned to this Discovery.

#### Advanced Settings

On the Advanced Settings tab of the form, configure the following settings:  
IMAGE MISSING 

* **Whitelist:** Specify devices within the **Targets** setting and from discovery which the Enterprise Agent should attempt to poll. Enter the IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\). Hostnames are not permitted.
* **Blacklist:** Specify devices within the **Targets** setting and from discovery which the Enterprise Agent should not attempt to discover. Enter the IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\). Hostnames are not permitted. Blacklists take priority over whitelists if the lists overlap.
* **Maximum Hops:** Limit the number of additional discovery attempts to perform, based on information returned by the discovered devices. See the Device Discovery section above. The default is 0, which results in polling only the devices in the **Targets** field \(no additional discovery attempts\).
* **Connection Attempts:** Set the number of connection attempts per device.  Heavily utilized devices or saturated networks may require multiple SNMP connection attempts per device.
* **Connection Timeout:** Set the timeout on each connection attempt.
* **Discovery Timeout:** Set the total time allowed for discovery. When the **Maximum Hops** setting is greater than 0, this setting can be useful to limit the discovery if discovered devices return large numbers of additional targets.

### Scheduled discovery

To start a scheduled device discovery, select the Device Discoveries tab and click the **Schedule Discovery** button. A discovery configuration form will appear.

#### Basic Configuration

On the Basic Configuration tab of the form, configure the following settings:

IMAGE MISSING

* **Discovery Name:** A name for the discovery.
* **Targets:** Specify which devices the Enterprise Agent should attempt to discover. Enter the hostname, IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\).
* **Credentials:** From the configuring device credentials step, select all the Credentials used by devices in the **Targets** field.
* **Monitoring Agent:** Select the Monitoring Agent that will perform the Device Discovery. This can be an Enterprise Agent or an Enterprise Agent cluster.
* **Interval:** Specify the frequency at which the discovery will be performed.
* **Notification Rules:** Select one or more Device Layer Notification Rules, in order to be notified when discovery produces new information, such as discovery of a new device or new interface on an existing device, or if an existing device is no longer contactable.

#### Advanced Settings

On the Advanced Settings tab of the form, configure the following settings:

IMAGE MISSING

* **Whitelist:** Specify devices within the **Targets** setting and from discovery which the Enterprise Agent should attempt to poll. Enter the IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\). Hostnames are not permitted.
* **Blacklist:** Specify devices within the **Targets** setting and from discovery which the Enterprise Agent should not attempt to discover. Enter the IP address, IP address range \(e.g. 192.168.1.1-192.168.1.10\) or subnet \(CIDR notation, e.g. 192.168.1.0/24\). Hostnames are not permitted. Blacklists take priority over whitelists if the lists overlap.
* **Maximum Hops:** Limit the number of additional discovery attempts to perform, based on information returned by the discovered devices. See the Device Discovery section above. The default is 0, which results in polling only the devices in the **Targets** field \(no additional discovery attempts\).
* **Connection Attempts:** Set the number of connection attempts per device.  Heavily utilized devices or saturated networks may require multiple SNMP connection attempts per device.
* **Connection Timeout:** Set the timeout on each connection attempt.
* **Discovery Timeout:** Set the total time allowed for discovery. When the **Maximum Hops** setting is greater than 0, this setting can be useful to limit the discovery if discovered devices return large numbers of additional targets.

## [Device discovery results]()

Upon completion of discovery, new devices will be displayed at the top of the list, above a solid horizontal line. Additionally, the count of new devices is displayed to the left of the **Find New Devices** button.

IMAGE MISSING

Click on a row to view the details of that device:

IMAGE MISSING

* **Name:** The SNMP name of the device. The **Name** field is populated from the discovered device's SNMP name, but can be changed.
* **Type:** The type of network device. The **Type** field is populated from the discovered device's SNMP device type, but can be changed. This setting controls the device's icon in the Topology view, but does not affect data collection.
* **IP / Hostname:** The IP address or hostname of the device. The **IP / Hostname** field is populated from the discovered device's SNMP device type, but can be changed to query the device on a different IP address.
* **Monitoring Agent:** Data from a discovered device is collected by a single Enterprise Agent. If a network device is discovered by multiple Enterprise Agents, use this setting to select which Enterprise Agent queries the device.
* **Monitored Interfaces:** The discovered network interfaces belonging to this device. All of a devices’s discoverable network interfaces are listed, but not monitored by default. Select the interfaces you would like to monitor, but keep in mind there is a maximum of 4000 interfaces that can be monitored by a single agent. Discovery is still performed using only the interface specified in the **IP / Hostname** field.
* **Interval:** The frequency with which queries are sent to the device. The Interval cannot be changed.
* **Credential:** The credential which is used to poll this device. The Credential can be changed.
* **Alert** **Rules:** Select Alert Rules for device events.
* **Notification Rules:** Select Notification Rules for device events.
* **General Information:** System name, Vendor, Platform and Description fields obtained via discovery from the device.
* **Device Uptime:** The device is polled every 5 minutes. If the device can respond to any SNMP queries, the device is considered up.
* **Stop Monitoring**: This button will stop the Agent from polling the device via SNMP. Once stopped, the **Test** button will be replaced with a **Monitor Device** button which will restart monitoring.
* **Cancel:** This button will allow cancelling of any changes made to the configuration.
* **Test:** If changes to the configuration are made, the **Test** button will become clickable, and the configuration can be tested by clicking the **Test** button.
* **Save:** Click the **Save** button to save any changes.

## [**Troubleshooting device discovery**]()

If a device cannot be discovered, perform the following steps:

1. Go to **Devices &gt; Device Settings**, select the Devices tab and click the **Find New Devices** button.
2. Enter the IP address of the device you would like to discover in **Targets** field.
3. Ensure the **Credentials** match those configured on the network device.
4. Ensure there is SNMP connectivity between the selected Enterprise Agent and the device \(destination UDP port 161\).
5. Leave the values on the Advanced Setting tab at default values.
6. Click the **Start Discovery** button.

If manual discovery fails, check the device's logs and the logs of any firewall or packet filter in between the Enterprise Agent and the device. Look for logged drops of UDP port 161 traffic. Alternatively, perform packet captures on the device to verify that SNMP communication reaches the device.

