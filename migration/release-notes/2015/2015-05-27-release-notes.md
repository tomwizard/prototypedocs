# Release Notes: 2015-05-27

As we eke our way into June, here's a list of things that we've been having fun working on over the course of the next month.

## New cloud agent locations

We've added cloud agents in the following locations:

* Santiago, Chile
* Cork, Ireland
* Hyderabad, India
* Kazan, Russia

These agents are immediately available to paying customers.  Please note that access to these agents is not included in trial subscriptions.

## Disabled to Enabled

With a focus on optimization of user experience, we've replaced the disabled built-in group for both tests and agents, in favor of adding a third state in the selector for enabled items.

IMAGE MISSING

Found in the Test settings, Alert settings, Alert Suppression Window and Reports interfaces, the selector will now allow users to filter only on enabled targets.

## Enterprise Agent notifications

To allow users to standardize on notifications for their Enterprise Agents, we've changed how we notify when an agent goes an extended period without a check-in with our collector, or when there is a time synchronization problem.

IMAGE MISSING

Notifications are configured in a similar manner to Alert rules, where users select the criteria and thresholds required to trigger the notifications, and configure notification targets. To configure an agent notification, navigate to _Settings_ &gt; _Agent Notifications_, and create a rule based on any combination of Last Contact and Clock Offset.

### Useful use cases for agent alerts

We often get asked for advice on alert rules, and this is an area that is no different.  As a broad recommendation, we'd advise creating rules to manage escalation of results, which may include an agent being offline for a protracted period of time.  For example:

* Last Contact &gt;= 30 mins OR Clock offset &gt;= 60s: Warning to operations team
* Last Contact &gt;= 180 mins: Escalation of warning to operations team

### Webhooks and PagerDuty

In addition to the configuration of rules, we've added the ability to configure PagerDuty and Webhook targets for the Agent notifications.

### Binding notifications to agents

Users can bind Enterprise Agents to Agent notification rules via either the Agent settings page or the Agent Notifications settings page.

IMAGE MISSING

### Upgrade behavior

During this deployment, a series of notifications will be created for each independent Enterprise Agent notification configuration.  If your organization has multiple enterprise agents deployed using different offline notification schemas, this would be a good time to standardize on the notification scheme.

## Dashboard Enteprise Agent Status widget

We've updated the Enterprise Agent status widget to show the map view, rather than the Path Visualization view as the default option in the widget.

## API

This is our final release reminder that we are discontinuing versions 2 and 3 of the ThousandEyes API on June 4, 2015. On June 4, 2015 at 02:00 UTC we will be taking the following actions:

* Removal of APIv2 and APIv3 \(requests for v2 and v3 will be redirected to the oldest available version, v4\)
* APIv5 will become the current version, so requests to https://api.thousandeyes.com without specifying a version in the endpoint will move to v5.

We've fixed a couple of minor bugs and introduced two new endpoints. Check out http://developer.thousandeyes.com/v5/\#/changesummary for more information.

## Questions, Comments?

As always, we love hearing from our customers. If you have any questions or comments, please [send us an email](mailto:support@thousandeyes.com?subject=2015-05-27+Release+Notes).

