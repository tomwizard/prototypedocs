# Release Notes: 2015-09-16

After taking a break over the US Labor day holiday, our development team has been working on some fun new features.  Check out the list below, and send us any questions you might have - we're always happy to answer.

## Transaction view

Two updates to the transaction view:

### Timing breakdown becomes its own tab

We've moved the Timing breakdown section from the summary section in the map view into its own tab.  Certain customers had very long and comprehensive transactions, and breaking it into a separate tab allows the section to grow without materially impacting other content in the view.

IMAGE MISSING

IMAGE MISSING

### Waterfall viewer optimized for long transactions

We've also optimized user flow for reviewing waterfall data.  In the legacy view, users would see each page visited shown as an individual waterfall, and when multiple pages are visited over the course of a transaction, each waterfall is appended to the bottom of the page, making the view slower to load when large numbers of pages are accessed over the course of a transaction.  We've optimized this process to allow the user to quickly navigate between pages visited through the course of the transaction, or to show multiple pages at once.  To quickly learn how to use the new waterfall viewer, check out the image below.  The numbered elements in the image correspond to the numbered elements below.

IMAGE MISSING

1. The page title is shown, along with the URL of the page accessed.
2. To change the context of the waterfall to show a single page, click the page number from the banner, which shows the time spent per page in the entire transaction.
3. Along with \#4, change the bounds of the scrubber to control the content shown in the waterfall.  Pull the left boundary to the right, and the right boundary to the left.
4. See \#3 above.  In the example above, we're showing all four pages worth of data.
5. Use the Left, Right and "Show All" buttons to change the context of what is being shown.  Where a single page is selected, the left button will change the context of the selection to the previous page in the transaction.

By default, the transaction will show each page visited starting with the start step and ending with the end step, as defined in the transaction script.  If a single page is selected, that page's DOM and Page Load times will be shown as normal using the red and blue vertical bars transiting the waterfall.  If the content being shown transits multiple pages, the DOM and Page Load times will not be shown.

For more information on using the Transactions view, see [this knowledge base article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmnKAC).

## Reporting

We've added a few more measures to reporting.  We've added the ability to use Minimum, Maximum and Standard Deviation measures in reports.  We've also added HTTP redirect time to the list of available metrics.  See [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS) for more information on using ThousandEyes reporting.

## Bugs fixed

As with any release, we've fixed a few bugs.

* HTTP Server data is now available for page load tests.  Prior to this update, running a request to https://api.thousandeyes.com/web/http-server/{testId} would return a bad request response
* Users accessing the test settings page without the "Accept inbound live shares" permission assigned to their role would see a "not authorized" popup
* Corrected a minor memory leak relating to logging on the agent
* Renamed "Edit snapshots sent to all users in account group" permission to "Edit snapshots for all users in account group"
* Interface groups are now enabled by default in the Path Visualization view
* Corrected a date rendering issue for scheduled notifications, whereby dates would appear as though they were in the 1970s.
* Fixed an issue which prevented users in certain roles from accessing their API token from the profile tab of the Account Settings view

## Questions, comments?

We still like hearing from you! Drop us a line at [support@thousandeyes.com](mailto:support@thousandeyes.com?subject=2015-09-15+Update) and let us know what you think.

