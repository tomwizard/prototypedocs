# Transactions \(Classic\) - Web Transaction tests for Salesforce

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

Many ThousandEyes customers employ the SaaS application Salesforce.com as an integral part of their business.  In order to ensure maximum availability or conformance to service-level agreements, ThousandEyes customers often wish to configure Web Transaction tests that target the Salesforce.com \(SFDC\) application.

For increased security, customers often configure Salesforce.com’s client IP address-based authentication feature.  This feature requires that any login to SFDC come from an IP address that has been entered into a whitelist in the SFDC application. If an Agent or client IP address is not whitelisted, then after login the Salesforce.com application will display a page similar to this:

IMAGE MISSING

##  ThousandEyes Agent access to Salesforce.com

To run a Web Transaction test which performs login, the public IP address of any ThousandEyes Cloud or Enterprise Agent running the Web Transaction test must be configured in the SFDC whitelist.  To access the whitelist in Salesforce.com and for additional information on the SFDC authentication features, consult the sections entitled "Login IP Address Ranges" and "Organization-Wide Trusted IP Address List" in Salesforce Help article [Setting Login Restrictions](https://help.salesforce.com/HTViewHelpDoc?id=admin_loginrestrict.htm&language=en_US).

To view the Agents assigned to a Web Transaction test, log into your ThousandEyes account and click on **Tests** under the **SETTINGS** menu. Click on the name of the test in the test name pull-down menu. The table at the bottom of the test results page will list the Agents assigned to the test. To obtain the IP address of an Agent, mouse over the Agent’s icon to the left of its row in the table. A pop-over appears, displaying the public IP address of the Agent \(along with private IP address if an Enterprise Agent with a private IP address\).  If your Enterprise Agents are configured to use a proxy, the pop-over will display the public IP address needed for the SFDC whitelist.

Alternatively, you may contact ThousandEyes Customer Success for a list of Cloud Agent IP addresses for [all our Agent locations](https://www.thousandeyes.com/product/agent-locations). Enterprise Agent IP addresses are assigned by your organization.  Consult your network or firewall administrator for a listing of public IP addresses of your Enterprise Agents if you have large numbers of Enterprise Agents, making the mouse-over technique impractical, or for other reasons.

**Note:** Within a geographical location, the specific Cloud Agent assigned to a test is subject to change.

Each geographical location representing a Cloud Agent is typically a cluster of physical systems, each running Agent software. When you assign an Agent to a test by selecting the Agent in the Agent pull-down menu, the ThousandEyes platform selects one Agent in the cluster of Agents to run the test.  Tests assigned to a geographic location are not guaranteed to use the same physical system, so may have different IP addresses.  Whenever a test is created or edited, a new Agent will be assigned.

For example, creating a test and assigning to the Cloud Agent in Boston, then creating a second test and assigning to the Cloud Agent in Boston, then checking both tests for the Agent IP addresses may display different IP addresses, if different agents within the Boston cluster were selected by the ThousandEyes platform.

**Note:** Cloud Agent IP addresses are subject to change, though typically they are constant for extended periods.

The IP addresses assigned to any given physical system in a cluster are generally stable.  However, circumstances infrequently arise \(such as changing the Internet service provider used by ThousandEyes at a given geographic location\) where new blocks of addresses need to be assigned to the physical systems. Therefore, the same physical systems may change IP addresses.

## Use of the Transaction Recorder

Using the ThousandEyes Transaction Recorder to create a Web Transaction script that logs into Salesforce.com requires that the public IP address of the client system with the Recorder be configured in the SFDC whitelist.  Note that your system’s public IP address will likely change as you move the device from one location to another \(e.g. from office to home or hotel\).

Additionally, if you wish to allow the ThousandEyes Customer Success team to assist in troubleshooting Web Transaction scripts, you may wish to include in your SFDC whitelist the IP address of the ThousandEyes corporate office, currently 38.122.6.66.

