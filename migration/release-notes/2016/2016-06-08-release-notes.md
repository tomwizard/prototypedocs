# Release Notes: 2016-06-08

As always, our product marketing team has been busy blogging about interesting happenings in the world of networking.  On deck this week are pieces from Archana Kesavan covering [Network Visibility in NAT Environments](https://blog.thousandeyes.com/network-visibility-nat-environments/), and [Network Visibility for Reverse Path](https://blog.thousandeyes.com/network-visibility-for-the-reverse-path/) of connections - two new features exposed by our Agent to Agent test capability, released last month.

In addition, we've got a great summary and video for Ivan Shepherd \(leader of the Network and Technical Security team at AIM Specialty Health\) presenting at our ThousandEyes Connect NYC event last month.  In this piece, he talks about [Visibility into Service Delivery for Telecommuters at AIM Specialty Health](https://blog.thousandeyes.com/visibility-telecommuter-services-aim-speciality-health/)

Without further ado, let's get to the updates for this week's release!

## Reporting

### New widget: Box & Whiskers

We've released a new reporting widget, called a Box & Whiskers chart. This chart plots 5 data points per time series value, plotting minimum, maximum, median, and first quartile \(25th percentile\) and third quartile \(75th percentile\) values, all on the same chart.  A sample of a Box & Whiskers report widget, reporting on HTTP Throughput can be found below:

IMAGE MISSING

Good for representing multiple metrics in a single chart, this shows minimum, maximum and spread data, with emphasis on the middle quartile of data. Add this widget to your reports by dragging in the icon that looks like this:  IMAGE MISSING

### Increased label column width

Coming from customer feedback, we've increased the width of the leftmost column in table widgets, and the label area in bar charts, to accommodate longer test names, when tests are aggregated by user-entered fields.

IMAGE MISSING

IMAGE MISSING

As always, refer to our [KB Article on Working with Reports](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS) for more information!

## Agent settings

We've changed the look & feel of the Agent Settings page, adding a set of tabs representing various options on the agent.

IMAGE MISSING

Under the **Basic Configuration** tab, you'll find the agent name, notifications, account groups and tests configuration options.  
Under the **Advanced Settings** tab, you'll find the "Behind a NAT" setting, as well as the "Target for Tests" option.    
Under the **Agent Statistics** tab, you'll find charts representing the historical usage of the agent, broken down on a task type basis.

We've also added the agent's primary account group \(the account group which owns the agent\) to the general info tab on the agent settings view, and made the primary account group a searchable field in the agent settings page.

##  User-Agent string changes

In tonight's release, our tests will retire the classic ThousandEyes default User-Agent string.

Web transaction and Page Load tests will supply the user-agent of the browser and operating system running the Browserbot component.  This will change over time as we continue to update the Browserbot component, and underlying Chromium distribution.

* **Ubuntu \(all versions\)**: Mozilla/5.0 \(X11; Linux x86\_64\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/49.0.2623.87 Safari/537.36
* **Red Hat Enterprise Linux/CentOS 6.x:** Mozilla/5.0 \(X11; Linux x86\_64\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/40.0.2214.115 Safari/537.36
* **Red Hat Enterprise Linux/CentOS 7.x:** Mozilla/5.0 \(X11; Linux x86\_64\) AppleWebKit/537.36 \(KHTML, like Gecko\) Chrome/49.0.2623.87 Safari/537.36

HTTP Server tests will run with a default User-Agent string of curl/7.48.0-DEV \(cURL's default behavior\), which will also change over time as we update this component.

Users can always override the User-Agent string used by their tests by modifying the User-Agent setting in the Test's advanced settings.

IMAGE MISSING

For users wishing to filter ThousandEyes traffic from ThousandEyes should do so based on the presence of the X-ThousandEyes-Agent header.  See [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnyKAC) for more details.

## \(Voice\) RTP Stream test updates

Users can now run RTP Stream tests on a 2-minute interval. In addition, we've made the duration of the test configurable. Users can now run RTP stream tests for durations of between 5 and 30 seconds.

##  Email styling

We've updated the styling of all outbound emails coming from the ThousandEyes platform. No major changes from a content perspective, but they'll look a lot nicer.

##  Bugs squashed

Here is a list of bugs corrected in tonight's release:

* We've corrected a problem where new organizations weren't provisioned with the "View sensitive data in web transaction scripts" permission in the built-in Organization Admin and Account Admin roles. This permission has been added to affected roles in all accounts.  Users who have created custom roles will need to manually add the permission to their roles as required.
* We've corrected a problem that could cause tests to lose their alert rule bindings when a Private BGP monitor being used on those tests was disabled.
* Webhooks triggered by alert notifications now contain the ruleId field, consistent with documentation.  

##  API

We've made some updates to the API as well.

### Version 5

* Added errorDetails field to the /net/metrics endpoint. This field was previously being omitted.
* We've added countryId to the /net/metrics endpoint, consistent with documentation.

### Version 6

* Added errorDetails field to the /net/metrics endpoint. This field was previously being omitted.
* Added countryId to the /net/metrics endpoint, consistent with documentation.
* Clarified documentation on use of the /net/metrics endpoint for bidirectional Agent-to-Agent tests. When querying this endpoint, the default direction will be shown - if a test is a bidirectional test, the aggregate bidirectional data is shown. If the test is a unidirectional test, then that direction will be shown. Direction information can be overridden for applicable tests by using the direction=\[FROM\_TARGET\|TO\_TARGET\|BIDIRECTIONAL\] parameter.

