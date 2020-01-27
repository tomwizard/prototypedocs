# Release Notes: 2016-09-28

A quick announcement or two, before the details on tonight's release.  First, ThousandEyes Connect is back!

IMAGE MISSING

Join us in San Francisco on November 17th or New York \(date TBD\). Learn more and save your spot [here](https://www.thousandeyes.com/events/connect).

Also, check out our latest blog posts:

[Two New Integrations: Slack and HipChat](https://blog.thousandeyes.com/slack-hipchat-alert-integrations/)  
[Monitoring FTP Servers and File Transfer Performance](https://blog.thousandeyes.com/monitoring-ftp-servers/)  
[Comprehensive Alerting for Route Leaks and Hijackings](https://blog.thousandeyes.com/comprehensive-alerting-route-leaks-hijackings/)

Nick and Young are always hard at work to provide you with information on product features and interesting outages we've observed. Feel free to post feedback in the Comments section of the blog. Nick and Young would love to hear from you.  Now onto tonight's release...

## Reports

We've added a set of built-in reports to give you information that is commonly needed from the Reports function in ThousandEyes.  On the Reports page, when you click on the Reports selector, you'll see the following new reports:

IMAGE MISSING

These reports contain a number of widgets which provide a variety of data commonly needed for the type of test indicated in the report title.  You may find the report useful as-is for your own reporting needs, or the plethora of widgets may give you some ideas for creating your own reports.  Feel free to play with the widget configuration in the reports to see what pretty maps and graphs result.  Consider creating a new Account Group for this experimentation, since each of these reports works on a per-Account Group basis \("Reports Sandbox" would be a good choice for the name\).  You can share tests from other Account Groups to your new Account Group in order to provide data to populate the experimental Account Group's reports.

This release also upgrades the Map widget with the **One Map Per Test** option, similar to the **One Chart per Line** option in Time Series widgets, and corrects an issue with the Reports calculation of percentages in Stacked Chart widgets.

In addition, we've improved the performance of widget loads on the Dashboard. So load 'em up with widgets!

## Web Layer tests

For customers wishing to perform Web Layer tests in environments behind one or more proxy servers, we've introduced support for the JavaScript-based PAC file.  If your browsers use PAC files, now your Enterprise Agents can use your PAC file, too!  Or use your Enterprise Agent to compare performance of multiple proxies \(ping us here at the Customer Success Center ask for Michael's power-user trick to test multiple proxies with the same test target\).

To configure a PAC file, Linux package and Docker users can consult the instructions on the **Settings &gt; Enterprise Agents** page, then clicking the **+ Add New Agent** button and selecting the appropriate type of installation. Virtual Appliances will soon have support through the Appliance's web interface.  For now, if you need to configure a Virtual Appliance to use a PAC file, contact us at [support@thousandeyes.com](mailto:support@thousandeyes.com).

## General enhancements & fixes

* Tests can now be edited while disabled
* HTTP request method now shown in Waterfalls tab via tool-tip when mousing in **Object** column
* Test groups can now contain up to 60 tests
* API's /alerts endpoint correctly links to the Alerts page for BGP monitors
* Our \(nested\) two-script Linux package installation is now one script, and works on Linux systems which only use systemd to start services
* Agent auto-updates behind proxies are now more robust with regard to Python modules
* Fixed an issue allowing Live Shares of tests to be editable
* Fixed an issue with certain European characters used in passwords
* Slack notifications now correctly link back to Agent to Agent tests, and don't display "NO CALLBACK DEFINED"
* In Agent to Agent tests, the Target to Source tab is now clickable when showing the traceroute-style output in both directions
* Entering large numbers of kilobytes in the Limit Download Size of Web Layer tests no longer results in an error or doesn't save. \(Yes, you really can limit your test to the first gigabyte, now.  Have fun racing your link speed against the test timeout.  Graph the results with a report.  Send us the code for the Embedded Widget. We'll embed it in into a future blog post.\)
* Best for last: the current name is now selectable in the current display selector:  
  IMAGE MISSING

  Now you can create long test, dashboard or other names, without fear you'll have to type the name you've chosen.  But don't tell your co-workers that you can copy and paste from the selector.  Let your boss think you're just that fast and accurate a typist.

## Questions or comments?

Lover our new features?  Hate our Release Notes? Either way, we would love to hear from you! [Send a note](mailto:support@thousandeyes.com?subject=Hate%20your%20release%20notes%2020160928) to us and let us know.

