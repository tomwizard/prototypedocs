# Static IP addresses for ThousandEyes repositories

ThousandEyes Enterprise Agents update their ThousandEyes software from one of two repositories: **apt.thousandeyes.com** for Appliances, Docker containers and Ubuntu-based Linux package installations, and **yum.thousandeyes.com** for Red Hat, CentOS and Oracle Linux-based Linux package installations.

The servers that host apt.thousandeyes.com and yum.thousandeyes.com are based in a content delivery network \(CDN\) for fast download performance and for redundancy. Using this CDN results in a dynamic mapping of the domain names to IP addresses. The IP addresses can change at any time, and the change frequency or timing is not controlled by ThousandEyes.

## Static IPv4 addresses

For customers whose Enterprise Agents' outbound network connections must be restricted to destinations with static IP addresses \(or domain names that resolve to static IP addresses\) ThousandEyes provides two additional repositories, **aptproxy.thousandeyes.com** and **yumproxy.thousandeyes.com**. Both domain names map to two static IP addresses hosted in Amazon Web Services. If only one IP address can be used, choose the address in the region that is geographically closer.

| IP Address | AWS Region |
| :--- | :--- |
| 54.235.118.60 | us-east-1 \(Northern Virginia\) |
| 54.188.155.71 | us-west-2 \(Oregon\) |

Customers may use these domain names in place of apt.thousandeyes.com and yum.thousandeyes.com in the repository configuration files of the Enterprise Agent systems, and use the domain names or IP addresses in the configuration of network devices if security policies or technical limitations \(firewalls or routers which which cannot resolve domain names in rules or ACLs\) require static IP address configuration. For guidance on changing the repository location used by your Enterprise Agents refer to the relevant steps for your installation type in how to [modify repository files on your Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYOCA0_Configuring-a-local-mirror-of-the-ThousandEyes-package-repository#modify-repository-files-on-your-agent). However, we strongly recommend using the default configuration \(apt.thousandeyes.com and yum.thousandeyes.com\) if at all possible. ThousandEyes attempts to maintain the stability of these IP addresses, but the addresses may change without warning.

## Troubleshooting

For customers using aptproxy.thousandeyes.com or yumproxy.thousandeyes.com, if the above IP addresses change, then Enterprise Agent software packages will not update. If using aptproxy.thousandeyes.com or yumproxy.thousandeyes.com and receiving warnings about out of date Enterprise Agent software on the [Enterprise Agents page](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents), run one or more of the following commands to determine whether the IP addresses have changed:

* `dig aptproxy.thousandeyes.com`

   `dig yumproxy.thousandeyes.com`

* `nslookup aptproxy.thousandeyes.com`

   `nslookup yumproxy.thousandeyes.com`

Any of the above commands should return two IP addresses. One or both may change.

## IPv6 addresses​

IPv6 addresses for aptproxy.thousandeyes.com or yumproxy.thousandeyes.com are not currently available. Contact [ThousandEyes Customer Success](mailto:support@thousandeyes.com?subject=Static%20IPv6%20addresses%20for%20ThousandEyes%20repositories) if package updates cannot be performed using IPv4.

