# Troubleshooting time synchronization on Enterprise Agents

#### Troubleshooting time synchronization on Enterprise Agents

## Problem

When viewing your Enterprise Agent's status on the **Agents &gt; Enterprise Agents** page, you see a time synchronization warning, such as:

Agent System Time: HH:MM UTC \(XX minutes behind\)  
IMAGE MISSING

or

_Unable to determine agent system clock offset_

In order for ThousandEyes Agents to report data to the ThousandEyes data collector, the data must have correct timestamps. If data timestamps are significantly out of sync with the ThousandEyes collector, the data will not be uploaded to the collector and the above error results.  

## Solution

In order for a ThousandEyes Enterprise Agent to keep proper time, the Network Time Protocol \(NTP\) must be configured on the Enterprise Agent.  NTP is the standard way to perform clock synchronization among networked devices.  NTP communication occurs between the device configured for NTP and an NTP server providing the clock synchronization.  The process for configuring NTP for an Enterprise Agent has three parts: 

1. Select NTP servers
2. Configure any needed firewall rules 
3. Configure NTP on the Enterprise Agent   

### Select NTP Servers

First, select primary and secondary NTP servers to use.  Public NTP servers are available. The most commonly used public servers are the [NTP Pool Project](http://www.pool.ntp.org/) servers, which ThousandEyes Agents are often configured to use.  If you have a limited number of Enterprise Agents, select two of the following servers:

0.pool.ntp.org  
1.pool.ntp.org  
2.pool.ntp.org  
3.pool.ntp.org

These two domain names will be used in step \#3, as the servers that each Enterprise Agent will contact to obtain time synchronization information.

Alternatively, you may choose NTP servers which are closer geographically to your location, which can help improve NTP performance.  This [link](http://support.ntp.org/bin/view/Support/SelectingOffsiteNTPServers) explains how to [search](http://support.ntp.org/bin/view/Servers/WebSearch) for NTP servers.  You may search by geographic region, such as "California" or "Canada".

In addition, your Internet service provider \(ISP\) or hosting provider will often provide NTP servers to its customers.  If your Enterprise Agents are located within your corporate/internal network, then contact the technical support for your ISP to obtain NTP server information.  If your Enterprise Agent is located at a hosting/colocation facility, contact the technical support for your hosting provider to obtain NTP server information.  If available, it is recommended that you use these NTP servers to avoid adding to the load on the public NTP servers.

For sites with a few dozen or more Enterprise Agents, it is recommended that the organization run its own NTP server locally.  Consult the documentation for your organization's server operating systems to select a server for the NTP software.  This [link](http://www.ubuntugeek.com/network-time-protocol-ntp-server-and-clients-setup-in-ubuntu.html) describes the process of installing and configuring NTP on Ubuntu Linux.

**NOTE: Most Microsoft Windows Active Directory servers are configured by default to provide NTP.**  
If both the AD servers and the Enterprise Agents are located on your internal network, then use the IP addresses of two of your AD servers as NTP servers for step \#3.  You may be able to skip step \#2, firewall configuration.  Consult your network administrator.

### Configure firewall rules

Second, ensure the correct firewall configuration to allow NTP from the Enterprise Agent to the NTP servers.  Review this [article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) for port and protocol details. The destination IP addresses or domain names for any firewall rules will be the NTP servers.

Additionally, if you have created NTP servers on your own network, ensure that your NTP servers can communicate through any firewalls with the NTP servers that provide time synchronization to your servers.

### Configure NTP

Third, enable the Network Time Protocol \(NTP\) on the Enterprise Agent.  Follow the instructions below for the type of Enterprise Agent requiring NTP: the Virtual Appliance or the Linux package.

#### Virtual Appliance

Connect your browser to the web administration interface of the Virtual Appliance \( http://&lt;agent-IP&gt; \), and select the Time tab. Enter the domain names or IP addresses of your primary and secondary NTP servers, then click Save.

#### Linux Package

To enable NTP for a ThousandEyes Linux package, consult the documentation for your Linux distribution.  An example for Ubuntu is available [here](http://www.ubuntugeek.com/network-time-protocol-ntp-server-and-clients-setup-in-ubuntu.html).  In other Linux distributions the steps will be similar.  The steps have been summarized below:

1. Install the NTP package

   ```text
   sudo apt-get install ntp
   ```

2. Open the NTP configuration file with a text editor \(nano, in this example\).  Use sudo if required by your security configuration.

   ```text
   sudo nano /etc/ntp.conf
   ```

  
    Add the NTP primary and secondary server domain names or IP addresses near the top

   ```text
   0.pool.ntp.org
   1.pool.ntp.org
   ```

3. Start NTP

   ```text
   sudo /etc/init.d/ntp restart
   ```

