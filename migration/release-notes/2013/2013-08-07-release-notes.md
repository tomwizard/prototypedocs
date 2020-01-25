# Release Notes: 2013-08-07

Well, it's the beginning of our eighth month of the year, and in keeping with our history of great new features, we've got some great stuff to tell you about today.

## Bandwidth Measurements

In tonight's release, we're enabling a feature to enable bandwidth measurements for network tests.  Available from Enterprise Agents only, a test with bandwidth measurements enabled will attempt to measure the maximum size of the end-to-end connection between the agent and the test target, and estimate the percentage of the available bandwidth.  We've recently published a blog post on the theory behind bandwidth estimation techniques -- check out these links for more information: [A Very Simple Model for TCP Throughput](http://blog.thousandeyes.com/a-very-simple-model-for-tcp-throughput/), and [Caveats of Traditional Network Tools, Part II](http://blog.thousandeyes.com/caveats-of-traditional-network-tools-iperf/).

IMAGE MISSING

To enable bandwidth measurements on a test, check the _enable bandwidth measurements_ checkbox on any test that includes network measurements.  Once the test begins collecting data, a fourth metric becomes available on the End-to-End Metrics view of a network test, showing results for the following metrics:

* _**Capacity \(Mbps\)**_ - an estimate of the maximum bottleneck capacity between the agent and the target
* _**Available Bandwidth \(Mbps\)**_ - an estimate of the bandwidth available on the connection
* _**Available Bandwidth \(%\)**_ -  of the percentage of bandwidth capacity available, calculated as \(estimated\) _Available Bandwidth_ / _Capacity_.

When the bandwidth metric is selected, the timeline shows the amount of available bandwidth, allowing users to identify times where total capacity, either for a single agent - or for the entire test - was constrained.

## Configure your own dashboard

We've introduced a new configurable dashboard in this release, which allows users to change the behavior of the dashboard page. This release allows users to choose which tests to show on the dashboard page, and facilitates grouping of tests. This is our first implementation of user controllable test grouping, and the first of many dashboard visualization enhancements we're working on.

IMAGE MISSING

To control the grouping, select the IMAGE MISSING link shown in the upper right corner of a test group. This opens a dialog that allows modification of the test group; users can choose which tests to include by searching based on test name, test type, or test ID, using the familiar boolean search interface found elsewhere in the ThousandEyes platform.

IMAGE MISSING

All of this information is accessible and manageable via the dashboard settings link, found in the upper right corner of the page. Here, users can configure multiple test groups which correspond to the criteria specified in the widget settings. Reposition your widgets In addition to creating new test groups, users can reposition the dashboard elements on the page, to customize their dashboard as required.

IMAGE MISSING

## Mini-Dashboard for Live Shares

We've added a new section to the Mini-Dashboard \(found on the left hand side of the page\) for live share notifications.  The new Mini-Dashboard, shown using a paperclip icon, will show notifications that a Live Share is pending your acceptance.  Clicking the accept button in the Mini-Dashboard has the same effect of clicking the verification email from outside ThousandEyes.

IMAGE MISSING

## Alerting changes

We've made some changes to our alert rules infrastructure this release. Prior to this release, the alert rules named "_Default {test type} Alert Rule_" were read-only, and were selected by default when the 'enable alerts' checkbox was checked.

Beginning with this release, users can change which alert rule is designated as a default alert rule for each alert type, and can modify the _"Default {test type} Alert Rule"_ rules.   Default rules are assigned automatically when the 'enable alerting' option gets checked for a test.  

To make changes to alerting, users must have Account Admin level permissions, and there are three rules which remain in place as of today's release:

* Each test type must have a default alert rule configured in the system.
* There can be only one default alert rule for each test type.
* The current default rule for a test type cannot be deleted.

To select a new default rule, check the **Default Rule** checkbox in the [Alert Settings](https://app.thousandeyes.com/alert-settings) page.  

IMAGE MISSING

Once a new alert rule is selected as default, it will be assigned to any new test created with alerting enabled \(including tests created using the ThousandEyes API\).  

## Transactions

As of this release, transaction scripts now accept foreign language content in text inputs.

IMAGE MISSING

Prior to this release, if a user used the agent settings page to change an agent to transaction test assignment, any text-based transaction inputs would be converted to asterisk characters.

**Important note**: we have audited our transaction database and manually updated all tests in the system to reflect prior transaction inputs, for tests which were affected by this issue. If you believe that one of your tests may currently be affected by this problem please contact the ThousandEyes Customer Success team by emailing support@thousandeyes.com and including the test name you believe is affected.

