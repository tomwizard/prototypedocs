# Release Notes: 2018-07-18

Welcome to tonight's release!

In ThousandEyes blog news, Engineering intern Kieran Halloran has written an article with useful information about the ThousandEyes API, while working on his summer project to compare performance of Amazon, Google and Microsoft cloud services. Entitled [Automating Test Creation with the ThousandEyes API](https://blog.thousandeyes.com/automating-test-creation-with-thousandeyes-api/), the article provides a great starting point for those who would like to learn how to use the ThousandEyes API, particularly if creation of large numbers of tests is needed.

## Cloud Agents

More additions to our Cloud Agents in broadband ISP networks. Two in the AT&T network, in Los Angeles, California and Dallas, Texas. Howdy!

## Unit Calculator

The unit calculator, which is available at [https://app.thousandeyes.com/calculator](https://app.thousandeyes.com/calculator) and linked from the Organization tab in the Account Settings, now includes a comprehensive list of tests and Agents contributing to the unit consumption of the organization. Customers can view the usage summary per Account Group under a new **Summary** tab, and filter usage by Account Group. 

## API

The /agents endpoint will now return a field called ‘errorDetails’ which contains an array of current Agent errors. Each error has a ‘code’ and a ‘description’ with information about the error. Example errors:

```text
            "errorDetails": [
                {
                    "code": "AGENT_VERSION_OUTDATED",
                    "description": "Agent Version 0.147.141 (latest: 1.40.0~15)"
                },
                {
                    "code": "BROWSERBOT_VERSION_OUTDATED",
                    "description": "Browserbot Version 0.83.3 (latest: 1.67.2)"
                },
                {
                    "code": "CLOCK_OFFSET",
                    "description": "3 mins behind"
                }
            ]
```

  
The errorDetails field will be returned in both the Agent list and Agent details endpoints, and as part of the ‘clusterMember’ field for Enterprise Agent Clusters.

* 
## Bug fixes & minor features

Here's the bug fixes and minor features in this week's release:

* For organizations using the Password Expiration feature, email notification of expiry will now be sent to users a week from expiration and a day before expiration.
* Waterfalls in Page Load and Transaction tests now provide a Response Code column with a link to the request and response headers
* Waterfalls in Page Load and Transaction tests now indicate "cancelled' rather than "no response" and "incomplete" in the mouse-overs for Object and Size columns, respectively, when object loads are cancelled by Transaction test steps or when encountering a [Chrome bug](https://bugs.chromium.org/p/chromium/issues/detail?id=811077)
* Fixed an issue where Target to Source path trace data was not shown in some bidirectional Agent to Agent tests
* Fixed an issue which caused incorrect timezones in PDF exports of reports
* Fixed an issue which caused incorrect dates in PDF exports of reports
* Fixed an issue which duplicated graphs in PDF exports of reports
* The /agents endpoint of the API returns the "location" parameter again, with each response

## Questions and comments

Got feedback on the new features? Just want to say "Howdy"? [Send us an email](mailto:support@thousandeyes.com?subject=2018-07-18+Release+Update)!

