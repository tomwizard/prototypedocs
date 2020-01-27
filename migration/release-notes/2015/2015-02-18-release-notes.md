# Release Notes: 2015-02-18

One of the biggest customer requests to our team - especially on large accounts - has been the ability to define user permissions in the system on a granular basis.... our team has been working long and hard on this task, and we're ready to release....

## New permissions model: "Role-Based Access Control"

The internal code name for the granular permissions project is the aptly named "Role Based Access Control" \(RBAC\).  We've implemented the RBAC model for user and user group management.  RBAC provides two principal benefits: First, RBAC eliminates the hierarchical relationships between users, accounts and organizations; Under RBAC, users may belong to more than one Account Group. Second, RBAC provides configurability of permissions that were previously fixed within the three predefined roles. With RBAC, you can create Roles for users which will allow them to do everything that they need to do - and no more.  

Our engineering team has worked hard to minimize disruption to all users.  Organizations who are happy with our built-in roles -  and don't want to make any changes - don't need to do anything: we've created the starting elements of the system using the traditional Organization Admin, Account Admin and Regular User roles, to use when adding new users to the system.  If you'd like to learn more about defining your own roles, and leveraging this more granular set of permissions, check out this knowledge base article for more details: https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnLKAS

Once you've read through the article on RBAC, [let us know](mailto:support@thousandeyes.com?subject=RBAC+Questions) if you have any questions and we'll be happy to answer.  We'll be making more information available in our knowledge base as we receive questions and comments from our user community.

## Enterprise agent changes

### Keep browser cache between tests

A new option is available for Enterprise agents only, which allows a user to toggle whether or not the browser maintains a browser cache.  This option \(newly introduced in tonight's release\) will allow page load and transaction test execution to cache objects, such that future rounds using the same cached objects take less time to execute \(and more accurately reflect user experience\).

IMAGE MISSING

### Agent utilization calculations

As we work on increasing the number of concurrent tests that agents can run, we've made some changes to the task queueing and execution model.  For the most part, this won't change anything from the perspective of a user, but it does change how utilization is calculated.  We've consolidated the separate queues for HTTP Server, DNS and Network tests to a single queue, and done the same for Page load and Transaction tests.  These new utilization queues can be seen by opening the Agent Settings page, selecting an agent, and checking the Agent Utilization charts shown in the lower right hand corner of the expanded section.

IMAGE MISSING

##  Reports

The new version of reports has been made available to all customers during this release.  As we work to transition from the legacy report system to the new version, members of our Customer Success organization may be in contact to help your organization transition.  Organizations not using the legacy version of reports have been moved entirely to the new system.

If you'd like assistance moving over to the fancy new \(and much more flexible\) reports system, don't hesitate to [send us an email](mailto:support@thousandeyes.com?subject=Reports+help): we're always happy to help.

We've also added user and account group default options, which will allow a user to set a report as their own personal default, or an administrator to set a default for the account group.  These options area available when clicking the Add/Manage widgets button in the reports interface.

IMAGE MISSING

## Dashboard changes

### Enterprise Agent Status widget

We've added an option to the Enterprise Agent Status dashboard widget to allow users to select which agents are shown in the widget: all agents shared with your current account group, or only agents owned by your account group.  Prior to this change, only enterprise agents owned by the user's account group would be shown.  Users can make this change by modifying the settings of the widget, and selecting either Owned Agents \(default option\), or All Assigned Agents.

IMAGE MISSING

## Cloud agent changes

We've removed the Shanghai, China \(China Netcom\) agent from our list of available agents due to instability concerns.  For customers who were using this agent, we have replaced it with another cloud agent based in Shanghai, which does not exhibit these instability issues.  

## Send us feedback

Thanks for reading all the way through.  We love feedback in all forms, from superlative to constructive.... [Send us a note](mailto:support@thousandeyes.com?subject=Feb+18+2015+Release+Comment) and let us know how the team is doing, to ask a question, or even just to say hi. 

