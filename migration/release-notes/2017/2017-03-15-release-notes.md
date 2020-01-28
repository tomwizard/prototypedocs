# Release Notes: 2017-03-15

ThousandEyes Connect in the Great Northwest!

IMAGE MISSING

Our next ThousandEyes Connect event will be held in Bellevue, Washington, on April 20th, 2017.  Swim on by, and hear some great speakers from Microsoft discuss how ThousandEyes makes their lives a little sunnier.  Learn more and save your spot [here](https://www.thousandeyes.com/events/connect).

Also, check out Young Xu's latest in her series blog posts on China, [Monitoring Application Delivery in China](https://blog.thousandeyes.com/monitoring-application-delivery-china/).

And with that... Welcome to tonight's release.

## Enterprise Agents

As noted in our March 2 release update, we are ending support for Virtual Appliances running on Ubuntu 12.04 LTS \(“Precise”\).  We’ve added a feature that will prevent any new Virtual Appliances from registering in the ThousandEyes platform if running Precise.  If a Precise-based Virtual Appliance attempts to register, the Agent's log will display the a message similar to:  

```text
2017-03-13 19:45:00.761 FATAL [b6adc740] [te] {} The agent's operating system is no longer supported. Please contact support@thousandeyes.com for assistance.
```

For more information, see our [end-of-life announcement](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnyqCAC).

## Voice Layer tests

With the upcoming release of SIP and Voice call testing, we’ve renamed the “Full Call” test type to “Voice Call”.

## Enhancements

* A change of wording: the “Both Directions” selection of the Path Trace Alert Rule’s **Direction** will now be called “Either Direction”, which better describes the functionality.
* Added an “Enabled tests” filter in the **Current Test** selector of the Views.  Click this filter to show only enabled tests, which will filter out Saved Events.
* Prefixes will now be sorted in the BGP View by both prefix and prefix length.

## Bug fixes

* Fixed an issue in certain accounts, in which creating a DNS Server test failed with an internal error
* When creating an Agent to Agent test with **Enable Throughput** checked, the position of the **Duration** slider for the throughput did not match the numeric value displayed beside the slider.
* When creating a multi-metric table widget for Endpoint Agent metrics, the **Filter** now displays Endpoint Agent-specific filter selections
* Fixed a bug that appeared in some cases of adding an Enterprise Agent Status widget to a Dashboard, which caused the progress indicator to spin indefinitely.
* Fixed a bug that could cause a location to be duplicated in an Endpoint Agent report if the **Group By** selector was set to "Locations".
* Fixed an issue with Agent to Agent tests that could cause the Utilization for the Agent to Agent queue to reach 100%.
* The Enterprise Agent installation script now works without modification on the workstation version of Red Hat Enterprise Linux 7, provided appropriate prerequisites are available.

## Questions or comments?

 Got questions? [Mail 'em our way](mailto:support@thousandeyes.com).  Come rain, snow, sleet or hail, Customer Success will never fail to get you answers to your questions about ThousandEyes.  
 

