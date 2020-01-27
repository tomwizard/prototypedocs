# Release Notes: 2019-02-20

Welcome to our latest release! We hope you had a lovely Valentine's Day, this past week.

Some heartwarming news, via the ThousandEyes blog. With ThousandEyes' recent announcement of our Series D round of funding, CEO Mohit Lad [takes a blog moment](https://blog.thousandeyes.com/series-d-raising-funds-and-making-new-mistakes/) to reflect on the ThousandEyes journey to date. Mohit discusses mistakes made, lessons learned and on what lies ahead, and also gives a shout out to our investor partners. And for all the folks who showed us some love and D-votion as customers, business partners, social media followers, supportive significant others or whatever role you've played to help make ThousandEyes what it is today... Much love back to y'all!

Not to be outdone in the blogging department, our VP of Product Marketing, Alex Henthorne-Iwane, dispassionately dissects Digital Experience Monitoring \(DEM\) in his post, [Don’t Deprecate Your Digital Experience Visibility](https://blog.thousandeyes.com/kafka-topics-pitfalls-and-insights/). Alex discusses application performance monitoring in the context of a recent APM vendor's decision to drop monitoring from diverse network vantage points.  \(Hint: their name begins with 'D'.\)

Last but not least, Senior Site Reliability Engineer, Raúl Benencia, has penned us a post that only a nerd could love: [Kafka Topics: Pitfalls and Insights](https://blog.thousandeyes.com/kafka-topics-pitfalls-and-insights/) \(just kidding, Raúl!\) If Apache Kafka is part of your architecture, then don't get down in the dumps over Kafkaesque dilemmas. Check out Raúl do's and don'ts for a rewarding relationship with Kafka.

And without further delay, the details of today's release!

## Enterprise Agents

### Warnings for unsupported Agents

In keeping with our [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy), Enterprise Agents will now display warnings on the Enterprise Agents Settings page when an Agent has reached End of Installation Support, End of Support or End of Life. Note that the next lifecycle date for Agent support is the end of support for Trusty-based Agents, on April 30th, 2019. For a full list of lifecycle dates, consult the ThousandEyes knowledge base article [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems). 

## New Filters for Tests Settings

We've added some additional filters to the Tests Settings page. Users can now filter their view of the Tests listing by:

* **Agents:** Agents assigned to tests
* **Monitors:** BGP Monitors assigned to Routing Layer tests
* **Interval:** Test's interval setting
* **Shared By:** Tests shared by an Account Group
* **Alert Rules:** Alert Rule assigned to tests
* **Modified By:** Tests modified by a user

## API

The API now permits configuration of the number of traces for a test, via the /test/{testId} endpoint. When reading from the endpoint the pathTraces property displays the current number of path traces configured for an existing test \(unless Network Measurements have been turned off \(networkMeasurements is set to 0\). When writing to the endpoint, pathTraces is an optional property which defaults to 3 \(except DNS Server tests, which default to 1\).

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* Fixed an issue with the Duplicate Tests button which could cause a tab in Chrome to close
* Fixed an issue which could return a 500 HTTP status code error when trying to view a Saved Event
* Fixed an issue which could prevent a path from highlighting when mousing over a node in the Path Visualization
* Saving changes in Test Settings for a Shared by ThousandEyes Test no longer removes the Test from the user's list of Tests and resets any changes

## Questions and comments

Got feedback for us? Want to send us a belated Valentine? [Send us an email](mailto:support@thousandeyes.com?subject=2019-03-05+Release+Update)!

