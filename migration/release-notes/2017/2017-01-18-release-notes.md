# Release Notes: 2017-01-18

If you're in the London area, come and visit our UK team at UKNOF, taking place on January 19th, 2017.  Check out [https://www.uknof.org.uk](https://www.uknof.org.uk/) for more details!

## Cloud Agent expansion

 We've continued to expand our Cloud Agent presence in Canada by introducing two new locations in Ontario: Kitchener/Waterloo and Ottawa.  These Agents are immediately available to customers with paid subscriptions.

## Instant Tests

 We’ve revamped the Instant Tests feature to make it accessible from more locations in the application, and easier and more flexible to configure Instant Tests, based on configuration of existing scheduled tests. Moreover, Instant Tests now look and feel more like scheduled tests. You can now save and share data produced by Instant Tests.

IMAGE MISSING

Check out the Knowledge Base article [Working with Instant Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnaUCAS) for more information.

## Minor changes and features

* In the Endpoint Agent Session Details view, we've renamed the "Organization" column to "Network", and renamed the "Network" column to "Private Network", to more appropriately reflect the data being presented
* We've added VPN and proxy destinations to the quick links shown on the Endpoint Agent Path Visualization interface.
* We've increased the maximum Alert Rule expression length from 1024 characters to 7000.   

## Bugs

* We've corrected an issue that could cause number widgets used in reports to display an incorrect number when the "both directions" option is used while defining the widget.
* We've corrected a problem with the BGP sparkline chart of the tests dashboard widget which rendered aggregate reachability for both the target BGP prefix and any covered prefixes, when the "Include covered prefixes" option was used in test settings.  
* We've corrected an issue causing the cursor on a time series report widget to become out of sync with the mouse.
* We've fixed a problem that caused API access by regular users to the v6/reports/{reportId}/{widgetId} endpoint to be incorrectly rejected with a 401 status code.

## Enterprise Agents

 We've introduced a new username to the Enterprise Agent, which is used to run the BrowserBot component of the Agent.  This "browserbot" user will be automatically created upon update to the latest Agent version, and will be completely transparent to end users.  This update applies to all versions of the Enterprise Agent including Virtual and Physical Appliances, and package-based installations except Enterprise Agents running on CentOS/RHEL 6.x.

