# Release Notes: 2014-09-04

As we send the kids back to school, we start the slow but steady unveil of what our development team has been working on throughout the summer. Check out a list of the major updates below, and let us know if you have any questions...

## Alert settings rewrite

If you follow our [blog](http://blog.thousandeyes.com/), you know that we're a big fan of the latest web technologies and frameworks. As with our test settings page, which had a rewrite earlier this year, we've updated our alert settings page to improve the user experience, speed, and allow our team to leverage [AngularJS](https://blog.thousandeyes.com/?s=angular).

With the new Alert Settings page, users will experience a familiar browsing experience to that in place for test settings: simply select the layer you're interested in, the type of alert, and create a set of alert conditions.  Configure notifications rules \(number of consecutive periods where alerting state is true, custom messages to send\) in the notifications tab

IMAGE MISSING

We've also added one alert criterion to the alert rule options: the ability to specify a specific HTTP response code.  To review our current list of supported alert criteria, check out the article listed [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work).

For detailed instructions on creating and editing Alert Rules, please review this knowledge base [article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmhKAC).  
 

## Disabling Enterprise Agents

As of today, users assigned to the Account Administrator role can now disable Enterprise Agents. This will allow organizations who have agents deployed in various locations to enable and disable those agents when they need to manage the measurements.

Enterprise Agents will:

* Not attempt to run assigned tests
* Not factor into alerting \(because it's not running tests\)
* Not alert when it goes offline or has time synchronization issues
* New group is available for disabled enterprise agents
* Only count against billing when enabled

This is ideal in circumstances where an organization needs to deploy agents to specific sites, but doesn't require the use of those agents on an ongoing basis.  This will facilitate the deploy &gt; use &gt; disable &gt; enable &gt; use &gt; disable workflow, allowing faster activation during future troubleshooting efforts, without complicating enterprise agent status widgets.  Disabled agents are shown in the Agent Settings page, with a  IMAGE MISSING icon next to the agent name.

IMAGE MISSING

To disable an Enterprise Agent, uncheck the "Agent Enabled" checkbox in the agent settings page.  _Note: an Enterprise Agent must be online in order to disable it, since the agent acknowledges an instruction to stop testing until reactivated._

We've added a built-in group for disabled agents to allow fast identification of those agents. Administrators can control the enablement of their agents via the Agent Settings page.  The Disabled built-in group will only be shown in the case where the account has access to at least one disabled Agent.  
 

## BGP Private Peering

As described in our Inside-Out BGP Visibilty article, the BGP Private peering capability has been moved from Beta into Production.   This means that all customers who maintain an edge router and want visibility from their own organization into Autonomous System availability are now able to take advantage of this feature.  Users with Organization Admin privileges can find this menu item in the Settings &gt; [BGP Private Peers](https://app.thousandeyes.com/settings/bgp-sessions) menu item.

IMAGE MISSING

Check out [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmjKAC) for more details on using the feature.  
 

## Bug Extermination

We've fixed a few issues that have cropped up over the last couple of weeks.

* Regular users are now able to configure a dashboard as their default. Prior to this fix, users in the Regular User role were unable to save a default due to a permissions error.
* We've corrected an issue where the links to view test results from the test settings page could take users to the correct view, but select the wrong test.
* The ThousandEyes Virtual Appliance package was previously resetting the web console to the default password. After this most recent update, web console passwords will persist between package upgrades.
* The End-to-End Metrics view will now sort by the loss metric by default, when jumping to this view from another Layer.

  
If you have any questions about this, or any release, please feel free to comment at the bottom of this thread, or to contact our Customer Success team by emailing support@thousandeyes.com.  We're always happy to answer any questions you may have.

