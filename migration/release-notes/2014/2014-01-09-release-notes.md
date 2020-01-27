# Release Notes: 2014-01-09

### Release update 2014-01-09

We at ThousandEyes wish everybody continued prosperity in 2014.  This is our first release of this year, and we're looking forward to continuing the amazing pace of development that we went through in 2013.  The list below identifies a list of user-facing changes that went live in the product during our January 9, 2014 release.

As always, we're here to help.  If you have any questions, please let us know by emailing support@thousandeyes.com, or engaging our team using the online chat interface available from the Help & Support tab on the right of the ThousandEyes interface at any time.

## Live Sharing

We've made some usability changes to the Live Sharing feature of ThousandEyes, in order to make sharing your data simpler.

Live Sharing allows users of ThousandEyes to share a live view of a test with other users of ThousandEyes, allowing organizations to share results from their Enterprise Agents, with users in other accounts.  You can share data with other accounts within your organization \(for Organizations which have more than one account\), and with other organizations that are using ThousandEyes.

### Sharing inside your Organization

To share a test with another account inside your organization, simply click the **Share this Screen** link at the top of the view you're using.  A dialog will open.  Select the **Live Sharing** tab.  If your organization contains more than one account, you'll see two buttons: **Outside My Organization** and **Inside My Organization**.  Select the Inside my Organization option to show a list of accounts in your organization.

IMAGE MISSING

Once you've selected the account  you want to share your test data with, add a message \(optional\), and click the **Share** button.  This will initiate the share acceptance process, which requires that a user with Account Administrator privileges accept the share; An email is sent to all account admin level users in that account, and once accepted, the share will show up in the list of tests for members of that account, shown in the dashboard and main views with a paperclip icon next to the test name, to indicate that the test has been shared with that account.

IMAGE MISSING

Users will be directed to this tab when attempting to Live Share tests with other members of their team.

### Sharing outside your Organization

To share with another organization, you can either share using email, or registered domain.  Registered Domain sharing requires that organizations register and verify a domain using the **My Domains and Networks** option within the settings interface.  Once a domain is verified, the request will be forwarded to users with account administrator privileges in accounts where the domain is registered and verified.  Attempts to live share data with unverified domains will receive a response indicating that no valid recipient has been found.  Only one domain can be included at a time.

To share using email, simply enter the email address used by another user to log in to ThousandEyes.  Attempts to live share tests with other members of your organization will be directed to use the 'Inside my organization' tab.

Users may receive the following responses, based on information entered into the Live Sharing recipients field.  If the message is shown in orange, the attempt to share did not succeed.  If it is shown in green, then the share attempt was successful.

* Share request sent successfully. You will receive an email when it is accepted.
* No valid recipient found
* The specified email belongs to your account and already has access to this test.
* The specified email belongs to your organization. Use the 'Inside My Organization' tab.

Note that these changes apply only to the Live Sharing tab of the sharing interface.  The Snapshot and API Link tabs of the sharing interface have not been changed.

## Additional Screencasts

We've released three new Screencasts, available from the Help & Support menu found on the right side of the ThousandEyes interface.  New Videos are available in the following views:

* "Working with Web Tests"
  * HTTP Server, Page Load and Transaction views
* "Working with DNS Tests"
  * DNS Trace, DNS Server, DNSSEC views
* "Working with Network Tests"
  * End-to-End Metrics, Path Visualization, and BGP Route Visualization views

In some views, the Video is shown above your test results.  Once you've seen the video, it can be dismissed by using the X in the upper right corner of the Video frame. 

IMAGE MISSING

Instructional videos, along with other useful resources, are always accessible via the Help & Support tab on the right hand side of the page.

## API 

Organization Admin users can now change account context while using v3 of the ThousandEyes API, by specifying an aid= parameter on their queries.  Prior to making this change, users could only query the API in the context of their primary account.  With the introduction of the /accounts endpoint, which lists each account, Users with Organization Admin privileges can access any test in any account inside their organization.

Our developer reference site http://developer.thousandeyes.com has been updated to reflect changes made in tonight's release. 

