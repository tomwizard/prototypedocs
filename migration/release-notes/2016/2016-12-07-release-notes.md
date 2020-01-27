# Release Notes: 2016-12-07

As we wind down 2016 and move into the holiday season, the remaining releases \(today's, and the release in two weeks\) will be relatively light and fluffy as snowflakes, as compared to many releases in the past year that introduced major features. One or two cool new features, a stockingful of bug fixes.  You'll need to look elsewhere for a really big haul of presents in the waning weeks of 2016. But look on the bright side: we won't give you an ugly sweater.  As anyone who has attended a ThousandEyes CONNECT event can attest, we only hand out great t-shirts...  

And if you're a last-minute type, live in the metro New York City and want one of those t-shirts, then procrastinate on your shopping this Wednesday, December 8th, and come on down to CONNECT NYC!  Register [here](https://www.thousandeyes.com/events/connect/new-york-fall-2016) or just come on down to [LMHQ](https://goo.gl/maps/vmag4nT3eCK2) in Manhattan and do day-of registration.

Onward to the details of today's release...

## ​Reports

The Transaction Step Time and Transaction Page Time metrics from the Timings tab of a Transaction test are now available in Reports.  Create a pie chart of page timings:

IMAGE MISSING

to show the relative sizes of the page timings. \(Wow, our staging site's "Log In" page is slow! And don't even ask what the orange thing represents...\) Or create a stacked area chart of step timings:

IMAGE MISSING

to show the change over time of each step's timing. Useful for quickly spotting a page or step that's occasionally being naughty instead of nice, and blowing up the timing results:

IMAGE MISSING

## Endpoint Agent

We've added new permissions available to a user's role that allow viewing the personally identifiable information \(PII\) returned by Endpoint Agents. The the PII is divided into two categories, each with a permission:

* machine and user information is covered by the View endpoint data that identifies users permission
* page title and URL information is covered by the View endpoint data that identifies visited pages permission

## Minor features & bug fixes

 The stocking stuffers...

### API

* Fixed an issue which caused the /alerts endpoint to fail to return the Agent list for DNS Server alerts

### Reports

* Fixed an issue which could cause the Agent to Agent tests to be missing from the Test filter in Reports widgets

### User Management

* Single sign-on users no longer need to set a local password upon activation

### Endpoint Agent

* The tooltips in Path Visualizations now include all wireless metrics
* Fixed an issue which caused the tooltip from the Page Title column in User Sessions to display "Unknown Page"
* Fixed an issue which caused systems with the same public IP address at one time in the past to be given the same organization name \(whois\) when a system moves to a network that maps to a different organization name
* When adding a filter in Views, the selector now opens automatically

### Tests

* Fixed an issue which allowed users with no test editing permissions to toggle the "Follow Redirects" checkbox of an HTTP Server test, even though the setting could not be saved.
* Fixed an issue in the Path Visualization view which could cause a negative Average Delay in the tooltip when mousing over a link
* Fixed a bug which generated an "Unable to process your request. Please try again later." error when creating a test.

### Miscellany

* A broken link on the Billing tab now correctly points to the Usage tab.
* Registration emails to users whose names were not entered upon initial account creation are now more aesthetically pleasing.

## Questions or comments?

 Give us the gift of your feedback, here at [support@thousandeyes.com](mailto:support@thousandeyes.com). No need to wrap it in pretty paper. Even if it's a lump of coal, we'll still treasure it--bow or no.

