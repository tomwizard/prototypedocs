# Release Notes: 2015-11-11

In light of the fact that we're releasing on November 11, I'd just like to take a moment to pay respect to those who have given their lives in service. This day, dating back to the cessation of hostilities in World War I, on November 11, 1918 and is known as Armistice, Remembrance, or Veteran's day, depending on where you live.

Ok, now onto business.

First, given that our release cycle would put our next release right before the US Thanksgiving holiday, we're pushing it out by a week. Our next release will be on December 2, 2015.  Next, onto our list of updates.

## Test layer name changes

In preparation for upcoming features, we've made nomenclature changes to layers and test names that you'll see in test and alert settings.

* **Routing** has become its own layer, and we've moved **BGP** tests into this layer.
* **Network** tests have been renamed to **Agent to Server** tests.
* **Voice** tests \(under the **Voice** layer\) are now known as **RTP Stream** tests.

These changes have made it into alert rule configuration, test settings, and the views interfaces.  We've updated corresponding documentation to reflect the changes, but [please let us know](mailto:support@thousandeyes.com?subject=You+missed+an+article) if you see anything that looks out of date!

## Reports: adios, pastels!

IMAGE MISSING

We've made the base colors of the time series report type consistent with the bar and column graphs. This will make it simpler to differentiate between time series values.

## SSLv3 decommissioned

As previously announced, SSLv3 has been decommissioned on the ThousandEyes API.

## Bugs squashed

We've made a few fixes, as well.  Quick summaries can be found below:

* ThousandEyes Virtual Appliances running behind proxies could fail to upgrade their version of the Virtual Appliance, due to a problem with "requirements.txt".
* Users requesting multiple password resets could get into a state where the expected token did not match the token in an email notification.  This process has been optimized to solve frustration around password resets.
* Corrected an issue whereby a test link sent from a Path Trace alert would send the user to a 404 \(Dud Link\) page.
* Voice alerts have been added to alert rule filters in report widgets.

## Questions & comments?

 We really do love hearing from our customers.  If you have anything you're curious about, or even want to learn more - just [drop us a note](mailto:support@thousandeyes.com?subject=2015-11-11+Release+Update).

