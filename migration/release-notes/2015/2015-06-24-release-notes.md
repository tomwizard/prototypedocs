# Release Notes: 2015-06-24

Just a quick update for this week; we're planning for some pretty significant updates in the next release in the queue, so stay tuned here for more updates.

## New cloud agent locations

Have you ever been curious on how we choose new agent locations?  [In this Blog post](https://blog.thousandeyes.com/how-to-find-and-test-hosting-providers/), DevOps Engineer [Victor Garcia](https://blog.thousandeyes.com/author/vgarcia/) explains some of the mysteries around how we choose Cloud agent locations.

This week, we've added cloud agents in the following locations:

* Northampton, United Kingdom
* Rio de Janeiro, Brazil

These agents are immediately available to paying customers. Please note that access to these agents is not included in trial subscriptions.

## Outdated agent version notifications

Users can now alert when an Agent is running an out of date version. Prior to this release, we would show a notification in the dashboard and on the agent settings pages when this situation occurred. This option can be combined with the Last Contact and Clock offset notification options as required. To configure an agent notification for out of date versions, navigate to Settings &gt; Agent Notifications and either create a new rule or modify an existing one.

Note: this notification will process once a new version of the agent is available for 2 hours, in order to give agents around the globe an opportunity to update.

## Agent target for tests

We've added a new field for Target address/hostname to agent settings. Intended for use in Voice and other agent-to-agent tests \(coming soon!\), this option determines the target address of a test which targets the agent.

IMAGE MISSING

For example, if my agent has internal IP 192.168.1.223 and public IP 50.184.189.59, I would determine how to set this field based on how I wanted to target the agent in an agent-to-agent test. If attempting to reach the agent from the cloud, I would configure the Target for Tests field to reflect the public IP \(50.184.189.59\). In the event I needed to configure tests from inside my network, I would configure it to use the private IP \(192.168.1.223\).  In the event that tests are required from both inside and outside the network, I would configure DNS in a split-horizon method, where DNS inside my network points to 192.168.1.223 and outside my network points to 50.184.189.59.

The Target for Tests field is configured with the agent's public IP address by default.

## Bugs squashed

We've corrected two minor issues in this release:

* Where a page load or transaction test shows PREFETCH requests which result in component errors, these requests will now be suppressed from the resulting waterfall data.
* Users can now replace the certificate used in Single-Sign-On configuration without changing other fields.

## Questions & comments?

We really do love hearing from our users. If you have any questions, comments or just want to send us your favorite Dilbert strip, please [drop us a note](mailto:support@thousandeyes.com?subject=2015-06-24+Release+Notes). 

