# Working with Instant Tests

### Working with Instant Tests

The Instant Test feature can be used to troubleshoot problems without waiting for a scheduled test, or to validate a new test's configuration.  Before running the Instant Test, an existing test's configurations can be adjusted, such as adding new Agents or increasing timeout values. Instant Test results are presented in the same layouts as scheduled tests. Data can be saved for later review and shared with interested parties. All Test types are supported by Instant Tests with the following exceptions:

* Routing Layer/BGP

## Required permissions

 In order to run an Instant Test the user must be assigned to the **Regular User** role or be assigned to a role with the following permissions enabled:

1. One or more login permissions, such as Login via ThousandEyes login page or Login via Single Sign-On
2. View agents in account group
3. View tests

## Running an Instant Test

 An Instant Test can be initiated in a number of ways:

* From Test Settings using a new test
* From Test Settings using an existing test
* From the Test View

### From Test Settings using a new test

 When adding a new Test, you may wish to verify the configuration immediately, rather than waiting for the first scheduled round of data to be returned. Follow the below steps to run an Instant Test from the **Add New Test** form \(note only users assigned to a role with **Edit tests** permission enabled will have the option to **Create New Test**\):

1. Navigate to **Cloud & Enterprise Agents &gt; Test Settings**
2. Click the **Add New Test** button to display the form
3. Select the **Layer** and **Test Type**
4. Set the **Basic Configuration** and **Advance Settings.** For more information review [Working with Test settings](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC).
5. Select **Run Once** to run the Instant Test IMAGE MISSING

Note that for users assigned to the **Regular User** role or to a custom role without the **Edit tests** permission enabled an Instant Test can be run as follows:

1. Navigate to **Cloud & Enterprise Agents &gt; Test Settings**
2. Click the **Run Test** button to display the form
3. Select the **Layer** and **Test Type**
4. Set the **Basic Configuration** and **Advance Settings.** For more information review [Working with Test settings](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC).
5. Select **Run Test** to run the Instant Test IMAGE MISSING

### From Test Settings using an existing test

 When an existing test is display errors, you may wish to troubleshoot by running the test on demand, rather than waiting for the scheduled rounds of data.  Or you may want to try minor variations on an existing test without having to duplicate the test. Follow these steps to run an Instant Test using an existing test's configuration:

1. Navigate to the **Tests** page
2. Expand the Test settings for the test you wish to run
3. Modify the **Basic Configuration** and **Advance Settings,** if desired
4. Select **Run Once** to run the Instant Test

**Note:** When **Run Once** is selected, any modified configuration will be used only for the Instant Test unless the changes to the test settings are saved by clicking **Save**.

IMAGE MISSING

### From the Test View

 Similar to running from the Test Settings page, you may also run an Instant Test from viewing the results of an existing test. Follow these steps to run an Instant Test using an existing test's configuration from the Test View:

1. Navigate to **Cloud & Enterprise Agents &gt; Views** and select the name of the test
2. Click the **Run Now** button IMAGE MISSING
3. Select "Without changes" to run immediately, or select "With changes" and adjust test parameters then click the **Run Now** button

**Note:** Any modified configuration will be used only for the Instant Test, and the scheduled test settings will revert back to their original state.

IMAGE MISSING

## Viewing Instant Test results

 Once an Instant Test has completed, the Instant Test View appears. From this view, you may select individual Views and tabs, or re-run the test.

The information seen in this view is not retained permanently.  Data that you wish to retain can be saved using the **Save** or **Share** buttons before navigating away from this page.

1. **Run Again:** Run the configured Instant Test, creating another round of data
2. **Standard Views:** Based on the type of test, you will see the standard [ThousandEyes view layouts](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmgKAC)
3. **Test Round:** A round of data that represents one Instant Test run
4. **Round Timestamp:** The date and time the highlighted round was run
5. **Save Button:** Create a Saved Event to retain the Instant Test data.  For more information, see [Retaining data beyond the 90-day limit](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn3KAC).
6. **Share button:** Create a Share Link to share the Instant Test data.  For more information, see [Sharing Test Data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC). IMAGE MISSING

## Notes

1. Instant Tests will be assigned to the front of queue for their test type. If the Agent is currently performing another test that will need to completed before the Instant Test can start.
2. Results will be displayed as soon as they are available. Agents displaying No Data means that the test has not yet been completed.
3. Settings are not editable after the test has been initiated. If you wish to add an Agent, or change the target you must start a new Instant Test.

