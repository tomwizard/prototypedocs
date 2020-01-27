# Release Notes: 2019-05-14

Welcome to our latest release!

Half a tick 'til we get to the details of the release; time for a tip of the old bowler to all who attended a smashing ThousandEyes Connect event in New York City, a half-fortnight past. Blimey, what a turnout of loverly ThousandEyes users. We were absolutely chuffed.

Take a miss on Connect NYC? Have no idea what all that meant? The solution to either is to make your bookings for...

IMAGE MISSING

Come join us for Connect London on Thursday, June 13th \(held at a pub, of course\). We've got a right cracking lineup of speakers, including ThousandEyes co-founders Mohit Lad and Ricardo Oliveira. [Registration](https://www.thousandeyes.com/events/connect/london-2019) is open and won't cost you a farthing. 

And now for the details of the release. [Bob's your uncle](https://en.wikipedia.org/wiki/Bob%27s_your_uncle).

## Enterprise Agents

A couple new authentication options are available for Enterprise Agents, as well as support for new hardware for Physical Appliance installations.

### Kerberos authentication for browser-based tests

Page Load and Transaction tests run from Enterprise Agents can now be configured to authenticate with websites using Kerberos and Kerberos-based authentication schemes.

IMAGE MISSING

From the Cloud & Enterprise Agents &gt; Agent Settings page, select the Kerberos Settings tab and configure the information for granting Kerberos tickets to Agents which allow access to the websites in the Page Load or Transaction tests. This configuration can also be selected for a specific Enterprise Agent under the Agents tab, in the Agent's Advanced Settings:

When creating a Page Load or Transaction test, select Kerberos in the HTTP Authentication section of the test's Advanced Settings. 

IMAGE MISSING

When you run the test from an Agent which has a Kerberos configuration, the test will use the Agent's assigned Kerberos configuration.

### NTLM proxy authentication

Enterprise Agents can now use NTLM authentication with web proxies. For ThousandEyes Appliances, select the NTLM option in the Web Proxy section of the Network settings. 

IMAGE MISSING

For Linux package-based and container-based Agents, set "proxy-auth-type=NTLM" in the /etc/te-agent.cfg file.

### Intel NUC8 support

Physical Appliances now support the Intel NUC8 platform. Consult the Hardware Requirements section of the ThousandEyes Knowledge Base article [Installing a Physical Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnOKAS_Setting-up-a-physical-appliance#hardware-requirements) for specific information on the supported configurations of this platform.

## Bug fixes & minor feature enhancements

Here are the bug fixes and minor features in this week's release:

* Endpoint Agent Lite has been renamed Endpoint Agent Pulse
* Columns in the Table tab of Agent to Agent tests have been renamed to make clearer which Agent is sending or receiving, for a given Direction \(Source to Target, Target to Source\)
* For the Device Settings page, the **Reduce Query Size** and **Query Mode** Advanced Settings of devices under the Devices tab are now available for devices under the Device Discoveries tab.
* Instant Tests now provide descriptive diagnostic messages when the test cannot be run when the cost of the test in units would exceed limits of either the Organization or the Account Group
* Users with the built-in role of Account Admin for a given Account Group will no longer be able to see users in other Account Groups of the same Organization
* In the Description field of the Activity Log, a User Login event now shows the type of login in parentheses, e.g. "User Login \(Interactive\)", "User Login \(Remember-me cookie\)" and "User Login \(SSO\)"
* In the Description field of the Activity Log, creation and update events for Agents, Labels and Snapshots now identify the specific Agent, Label or Snapshot
* When creating a new Endpoint Agent Label, deleted Endpoint Agents are no longer displayed in the **Filter** setting's Agent selector
* Custom Roles with Endpoint Agent permissions now can access Endpoint Agent Test Settings
* Under the Organization tab of the Account Settings, the **Currently Active** bar of the Endpoint Agent Licenses now displays the licenses used and available
* Fixed an issue which caused a custom User Agent string configured for a Web Layer test not to be displayed in the test's settings after saving the configuration
* Fixed an issue that displayed a "Badly formed target" diagnostic message when entering an IP address in the **Target** field of an Agent to Server test
* Fixed an issue which could cause overlapping diagnostic messages on the Quotas tab of the Account Settings
*  Fixed an issue which could cause a "ERR\_FAILED: A generic failure occurred." message from the Network view of an Endpoint Agent's scheduled test

## Questions and comments

Got feedback for us? A nod or a wink? Pop 'round the postbox and [send us an email](mailto:support@thousandeyes.com?subject=2019-05-14+Release+Update)!

