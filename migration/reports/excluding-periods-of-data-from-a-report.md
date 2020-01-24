# Excluding periods of data from a report

When creating reports, customers often wish to exclude periods of time that represent maintenance or similar events. The use case is often to create SLA reports for their customers.

Currently, ThousandEyes [Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports) feature does not provide exclusion of test data by time period. To exclude periods of test data, we recommend exporting the data using [API](https://developer.thousandeyes.com/), then importing the data into your preferred data analysis tool that supports timestamp-based data filtering.

However, there is an alternative approach available - reporting can be configured to use alert data as a source. The [Alert Suppression](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmYKAS_Alert-Suppression-Windows) feature will block [Alert Rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) from being triggered during the time specified in the Alert Suppression configuration. Therefore, if your report uses Alerts as a Metric, then you can indirectly affect reporting during an Alert Suppression window, as no alerts would appear during the suppression window.

## Example data exclusion based on Alert Suppression

The following figure shows an [HTTP Server test results view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmvKAC_Using-the-HTTP-Server-view) with a configured Alert Suppression window \(2\):

IMAGE MISSING

 During the time period shown above, two outage events happened - the first one fired an alert \(1\) while the second one \(3\) happened during an \(at that time\) active Alert Suppression window, which prevented the alert rule from triggering.

The next figure shows how the test data and the Alert Suppression configuration reflected in a report. The widgets on the left side \(1\) are based on test results data, while widgets on the right-hand side \(2\) use alert data:

IMAGE MISSING

The important difference is the presence of the second outage event in the widgets that are based on test results. This is clearly visible as an availability drop in the time-series widget \(3\) on the left side. Since there was no alert generated during the Alert Suppression window that covered the event, no similar dip can be found in the corresponding widget on the right-hand side.

Naturally, widgets that present all available data as a single value, the ones that are most often used as final SLA figures, are also affected by Alert Suppression windows. Above, both bottom widgets are configured to present the service availability in a selected period as a single percentage figure. The test data-based widget on the left side \(4\) is showing a considerably lower value compared to alert data-based widget on the right-hand side.

## Caveat

**Alert Suppression feature cannot be used for data exclusion retroactively.** Since the alert-based reporting works on created alerts and their duration, Alert Suppression windows need to exist beforehand to prevent the alert rules from being triggered in the first place.

