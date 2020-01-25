# Using the Device Layer View

The Device Layer View displays the data collected from monitored devices you have previously discovered using the [device discovery process](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpmKAC). Enterprise Agents which monitor devices will poll the devices at 5-minute intervals to collect data for the two views within the Device Layer view: the Topology view and the Interface Metrics view.

## Timeline

The Timeline shows a selected Metric for devices monitored by the Enterprise Agent selected in the Current Monitoring Agent setting.

IMAGE MISSING

1. **Current Monitoring Agent:** Select the Current Monitoring Agent. A device is monitored by one Enterprise Agent at a time.
2. **Metric:** Select the Metric:
   * **Throughput:** The aggregate throughput of all selected Interfaces on all selected devices.
   * **Discards:** The number of discarded packets of all selected Interfaces on all selected devices. Input packet discards typically indicate device resource constraints. Output packet discards typically indicate network connection saturation.
   * **Errors:** The number of errors of all selected Interfaces on all selected devices. Errors typically indicate faulty cables, switch ports or interfaces.
3. **Device:** A discovered device name or IP address.
4. **Interface:** A discovered interface name on the **Device**, or all discovered interfaces if the **Device** setting is set to "All Devices".
5. **Interfaces axis:** The number of interfaces participating in the aggregated data, as indicated by the solid grey color.
6. **Metric axis:** One or more lines indicating the value of the selected **Metric**.

## Topology View

The Topology View builds a network diagram of all discovered devices and other devices, along with their layer 2 links. Enterprise Agents poll devices via SNMP, querying each device's management information base \(MIB\) for Link Layer Discovery Protocol \(LLDP\) and for Cisco Discovery Protocol \(CDP\) data to obtain the topology information.

IMAGE MISSING

1. **Highlighting/Selecting/Quick Links:** Standard visualization tools to locate devices and connections that match specified criteria.
2. **Discovered Device:** Each device is represented by an icon according to the Device Type setting. You can change Device Type in Device Layer settings. Hover over a device for additional information about the device.
3. **Non-reporting Device:** Devices that were discovered, but provided no information about the links to other discovered devices are not connected to any other device in the Topology view.
4. **Undiscovered Device:** Devices that were not discovered by device discovery, but are reported as neighbors by discovered devices are shown as Unknown devices.
5. **Link:** Devices are interconnected with layer 2 links. Hover over a link for additional information about the link.
6. **Edit Topology Layout:** If the discovered topology does not reflect your network, click the **Edit Topology Layout** button to change the Topology view layout. Change the layout by placing discovered devices into different tiers.

## Interface Metrics View

The Interface Metrics view displays per-interface metrics, identifying devices and interfaces that contribute most to the metrics.

### Devices

The Devices tab displays device status, device description information, number of active Interfaces and aggregated interface metrics.

### Interfaces

Interfaces tab displays interface status for every monitored interface of the selected device. Speed indicates reported speed of an Interface. If an interface is a layer 3 interface and has an IP address, the IP address is shown. 

### Diagram

The Diagram tab graphically presents data from the interfaces of the selected device, which permits quick identification of the interfaces with the highest amount of throughput. Additionally, by displaying side-by-side the throughput per input and per output interfaces, from highest to lowest throughput, the direction of the traffic flows can be inferred. Click and drag down or up on the slider window between the INPUT and OUTPUT columns to scroll through the interfaces displayed in the window. Inside the slider window are the throughput histograms for the currently displayed input and output interfaces.

IMAGE MISSING

Aggregate metrics for the device and some additional information about the device are also displayed.

## Troubleshooting

**A network device is discovered and can be selected in the Timeline view, but is not seen in Topology view.**

Ensure the network device has either or both LLDP and CDP configured and active, and ensure either or both LLDP and CDP MIBs are exposed through the SNMP protocol.

**A new device was discovered, but timeline shows no interface metrics**

Ensure you have enabled one or more interfaces in the Monitored Interfaces selector of the Device Settings page. Please note that first interface metrics are available 15 minutes after the initial device discovery.

