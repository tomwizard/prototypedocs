# Release Notes: 2015-03-04

Pheew! With role-based access control in the bag \(see our release notes from February 18\), we're keeping the new feature train rolling with Alert suppression windows.  That, and a few other changes make this a release that you'll want to pay attention to.

## Alert suppression windows

Ever have planned maintenance, but get a flood of alerts when you're working on your site? We have too. Nobody likes being annoyed with notifications when there's something you're actively working.  Effective this week, you can create alert suppression windows, to coincide with planned maintenance. This feature will allow the system to suppress alerts for tests which meet alerting criteria during a planned outage.

To manage Alert Suppression Windows, navigate to Settings &gt; Alert Suppression.

Using this feature is simple: create a suppression window, and assign it to specific tests. You can even create recurring windows, to handle planned maintenance that occurs on a regular basis. Each test whose results meet alerting conditions during an alert suppression window will not trigger an alert until the window has closed.

IMAGE MISSING

While a suppression window is active, when viewing tests to which this alert suppression window is assigned, users will see a blue bar on the alerting timeline, showing the name of the window. 

IMAGE MISSING

For more information, check out [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmYKAS) which discusses how to use the Alert Suppression Window feature of the ThousandEyes platform.

## Creating multiple users at once

As a minor feature enhancement to the Role-Based Access Control [release on February 18](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmlgKAC), we've added the ability to add multiple users in a single move. To add multiple users in a given role, simply paste a comma-separated list of email addresses into the emails field of the add new users interface. Once the new users field loses focus, the entry will be parsed and will create a new user for each address entered.

## Agent changes

### Virtual appliance compatibility

We've updated the format of our virtual appliance for Microsoft Hyper-V servers. Prior to this update, it was not possible to import the virtual appliance on Windows Server 2012 R2 or Windows 8.1 destinations.  

### SSL certificate verification handling

We've updated the process we use to handle verification of SSL certificates. This was due to a reported increase in time required to verify certificates on agents that were reporting high utilization values. We expect this change to be transparent to end users.

### End of installation support for Ubuntu 10.04

Leading up to end of life of the popular Ubuntu Lucid \(coming in April\), we have removed the ability to install a ThousandEyes Enterprise Agent on Ubuntu 10.04. While we will still support Ubuntu 10.04 through end of life for the operating system, we have introduced measures which will prevent installation on the near end of life operating system.

Our Customer Success team will contact organization administrators running Enterprise Agents on this version of the operating system beginning this week to coordinate replacement of the agent with a supported operating system.

## API

Tonight, we release version 5 of the ThousandEyes API. Per our published change policy, the clock begins ticking before version 5 becomes the default version of the API called, when targeting an endpoint without a version.

There are a number of changes made to the API, which can be found on the Change Summary of the [ThousandEyes Developer Reference](http://developer.thousandeyes.com/) site. Please note that each version of the API will show different change summaries, so be sure to target the appropriate version. Version 5's change summary can be found here: http://developer.thousandeyes.com/v5/\#/changesummary

We'll begin reaching out to organizations using versions 2 and 3 of the API over the course of the next few weeks to help you manage the transition.

## We can't get enough feedback

If you've got something interesting to say about these release notes, a feature covered here, or just want to say hi, please feel free to [contact us.](mailto:support@thousandeyes.com?subject=Release+Notes+2015-03-04)

