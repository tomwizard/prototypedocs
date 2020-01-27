# Release Notes: 2016-11-23

It's that time of the year here in the United States where we give thanks for the bountiful harvest, and stuff ourselves with Turkey while enjoying the pleasure of the company of our friends and family.  Please note that in order to allow our teams to enjoy the holiday with their families, we will be providing email-based support on Thursday and Friday of this week.  Our European team will continue to provide service in line with normal levels.

Last week, we ran ThousandEyes Connect in San Francisco, and had great sessions by presenters QuantCast and ServiceNow.  In 2 weeks we'll be running ThousandEyes Connect at LMHQ in New York City - you can register for the event [here](https://www.thousandeyes.com/events/connect/new-york-fall-2016).

Ok, now on with the good stuff!  

## Automatic user provisioning

 We've implemented the System for Cross-domain Identity Management \(SCIM\) protocol for use with organizations that have Single Sign-On \(SSO\) configured.  What does this mean for you?  It means that you can now configure ThousandEyes in conjunction with an SSO provider to automatically add new users into ThousandEyes when they're added or removed from your provider's system.

You can find more information feature by reviewing this article: [ThousandEyes Support for SCIM](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK)

ThousandEyes implements the SCIM specification, however in practice it appears that many identity provider implementations of this protocol vary slightly.  Our initial implementation will be updated as soon as we have certification from Okta, Microsoft Azure Active Directory \(Premium\), and OneLogin.  If your provider isn't listed here but does support SCIM 2.0, please let us know and we'll be happy to look into the implementation.  If you're using one of these Identity Providers and would like to be an early SCIM adopter with ThousandEyes, let us know and we'll be in touch as soon as we have certification from those providers.

In addition to the SCIM implementation, we've added support for ways to configure your SAML 2.0 compliant provider, using explicit, imported XML or dynamic configuration.  Check out [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnEKAS) for more information.

## Change ownership of tests

 We've long supported live sharing of tests, which allows a test to be shared both with other account groups inside your organization, and to other organizations altogether.  With this new feature, rather than sharing the test, you can move the test into another account group.  This can be useful for keeping your tests organized, attributing cloud usage to a specific account group, or reorganizing your company's ThousandEyes organization to keep it in line with business needs.

Find out more about moving tests between accounts by reviewing the Knowledge Base article [Changing ownership of a test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWcCAK).

## API for reporting

 We've introduced our reporting API.  This capability will allow experienced API users to access the aggregate metrics shown in our reporting interface.  This feature is currently in beta, and is only exposed via version 6 of the API.  For more information on the new reports API, along with other changes, see our [developer reference site](http://developer.thousandeyes.com/).

## Test settings change

 We've moved a few things around on the Test Settings interface.  We now have a More Actions menu for each test on the test settings page. You can now duplicate, delete or transfer ownership for a test.  We've removed buttons for duplicating and deleting tests.  We've also changed how the test settings panels are rendered.

IMAGE MISSING

In addition, we've enabled live sharing of DNS+ and BGP tests.

## New cloud agents

 We've recently added another 3 locations to our Cloud Agent list.  These new agents can be found in Mississauga, Canada, Markham, Canada and Tunis, Tunisia.  Look for more exciting locations as we continue to build out our cloud agent network.  The full list can be found [here](https://www.thousandeyes.com/product/cloud-agents).

## Subscription agreement updates

 We've updated our click-through subscription agreements, found at [https://app.thousandeyes.com/legal/agreement](https://app.thousandeyes.com/legal/agreement), and moved the Support Services and Security Policy into a separate click-through agreement, found at [https://app.thousandeyes.com/legal/support-security](https://app.thousandeyes.com/legal/support-security).

## Bugs squashed

 ...and last but not least, we've corrected a number of bugs.

* Corrected a problem that caused the Agent to crash in certain circumstances when installed on a RedHat/CentOS 6 server when ipTables is enabled.
* We've taken steps to ensure that we are auditing deletion of external emails \(non-ThousandEyes users\).  Prior to this update, deletion of an external email address was not being added to the Activity Log.
* Corrected a problem that caused the BrowserBot component to crash while executing certain transaction steps.
* Fixed the link shown in the "Views enabled for this test" information panel for the test settings interface with Agent to Agent tests
* Fixed an issue that caused snapshot shares to not show any data in the Page Load view.
* We've corrected an issue that caused ICMP network tests to send traffic to port -1
* We've corrected an issue that warns about problems with a test configuration before any data is entered.
* Fixed an issue that caused the dateStart, metricsAtStart, metricsAtEnd fields in the API from being shown when making calls to the /alerts endpoint.
* Corrected the permalink returned in the /alerts endpoint to include the account ID of the test.
* Corrected the behavior of test settings changes for DNS Server tests with the recursive bit enabled.  
* Corrected the behavior of the /usage endpoint that caused the cloudUnitsProjected field to fluctuate between hourly tabulations of actual usage.
* Fixed the card labels in the built-in Page Load test report. 
* Fixed a problem with Transaction tests created via the API: tests were not defaulting to a 30-second timeout.
* Added support for advanced fields \(dnsOverride, desiredStatusCode, clientCertificate, userAgent, pingPayloadSize\) via API write endpoints for tests.

