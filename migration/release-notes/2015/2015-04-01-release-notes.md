# Release Notes: 2015-04-01

No jokes, but it's April Fool's day!  Check out the notes below, and let us know if you have any questions!

## Custom Headers on Browserbot tests

We've added the ability to add custom headers to Page Load and Transaction Tests in this release.  Previously available only on HTTP Server tests, users can now modify the advanced settings of Page Load and Transaction tests, in order to modify headers of the request.

Set your custom headers using the Advanced Settings tab of the test's settings, under the HTTP Request heading:

IMAGE MISSING

It's important to note that the custom header is only set on the main page request \(for each main page request in a transaction\), but not in components subsequently loaded each page \(including iFrame requests\).  We recommend setting the option to show HTTP headers in the event that there is an adverse impact on content rendering.

## Alert Suppression Windows: set in your own time

We introduced Alert Suppression Windows a few weeks back: this feature allows users to suppress alerts during a fixed period of time, which can be either a single point in time or scheduled on a recurring basis.  We released just before daylight savings time kicked in, and realized: hey, what If I just want maintenance to occur every other Tuesday, at 6pm local time, instead of adjusting time relative to UTC when the clock changes?

With tonight's release, you can now set your Alert Suppression Window to be based on a specific time zone's time.  The system will default to UTC, but simply select your time zone, and save your Alert Suppression Window.  The system will maintain the setting relative to your local time zone, rather than shifting based on UTC settings.

IMAGE MISSING

This is our first - but certainly not our last - step into timezone support.  Stay tuned for more :\)

## Role-Based Access Control \(RBAC\) changes

As the RBAC system continues to mature, we've made a few minor changes to the permissions in the system.  These are detailed below:

* We've changed the _View Account Groups_ permission label to _View Account Groups Settings_, and made this permission a management permission.  This permission controls whether or not users can see the Account Groups section of the Account Settings page.  If a member of your organization had created a custom role including this permission, that role will now reflect having management permissions.
* Bug fix which prevented users assigned to multiple accounts from changing their login Account Group
* Bug fix which prevented deletion of an empty account group

## Agent changes

### Virtual appliance changes

We've made some minor tweaks to the Virtual Appliance interface:

* The hyperlink shown to look up your account token in the setup wizard now points to the Add Agent page with the account token preselected.  Prior to this change, the hyperlink would take users to the account settings page.
* We've corrected a form validation issue on the network settings page of the setup wizard, which would prevent data being entered into the proxy information fields
* Effective in tonight's release, the agent will now check for Virtual Appliance package updates hourly.  Prior to this update, updates were fetched daily.

### End of support for Ubuntu Server 10.04 LTS

As previously announced, we'll be officially ending support for Ubuntu Server 10.04 LTS on April 14, 2015.  Customers running this version of Ubuntu have been warned and offered support in migration to a new version of Linux.  If your organization is running Ubuntu 10.04, and needs guidance in getting upgraded to either version 12.04 or 14.04 LTS, contact our Customer Success organization by emailing support@thousandeyes.com for assistance.

### End of support for Debian 6

We've updated our installers to prevent installation on Debian 6 systems.  Existing systems running Debian 6 will continue to be supported through the end of May, but will no longer be updated after tonight's release.  We plan on releasing an update in the immediate future which will support Debian 7.

## Special maintenance notification 4/15/2015

We're advertising a 90 minute maintenance window for April 15, 2015 lasting from 0130 UTC through 0300 UTC.  During this maintenance window, we will be performing extensive network maintenance at our primary datacenter.

## Happy Easter \(EU office closed\)

Happy Easter to all those who celebrate the holiday.  Our EU-based team will be on vacation on Friday, April 3rd and Monday, April 6th, celebrating Easter.  Our offices will maintain US hours and be open from 9am through 6pm PDT.

## Send us your feedback

If you've got something interesting to say about these release notes, a feature covered here, or just want to say hi, please feel free to [contact us.](mailto:support@thousandeyes.com?subject=Release+Notes+2015-03-04)

