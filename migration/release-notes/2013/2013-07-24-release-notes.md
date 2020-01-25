# Release Notes: 2013-07-24

As with previous releases, our team has been busy working on evolving the ThousandEyes platform.  We're happy to announce our July 24, 2013 release, chock full of features!  See below for the highlights.

## Bug Fixes

A few minor updates to recently reported issues:

* We've fixed a minor issue where under certain circumstances, users of Internet Explorer were unable to click an agent, or hover over agents in the World Map view.
* Last modified date of a test will now be updated when a change is made to the test via either the Agent Settings page, or the Alert Rules page.  Prior to this update, modification of a test using this method would not trigger an update to the last modified date.
* When deleting an account from an organization, the organization administrator making the change would be warned that the account deletion would delete all agents assigned to the account.  This warning will only be shown when there are Enterprise Agents installed using that account's account token.
* Attempts to return page load data using the /web/page-load/{testId} endpoint were previously returning two sets of data for every agent assigned to the test.  This error has been corrected and will now return only one set of data for each agent assigned to the test.

## Changes to Alerting

We've made some substantial updates to the behavior of our alerting.  In our last release, we changed our alert clearing logic to clear active alerts when they were no longer relevant - for example, if the test was disabled, if the alert rule was disabled, or if an agent was removed from the test \(release notification can be found [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmm9KAC)\).

### Alerts now show on the timeline

Beginning with this release, users will now see alerts show up on the reference line below the timeline.  Shown in an orange bar \(similar to agent reference problems, shown in grey\), users will see the alert rule triggered, and if the alert is for a view which is not being shown in context, will see a link to the appropriate view. See the image below, where the timeline shown for an HTTP server rule shows a network alert triggered for that test.  Note the _Jump to Network_ link, which will open the End-to-End Metrics view, with the error in context.

IMAGE MISSING

###  BGP Alerts for Network Tests

BGP Alerting is now possible on Network, Web \(HTTP Server and Page Load\), as well as DNS Server tests.  Prior to this release, BGP Alerts only applied to BGP tests.  The Default BGP rule \(Reachability &lt; 100%\) will now apply by default to any newly created tests which include network measurements.

### Third Alert status: "disabled"

We've added a third alert status in this release.  Prior to this release, alerts could only be active or inactive, at any given time.  Inactive indicated that an alert had been resolved, where active meant that an alert was in progress.  We've added a "disabled" state for alerts, which will trigger under the following conditions:

* Test gets disabled while an alert is active
* Alert rule is removed from a test with an active alert
* Alerts are disabled on a test while an alert is active
* Deleting the alert rule when the alert is active
* Removing a server from a DNS Server test while an alert is active
* Removing an agent from a test while it has triggered an active alert

When an alert goes into the disabled state, the reason that the alert was marked as disabled can be found in the column labeled **Metrics @ Alert End**.  See below for a screenshot of an alert which has entered the disabled state.

IMAGE MISSING

## Account management changes

Beginning with this release, users with Organization Admin privileges can now move users from one account to another.  To move a user, open the account settings page, select the Accounts & Users tab, and select the account you wish to administer.  Drag the user from the list of users on the right, into the destination account on the left.

## Default metric for BGP Route Visualization view

In addition to adding BGP alerting for network tests, we've adjusted the default view for BGP Route Visualization to be the Path Changes metric.  Prior to this release, the default metric in the BGP Route Visualization view was Reachability.

## Agent changes

We've made a minor change to how Enterprise Agents handle DNS trace tests.

### DNS Domain Trace tests on agents without UDP port 53 open

We've had a few reports of Enterprise Agents reporting excessive utilization when located in a network that doesn't have UDP port 53 open to the internet, and configured to run DNS Domain Trace tests.  Our code has been adjusted to do a fast failure on DNS Domain Trace tests where the target server is unreachable.  Beginning with this release, DNS Domain Trace tests will time out if the first 5 queries for a test fail to return a response, when in this type of configuration.

## Instant test changes

Starting today, advanced options available in HTTP Server and Page Load tests are now available in the instant tests interface.

IMAGE MISSING

## API changes

A ThousandEyes release wouldn't be complete without some API changes!

### New generic /tests/{testId} endpoint

We've added a generic /tests/{testId} endpoint to the API, to allow users to submit an API query to determine the type of test, and the options enabled on the test.  This returns the following data:

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| enabled | whether or not the test is currently enabled | 0 \| 1 |
| testId | the ID of the test as a bigint | 1234 |
| testName | the name of the test | my test |
| type | the type of the test; corresponds to target endpoint for return values  | page-load \| http-server  |
| interval | integer value, number of seconds between testing iterations | 900 |
| url | target of the test | http://www.thousandeyes.com |
| agents | an array of agents assigned to the test |  |
| createdDate | date that the test was created, in YYYY-mm-dd HH:nn:ss \(UTC\) format | 2013-06-06 22:53:53 |
| createdBy | name and email address of creator |  |
| modifiedDate | date that the test was modified, in YYYY-mm-dd HH:nn:ss \(UTC\) format | 2013-03-29 19:58:42 |
| modifiedBy | name and email address of last modifier |  |
| networkMeasurements | whether or not network measurements are enabled, for appropriate tests | 0 \| 1 |

 **Example**

```text
{
    "test": [
        {
            "enabled": 1,
            "testId": 1158,
            "testName": "https://app.thousandeyes.com",
            "type": "page-load",
            "interval": 900,
            "url": "https://app.thousandeyes.com",
            "agents": [
                {
                    "agentId": 2,
                    "agentName": "Sao Paulo, Brazil",
                    "location": "Sao Paulo, Brazil",
                    "countryId": "BR",
                    "ipAddress": "200.134.255.40",
                    "prefix": "200.134.128.0/17",
                    "network": "FUNPAR - Fundacao da UFPR para o DCTC (AS 10881)",
                    "public": 1
                },

            ],
            "modifiedDate": "2013-06-06 22:53:53",
            "networkMeasurements": 1,
            "createdBy": "Dave Fraleigh (dave@thousandeyes.com)",
            "modifiedBy": "Dave Fraleigh (dave@thousandeyes.com)",
            "createdDate": "2013-03-29 19:58:42"
        }
    ]
}
```

### Instant web tests now support advanced configuration

Beginning today, you can now specify advanced configuration options for instant HTTP Server and Page Load tests, using the following input:

**HTTP Server**

```text
/instant/web/http-server/
```

**Inputs**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| url | URL to retrieve | [http://www.google.com](http://www.google.com/) |
| username | the username you wish to use, can be domain qualified.  If using a  backslash character to qualify the domain, it must be escaped with  a second backslash. | DOMAIN\\myusername |
| password | password of the user | mypassword |
| useNtlm | Defaults to 0, set to 1 if using NTLM authentication, 0 if using basic authentication | 0 \| 1 |
| verifySslCertificate | Defaults to 1, set to 0 if you don't want to verify the SSL certificate | 1 \| 0 |
| headers | Key-value pairs for headers | user-agent: bogus browser 0.0 |

**Example**

```text
curl https://api.thousandeyes.com/instant/web/http-server.json?authToken={authtoken} \
 -d '{"agentId":35, "url":"http://www.google.com", "username":"domain\\user", "password":"mypassword", "useNtlm":0, "verifySslCertificate":0, "headers":["user-agent: bogus browser 2.0"]}' -H "Content-Type: application/json"
```

**Page Load**

```text
/instant/web/page-load/
```

**Inputs**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| url | URL to retrieve | [http://www.google.com](http://www.google.com/) |
| username | the username you wish to use | myuser |
| password | password of the user | mypassword |

**Example**

```text
curl https://api.thousandeyes.com/instant/web/page-load.json?authToken={authtoken} \
 -d '{"agentId":35, "url":"http://www.google.com", "username":"domain\\user", "password":"mypassword"}' -H "Content-Type: application/json"
```

