# Release Notes: 2016-10-12

We've got plenty of updates to share regarding updates this week - but before that, a word from our sponsors \(aka the Marketing team\):

We’ll be at [NANOG 68](https://archive.nanog.org/meetings/nanog68/home) and [WAN Summit London](http://www.wansummit.com/london/index/) next week, and [Open Networking User Group](http://opennetworkingusergroup.com/) and [RIPE 73](https://ripe73.ripe.net/) in Madrid the following week. Be sure to come by and say hello, pick up a free t-shirt, and get an overview of some of the latest innovations we've been releasing to the world!

We'll also be hosting ThousandEyes Connect in San Francisco on November 17th. Registration is free - learn more and save your spot [here](https://www.thousandeyes.com/events/connect).

Finally, our team ran a webinar earlier this week related to Monitoring of VoIP and RTP in an Enterprise WAN environment.  Here's an accompanying [blog post](https://blog.thousandeyes.com/monitoring-voip-rtp-enterprise-wan/)!

## Reports & dashboards

### Reports

No new features, but a few bugfixes for dashboards and reports in this release.

* Between last release and this one, we made an update to the reporting interface to revert a change introduced in the 9/28 release.  Users using the % Inactive time option for alert reporting will have noticed a change in the numbers reported by this widget.
* For time series widgets reporting on a standard deviation measure, using the "one line per chart" option could result in some charts being missing.

### Dashboard updates

* We've done some optimization work around the load time for dashboard widgets, to speed up the initial landing flow for end users.
* We've added additional filter options for the Enterprise Agent status widget.  Now, users can filter on Agent and Agent group, as well as owned vs all assigned Enterprise Agents.

###  Single sign-on assertion handling

We've made an update to how our system processes assertions from registered identity providers \(IdPs\).  Prior to this update, users who used a non-routable address as a login name would be unable to register with our system when implementing strict SSO login requirements because the email address in our system must match the address sent by the IdP when making an assertion.  This has been updated, and our system will now accept an assertion from an IdP as long as the assertion includes a name claim which matches an address in an account registered to use ThousandEyes, leveraging the IdP making the assertion.

###  Bugs & minor enhancements

* Our HipChat integration was previously restricted to the cloud version of HIpChat \(URLs ending in hipchat.com\).  This has been expanded, and users can now configure integrations with the on-premise version of HipChat.
* Search for users by role using the Users tab of the Account Settings page.  Previously this was restricted to user name, email or account group name.
* Some problems were encountered following our 9/28/2016 release related to handling of proxy servers on Enterprise Agents.  These issues were all resolved midstream of the release cycle, and included: problems running BrowserBot-based tests \(Page Load and Transaction tests\) running instant tests, and installing Enterprise Agents behind a proxy.
* We've made an update to ensure that the numeric keypad on a macOS X computer works in all fields when using the FireFox browser.  In some cases, the keypresses weren't registering.
* The test settings interface will now throw an error when attempting to set an invalid value for the ping payload size on a Network layer Agent to Server test.  Prior to this update, a test settings change which set this to an invalid value \(valid options are 1-1400 bytes\) would be silently ignored.
* We've made an update to enabling alerting on a test, in order to be consistent with documentation. Users now can enable alerting on a test only when at least one alert rule is selected.  
* We've corrected a problem that would cause users to see a DSCP change to Best Effort on the last hop of the Path Visualization.

## New Customer Success Center site

And now, the part I'm especially excited for: our team has been busy integrating the Customer Success Center \(CSC\) into the application, which will allow our teams to streamline internal processes, make content available without authentication, and improve your experience overall when interacting with the support team.  So, how are things better?

IMAGE MISSING

First, if you're a subscriber to our release notes content, you'll probably notice that this message is in a slightly different format than usual.  This is because it's coming from the new system.

### New look and feel

The CSC now looks just like the rest of the application.  Navigate as you would elsewhere in the application, and leverage the search bar at the top of the page to find relevant content.  Click the **?** icon in the upper right corner of the page and click either the Customer Success Center heading, or any of the embedded links to open content in the new system.

### Optimized search

We've done two things related to search.  First, as you type, you'll see a list of articles, questions and ideas that match your search text.  This should make it simpler to find content.  We'll also be optimizing search based on queries you enter - using synonym groups and similar technology to make your search results more accurate.

Second, you no longer have to be logged in to see much of our content.  We've made it available to everybody, and you can access it at https://success.thousandeyes.com.  If you find an article that you like, simply click the share button in the upper-right corner of the article, and you'll get a public link you can share with a friend, regardless of whether they have access to the platform.  Based on this, we'll soon be opening portions of our KB to the googlebot, so you can now search our content directly in Google - just add site:success.thousandeyes.com to target the search on our site.

### Community prominence

Have something you'd like to share with other customers?  How about an idea that would make your life easier?  You can either ask a question or post an idea to the site.  Other ThousandEyes users can comment, provide answers, and share content.  Use the Community and Ideas tabs of the community to interact.  Note that you'll need to be authenticated to contribute to the Community, and of course we'll be moderating the site.

### Easy access to email subscriptions

Email subscriptions are finally easy to manage in once place.  Go to the Profile tab, and check the categories you're interested in.  You'll get an email any time we post a new article to a category.  Oh, and if you want your image to show up in our Community, just head over to gravatar.com to upload an image that's bound to your email account.

### We'll be making a lot more changes

 There is still a lot of work to be done.  It's surprising how much work there is to keep two systems talking to one another without disturbing everybody while we make changes.  We'll continue to evolve the site, content and notifications and workflows over the course of the coming weeks.  A lot of what we'll be doing will be focused on making the user interaction better.  If you see something that you like, love or hate, just [let us know](mailto:support@thousandeyes.com?subject=your+new+support+site). 

