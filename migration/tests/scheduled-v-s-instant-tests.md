# Scheduled v/s instant tests

ThousandEyes offers tests in Scheduled and Instant forms.

## Scheduled Test

 A Scheduled test will perform measurements periodically and visualize the results for the particular test round. A test round is one measurement cycle. Periodicity of test rounds is a user-configurable variable that can be selected and updated from the test configuration window by changing Interval. All [Cloud and Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent) tests are available in Scheduled test forms. [Endpoint Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpWKAS_Quick-Guide-on-Endpoint-Agent) support Web HTTP Server and Agent to Server test in [Scheduled test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Q11WCAS_Creating-scheduled-tests-on-Endpoint-Agents) forms. A scheduled test round is similar to an instant test round fo all tests except Page load and Transaction tests. For these two test types a scheduled version records a screenshot only if the test fails, while instant tests always record a screenshot.

## Instant Test

 Unlike the scheduled counterpart, an **instant test performs the measurement only once**. The visualization of collected instant test results is using the same views as scheduled tests, keeping the user experience uniform and simple. Changes can be made to an existing test and be run in an Instant form. The ThousandEyes Alerts feature is not available for instant tests. The following article provides guidance with Instant tests: [Working with Instant Tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnaUCAS_How-to-use-Instant-Tests).

**Note: BGP and DNS+ tests cannot be run in instant forms.**

## Creating a new Test

 Go to [Cloud & Enterprise Agents &gt; Test Settings](https://app.thousandeyes.com/settings/tests/?tab=settings) and click **Add New Test**. Complete the required test configuration as per the [Working with Test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn7KAC_Working-with-Test-settings) article.

IMAGE MISSING

1. Clicking the **Run Once** button will preserve the current test configuration window and run an instant test in a new tab.
2. Clicking the **Create New Test** button will close the test configuration window and start running a scheduled test with configured settings. 

### Running an existing test in instant form

IMAGE MISSING

1. Click **Run Now** in the existing test views. 
2. Click **Without changes** to run an instant test with existing test settings.
3. Clicking the **With changes** option will open up a test configuration pop as below. Changes can be done here and click **Run Now** to run an instant test with these configurations.  IMAGE MISSING

### Rerun an instant test 

 Click **Run Again**\(\#1\) to re-run the existing instant test.

IMAGE MISSING

## Related Articles

* To know more on how to share your results see [Sharing Test Data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data) article. 
* [How long does ThousandEyes retain customer data?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn0KAC_How-long-does-ThousandEyes-retain-customer-data) article explains the duration for which test data is preserved.

