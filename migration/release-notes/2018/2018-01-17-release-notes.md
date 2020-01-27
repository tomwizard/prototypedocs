# Release Notes: 2018-01-17

Welcome to the second release of the last two weeks. As mentioned in last week's Release Update, we're doing releases on back-to-back weeks, to kick off 2018 with a fast start!

In keeping with our recently introduced feature of 1-minute test intervals, our Director of Product Management, Nick Kephart, answers the question "How much data is enough," in his blog post [How Much Data is Enough? Tips on Selecting a Test Interval](https://blog.thousandeyes.com/tips-selecting-test-interval/). Practical advice for getting the most bang for the buck.

On to the details of the release.

## Public BGP Monitor changes

A "heads-up": in a release coming in the near future, we will be changing test behavior with respect to public BGP Monitors, in order to increase the number of public BGP Monitors. Currently, a test can be configured with any number of up to 38 public BGP Monitors. The change will remove individual selection in favor of selecting either all or none. Once the change is made, existing tests which were configured to use a subset of BGP Monitors will now be configured to use the full set.

Customers should review their configurations to determine if any tests use a subset of public BGP Monitors, particularly those tests which have Alert Rules for the BGP metrics. If a test with a subset of monitors has Alert Rules which can apply to all Monitors, then the change could cause unexpected alerts from newly added Monitors. If additional alerts are undesirable, consider changing the Alert Rule configuration to exclude Monitors which were previously excluded from the test itself.

## Virtual Appliance support for PAC files

Virtual Appliance Enterprise Agents including the ThousandEyes Physical Appliances\) now support selection of proxy server through PAC files, using the **Proxy Type** setting. The behavior of this feature is identical to the Linux package and Docker container Enterprise Agents, with the exception that a PAC file hosted on the Agent \(accessed by a URL using the file:// syntax\) will normally be restricted to locations on the file system which can be written by the thousandeyes user.  We suggest /home/thousandeyes as a location for PAC files. Avoid /tmp at all costs unless you want your  PAC file to disappear after reboot!

## Alert Rules

Two new metrics on which to alert:

* A Path Trace Alert Rule can now be configured to alert on DSCP value for Any Hop, Hop \# and Last Hop settings.
* An HTTP Server Alert Rule can now be configured to alert on Redirect Count.

## dynamicType Transaction test command

Transaction tests have a new command called **dynamicType**:

IMAGE MISSING

This command is similar to the standard **type** command, but instead of specifying static text in the Value field, we now permit a JavaScript expression, the results of which are provided to dynamicType via the JavaScript return statement.  The returned value must be a number or a string.

An example use case: the dynamicType command allows Transaction tests to navigate login mechanisms such as a security question chosen from a list of questions. A monitoring account could be given answers to security questions which are a sequence of characters or words chosen from a text element on the page with the security question. If a login page displayed a security question with the text of "What is your least favorite relative's name?" and the answer to each security question is the 4th word of the question, then the JavaScript in the Value field could extract the string "least" using the following:

| Command | Target | Value |
| :--- | :--- | :--- |
| dynamicType | //\*\[@id="securityQuestion\_responseText"\] | var myAnswer = document.evaluate\('//\*\[@id="securityQuestion"\]', document, null, XPathResult.FIRST\_ORDERED\_NODE\_TYPE, null\).singleNodeValue.innerText.split\(" "\);return myAnswer\[3\]; |

Note that the Value field is not currently obscured in the Test view or the test configuration, per the View sensitive data in web transaction scripts permission, as is the case with the standard **type** command. Also, please note that the **dynamicType** command is not yet supported for playback in the Transaction Recorder. Stay tuned for those features!

## Bug fixes & minor features

Here's the list of bug fixes and minor features in this week's release:

* Share this Snapshot link is no longer missing from the Reports Shapshots view.
* Stacked Bar Chart widgets now properly display the legent.
* When saving a Stacked Bar Chart widget as an image, the legend is now properly displayed.
* Fixed an issue in the Path Visualization view which could cause Device Layer information to be missing from tooltips.
* Fixed an issue with the Calculator that created some incorrect calculations for a limited number of organizations.
* Fixed an issue which resulted in incorrect metered Agent usage calculation for a limited number of organizations.

## Speculative execution vulnerabilities

 Our Operations and Information Security teams have been closely monitoring our infrastructure and the patches that are being made available to address the vulnerabilities known as Meltdown and Spectre.  Our initial statement can be found [here](https://app.thousandeyes.com/sfdc/community/home?communityTabId=Knowledge%20Base&communityObjectId=kA0440000009SQkCAM) \(authentication required\).  Watch that article for updates as we continue to make progress addressing these vulnerabilities.

## ​Questions, comments?

Got a question or a comment to share with us? [Send us an email](mailto:support@thousandeyes.com?subject=2018-01-17+Release+Update)!

