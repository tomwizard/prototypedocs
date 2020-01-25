# Release Notes: 2013-11-13

Hard to believe it's November already! With four more releases to go in 2013, our team has been hard at work developing and refining new features, to give you the most out of your investment in ThousandEyes.  Check out the list of updates below, and let us know if you have any questions, or comments -- we're always interested in hearing your feedback.

## New Features

### Alerts dashboard widget

We've released a new dashboard widget, and made it appear by default on all user dashboards. The alerts widget provides a matrix view of your tests and agents over the trailing 24 hours, showing alerting trends, and allowing users to pinpoint trends on an agent-by-agent or test-by-test basis. In the absence of alerts occurring over the previous 24 hours, no content will be shown in the widget.  An example screenshot the alerts grid widget can be found below:

IMAGE MISSING

In the widget, the size of the circle indicates the duration of the alert \(larger size means longer duration\).  A red circle indicates that the alert is still active, and orange indicates that the alert was active in the past 24h, but is no longer active.  Presence of an empty square in the grid indicates that the agent is assigned to the test, but that no alert has been active in the previous 24h.

### Saved events

This release introduces a new way of preserving an event, in the form of Saved Events. Prior to this release, the best method of preserving an event for future access was to create a Snapshot share, which would make an link available without authentication, for future access. With this new feature, you can save an event at any time using the same surrounding windows as a snapshot share, and have those saved events permanently accessible via the saved events interface in the UI.

To save an event, click the  menu item, shown just above the timeline.  This will open a dialog prompting for the timing of the event; choose how much time around the event to preserve, then click the save button.  The name of the event will be used in the test selector, in the upper left corner of each view.

IMAGE MISSING

To review the saved events available to your organization, click the [Saved Events](https://app.thousandeyes.com/settings/events) option under the settings menu.  A list of saved events will be shown, per the screenshot below:

IMAGE MISSING

## API updates

We've launched version 3 of the ThousandEyes API today, and a new documentation site \(http://developer.thousandeyes.com\), which is the new definitive reference for API-based inquiries.  The content below applies only to version 3 of the API; prior versions remain unchanged.

References to https://api.thousandeyes.com will now be directed to version 3 \(https://api.thousandeyes.com/v3\), unless another version is explicitly specified in the request.

### Authentication

Parameter-based authentication to the ThousandEyes API has been deprecated in APIv3, in favor of Basic HTTP Authentication. See http://developer.thousandeyes.com/\#/authentication for authentication details.

Any requests which contain an authToken parameter will be receive an HTTP/302 response, and be directed to version 2 of the API.

### Result pagination changes

We've updated our pagination structure to only show the next, previous, and current elements \(removing first, last and total\) elements. This was done to optimize the performance of long-running queries for result pagination.

### Indexed paths in path-vis endpoint

We've modified the structure of the path visualization data to show a pathId reference, allowing users to correlate data returned in summary and individual rounds of testing for path-vis data. This affects the following endpoints:

```text
/network/path-vis/{testId}
/network/path-vis/{testId}/{agentId}/{roundId}
/instant/net/path-vis
```

### DNS+ Reference metrics

Reference metrics are now available in the DNS+ availability \(dnsp/availability/{testId}\) and responseTime \(dnsp/response-time/{testId}\) endpoints.  The example below shows an example for thousandeyes.com A availability measurement.

```text
{
    "dnsp": {
        "test": {
            "enabled": 1,
            "testId": 812,
            "testName": "thousandeyes.com",
            "type": "dnsp-domain",
            "interval": 900,
            "ttl": 120,
            "domain": "thousandeyes.com A",
            "modifiedDate": "2012-06-28 19:35:19",
            "createdBy": "API Sandbox User (noreply@thousandeyes.com)",
            "modifiedBy": "API Sandbox User (noreply@thousandeyes.com)",
            "createdDate": "2012-06-28 00:26:02",
            "apiLinks": [...]
        },
        "availability": [
            {
                "countryId": "*",
                "date": "2013-11-13 04:42:19.0",
                "domain": "thousandeyes.com A",
                "availability": 99.7154,
                "permalink": "https://app.thousandeyes.com/dnsp/availability?__a=75&testId=812&roundId=1384317000&countryId=",
                "totalVantagePoints": 2108,
                "totalIsps": 631,
                "referenceAvailability": "99.6424"
            },
            {
                "countryId": "AR",
                "date": "2013-11-13 04:41:49.0",
                "domain": "thousandeyes.com A",
                "availability": 100,
                "permalink": "https://app.thousandeyes.com/dnsp/availability?__a=75&testId=812&roundId=1384317000&countryId=AR",
                "totalVantagePoints": 49,
                "totalIsps": 12,
                "referenceAvailability": "100"
            },
            ...
        ]
    }
    "pages": {
        "current": 1
    }
}
```

### Alert changes

We've added a new endpoint \(alerts\), which will return a list of all alerts on an account.  This endpoint accepts the window and from/to parameters, in order to return data about historical alert activity.  Without a time range parameter, only active alerts will be shown.  We've also modified the behavior of data returned by alert endpoints as follows:

* Permalinks have been changed, and now target active view of requisite alert.  For example, a network alert will target the End-to-End metrics view at the time the alert was generated.  Prior behavior was to target the alerts page, with the selected alert in context, requiring an extra click to get to the main view.
* For inactive alerts older than 14 days, permalinks will no longer be available, since these are no longer visible in the UI.
* Start and end metrics are now available from API alert endpoints; Provided as a string value, the same detail which is available in the alert emails, and in the alerting interface, these values are now shown in the alerts API endpoints.

### API Reference links

We've added reference links to other areas in the API, using the apiLinks object in a response.   The use of these links is to provide a link between two related views.  For example, from an active alert, the permaLink element provides a browser target for users to open and view the content within the ThousandEyes interface.  A relevant API link on a network alert may target the /net/metrics endpoint, or the net/bgp-metrics endpoint.

An example of the apiLinks content using an example of an alert can be found below:

```text
{
    "alert": [
        {
            "alertId": 31715,
            "testId": 2724,
            "testName": "v6 subprefix test",
            "active": 1,
            "ruleExpression": "Subprefix exists",
            "dateStart": "2013-10-26 02:00:00",
            "violationCount": 9,
            "ruleName": "subprefix rule",
            "metricsAtStart": "Subprefix: 2001:500:2f::/48, 2001:500:2e::/48",
            "metricsAtEnd": "Subprefix: 2001:500:2f::/48, 2001:500:2e::/48",
            "createLinks": true,
            "permalink": "https://app-dev.thousandeyes.com/alerts/list?__a=11&alertId=31715",
            "type": "BGP",
            "apiLinks": [
                {
                    "rel": "related",
                    "href": "https://api-dev.thousandeyes.com/tests/2724"
                },
                {
                    "rel": "data",
                    "href": "https://api-dev.thousandeyes.com/net/bgp-metrics/2724"
                }
            ]
        }
    ],
    "pages": {
        "current": 1
    }
}
```

