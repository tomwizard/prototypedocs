# Firewall configuration for Enterprise Agents

## Problem

What firewall rules are required to allow an Enterprise Agent to execute tests, report data to the ThousandEyes platform, and access necessary infrastructure services such as the Domain Name Service \(DNS\) or the Network Time Protocol \(NTP\)?

## Solution

Create rules to allow communication as follows.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Protocol</b>
      </th>
      <th style="text-align:left"><b>Port</b>
      </th>
      <th style="text-align:left"><b>Destination</b>
      </th>
      <th style="text-align:left"><b>Direction</b>1</th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">53</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">DNS Server tests</td>
    </tr>
    <tr>
      <td style="text-align:left">UDP</td>
      <td style="text-align:left">53</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">DNS queries</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">Web tests</td>
    </tr>
    <tr>
      <td style="text-align:left">UDP</td>
      <td style="text-align:left">123</td>
      <td style="text-align:left">NTP servers</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">NTP time synchronization</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">443</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">Web tests</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP or UDP</td>
      <td style="text-align:left">5060</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">SIP Server tests</td>
    </tr>
    <tr>
      <td style="text-align:left">ICMP</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">outbound2</td>
      <td style="text-align:left">ICMP-based Network Layer Agent to Server tests, Path Visualization</td>
    </tr>
    <tr>
      <td style="text-align:left">UDP</td>
      <td style="text-align:left">
        <p>As per Server Port field on Advanced Settings tab of the Voice Layer&apos;s
          RTP Stream Test.</p>
        <p>Default = 49152</p>
      </td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">inbound/outbound</td>
      <td style="text-align:left">Voice Layer Metrics</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP and UDP</td>
      <td style="text-align:left">
        <p>As per Server Port field on Advanced Settings tab of the Agent to Agent
          Test</p>
        <p>Default = 49153</p>
      </td>
      <td style="text-align:left">*</td>
      <td style="text-align:left">inbound/outbound</td>
      <td style="text-align:left">Agent to Agent tests</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">443</td>
      <td style="text-align:left">192.150.160.0/24 AND
        <br />208.185.7.0/24</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">All Enterprise Agents,
        <br />connections to ThousandEyes collector</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">443</td>
      <td style="text-align:left">sc1.thousandeyes.com,
        <br />c1.thousandeyes.com,
        <br />data1.agt.thousandeyes.com,
        <br />crashreports.thousandeyes.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">All Enterprise Agents,
        <br />connections to ThousandEyes collector
        <br />(same as above, for domain-based firewalls)</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">9119 and 9120</td>
      <td style="text-align:left">ntrav.thousandeyes.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">NAT traversal6 for TCP-based Agent to Agent tests</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP and UDP</td>
      <td style="text-align:left">9119 and 9120</td>
      <td style="text-align:left">ntrav.thousandeyes.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">NAT traversal6 for UDP-based Agent to Agent tests</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">443</td>
      <td style="text-align:left">hub.docker.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">Docker-based Agents (install only)</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80 and 443</td>
      <td style="text-align:left">yum.thousandeyes.com OR apt.thousandeyes.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">All Enterprise Agents3
        <br />
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">archive.ubuntu.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">Virtual Appliance and Ubuntu-based Linux package Agents</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">archive.canonical.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">Virtual Appliance and Ubuntu-based Linux package Agents that use Adobe
        Flash (optional)</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">443</td>
      <td style="text-align:left">cdn.redhat.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">RedHat Enterprise Linux-based Linux package Agents4</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">mirror.centos.org and mirrorlist.centos.org</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">CentOS-based Linux package Agents4</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">80</td>
      <td style="text-align:left">linuxdownload.adobe.com</td>
      <td style="text-align:left">outbound</td>
      <td style="text-align:left">RedHat Enterprise Linux-based and CentOS-based Linux package Agents that
        use Adobe Flash (optional)</td>
    </tr>
    <tr>
      <td style="text-align:left">TCP</td>
      <td style="text-align:left">8998</td>
      <td style="text-align:left">127.0.0.1</td>
      <td style="text-align:left">inbound</td>
      <td style="text-align:left">BrowserBot5
        <br />
      </td>
    </tr>
  </tbody>
</table>  
Additionally, if a customer desires remote management connections that traverse a firewall, then the following connections may need to be allowed.

| **Protocol** | **Port** | **Destination** | **Direction**1 | **Description** |
| :--- | :--- | :--- | :--- | :--- |
| TCP | 22 | Enterprise Agent | inbound | Secure Shell \(SSH\)7 |
| TCP | 80 | Enterprise Agent | inbound | Virtual Appliance management7 |
| TCP | 443 | Enterprise Agent | inbound | Virtual Appliance management \(HTTPS\)7 |

### Notes

1. Direction assumes dynamic or stateful packet filtering \(pseudo-stateful, in the case of stateless protocols like UDP and ICMP\) which would permit the returning packets automatically. If your firewalling or filtering device uses static packet filters, you must create rules in both directions of the communication.
2. For the Path Visualization layer, be certain that your routers and firewalls do not block ICMP time-to-live \(TTL\) exceeded messages \(ICMP type 11\) returning to the Enterprise Agent \(inbound direction\) if you want Path Visualization beyond your router or firewall.  Both packet filtering rules and NAT rules \(if NAT is used\) will need to allow for ICMP TTL exceeded messages from the target to the Enterprise Agent.

    Additionally, under certain circumstances path tracing may not work properly, such as when the Identification field in the IP headers of packets sent from the Agent to the target is modified by the firewall.  This has been observed with certain NAT devices, such as Apple Airport wireless gateways.

3. Enterprise Agents automatically perform periodic updates.  Ubuntu-based systems \(including Virtual Appliance-based and Docker-base Agents\) use the apt.thousandeyes.com repository for ThousandEyes-specific packages; Red Hat and CentOS-based systems use the yum.thousandeyes.com repository for ThousandEyes-specific packages. For more information on addressing of these repositories, consult the ThousandEyes Knowledge Base article [Static IP addresses for ThousandEyes repositories](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q0k1CAC_Static-IP-addresses-for-ThousandEyes-repositories).
4. General Linux repositories for RedHat and CentOS can vary depending on the environment.  Check your system's /etc/yum.repos.d for the full list of repositories that may need to be given access via http or https. These sites may be CDN-based. If your firewall or filtering device cannot dynamically resolve a hostname for a filter rule, you may need to manually determine the IP addresses periodically using a tool such as dig or nslookup, and update the filter rule.
5. If the Browserbot package for Enterprise Agents has been installed \(used by the **Page Load** and the **Web Transaction** test types\) then the Agent process will try to make a connection to the Browserbot, which listens on port 8998/TCP of the loopback interface \(normally 127.0.0.1\).  Some host-based Linux-based firewall software, such as iptables, require that you explicitly allow loopback-based connections.
6. If **Behind a NAT** is checked on the Enterprise Agent's Settings page.  For more information, see the ThousandEyes Knowledge Base article [NAT Traversal for Agent to Agent Tests](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnWKAS).
7. The Virtual Appliance Enterprise Agents listen on port 22 TCP \(SSH\) and ports 80/443 TCP \(Virtual Appliance web administration interface\). Enterprise Agents installed using the Linux package method do not have these services installed by ThousandEyes.  See Knowledge Base article [How to set up the Virtual Appliance](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnwKAC) for more information.  Depending on your organization’s security policy, access to these ports may be allowed or blocked by default.  If you wish to manage the Virtual Appliance with a remote connection which traverses firewalling or filtering devices, access to these ports must be allowed.

