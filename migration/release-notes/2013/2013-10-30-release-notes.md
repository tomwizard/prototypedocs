# Release Notes: 2013-10-30

It's been a while since our last update, so we wanted to let you know that we've been working hard to extend our feature set, and make management of your ThousandEyes infrastructure simpler and easier to manage.

## Make a wish

Have you ever had an idea for something cool that you could do with your data, or something was missing from a view in ThousandEyes? We've added a feature to the footer of our user interface to allow you to submit your requests; just enter your suggestion and our system will notify the product team!

IMAGE MISSING

  
_Wish for your favorite feature using the Make a Wish button in the footer_

## Alerting changes

A few minor changes \(largely based on suggestions from our Customers\) have recently gone into alerting that will make your lives easier. 

* You can now set the minimum number of successive periods required in order to trigger an alert, in order to account for alert blips that don't need action. Set the number of required periods on the [alert rules interface](https://app.thousandeyes.com/alerts/settings), between the number of agents, and the email addresses to notify.   Valid options are from 1-4 successive alert violations.

  IMAGE MISSING

* Emails coming from our system for alerts now link to the appropriate view for an alert, rather than to the alerts page. The target for the link is defined by the alert rule being violated, rather than the test type; for example, if a network alert rule is triggered on a page load test, clicking the link in your email will take you to the end to end metrics view, rather than the page load view. 
* Available bandwidth is now available as an alert-able metric for tests which run from Enterprise Agents; simply select available bandwidth from the metric list, and define the appropriate threshold for your test.
* The Minimum and Maximum latency options have been removed from the alert rule options, and have been replaced with the ability to run automatic alerts based on latency.  To configure an automatic alert based on network latency, select the Latency option in metrics, then select the auto checkbox.  When this option is configured, an alert will be triggered when the network latency exceeds the norm by 1.5 standard deviations.
* We've added alert information to each of the standard views, which will show active alerts for your selected test;  When reviewing test results in our standard views, active alert information is now shown in the leftmost section of the page; an example is shown below, where one alert is active:

  IMAGE MISSING

## Customize your Virtual Appliance

The latest addition to our Enterprise Agent suite allows faster deployment of virtual appliances by reducing the number of steps required for deployment in an enterprise. Purpose-built for organizations deploying virtual appliances to clients, or for wide-scale deployment within your own enterprise, the custom virtual appliance allows the creator to build a virtual appliance and preconfigure the account token, proxy settings and SSH keys used for management of the appliance.

IMAGE MISSING

To generate a custom virtual appliance, click the add &gt; New Agent link, and select the **Custom Virtual Appliance** tab. Give the appliance a name, select a format per the below list, and add SSH keys as applicable.

* **ova**: our most popular VA offering, formatted for use in VMware products, as well as XenServer and VirtualBox.
* **zip**: for use with Microsoft Hyper-V server 2008
* **both**: provides links containing both .ova and .zip formats.

Once you click the Generate Custom VA button, it will take some time to generate the virtual appliance, depending on the format requested and request load. You will receive an email containing a download link, as soon as the the virtual appliance generation is complete. Accounts can have one Custom VA available at any given time; the installation token is preconfigured by the system based on the account context of the user making the request.  Currently available custom virtual appliance is shown in the Custom VA tab, on the right of the Custom VA tab.

Note: This feature is being introduced as a beta feature, and access will be granted on an as-requested basis. Click [here](mailto:support@thousandeyes.com?subject=Custom%20VA%20Opt-in%20request) to request access to use the Custom VA feature.

