# Release Notes: 2017-03-29

A reminder as gentle as an April shower:

IMAGE MISSING

The next ThousandEyes Connect event will be held in Bellevue, Washington, on April 20th, 2017.  Still time to [save yourself a spot](http://www.thousandeyes.com/events/connect).

The third article by Young Xu in her series on application and network monitoring in China, [Monitoring DNS in China](https://blog.thousandeyes.com/monitoring-dns-in-china/), is available on the ThousandEyes Blog.

## Enhancements

**Tests**

Instant Tests now provide the RTP Stream, Agent to Agent and Voice Call \(available to Beta users\) test types, which were the only test types not previously available as Instant Tests.  Also, in the [March 2nd release](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnwuCAC), we added the capability to switch test type in the middle of creating a new test, and configuration information already entered will be preserved.  We now allow this switch with preservation when doing an Instant Test with the **Run Now** link from the Views of any test. Additionally, we've changed the Instant Test's **Run Now** link in the **+ Add New Tests** form and when editing existing tests into a **Run Once** button, in order to better highlight the feature.

**Enterprise Agent**

In the [February16th release](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CntvCAC), we added the capability to unlock a Virtual Appliance if customers required \(unsupported\) modifications to the underlying Linux operating system.  We now show unlocked status in the General Info section of an unlocked Agent, in the Enterprise Agents page:

IMAGE MISSING

  
**Endpoint Agent**

 The Mac OS X installer for Endpoint Agent can now be used to perform updates to an existing Endpoint Agent installation.

**API**

Path MTU discovery and TCP maximum segment size \(MSS\) information are now available from the /path-vis endpoint in the API, for those test types that have Network measurements.

**Other**

We've standardized the look and feel of creation and duplication actions in Reports and in Dashboards, making for a simpler, more consistent user experience.

## Bug fixes

* Fixed an edge case where Instant Tests could trigger an Alert Rule.
* A pop-up error message indicating "Invalid URL parameters" no longer appears when clicking links in an Alert Grid widget on a Dashboard.
* Fixed an issue that caused BrowserBot to fail to start for Page Load tests on CentOS 7 Enterprise Agents.
* Fixed an issue that prevented creation of the browserbot group when installing the Enterprise Agent package on Red Hat or CentOS.
* Fixed an issue that prevented removal of the te-browserbot package via  `yum` on Red Hat and CentOS Enterprise Agents.

## Questions and comments?

 As always, we'd love to hear from you.  Whether you want to throw us some sunshine or rain on our parade, [drop us a note](mailto:support@thousandeyes.com?subject=Release+Notes+2017-02-16).

