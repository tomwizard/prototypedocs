# Enterprise Agent Hardware Requirements

This document describes the hardware requirements to run a ThousandEyes Enterprise Agent in virtualized and non-virtualized environments.

## Common Enterprise Agent requirements

The table below provides requirements common to all types of Enterprise Agent, with and without the BrowserBot component. The BrowserBot component performs Page Load and Transaction tests.

|  | **With BrowserBot** | **Without BrowserBot** |
| :--- | :--- | :--- |
| **CPU count** | 2 | 2 |
| **RAM** | 2 GB | 1 GB |
| **Hard disk space**  | 20 GB | 20 GB |
| **Network interface** | required | required |
| **Internet connection** | required | required |

## Additional requirements

Depending on the type of Enterprise Agent installation \(Virtual Appliance, Physical Appliance or Cisco IOS XE container\), some additional requirements must be met.

### Virtual Appliance

Installation of the Enterprise Agent Virtual Appliance requires a serial communications device/serial port connection to the virtual machine's console for keyboard and text terminal input and output. When importing the Virtual Appliance in OVA format into VMware or Oracle VirtualBox hypervisors, or importing the ZIP format into Microsoft Hyper-V, a serial port is included in the virtual machine definition. Normally, customers using those hypervisors do not need to perform any configuration to meet this requirement.

For other hypervisors that may not support the OVA or ZIP templates, ensure that the configuration of the virtual machine provides a serial device for console access, prior to importing the Virtual Appliance. When a serial device is not present for the console, warnings appear in the Virtual Appliance's log file which can consume available disk space.

The Virtual Appliance uses the console to provide a text-based configuration menu.  Basic network configuration can be performed using the menu in times when DHCP is not available or similar circumstances. Additionally, the Virtual Appliance's web admin console password can be reset through the text menu.

### Physical Appliance

Hardware requirements for the Enterprise Agent Physical Appliance are specified in the ThousandEyes Knowledge Base article [Installing a Physical Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnOKAS).

### Cisco IOS XE Container

Hardware requirements for the Enterprise Agent Cisco IOS XE container are specified in the ThousandEyes Knowledge Base article [Enterprise Agent Installation for Cisco IOS XE Containers](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnRKAS).

