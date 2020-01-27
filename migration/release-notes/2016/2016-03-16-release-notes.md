# Release Notes: 2016-03-16

Today, we held ThousandEyes Connect SF 2016 in San Francisco. Between great presentations from Microsoft, RichRelevance, Zendesk and Cisco, and advanced & essentials workshops, we had some fantastic discussion. For those who couldn't make it, we'll be posting some of the content up on the [ThousandEyes Blog](https://blog.thousandeyes.com/), so be sure to keep an eye out for updates.

IMAGE MISSING

And... without further ado, here are tonight's release updates.

## Cloud agent provider information

Provider information for cloud agents will now be shown in circumstances where a single provider is used for at least 30% of outbound routes.  This information is shown in three locations:

* in Cloud Agent settings

  IMAGE MISSING

* in the Agent picker in test settings and Instant tests

  IMAGE MISSING

* in Views which contain a table tab, when hovering over the cloud icon next to the agent name

  IMAGE MISSING

In order to keep this list of providers short, we are leveraging custom names \(ie, _Level 3_ instead of _Level 3 Communications, Inc._\), and only showing providers where a majority next hop provider is identified from BGP information for the agent.  If you're unclear on the specific network where traffic is routing through, check the path trace information for your tests.  In this case, a minimum threshold of 30% must be seen in order to show a provider.  Up to 2 providers will be shown.

## Squashed bugs

Our team of exterminators has been busy making minor feature updates and exterminating bugs.  A list of customer-facing bugs identified can be found below:

* Prior to this update, when running an instant web transaction test, all settings except for advanced options would be used to run the test.  Following this week's release, all specified advanced settings will be used.
* We've made an update that will prevent multiple Alert Suppression Windows from appearing in the timeline for a single test.  
* Username and password fields in advanced test settings will no longer be autofilled by browsers.
* When creating page load or transaction tests, if the target content type was not HTML, a user would receive an error message which prevented creation of the test.  This error has been changed to a warning.
* We've corrected a problem whereby searching from the Account Settings &gt; Users tab would not properly search on account names.

## Feedback?

Just [drop us a note](mailto:support@thousandeyes.com?subject=2016-03-02+release+update), any day, any time.  Feedback is always welcome! 

