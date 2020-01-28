# Release Notes: 2016-01-06

Happy New Year from the team at ThousandEyes!

Our marketing team spent some time between celebrating with their families and friends by writing up a blog post looking back on some of the top Internet outages of 2015. Check out Young Xu's post on the Top Internet Outages of 2015 on the [ThousandEyes Blog](http://blog.thousandeyes.com/), at [this link](https://blog.thousandeyes.com/top-internet-outages-2015/).

We have a relatively light release for you today - not much in the way of new features, however we've corrected a few bugs and are setting the stage for more exciting updates throughout the course of 2016.

## Widget settings dropdown

We’ve regrouped functions common to all Dashboard widgets and Report widgets \(Delete, Duplicate and Rename\) under a new “More Actions” menu, accessible via the  icon on each widget, to the right of the Settings \(gear\) icon. This saves clicking on the Add/Manage Widgets button — previously required to access duplication and deletion options. Additionally, the current Dashboard can now be deleted from the Dashboard Settings menu \(gear icon next to the Dashboard name selector\) in addition to the Edit, New and Duplicate menu option. As with those options, the new Delete option will affect the entire Dashboard, rather than a widget within the Dashboard.

For more information on working with Reports, refer to [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS).   
For more information on Customizing the Dashboard, refer to [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmcKAC).

##  Bugs fixed

With any software development process, an occasional bug manages to sneak along for the adrenalin-inducing release ride. They inevitably get squashed. Rest in pieces, bugs.

* **BGP billing**: we discovered a long-standing problem in usage calculation for standalone BGP tests, whereby the BGP tests were being billed at 1/24th the rate they should have been \(based on the data shown in the ThousandEyes calculator\). If your organization has a large number of BGP tests, it might be a good idea to review your usage following this week's release.
* **"Some parameters are incorrect" popup**: this feature, introduced in our last release of 2015, was introduced to let users know when they were trying to go to a URL that didn't make sense in the context of their account group. We've muted it somewhat.
* When changing an Enterprise Agent's location information, some users were encountering an error. We've corrected this.
* Finally, some customers have noticed additional invoices present in the billing tab. These came up as a part of a series of changes related to invoicing systems. This has been corrected, and the phantom invoices will no longer be seen.

## We love hearing from our customers

We sure do love hearing from our customers. If you set yourself an amazing new year's resolution, \(or even have a question or comment about our product\), let us know.

