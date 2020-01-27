# Release Notes: 2013-05-01

### Release update 2013-05-01

Our team has been hard at work again, making tweaks to the system to make sure that it's running optimally... and of course, delivering some fun new features!

## New timeline widget

Our team has modified the timeline, to make it more functional, and to enable some fun new features as follows:

IMAGE MISSING

### All new event timeline

Prior to this release, a test which showed errors from one or more location \(primarily related to web tests\) would show a red dot on the bottom of the chart for completion.  These dots have been moved below the chart, to allow users to see data in the chart more clearly, and you can hover over the event timeline to show the errors. When no agent is selected, if an error is present, the mouseover text will show the number of agents excluded from the aggregated values.  When an agent is selected, the mouseover text will show the detailed error message which caused the error to to appear on the event timeline.

Watch the event timeline for some cool new features in the not so distant future.

### Jump to... links now remember zoom level

We found that when jumping between the various views associated with a test, a majority of users wanted to see the same amount of context in the new view, as they were showing in the previous view.  As of this release, using the jump to menu to show another view will not only remember the moment in time selected on the timeline, but will also remember the zoom level of the overall chart.

Note: when entering a new view using the top nav, or by selecting another test, the default zoom level is 24h.

## Detailed metrics shows agent details

Each location being used for a test will now show full network details and source IP information.  Public and Enterprise Agents show up using different icons:  for public, and   for Enterprise Agent.  When you hover over the agent, the full network information will be shown for the agent, as shown below:

IMAGE MISSING

## More API developments

We've added a new endpoint to the ThousandEyes API, to allow you to pull more information about the agents assigned to specific tests:

```text
/tests/http-server/{testId}
/tests/page-load/{testId}
/tests/transactions/{testId}
/tests/dns-server/{testId}
/tests/dns-dnssec/{testId}
/tests/dns-trace/{testId}
/tests/network/{testId}
```

Using http-server, test ID 1158 as an example, this a query to https://api.thousandeyes.com/tests/http-server/1158.json will return the following values:  


```text
{
   "test": [
       {
          "enabled": 1,
          "testId": 1158,
          "testName": "https://app.thousandeyes.com",
          "interval": 900,
          "url": "https://app.thousandeyes.com",
          "agents": [
             {
                "agentId": 9,
                "agentName": "Seattle, WA",
                "location": "Seattle Area",
                "countryId": "US",
                "ipAddress": "4.53.150.242",
                "prefix": "4.0.0.0/9",
                "network": "Level 3 Communications, LLC (AS 3356)",
                "public": 1
             },
             ...]
        }
      ]
   }
```

Note - Cloud Agents shown in test settings may be assigned multiple IP addresses, though the agent assigned to each test will remain the same IP unless there is a problem with our infrastructure.  It is possible to have the same agentId in two different tests showing different IP addresses and/or networks.  All other information should remain the same.  

Here's a [link](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmo0KAC) to the API reference document for more information.

## A fancy new back-end!

Because the guys in the server room never get enough credit for what they do, we wanted to specifically call out the mammoth amount of work that went into upgrading our back-end, which has been ongoing for a while.  We've been spending a lot of time building performance and redundancy into the product, and this release moves much of the back-end to fancy new servers, helping us accomplish this task.

