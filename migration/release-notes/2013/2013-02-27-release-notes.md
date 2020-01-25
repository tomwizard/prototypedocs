# Release Notes: 2013-02-27

Today's release contains a number of changes designed to help us scale our tools better, and to facilitate some major upgrade steps coming soon.  In addition to this, we have made some rather large customer-facing changes today:

## Customer Success Center launch

You're reading this article in our new Customer Success Center, which can be accessed at https://support.thousandeyes.com.  Until we exit from stealth, this site is a portal for our customers only.  Here, you can find a comprehensive \(and growing daily\) knowledgebase, access to your legacy support requests, and a rich community for interaction with your peers across the ThousandEyes customer base.  

When you find something interesting, subscribe to that forum -- and you'll receive email notifications from the forum when someone makes an update, posts an feature idea, or asks a question. You're our real experts, and we want to cater to the requests of the many.Take us for a test drive, kick the tires, and let us know what you think.

## Reduction in alert email volume

Prior to this update, when multiple recipients were defined on an alert notification, one email went out to each recipient.  Following this change, a single email will be sent with all alert recipients mentioned in the TO: line of the message.  This will allow organizations to be aware of other alert recipients, and reduce email traffic on the inbound messages.

## Reduced number of "white nodes" in Path Visualization

An immensely complex topic, this effectively means that we are reducing the number of "white nodes" which appear on path visualizations by using a new path reduction algorithm.  

The net result is a reduction in the complexity of path visualizations showing white nodes, per the two very simple examples below:

IMAGE MISSING

becomes

IMAGE MISSING

and this:

IMAGE MISSING

becomes

IMAGE MISSING

Not to worry:

* Where a star node \(node that appears as a star in a traceroute\) is non-transient, we will never reduce it into another path
* A path which is taken at least 3 times more often than a transitive star \(\*\) path will consume the star path 
* You can control display of loss thresholds using a slider on the right of the ThousandEyes interface.

