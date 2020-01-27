# Release Notes: 2015-10-14

It's a relatively light release for us feature-wise as summer grinds to a halt and we start stepping into Autumn.  These few updates are covered below.  By the way, for those of you who are in the New York City area, we're hosting an event this coming Friday that I'm sure our marketing department has told you plenty about, but I wanted to plug it in this week's release notes in case you'd forgotten. We're hosting ThousandEyes Connect NYC - this free event will allow you to connect with others who live and breathe networks - and is free.  Register and check out the details for the session here: https://www.thousandeyes.com/events/connect

## New BGP View link in Path Visualization

In the Path Visualization view, when you hover over an agent, you're used to seeing a plethora of information about the agent: The IP address, which network it's hosted in, geolocation information, as well as the detailed network metrics associated with the end-to-end measurements we've taken in the network component of a test.  We've added destination IP and a link to the BGP Route Visualization view for the specific IP being hit by the agent in the context of the current test.  In the figure below, we're hovering over the New York agent on the left, and showing the destination IP as 199.16.156.38.  When clicking the BGP View link, BGP Route visualization will open in the context of this test, and in the context of the most specific prefix we've detected advertising this IP.

IMAGE MISSING

This can be tremendously useful when attempting to correlate application failures to BGP events, particularly in a geographic server load load balancing \(GSLB\) situation where multiple IPs are seen in different prefixes.

## Reset virtual appliance password

We've been shipping a script with the ThousandEyes Virtual Appliance \(te-va-webpwdreset\) for some time which allows you to reset the password on the appliance.  Until now, it's always reset the password back to the default - but with today's update, you can now call it with a password parameter to set the password of your own choosing.  In order to do so, you require SSH access to the Virtual Appliance.  To reset the password without SSH access, users can now press the R key from the VA console in order to reset the password.

IMAGE MISSING

## Transaction steps read/write support via API

Following on the heels of our [August 8, 2015 release](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmlSKAS) where we added the ability for users to import a web transaction script exported from the ThousandEyes Recorder, we've extended v5 of the API to allow users to read and write transactionStep data, as well as control which steps are used for measuring the efficiency of the transaction \(using startStep and endStep\).  Three new fields \(available on read, create and update, for users with appropriate permissions\) are now available in the /tests/transactions family of endpoints.

Check out the [ThousandEyes Developer Reference](http://developer.thousandeyes.com/) for more information.

## Questions & comments?

Yep, even though nobody ever emails us to comment on these release notes, we do love hearing from our customers.  If you have anything you're curious about, or even want to learn more - just [drop us a note](mailto:support@thousandeyes.com?subject=2015-10-14+Release+Update).

