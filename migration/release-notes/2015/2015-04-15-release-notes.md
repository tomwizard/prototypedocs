# Release Notes: 2015-04-15

For those of you in the United States, Happy Tax Day! Hope you're spending your well-earned refund checks on more monitoring for your critical infrastructure.  We've been busy on our end this past release: we've rearchitected our datacenter network, and made a number of changes in our databases that will improve the efficiency of our code. In addition, we've hit some major milestones we'd like to share with you from a feature perspective...

## Time zone support

By popular demand \(seriously, our \#1 most requested feature of all time\), we've introduced support to show results in your local time zone. Users can select their local time zone, which is detected based on locale settings - and users with management permissions can set defaults for their organization. Emails from the system will be sent in the organization's default time zone.

IMAGE MISSING

We've published an article that outlines time zone selection and support [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmSKAS).

## New cloud agent locations

We've added cloud agents in the following locations:

* Houston, Texas
* Maidstone, United Kingdom
* Coventry, United Kingdom
* Coventry, United Kingdom \(IPv6\)

These agents are immediately available to paying customers.  Please note that access to these agents is not included in trial subscriptions.

## Usage calculator

Now available in the Settings &gt; Account &gt; Usage tab, the usage calculator will help customers calculate the cost of each test, and explore the impact of modifying the configuration of tests on their pricing.

## Linux distribution support

We've added support for Red Hat Enterprise Linux 7, CentOS 7, Oracle Linux 7, and Debian 7.

As a part of this change, support for Debian 6 and Ubuntu Server 10.04 LTS has been removed from the product, and our repositories have been removed for those distributions.

## Reporting

We've made some enhancements to the query performance of underlying data gathered when reporting on BGP metrics. This should result in an appreciable improvement in reporting on path changes and reachability in the new reports interface.

## BGP peering

Our aggregation server was upgraded, to allow it to handle more client connections and reduce the occurrence of flapping. Customers using the BGP Private Peering feature of our product will have noticed connectivity issues between their routers and our aggregation server during our maintenance window between 2015-04-15 01:00 and 2015-04-15 02:30 UTC.

## API

We've updated our permission model to allow users who are assigned to multiple account groups to access the accounts endpoint of the ThousandEyes API, as well as change account context on API calls.

## We'd love to hear from you

Whether you've got something to say about tonight's release, or just want to say hello - send us your questions or comments at any time.

