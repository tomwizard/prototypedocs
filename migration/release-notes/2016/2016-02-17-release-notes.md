# Release Notes: 2016-02-17

Don't forget about ThousandEyes Connect, coming up in both [San Francisco](https://www.thousandeyes.com/events/connect/san-francisco-2016) and [New York City](https://www.thousandeyes.com/events/connect/new-york-2016).  We've got an exciting group of customer presenters lined up - and it'll be a great opportunity to network \(yes, pun kind of intended\) with your peers.   

Our team has been busy working through getting some new features ready for your consumption.  Check out the list below, and let us know if you have any questions.  

## New login page styles

We've modified the look of our login page somewhat. It still works the same, but it's a lot prettier.

IMAGE MISSING

## Reports

We've added some new features to reporting in this release:

### DNS Server tests: aggregate by server

Users can now report on individual DNS server metrics, at either the DNS or network layer.  Simply choose to group by server to get your widgets configured.

IMAGE MISSING

### Custom percentile

Users can now configure a custom percentile option in reporting. Add a measure using a percentile value, select a metric, and choose the 'nth Percentile' measure, then add the percentile value.  The 98th percentile option has been removed from the list of selectable measures, and replaced with this option.

IMAGE MISSING

### Pie charts have tooltips

We've also added tooltips to pie charts; when hovering over a section of a pie chart \(or the legend\), you'll see the values for the particular pie segment the mouse is hovered over.

IMAGE MISSING

### Renaming report widgets

We've changed the method to rename a widget. Prior to this release, users would click the pencil icon beside the widget label to rename the widget. Beginning today, click the menu option \(in the upper right corner of the widget\), select 'rename' from the context menu and give your widget a new name.

IMAGE MISSING

## Agent-to-Agent beta updates

As we continue working through the Beta phase for Agent to Agent tests, we've made a few changes.

### Alerting

We've enabled path trace and BGP alerts on these tests. Users can now select these alert rules in their test settings.

### Reporting

Users can also report on Agent-to-Agent metrics.  We've added the following metrics to the list of reportable metrics:

* Errors
* Jitter
* Latency
* Packet Loss
* Throughput

All of the options can be charted in either a specific direction, or both directions.

## Activity log search improvement

We've made some changes which vastly improve the performance of activity log searches.

## DNS+ with new TLDs

For customers leveraging DNS+, you'll now be able to add tests for new top level domains \(TLDs\). Prior to this update, certain top level domains would come up unresolvable.

## Bugs squashed

On the bug front, our in-house exterminators have been busy. All of the bugs below were corrected between releases, however they are being included here to close the loop.

* Organizations leveraging our Lite plan would under certain circumstances show an incorrect agent allocation, preventing customers from adding up to 3 enterprise agents.
* On test settings, for HTTP Server and Page Load tests, customers may have noticed newly created tests were ignoring some advanced options. 
* In certain cases, tests cloned from other tests where advanced options were configured were cloned without the advanced options set.

## Feedback, feedback, and feedback

Why so much feedback?  Because we love hearing from you - just [drop us a note](mailto:support@thousandeyes.com?subject=2016-02-17+release+update), any day, any time.  Feedback is always welcome!

