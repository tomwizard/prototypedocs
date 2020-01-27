# How Unit consumption works

ThousandEyes bills for scheduled tests and Instant Tests based on whether the test is run from a Cloud Agent or an Enterprise Agent, and for two-way tests \(Agent to Agent and Voice Call tests\) whether the target Agent is a Cloud Agent or an Enterprise Agent. Any test run from or to a Cloud Agent will incur a cost in Units. When a test is run, the test's cost is deducted from the monthly Units purchased by the customer's organization, as specified in the customer's contract. Each month the account is reset to the number of Units that was contracted by the customer's organization.

For tests run from Enterprise Agents \(or two-way tests between two Enterprise Agents\) two billing models exist: non-metered Agents and metered Agents. Tests run from/to non-metered Enterprise Agents do not have a cost in Units. Customers are billed for Enterprise Agents on a fixed monthly rate, so tests run from Enterprise Agents do not incur per-test charges. For metered Enterprise Agents, the cost of a test in Units is calculated similar to a Cloud Agent, up to a certain monthly dollar limit, after which additional tests do not incur per-test charges.

## Calculating the cost of a test

For tests which incur Units, the cost in Units is based on the following:

1. Type of test
2. Test Interval setting \(frequency\)
3. Number of ThousandEyes Agents running the test
4. Test Timeout setting
5. Metered or non-metered model \(Enterprise Agents\)

These settings are available for each test from the Test Settings page, on the Basic Configuration tab \(1 - 3\) and the Advanced Settings tab \(4\):

IMAGE MISSING

The number of Units consumed by a test per hour is calculated according to the following formula:

IMAGE MISSING

The _**test interval**_ parameter is measured in minutes. The number of Units per test run is listed in the following table. The table assumes Enterprise Agents are using the metered model.

| **Test Type** | **Units per test run** | **Notes** |
| :--- | :--- | :--- |
| Agent to Server | 5 or 2.5 | Cloud Agent or Enterprise Agent \(source\) |
| Agent to Agent | 5 or 2.5 | Cloud Agent or Enterprise Agent \(source\), per direction |
| DNS Server | 5 or 2.5 per DNS server | Cloud Agent or Enterprise Agent \(source\) |
| DNS Trace and DNSSEC | 5 or 2.5 | Cloud Agent or Enterprise Agent \(source\) |
| HTTP Server | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\) |
| FTP Server | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\) |
| Page Load | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\)HTTP Server; see note below |
| Web Transaction | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\)  Minimum Timeout is 5 seconds, maximum is 180 seconds |
| DNS+ Domain | 217 |  |
| DNS+ Server Latency | 868 |  |
| BGP | 8 | The cost of a Routing Layer BGP test is independent of the number of BGP monitors selected |
| Voice - SIP Server | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\)    |
| Voice - RTP Stream | 1 or .5 x Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\) |
| Voice - Voice Call  Enterprise Agent source | 1 or .5 x each Timeout setting \(in seconds\) | Cloud Agent or Enterprise Agent \(source\) |

**Note regarding Page Load tests:**

Page Load tests allow the configuration of different frequencies for the Page Load view and HTTP Server view. The consumption of units will be calculated using the frequencies of both views if the timeouts are different. Consider the following example.

1 Page Load test running from 1 Cloud Agent, with a frequency 15 minutes, with a 30-second Timeout. The hourly consumption for this test would be 120 units:

```text
1 Cloud Agent x 30 units per run x (60 minutes per hour / 15 minutes) = 120 units per hour.
```

When the testing interval for HTTP Server tests is reduced from 15 minutes to 5 minutes, we are now running 12 HTTP Server tests for the HTTP Server view.  The calculation is thus 4 Page Load tests and 12 - 4 = 8 additional HTTP Server tests.  Assuming a 5-second HTTP Server Timeout setting, this causes the hourly consumption to increase to 160 units per hour:

```text
 1 Cloud Agent x 30 units per run x (60 minutes per hour / 15 minutes) = 120 units per hour. (Page Load)
 1 Cloud Agent x 5 units per run x ( (60/5) - (60/15) ) = 40 units per hour (additional HTTP Server tests) 
```

120 + 40 = 160 units per hour

##  Why this model?

We’ve chosen this model to allow our customers to have flexibility in test deployment.  Rather than locking in a contract based on specific test types, locations and intervals, we’ve given you enough flexibility to manage your own testing use cases.  Consider the following Cloud Agent scenario: ACME Manufacturing has purchased a total of 10 Page Load tests running at 15 minute interval from 20 locations, for a total monthly consumption of 17,856,000 units.

| Test Type | Cloud Agent Locations | Tests | Interval \(mins\) | Timeout | Monthly unit consumption |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Page Load | 20 | 10 | 15 | 30s/5s | 17,856,000 |

Acme subsequently purchases another company, and needs to monitor a new website, as well as an API integration website for their product, meaning addition of 1  HTTP Server test every 5 minutes from as many locations as possible, one Page Load test for the new company’s website, and one DNS Trace test to validate the new company’s DNS configuration.  Rather than extending the contract, they are able to be flexible in the deployment of the new tests by reducing the number of Agents running the Page Load test from 20 to 16, and reallocating the saved Units to the new tests:

| Test Type | Cloud Agent Locations | Tests | Interval \(mins\) | Timeout | Monthly unit consumption |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Page Load | 16 | 11 | 15 | 30s/5s | 15,713,280 |
| DNS Trace | 20 | 1 | 5 | 5s | 892,800 |
| Basic HTTP | 20 | 1 | 5 | 5s | 892,000 |
| Total |  |  |  |  | 17,498,880 |

This would leave 357,120 units available for additional tests.

For Enterprise Agents, the metered and non-metered options allow customers similar flexibility. Metered Agents allow customers who have low levels of use to pay only for what they need and no more. Customers who need to run larger quantities of tests can take advantage of the flat monthly cost of non-metered Agents by running as many tests as the Agent can execute.

## [Frequently Asked Questions]()

### How are units deducted from my balance?

Every time a test is run, the number of Units consumed by the test are deducted from the balance on the organization’s account.  This information is accessible to users having a role with the View organization usage permission, by navigating in the app to the [Usage tab](https://app.thousandeyes.com/settings/account/?section=usage) of the Account Settings.

### How can I estimate the consumption of units by a test?

ThousandEyes provides a calculator for customers to determine the cost of a test based on the inputs:

[https://app.thousandeyes.com/calculator](https://app.thousandeyes.com/calculator)

### How can I view my balance?

Users having a role with the View organization usage permission can view both to-date usage and usage projected to the end of the billing period by navigating in the app to the [Usage tab](https://app.thousandeyes.com/settings/account/?section=usage) of the Account Settings.  For organizations which have multiple accounts, administrators can view a breakdown on an account by account basis.

### What is the projected usage?

Projected usage is calculated by taking the current amount of Units consumed and adding to it the current rate of Unit consumption X the remain days in the billing cycle. This projection will change if test configurations change with alter the rate of Unit consumption.

### What happens if my organization exceeds our monthly quota of Units?

The billing contact for the organization will be notified by email when:

* estimated usage is greater than 100%,
* actual usage exceeds 90% AND the estimated usage is greater than 100%, 
* and when actual usage exceeds 100%.  

For more information on alerting based on unit consumption, see Knowledge Base article [Alerting for Test unit consumption](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn9KAC).

Accounts on monthly terms with ThousandEyes will be billed for overages in accordance with contractual terms and conditions based on actual usage.  Accounts on longer-length terms will be contacted by their ThousandEyes account representative.

