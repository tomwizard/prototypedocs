# PagerDuty Integration

On our October 29, 2014 release, we introduced an integration with PagerDuty for Alert management.

IMAGE MISSING

In order to integrate with PagerDuty, you need the following components in place.

1. ThousandEyes test\(s\)
2. ThousandEyes alert rule\(s\)
3. A PagerDuty service \(which is based on a PagerDuty escalation policy\)

For those of you not familiar with PagerDuty, think of a PagerDuty service as a destination for your alerts. Just as with Email Notification, the alerts need to be sent somewhere: the reason you'd integrate into a system like PagerDuty allows you to manage notification destinations, repeat notifications, and escalation rules for each recipient of the alert.  Follow the instructions below to create a PagerDuty Service:

## Creating a PagerDuty Service

If you don't have an Escalation Policy defined for your alerts coming from ThousandEyes, Log in to PagerDuty and create an Escalation Policy. This will define how frequently users are notified, and who receives the notifications.  

### Create an Escalation Policy

On the top nav, click Escalation Policies, then on the upper right side of the page, click New Escalation Policy. In an escalation policy, you can define who gets notified, how frequently, and using which methods. Depending on the configuration of your team, you can configure an On-Call Schedule - which allows users to rotate through an on-call schedule, allowing handoffs of active incidents, or a user-based Escalation Policy. If you want to configure your Escalation Policy to use a schedule, create this schedule \(Top Nav &gt; On-Call Schedules\) before attempting to create the Escalation policy.

IMAGE MISSING

1. Give your policy a name
2. Add users or on-call schedules to the policy
3. Determine how long before the alert gets escalated
4. Repeat steps 2-3 for escalations
5. Set repeat notifications until acknowledged
6. Save your Escalation policy

Once you have an escalation policy defined, you can configure a service which will accept notifications from ThousandEyes and begin the escalation policy. 

### Creating a Service using ThousandEyes

There are two methods of PagerDuty service creation, but we'll only show our side here, since the PagerDuty team will likely put together an update on their end once people start using the integration.  

From ThousandEyes, under **Alert Settings**, open the rule you wish to link to PagerDuty, then click the **Notifications** tab.  Under the PagerDuty section, click the Edit Services link. 

IMAGE MISSING

If you already have one or more PagerDuty services configured, they will be shown in the list, otherwise click the Add New PagerDuty Service link to add a new service.

IMAGE MISSING

This will take you to an authorization page on the PagerDuty site, which will request your username and password, then log you in.

IMAGE MISSING

Once you've authenticated and authorized the integration, you can either select an existing PagerDuty service, or create your own based on the Escalation policy you created above.  In the example below, I've created a new service based on the TE Documentation Escalation policy.

IMAGE MISSING

Finally, click the "Finish Integration" button.  You can ignore the warning about being "almost done".  You're done, and alerts triggering on the basis of this alert rule will be routed to users in your escalation policy.

## How the integration works

Once you've configured a PagerDuty service, and an alert is generated, the alert will trigger a new Incident in PagerDuty, which will follow the Escalation policy upon which the service is based.  This escalation policy may:

* Notify by email
* Notify through mobile push notification \(iOS/Android\)
* Notify by SMS
* Notify by calling you and using Text to Speech

In most cases the alert must be acknowledged, at which point the escalation policy stops.  Users can add notes following an acknowledgement, and can clear the mark the alert as Resolved as required.  If the alert rule conditions are no longer met by your test \(or the alert rule is updated such that the conditions no longer meet the criteria of the alert\), the alert rule will be marked as cleared within PagerDuty via an incident update.

IMAGE MISSING

IMAGE MISSING

IMAGE MISSING

