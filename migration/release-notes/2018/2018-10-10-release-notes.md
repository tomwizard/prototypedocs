# Release Notes: 2018-10-10

Welcome to tonight's release!

IMAGE MISSING

Before we get to the new features, there's still time to tell you there's still time to register for [ThousandEyes Connect in Dallas](https://www.thousandeyes.com/events/connect/dallas-2018), on October 11th! [Registration](https://www.thousandeyes.com/events/connect/dallas-2018) is free and open for one more day.

For those not in the Dallas area tomorrow, maybe [ThousandEyes Connect in Seattle](https://www.thousandeyes.com/events/connect/seattle-2018) on November 8th, or [ThousandEyes Connect in Chicago](https://www.thousandeyes.com/events/connect/chicago-2018) on December 5th. Check out the lineup of great speakers. No matter which Connect you choose, a great ThousandEyes t-shirt is waiting for you. And if those locations don't work for your schedule, you can still come say hello to us at an [event near you](https://www.thousandeyes.com/events) \(and grab a t-shirt\).

And now for the feature event... Features!

## Dashboards and Reports

We've added a new Dashboard widget type! Say hello to the Color Grid:

IMAGE MISSING

Combining numbers and colors, the Color Grid is a great way to track a large number of measurements of the same metric, such as loss, latency or load times, from Tests, Agents, groups of Tests or Agents in a Label, or other sources.

## ServiceNow Integration

In the ServiceNow Integration of the Alert Rules Notifications, we've replaced the username and password authentication with OAuth token-based authentication.

IMAGE MISSING

Obtain the Auth URL and the Client ID from your ServiceNow account. Clicking the **Get Token** button will open a new browser tab or window, requesting approval to add the Integration to your account. If the addition is successful, the Edit Integrations window will display a message indicating success, and the **Token** field will contain the received OAuth token. Once the token is received, users can run a test of the Integration by clicking the **Test** button. Complete the creation of the new Integration by clicking the **Add New Integration** button.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Endpoint Agent no longer forces a restart to install updates in some circumstances.
* Previously, adding a Test or Agent to a Label would overwrite the previous Label members. Now, the Label endpoint \(/groups\) can support creating and adding or subtracting with a JSON or XML list of Test or Agent members.

## Questions and comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2018-10-10+Release+Update)!

