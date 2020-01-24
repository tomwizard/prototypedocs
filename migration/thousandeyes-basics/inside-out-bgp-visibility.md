# Inside-out BGP visibility

You're familiar with the capabilities that ThousandEyes provides with regard to external BGP visibility, using public monitors to show the reachability of a particular network prefix, but want data that is more relevant to your organization?

Let's say you have a business critical process which depends on an external software provider, such as salesforce.com -- and you want to be able to monitor the reachability of the Salesforce prefix from inside each of your office locations where Salesforce is used.

A second use case is for an internal BGP monitor when you're originating a prefix of your own; by virtue of having a monitor which tracks all routing changes inside your AS, you'll have direct visibility over path changes that occur on your own network \(origin AS\). This allows deeper visibility into the origin network, from the vantage point of your internal monitors, which can be instrumental in diagnosis of problems.

So, how do you accomplish this? You're already monitoring the target site using a web or network test and Enterprise Agents, but perhaps you want BGP data that is more relevant to your own network topology.

We've introduced the ability to obtain inside-out BGP visibility, using the private eBGP peer capability of our platform. This allows your network administrators to configure their BGP speakers to peer with our route collector, which will show the reachability of each BGP target, from the vantage point of your own networks.

IMAGE MISSING

## To configure your BGP speaker to interface with our collector:

Your user must be in a role that has the Edit BGP monitors permission assigned in order to make these configuration changes.

IMAGE MISSING

 Browse to [Cloud & Enterprise Agents &gt; BGP Monitors](https://app.thousandeyes.com/settings/bgp-sessions/) and click **Add Private BGP Monitor**; this will show a new monitor form. Enter fields as per below:

* **Monitor Name** - the name you wish to show in the list of BGP monitors.
* **Remote IP Address** - the external \(non RFC-1918\) address allocated to your router.
* **Remote AS Number** - your Autonomous System number. You must maintain your own AS number in order to configure peering with our route collector.
* **TCP MD5 Password** - \(optional\) the authentication key used to establish the peering session on your router.

_Caution: edge router configuration changes should only be done by qualified personnel. Consult your network administration team for assistance if any of the steps shown below are unclear._

Once you complete all the required fields, click on **Request Peering**. You will see a modal window like this:

IMAGE MISSING

An email will be sent out to the recipients configured in the Notifications Tab along with configuration commands to be entered on your router.

The BGP monitor will appear with "Pending" Status along with the entered information as shown below:

IMAGE MISSING

If you wish to Delete a Private BGP Monitor or Cancel a Pending Request, click the Trash icon next to the Status field of the desired BGP Private Monitor. You will be asked to confirm your action. 

Next, you'll need to configure your router as a multi-hop peer with ThousandEyes, using private AS number 65315. Sample instructions and targets will be shown in the dialog.

Peer AS number: **65315**  
BGP type: **external**, **multihop**  
Neighbor address: **&lt;Peer IP as per email from ThousandEyes&gt;**

Once configured, we strongly recommend that the peering session be configured to reject all route changes.  After the request is received and approved by our team, we will approve the peering session, and coordinate with you on timing for establishing sessions with your BGP speakers.

Once approved, and the peering session established, the monitor will show in the list of private peers, indicating the remote IP of the monitor, target AS number, and the length of time that the peering session has been established. Changes to Account Group bindings are now permitted for Private BGP Monitors, if needed a private peering will need to deleted and requested again from desired Account Group.

Administrators can optionally trigger alerts from ThousandEyes when the BGP monitor unavailable. This works in the same general manner as our Enterprise Agent availability notifications. You can enter a list of email addresses to notify, via this interface.

If you have any questions around using this feature, please contact our Customer Success team at [support@thousandeyes.com](mailto:support@thousandeyes.com)

