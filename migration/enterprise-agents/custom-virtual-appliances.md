# Custom Virtual Appliances

We've also introduced the ability to download a custom Virtual Appliance.  Purpose-built for organizations deploying Virtual Appliances to clients, the custom Virtual Appliance is pre-configured with the account token and SSH keys used for management of the appliance.  This streamlines configuration management and eliminates complexity for organizations deploying large numbers of virtual Virtual Appliances.

To generate a custom Virtual Appliance, click the Agent &gt; [Enterprise Agent](https://app.thousandeyes.com/settings/agents/enterprise/) &gt; Add New Agent, and select the **Custom Appliance** tab, then select the **Virtual** tab

IMAGE MISSING

Give the Virtual Appliance a name, select a format per the list below, select if you want the Web Server and add **public SSH keys** as appropriate:

* **ova** - our most popular VA offering, formatted for use in VMware products, XenServer and VirtualBox.
* **zip** - for use with Microsoft Hyper-V server 2008
* **Cisco OVA** - for use within Cisco IOS XE based Integrated Service Routers \(ISR\)/Aggregated Service Routers \(ASR\)

Once you click the **Generate** button, it will take up to 30 minutes to generate a Virtual Appliance, depending on the format requested. You will receive an email when the generation process is complete.

