# Release Notes: 2013-09-18

Continuing along in the vein of making your lives more simple, we've added some great new features to the product this week.

## Managed Enterprise Agent package deployment for linux servers

For organizations running managed linux servers inside their organization, we have a new managed package module which can be leveraged to manage the configuration and deployment of ThousandEyes agents across the enterprise.  Our approach to managing the configuration and deployment for enterprises is to make a Puppet module available.

Paulo, our DevOps lead has created a Puppet module which can be used to manage the configuration of many linux servers remotely.  Organizations using Puppet \(either the Open Source or Enterprise version\) can clone the public GitHub repository [here](https://github.com/thousandeyes/puppet-teagent).  Be sure to check out Paulo's post on the ThousandEyes blog \(containing instructions\) [here](http://blog.thousandeyes.com/deploying-thousandeyes-agents-with-puppet)!

Puppet documentation can be found on the [Puppet Labs](https://www.puppetlabs.com/) site.

## Enforced Password Expiration

Beginning tonight, organizations can \(optionally\) enforce a password expiry option within their organization. Organization administrators can optionally define a password expiration rule forcing password expiry every 3, 10, 30, 60 or 120 days. For organizations using Single Sign On \(SSO\), this applies to ThousandEyes passwords, and not to passwords managed by your SSO provider.  To change the organization's password settings, open [Account Settings](https://app.thousandeyes.com/account), and under the profile tab, check the box to enable password expiration for your organization, and then set the expiration period.  See the image below.

IMAGE MISSING

Note: this option can only be set by a user with Organization Admin privileges.  
 

## Content Verification for HTTP Server tests

Have you ever had a problem reported by users, where a user is looking at a previous version of a page? Do you use a content delivery network to host your website? If so, you may find this next update useful.

With today's release, users can define a content verification expression as part of an HTTP Server test. Content is verified based on the entire content of the page, including comments, script, headers and HTML markup.  This will facilitate measurement of time required for CDNs to update, and validation that all sites are running expected versions of the content.

To add content verification to an HTTP Server test, open [test settings](https://app.thousandeyes.com/test-settings) for the test you wish to modify, and expand the advanced options section.  In this section, enter a POSIX extended regular expression.  Upon save, the next iteration of this test will validate the content found in the target page against the regular expression defined in advanced options.  A screenshot for this field \(labelled **Verify Page Content**\) is shown below:

IMAGE MISSING

Refer to these links for more details on using POSIX Extended Regular Expressions in ThousandEyes:

* [Regular expression quick reference chart](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn6KAC) 
* [Content validation using POSIX Extended regular expressions](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnCKAS)

For tests with content verification enabled, a new element "Content" will appear when viewing the availability metric for a page. Any agent failing content validation will appear in red on the map, and the content validation error message will appear in the detailed metrics view.  A drop in availability indicates an error encountered while accessing a page, which can occur in any of the following phases:

* DNS
* Connect
* SSL
* Send
* Receive
* HTTP
* Content

You'll see the reason for the error shown in the error details column -- in most cases, reflecting **Page content did not match "{your regexp}"**.  See the image below for an example.

IMAGE MISSING

**Note**: Since content validation affects the availability metric, users may want to adjust alert rules assigned to HTTP Server tests which are based on availability, to reflect special handling of content errors. To exclude content errors from availability tests, simply add a rule line for _Error Type is not Content_.

IMAGE MISSING

## Deep Path Analysis: Demystifying transit MPLS tunnels

We've always shown some unique information on MPLS tunnel information, but with this release, our algorithms have become smarter, and enable users to better identify partially obscured transit paths which leverage MPLS.  This allows users leveraging our Deep Path Analysis \(DPA\) technology to view the path taken over the Internet between each agent and destination.  As a refresher, we identify MPLS networks using the quick selection section of the Path Visualization interface, stating that X links are part of an MPLS tunnel.  Based on some academic papers, there are four types of MPLS tunnels which can be in place - controlled through configuration of individual routers within the MPLS network.  We'll cover the three we support here:

### Explicit tunnel

We've always displayed explicit MPLS tunnels \(tunnels not obscured using router configuration\), with the links between each hop of an MPLS network being shown, complete with label information.  When an MPLS hop is detected in the path, the quick selection link will identify links which are part of MPLS networks, and display the label stack, when hovered over an affected link.  Explicit tunnels remain unchanged.

IMAGE MISSING

### Implicit Tunnel

When devices are configured not to send MPLS stack entries, we can still infer that the link is part of an MPLS tunnel, and attempt to infer the hop number of the tunnel.  This will be represented in ThousandEyes as **Hop X in an MPLS Tunnel**.  While no label information may be available \(due to provider router configuration\), having the source IPs of the transit network may allow a service provider to cross-reference the externally-visible map against internal documentation, to find the true path taken.

IMAGE MISSING

### Opaque Tunnel

In circumstances where a single MPLS label is encountered but the IP TTL is reset at the ingress router, ThousandEyes will show the single hop, as an **X-hop MPLS tunnel**. This information can be helpful when diagnosing network connectivity issues while transiting a service provider's network, since some hops may be obscured from the path visualization output, inferring a sometimes incorrect one-hop transit across the MPLS network.

IMAGE MISSING

## API Enhancements

### Alert rule list

We have added a new alert-rules endpoint to the ThousandEyes API, which will allow users to pull a list of currently configured alert rules.  The output of this endpoint can be used during API-based test creation, using the update from the next section below.  Access the alert rule list using the following endpoint:

```text
https://api.thousandeyes.com/alert-rules
```

Sample output:

```text
{
    "alertRules": [
        {
            "enabled": 1,
            "ruleId": 1687,
            "ruleName": "Default BGP Alert Rule",
            "alertType": "Bgp",
            "notes": "",
            "expression": "((reachability < 100%))",
            "default": 1,
            "notifyOnClear": 0
        },
        ...
    ]
}
```

###  Custom rule assignment on test creation/edit

Beginning with this release, it is possible to assign alert rules to tests created via the ThousandEyes write API.  Prior to this release, tests created using the ThousandEyes API would automatically assign the applicable default rules, based on the test type.  Note: Specifying one or more alert rules will override automatic assignment of default alert rules.

Alert rule assignment for tests created or edited using the ThousandEyes API follows this logic:

* if the alertRules field is present and non-empty on a request, it will assign the specified rules to the test
* if the alertRules field is present and empty on a request, no alert rules will be assigned
* if the alertRules field is omitted from a request, default alert rules \(based on the test type and configuration\) will be assigned

The alert rule list is specified as an array of ruleId objects \(which can be obtained from the alert-rules endpoint, documented above\), similar to the content below:

```text
{"interval":"900", "agents":[{"agentId":26}], "alertRules":[{"ruleId": 233}, {"ruleId": 174}]}
```

**Note:** Only valid rules can be assigned. See the chart below for a compatible alert rule to test assignments

| **Test Type** | **Alert Rules** |  |  |  |  |  |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
|  | **BGP** | **Network** | **HTTP Server** | **Page Load** | **Web Transaction** | **DNS Trace** | **DNS Server** | **DNSSEC** | **DNS+ Domain** | **DNS+ Server** |
| **BGP** | X |  |  |  |  |  |  |  |  |  |
| **Network** | X | X |  |  |  |  |  |  |  |  |
| **HTTP Server** |  |  | X |  |  |  |  |  |  |  |
| **HTTP Server\(\*\)** | X | X | X |  |  |  |  |  |  |  |
| **Page Load** |  |  | X | X |  |  |  |  |  |  |
| **Page Load\(\*\)** | X | X | X | X |  |  |  |  |  |  |
| **Transaction** |  |  |  |  | X |  |  |  |  |  |
| **DNS Trace** |  |  |  |  |  | X |  |  |  |  |
| **DNS Server** |  |  |  |  |  |  | X |  |  |  |
| **DNS Server\(\*\)** | X | X |  |  |  |  | X |  |  |  |
| **DNSSEC** |  |  |  |  |  |  |  | X |  |  |
| **DNS+ Domain** |  |  |  |  |  |  |  |  | X |  |
| **DNS+ Server Latency** |  |  |  |  |  |  |  |  |  | X |
| Items marked with \(\*\) have optional network measurements enabled |  |  |  |  |  |  |  |  |  |  |

Attempts to assign an incompatible alert rule to a test will result in an error when attempting to create or edit the test via the API.

### Page and Step-level detail for Transactions

A new API endpoint has been introduced to provide more detail on page- and step-level detail for transactions, which is shown on the transactions view \(example below\):

IMAGE MISSING

Due to the volume of data retrieved using these queries, the data must be requested on an agent-by-agent basis, for each round.  To access this endpoint, provide test, agent and round IDs in the request:

```text
https://api.thousandeyes.com/web/transactions/{testId}/{agentId}/{roundId}
```

To obtain the test ID for a test, use the following request, which will return a list of transaction tests configured in the account.

```text
https://api.thousandeyes.com/web/transactions
```

To obtain the agentId and roundId for a set of test results, use the following request, specifying **from** and **to**, or **window** parameters, to identify a specific set of results of interest.

```text
https://api.thousandeyes.com/web/transactions/{testId}
```

The step-level detail is found as an array of step-level objects, for each step completed during the transaction attempt.  Within the step object, the following data will be shown:

| stepNum | zero-indexed step number from the transaction script. |
| :--- | :--- |
| pageNum  | zero-indexed page number visited during execution of the transaction.   Page detail can be found in the pages object, which contains an array of pages visited during a transaction. |
| duration | time spent executing the step, in milliseconds |
| offset | time spent waiting for previous steps to complete |

Page-level detail can be found in the pages object, which is an array containing a page object for each page visited during the transaction attempt.  Within the page object, the following data will be shown:

| pageNum  | zero-indexed page number visited during execution of the transaction.  |
| :--- | :--- |
| pageName | the title of the page visited |
| componentCount | number of components found in the target page, including images, css, javascript, etc. |
| errorCount | number of errors encountered while loading components on the page |
| duration | time spent on this page in the transaction |

Sample output from a transaction detail request can be found below.  Note the steps and pages objects, identified in bold.

```text
{
    "web": {
        "test": {
            "enabled": 1,
            "testId": 1234,
            "testName": "Twitter test",
            "type": "transactions",
            "interval": 900,
            "url": "http://www.twitter.com",
            "modifiedDate": "2012-12-04 00:42:23",
            "totalSteps": 7,
            "createdDate": "2012-02-23 15:11:31"
        },
        "transaction": [
            {
                "date": "2013-09-16 23:30:17",
                "stepsCompleted": 5,
                "totalSteps": 7,
                "steps": [
                    {
                        "stepNum": 0,
                        "pageNum": 0,
                        "duration": 2739,
                        "offset": 0
                    },
                    ...
                  ],
                "pages": [
                    {
                        "pageNum": 0,
                        "pageName": "Twitter",
                        "componentCount": 11,
                        "errorCount": 0,
                        "duration": 2729
                    },
                    ...
                ],
                "permalink": "https://app.thousandeyes.com/web/transactions?__a=null&testId=1234&roundId=1379374200&agentId=2",
                "agentId": 2,
                "transactionTime": 3130,
                "errorDetails": "Step 5: Element id=user-dropdown-toggle not found",
                "roundId": 1379374200
            }
        ]
    }
}
```

### New field exposed: roundId

Beginning with this release, we have added the roundId field to test result endpoints.  This field has been obscured from version 1 of the ThousandEyes API.  RoundId is used to pull time-specific results for test.  RoundId is based on the epoch time reflecting the start of a testing round.

```text
                "roundId": 1379374200
```

