# Release Notes: 2019-11-26

Welcome to our latest release!

**Note:** This release occurred December 2nd rather than November 26th, due to the Thanksgiving holiday in the United States. The next release will be December 10th, 2019.

## Internet Insights™

 On November 13th, ThousandEyes publicly announced Internet Insights. Leveraging de-identified data from billions of service path measurements each day, Internet Insights provides users with unprecedented knowledge of Internet outages - and the power to do something about them. The following features are included with Internet Insights:

* Overview Dashboard: A global network outage dashboard.
* Topology View: Understand the scope and impact of network outages.
* Timeline View: Track outages over time.
* Outage Alerts: Take action when network outages occur, even where you don't have the infrastructure needed to install agents.
* Outage Snapshots: Capture and share network outages and affected test data.
* Outage History: A full year of outage data for you to analyze past outages and correlate outage data by provider to compare their performance over time.

## Synthetic Transactions

 ThousandEyes' new Synthetic Transaction tests are now generally available. The new tests offer major improvements to legacy transaction tests, allowing users to:

* Correlate app performance with network performance - the new transaction tests will also run an HTTP server test and a network test.
* Create scripts with the recorder, which includes a Selenium development environment that provides syntax highlighting and autocomplete.
* Generate as output a script that can be further modified.
* Take screenshots at custom points in the script execution.
* Add markers into scripts for finer timing resolution of workflow steps.
* Program conditional steps into scripts \(for example, if a pop-up window is present, click OK; otherwise, proceed with the rest of the script\).
* Log into websites using a secure credential store.

## ThousandEyes Blog

 There has been a lot of activity on the ThousandEyes blog recently:

* "Is it just me, or am I affected by an Internet outage?" That is the question that ThousandEyes aims to answer with its new product, Internet Insights. Conley Read, Principal Product Manager at ThousandEyes, highlights the changes in how we use the Internet that led to the creation of Internet Insights, what it offers, and where we are taking it next, in his new blog, [Introducing Internet Insights™](https://blog.thousandeyes.com/introducing-internet-insights/).
* One of the fundamental challenges to improving customer experience across the Internet is the vast, decentralized nature of the Internet itself. ThousandEyes' Director of Product Marketing Angelique Medina explains how this idea led to Internet Insights \(and why you need it\) in her post, [Managing Digital Experience at Internet Scale](https://blog.thousandeyes.com/managing-digital-experience-at-internet-scale/).
* In September, Garner published its Market Guide for Digital Experience Monitoring \(DEM\). ThousandEyes' Alex Henthorn-Iwane, VP of Product Marketing, explores what DEM is and why it is important to SaaS applications, in his blog post, [What is Digital Experience Monitoring?](https://blog.thousandeyes.com/what-is-digital-experience-monitoring/)
* In his blog [Diving into Application Monitoring with New Synthetic Transaction Tests](https://blog.thousandeyes.com/application-monitoring-new-synthetic-transaction-tests/), Hans Ashlock, Director of Technical Marketing at ThousandEyes, walks you through how to use the new synthetic transaction test functionality. Learn about the new recorder, get started with creating transaction tests in native Javascript, and see how the new tests shift the focus towards the end-user workflow.
* On November 13th at the second annual Cloud State Live launch event, ThousandEyes unveiled the 2019 Cloud Performance Benchmark report. Archana Kesavan, Director of Product Marketing at ThousandEyes, outlines the major findings and what we can take away from the report in her post, [Top Takeaways from the Cloud Performance Benchmark](https://blog.thousandeyes.com/top-takeaways-cloud-performance-benchmark/).

 And now for the release details.

## Features and Enhancements

* The UI has been updated for the Dashboards and Reports tabs to improve user experience. See the following knowledge base articles for information on how to configure reports and dashboards:
  * [Working with the Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmdKAC_Working-with-the-Dashboard)
  * [Customizing Your Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmcKAC_Customizing-your-Dashboard)
  * [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports)
* Users can create alerts using Endpoint Agent browser sessions metric data.
* Timeout rules for new page load, transaction, and synthetic transaction tests have been updated. See [Working with Test Settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn7KAC_Working-with-Test-settings#web_test) for more information.
* Dashboards and reports can now be shared with another account in the same organization.
* Network layer metric alert rules can now be created for Endpoint Agent scheduled HTTP server tests.
* Specified domains in HTTP, page load, and transaction tests now default to HTTPS.
* A new preview version of the v7 API has been released, allowing users to access detailed path visualization data by providing the testID, rather than the summary that is returned when providing the testID with v6.

## Bug Fixes

 The following issues have been fixed in this release:

* An error that caused test tables to show the availability of one DNS server, rather than the average across all DNS servers, has been corrected.
* Connection failures are now shown correctly in the timeline scrubber.
* An error in ordering when transaction tests were sorted by Completion in the Table view has been corrected.

## Questions and Comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-12-02+Release+Update)!

