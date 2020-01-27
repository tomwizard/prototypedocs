# Release Notes: 2014-01-22

### Release update 2014-01-22

This is our second release update for 2014.  This week, we're making ThousandEyes more ubiquitous, by providing command-line network utilities that run and gather data, in the same fashion as tests which are scheduled via the web.  Beyond this, we've got some cool updates in the area of customizing your experience with ThousandEyes, and some other updates to help you get the best experience possible with the platform.  Each section is laid out below; take a look and feel free to ask any questions you need via our community, at https://support.thousandeyes.com.

##   IMAGE MISSING A little bird told me...

You already know our official launch came with some help from our friends at Twitter, but beginning with this release, we've begun using Twitter to provide information regarding our maintenance notifications, as well as issues affecting our infrastructure.  Follow [@thousandeyesOps](http://twitter.com/thousandeyesops) for information on the operations side of the shop.

##  New Features & Enhancements

Drumroll please! Here's a quick taste of each of the new features releasing in tonight's release.

### Enhanced Dashboard Configuration

You can now configure the dashboards on your account by configuring _templates_.  The Dashboard Settings link at the top of the page has been replaced with a new template-based configuration.  To modify your dashboard configuration, you can select from pre-defined templates created by your account administration team, or create your own. 

IMAGE MISSING

1. To select a different dashboard, use the template selector \(\#1\).  All dashboards shared amongst your account, as well private templates you've created for yourself will be shown.
2. To edit a dashboard, click the Edit button.  This will open the Template settings dialog, with the template's settings already open - see the template settings dialog shown below.
3. To create a new dashboard, click the new button.  This will open the Template settings dialog, and allow you to design your own dashboard from scratch.

IMAGE MISSING

With the template settings dialog open, if you have permission to edit the template, you'll be able to change the name, as well as the widgets shown in the template.  Be careful, since all changes are live for all users using the template for their dashboard.  In cases where you do not have permission to edit the template, you'll see an option to Duplicate \(\#1 above\) the dashboard template, and create your own based on the one shown.  Instructions for the User default and Account default options can be found below \(\#3, \#4, respectively\)

IMAGE MISSING

While working with a new template, you can edit, using interface elements shown above:

1. This is the name of the template that will appear on the dashboard page.  When duplicating a previously created dashboard, the word "Copy" will be appended to the name.  
2. Check the **private** checkbox if you don't want your dashboard template to be shared with other users in your account.  Only non-private dashboards can be seen by other users in your account.
3. The **user default** checkbox indicates that it will be your user's default dashboard template \(the one that appears when the page is opened\).  You can still select another dashboard at any time by selecting one from the selector found on the dashboard page.  This only affects your user.
4. The **account default** checkbox indicates that this template will be used as a default for all users in the account.  User-selected defaults supersede account defaults.   Only users with Account Admin or Org Admin privileges can define a template as an account default.
5. You can drag instances of widgets from the widget list into the configuration.  
6. Once a widget is shown in the configuration, it can be configured depending on the usage requirements of the account.  To reposition a widget, drag it above or below another widget in the configuration.
7. Click the X button to remove a widget from the template configuration.

Once complete, click the close button, and your widget will be shown in the dashboard.

### CLI utilities released

We've released a suite of command-line interface utilities, as a part of the _te-agent-utils_ package, which can be used to work on diagnosis of network issues.  For more information on these CLI utilities, check out this [link](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmoAKAS).

### DNS Trace shows final query result

We've enhanced the output of DNS Domain Trace tests to return the final query response, even when a non-authoritative response is received.  Prior to this release, in the event that a DNS Domain Trace test did not receive an authoritative response, it would show a failure with no result.  We also show the mapping returned for the request in the details table shown below the map, to help identify domain names that are not resolving to the correct mapping.

With this addition, you can also configure alert rules to work with mapping based criteria - for example, Mapping is not in \(a list of mappings\).

### API field additions

* ruleId field now exposed in /alerts endpoint
* roundId field exposed in all test data endpoints

Check out the ThousandEyes Developer Reference site [here](http://developer.thousandeyes.com/).

### Enterprise Agent support for RHEL/CentOS 6.5

* We've added official support for Enterprise Agents running version 6.5 of Red Hat Enterprise Linux and CentOS.

## Bugs Squashed

And finally... with any release, we've resolved a few minor bugs:

* Agents weren't being shown in network alert data, using v3 of the ThousandEyes API.
* Bandwidth measurements were returning no data from agent locations running with less bandwidth
* Newark, NJ agents have been replaced with New York, NY agents

