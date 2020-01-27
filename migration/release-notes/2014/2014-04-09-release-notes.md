# Release Notes: 2014-04-09

### Release update 2014-04-09

## Security update

Over the past 24 hours, reports of [CVE-2014-0160](http://www.us-cert.gov/ncas/alerts/TA14-098A) have surfaced, relating to a critical zero-day vulnerability in OpenSSL.  Our application servers were updated at 3:00am Pacific Time this morning \(4/8/2014\)  We have replaced the SSL certificates \(both public and private keys\) on critical customer-facing servers running OpenSSL \(api.thousandeyes.com, app.thousandeyes.com and share.thousandeyes.com\).  Our security team is actively monitoring the development of this advisory and will take further steps as appropriate.

At this time we do not have any known exposure to the vulnerabilities described by CVE-2014-0160.

## Timeline update

We've been listening to your requests: **Access 30 days of data**.  **Better zoom controls**.  Our new timeline includes all of these features, and more.  Let's look at the new timeline:

IMAGE MISSING

The new two-part timeline is divided into two parts: an upper and lower timeline.

### Upper timeline

The upper timeline shows a zoomed in view of the selected metric, allowing quick selection and identification of large spikes.  The behavior of this timeline is similar to the behavior of the classic ThousandEyes timeline - except that the old 24h \| 14d links will now show 24h \| 7d \| 14d, to change zoom controls.  The visible area on the upper timeline is controlled by the lower timeline, and the selected round will be identified by shading the entire round in a grey color.  

IMAGE MISSING

The higher the zoom level, the more evident the size of the round will be.  The upper timeline still supports the click and drag to zoom capabilities you're familiar with.

### Lower timeline

The lower timeline shows up to 30 days worth of data.  The area selected on the lower timeline controls the area shown in the upper timeline.  The timeline is shown shaded in grey, but the time visible in the upper timeline is be shown in color.  There are three ways of interacting with the lower timeline:

* _Click to select an area_: The upper timeline will center based on the selected datapoint; it will maintain the existing selected zoom level.
* _Drag the selected area_: click and drag the selected area to the left or right, in order to change the data shown in the upper timeline.
* _Click and drag to select a specific area_: click and drag to draw a window on the lower timeline, which controls the data shown on the upper timeline.  

## Virtual Appliance permissions change

We've added reboot to the list of applications which can be run without entering the sudo password.  

## Alert notifications

We've made a slight change to alert notifications in this release; these notifications will still come from support@thousandeyes.com, but will now contain a reply-to address of no-reply@thousandeyes.com.  This will no longer cause a support ticket to be opened on your behalf when replying all to an alert notification. This change applies to both standard alerts, and agent-based \(agent offline, agent clock out of sync\) alerts.

## BGP Private Peering Beta

We've enhanced the notification workflow on our BGP Private Peering capability.  Now, once a peer is authorized and enabled from within the product, the requestor will receive an email notification.  To request access to the private peering beta, send an [email](mailto:support@thousandeyes.com?subject=BGP%20Private%20Peering%20Beta%request) to our Customer Success Team.

## API changes

A few additions to the API; check out the list below:

* Users can now view alert details, using the /alerts/{alertId} endpoint
* Live share data is now available, under the /tests endpoint.  Live share data will show liveShare=1 in the test list.
* Fixed a few minor issues related to the generic /alerts endpoint.

 Be sure to check out http://developer.thousandeyes.com for more details. 

