# Release Notes: 2014-06-26

### Release update 2014-06-26

This week's updates contain a few customer-requested features.  To request a feature of your own, use the "I wish this page would..." option at the bottom of the ThousandEyes interface, and let us know what you need!

IMAGE MISSING

[Let us know](mailto:support@thousandeyes.com?subject=2014-06-26%20Release%20Update) if you have any questions, we'd love to hear your feedback.

## Test Cloning!

We've added a Duplicate button to the test settings interface.  The button can be found on the lower left of the test settings interface, while a test is expanded.  Check out \#1 in the image below.  When clicked, the system will open a new test form with all options prepopulated based on the cloned test.

IMAGE MISSING

## Collect and show request/response headers

We've added the option to include request and response headers in page load and transaction tests.  The option can be found at the bottom of the HTTP Response section of the Advanced Settings tab for Page Load and Transaction tests.  Check the box to Include headers during data collection.

When reviewing the waterfall for test results for a test whose settings show the 'Include Headers' box checked, \(1\) hover over the object name in the waterfall, and \(2\) click the 'Click to view headers' link, per the image below:

IMAGE MISSING

This will open a dialog which shows the request and response headers for the object, in separate tabs:

IMAGE MISSING

## HTTP Server tests: new options

### 60-second timeout

In order to accommodate larger downloads, we've increased the maximum timeout on the HTTP Server test. Tests can now be configured to run with durations of 5 to 60 seconds.

### Limit Download Size

Found in the HTTP Response section of the Advanced Settings tab for an HTTP server test, you can now define the maximum number of bytes that an HTTP Server test will fetch.

IMAGE MISSING

This option is tremendously useful when you only need to validate HTTP throughput for a larger object; simply set the number of kb \(whole numbers only\) and save the test in order to decrease the running duration of your test, so that it fits into a smaller timeout.

## ThousandEyes recorder 

The ThousandEyes Recorder \(used for recording Selenium scripts, for use with ThousandEyes Web Transaction tests\) is now available from the Chrome store.  Click this [link](https://chrome.google.com/webstore/detail/thousandeyes-recorder/hnmekclmbdhoicblhbcloiemofnengnn) to access it, or search for ThousandEyes in the store.

IMAGE MISSING

This version is self-updating, and since it's from the Chrome store, won't be subject to limitations imposed by Chrome on extensions that are installed manually.  _**We strongly recommend that all customers who have installed the legacy ThousandEyes Recorder extension remove the legacy extension and install the latest version from the store.**_

To check which version you have installed, look for the "not from Chrome web store" comment below the extension's controls in the chrome://extensions page. 

IMAGE MISSING

Click the trash can to remove the extension, and install the new version from the store.

## API update

We've updated the API to accept HTTP Server and Page Load timeout values for test creation and update.  Check out the [ThousandEyes Developer Reference site](http://developer.thousandeyes.com/#/changesummary) for more information.

