# Release Notes: 2019-12-10

Welcome to our latest release!

## ThousandEyes Blog

There is new activity on the ThousandEyes blog:

* Steve Mazzuca, Sales Director at ThousandEyes, discusses the importance of visibility in managing a distributed and diverse infrastructure in his new blog post, [Leveraging Modern Visibility Tools to Tame Your IT Infrastructure](https://blog.thousandeyes.com/leveraging-modern-visibility-tools-tame-your-it-infrastructure/).
* In his presentation at the ThousandEyes Connect event in London, Adam Litman, the Director of the Internet Center of Excellence at Refinitiv, discusses how Refinitiv uses ThousandEyes to help measure cloud performance as it migrates services to the cloud. To see the presentation, check out [Delivering Predictable Financial Services Applications Over the Internet with Refinitiv](https://blog.thousandeyes.com/delivering-predictable-financial-services-applications-refinitiv/).

## New Cloud Agents

We've added new cloud agent locations for Mobile providers:

* Chicago
* Dallas
* Los Angeles
* New York
* San Jose

  Each location covers one of the following providers:

* AT&T Mobile
* T-Mobile
* Verizon Mobile

  And now for the release details.

## New Features and Enhancements

* Scripts for the new transaction tests now support an authentication module for generating TOTP two-factor authentication secrets based on a credential.
* The upper bound on the size of a file download test now defaults to 500MB, rather than 10MB.

## Bug Fixes

The following issues have been fixed in this release:

* An error occurred when users edited an existing test that resulted in the Run Once option failing due to an issue in the test configuration.
* An error that resulted in tests’ filter options not being visible in public snapshots.
* An issue causing endpoint filters to be hidden in a multi-metric widget.
* An issue caused by conflicting permissions resulted in data failing to load in report widgets used in dashboards. Users without the View Report permission can now load data for Report widgets in a dashboard.
* Endpoint Agents running on MacOS 10.15 systems now populate Network Access Layer wireless data correctly.
* An error in ordering when Transaction tests results were sorted by “Transaction Time” or “Errors” in the Table tab has been corrected.
* Screenshot icons are no longer half-hidden when they happen near or at the end of a Transaction script.

## Questions and Comments

Got feedback for us? [Send us an email](mailto:support@thousandeyes.com?subject=2019-12-10+Release+Update)!

