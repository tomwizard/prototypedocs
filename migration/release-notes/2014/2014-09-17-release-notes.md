# Release Notes: 2014-09-17

This week, our team has continued prepping for our next couple of releases, which will be packed with new features that we're certain you'll love.  We've managed to sneak a few changes into this release, most due to popular demand by our users.

## Dashboard

We've updated the Enterprise Agent Status widget and added the capability to toggle between the Traditional Path Visualization view, which shows the path visualization from the agent to our Agent Collector, and the World Map, showing geolocation data for your agent.  To configure the Enterprise Agent Status widget, click the gears icon and change the view from Path Visualization to World Map view, or vice versa.  The screenshots below show examples of the widget's options:

IMAGE MISSING

IMAGE MISSING

## Alert rules

We've modified a couple of our out of the box default alert rules, to reduce alert noise.  This was done based on data analyzed across our client base, with input from several customers.

* Default Network Alert Rule has been changed to require a minimum of 3 agents showing 25% loss to the destination.
* Default Page Load Alert Rule has been changed to require a page load failure from 3 agents on 2 consecutive rounds.

These defaults are changed on new accounts only at this time.  if you would like assistance updating your default rules, please [engage our Customer Success Team.](mailto:support@thousandeyes.com?subject=Alert%20Rule%20Changes)

We've also added a new metric for DNS+ Domain Trace tests.  When setting up a Mapping _is not in_ rule, you can add the option to alert when a percentage of mappings is above or below a certain threshold.  Click the Add % of Mappings option after configuring this rule, to add a percentage constraint.

IMAGE MISSING

This rule was introduced to allow users to monitor changes to GLB DNS scenarios.  As an example, consider the record www.company.com is mapped to 1.1.1.1 in North America, 2.2.2.2 in Europe, and 3.3.3.3 in Asia/Pacific. In the past, monitoring for specific record changes could result in a significant number of false positives.  This option will allow more specificity in alert management, in order to allow alerting on regional changes with minimal numbers of false positives.

## API

We've published a number of changes to v4 of the ThousandEyes API, in order to harmonize the feature set available on test creation and edit, between the user interface and the API.  Check out our [Developer Reference site](http://developer.thousandeyes.com/) for more details on these changes.

As always, feel free to contact our [Customer Success team](mailto:support@thousandeyes.com?subject=Release%20update%20questions) if you have any questions.  We're here to help!

