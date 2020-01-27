# Release Notes: 2013-07-10

Welcome back from the July 4th long weekend!  Our team has been hard at work developing some new features for the platform.  The big features are documented below:

## Alert management

In this release, our alert clearing algorithms got a little smarter. Prior to this release, if you made a modification to either a test or an alert rule while an alert was active, those alerts would never reset to an inactive state. We have added clearing logic for the following use cases:

* test which gets disabled or deleted
* test where alerting is disabled
* server removed from DNS Server test
* agent removed from test

##  Dashboard changes

We've adjusted the charts shown

Dashboard views have been adjusted to show the last complete round of data in the trending value graphs, as well as the most recent data.  This was introduced to avoid showing partially completed round data.

IMAGE MISSING

While the change to the dashboard will not be obvious, the values shown in the charts will now reflect the last complete round of data, rather than partially completed rounds.  

1. Clicking the availability chart will open the HTTP Server view, and show the availability metric, and show the data for the round selected on the timeline.
2. Clicking the response time chart will open the HTTP Server view, and show the response time metric, and show the data for the round selected on the timeline.
3. Clicking either of the current value entries will open the appropriate view in the context of the selected metric, and show the last full round of collected data.

### New Getting Started page

New users will now see a revised Getting Started page, complete with our inaugural screencast, which runs through agent installation and test deployment in ThousandEyes.

IMAGE MISSING

We'll also be updating the Help & Support section on the left to show more ThousandEyes screencasts, as they become available.

## Network tests now support ICMP protocol

Beginning with today's release, we now support configuration of all network tests using ICMP.  Previously, ICMP was only supported on instant ping tests.

IMAGE MISSING

To create a new network test using the ICMP protocol, use the test type selector, and select the ICMP button.  When you choose ICMP as the test type, the TCP Port field will disappear.  The key use case for this would be to trace the path to network devices.

**Two items of note:**

1. Tests cannot be converted from TCP to ICMP, or vice versa.  
2. The _Enable Network Measurements_ option included with Page Load, HTTP Server, and DNS Server tests are only available with the TCP protocol.

As with our classic TCP network tests, the Path Visualization and BGP Route Visualization views become available when creating an ICMP network test. 

##  Single Sign-On 

ThousandEyes now accepts configuration of a SAML provider to enable Single-Sign on \(SSO\).  SSO settings apply for an entire organization, and must be configured by an Organization Admin user.  To open SSO settings, click click the **Settings** \| **Account** option in the navigation menu, then click the **Single Sign-O**n tab.

IMAGE MISSING

Please refer to [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnKKAS) for instructions before enabling SSO on ThousandEyes.

## API Changes

We've extended the ThousandEyes API to include the ability to execute instant tests via the API.

For this release, the feature is restricted to Enterprise Agents only; attempts to run an instant test against a ThousandEyes Cloud Agent will result in an "Only Enterprise Agents are allowed for instant tests" error message, responding with a 400 BAD REQUEST response code.  As with the methods introduced in our June 11, 2013 release \(see release notification [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmm4KAC)\), data for each request type must be POSTed to the target endpoint.

The endpoints are documented below, along with some code samples, using cURL:

### /instant/net/ping

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| server | server name or IP address of target test.   If a webserver, do not include the protocol \(ie, http://\) | www.google.com |
| port | port number to use for the ping test, if using TCP for the test type | 80 |
| pingType | can be one of the following values: ICMP, TCP.   If using ICMP, the port number parameter is not required | ICMP \| TCP |

**Example:**

```text
curl https://api.thousandeyes.com/instant/net/ping.json?authToken={authToken} \
 -d '{"agentId":35, "server":"www.google.com", "port":80, "pingType":"TCP"}' -H "Content-Type: application/json"
```

**Outputs:**

Single "net" object, with a "ping" property, showing 50 sequential pings, similar to what would come out of a command-line ping.

```text
{
 "net": {
    "ping":"44 bytes from 74.125.128.147: tcp_req=1 ttl=46 time=165 ms\n44 bytes from 74.125.128.147: tcp_req=2 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=3 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=4 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=5 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=6 ttl=46 time=163 ms\n44 bytes from 74.125.128.147: tcp_req=7 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=8 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=9 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=10 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=11 ttl=46 time=161 ms\n44 bytes from 74.125.128.147: tcp_req=12 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=13 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=14 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=15 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=16 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=17 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=18 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=19 ttl=46 time=160 ms\n44 bytes from 74.125.128.147: tcp_req=20 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=21 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=22 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=23 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=24 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=25 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=26 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=27 ttl=46 time=160 ms\n44 bytes from 74.125.128.147: tcp_req=28 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=29 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=30 ttl=46 time=163 ms\n44 bytes from 74.125.128.147: tcp_req=31 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=32 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=33 ttl=46 time=161 ms\n44 bytes from 74.125.128.147: tcp_req=34 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=35 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=36 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=37 ttl=46 time=163 ms\n44 bytes from 74.125.128.147: tcp_req=38 ttl=46 time=163 ms\n44 bytes from 74.125.128.147: tcp_req=39 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=40 ttl=46 time=160 ms\n44 bytes from 74.125.128.147: tcp_req=41 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=42 ttl=46 time=160 ms\n44 bytes from 74.125.128.147: tcp_req=43 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=44 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=45 ttl=46 time=159 ms\n44 bytes from 74.125.128.147: tcp_req=46 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=47 ttl=46 time=162 ms\n44 bytes from 74.125.128.147: tcp_req=48 ttl=46 time=156 ms\n44 bytes from 74.125.128.147: tcp_req=49 ttl=46 time=160 ms\n44 bytes from 74.125.128.147: tcp_req=50 ttl=46 time=159 ms\n\n--- 74.125.128.147 ping statistics ---\n50 packets transmitted, 50 received, 0.0% packet loss\nrtt min/avg/max/mdev = 156.00/159.50/165.00/2.20 ms\n"}
 }
```

### /instant/net/path-vis 

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| server | server name or IP address of target test.   If a webserver, do not include the protocol \(ie, http://\) | www.google.com |
| port | port number to use for the ping test, if using TCP for the test type | 80 |
| pingType | can be one of the following values: ICMP, TCP.   If using ICMP, the port number parameter is not required | ICMP \| TCP |

**Example:**

```text
curl https://api.thousandeyes.com/instant/net/path-vis.json?authToken={authToken} -d '{"agentId":35, "server":"www.google.com", "port":80}' -H "Content-Type: application/json"
```

**Outputs:**

10 attempts at path visualization to the target, shown as an array of 10 routes to the target, with each hop indexed from 1.

```text
{
 "net": {
      "pathVis": [
           {
                "agentName": "Bucharest, Romania",
                "countryId": "RO",
                "date": "2013-06-06 12:46:01",
                "server": "app.thousandeyes.com:443",
                "serverIp": "208.185.7.120",
                "routes": [
                     {
                          "hops": [
                           {
                                "hop": 1,
                                "ipAddress": "83.246.0.1",
                                "prefix": "83.246.0.0/20",
                                "rdns": "vl150-20GbE.VSS-CR.hostway.ro",
                                "network": "HOSTWAY ROMANIA SRL (AS 39756)",
                                "responseTime": 0,
                                "location": "Bucuresti, Romania"
                            },
                          ...
                          ]
                      }
                 ]
           }
      ]
 }
```

### /instant/net/tcp-connect

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| server | server name or IP address of target test.   If a webserver, do not include the protocol \(ie, http://\) | www.google.com |
| port | port number to use for the tcp-connect test | 80 |

**Example:**

```text
curl https://api.thousandeyes.com/instant/net/tcp-connect.json?authToken={authToken} -d '{"agentId":35, "server":"www.google.com", "port":80}' -H "Content-Type: application/json"
```

**Outputs:**

Time required to establish a TCP connection to the target server.

```text
{
 "net": {
      "tcpConnect":160.0
      }
}
```

### /instant/dns/trace 

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| domain | domain to retrieve | www.google.com |
| type | record type to retrieve - typically is used for A, CNAME or NS records.  | A \| CNAME |

**Example:**

```text
curl https://api.thousandeyes.com/instant/dns/trace.json?authToken={authToken} -d '{"agentId":35, "domain":"www.google.com", "type":"A"}' -H "Content-Type: application/json"
```

**Outputs:**

Output of dig +trace to the target.

```text
{
 "dns": {
   "trace": [
      {
        "agentName":"My Enterprise Agent",
        "countryId":"US",
        "output":"com.\t172800\tIN\tNS\ta.gtld-servers.net.\ncom.\t172800\tIN\tNS\tb.gtld-servers.net.\ncom.\t172800\tIN\tNS\tc.gtld-servers.net.\ncom.\t172800\tIN\tNS\td.gtld-servers.net.\ncom.\t172800\tIN\tNS\te.gtld-servers.net.\ncom.\t172800\tIN\tNS\tf.gtld-servers.net.\ncom.\t172800\tIN\tNS\tg.gtld-servers.net.\ncom.\t172800\tIN\tNS\th.gtld-servers.net.\ncom.\t172800\tIN\tNS\ti.gtld-servers.net.\ncom.\t172800\tIN\tNS\tj.gtld-servers.net.\ncom.\t172800\tIN\tNS\tk.gtld-servers.net.\ncom.\t172800\tIN\tNS\tl.gtld-servers.net.\ncom.\t172800\tIN\tNS\tm.gtld-servers.net.\n;; Received 492 bytes from 199.7.83.42(l.root-servers.net.) in 9 ms\n\ngoogle.com.\t172800\tIN\tNS\tns2.google.com.\ngoogle.com.\t172800\tIN\tNS\tns1.google.com.\ngoogle.com.\t172800\tIN\tNS\tns3.google.com.\ngoogle.com.\t172800\tIN\tNS\tns4.google.com.\n;; Received 168 bytes from 192.5.6.30(a.gtld-servers.net.) in 85 ms\n\nwww.google.com.\t300\tIN\tA\t74.125.129.99\nwww.google.com.\t300\tIN\tA\t74.125.129.104\nwww.google.com.\t300\tIN\tA\t74.125.129.106\nwww.google.com.\t300\tIN\tA\t74.125.129.147\nwww.google.com.\t300\tIN\tA\t74.125.129.103\nwww.google.com.\t300\tIN\tA\t74.125.129.105\n;; Received 128 bytes from 216.239.34.10(ns2.google.com.) in 78 ms\n\n",
         "agentId":35,
         "queries":3,
         "finalQueryTime":78 
      }
   ]
 }
}
```

###  /instant/dns/server 

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| domain | domain to retrieve | www.google.com |
| type | record type to retrieve - typically is used for A, CNAME or NS records.  | A |
| server | nameserver to query | ns1.google.com |
| queryClass | IN or CH | IN |

**Example:**

```text
curl https://api.thousandeyes.com/instant/dns/server.json?authToken={authToken} -d '{"agentId":35, "server":"ns1.google.com","domain":"www.google.com", "type":"A"}' -H "Content-Type: application/json"
```

**Outputs:**

```text
{
 "dns": {
    "server": [
      {
        "agentName":"My Enterprise Agent",
        "countryId":"US",
        "agentId":35,
        "server":"ns1.google.com",
        "resolutionTime":52,
        "mappings":"74.125.129.104\n74.125.129.106\n74.125.129.105\n74.125.129.103\n74.125.129.99\n74.125.129.147"
     }
   ]
 }
}
```

### /instant/web/http-server

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| url | URL to retrieve | http://www.google.com |

**Example:**

```text
curl https://api.thousandeyes.com/instant/web/http-server.json?authToken={authToken} -d '{"agentId":35, "url":"http://www.google.com"}' -H "Content-Type: application/json"
```

**Outputs:**

```text
{
 "web": {
    "httpServer": [
       {
         "agentName":"My Enterprise Agent",
         "countryId":"US",
         "responseCode":200,
         "numRedirects":0,
         "errorType":"None",
         "dnsTime":17,
         "connectTime":159,
         "sslTime":365,
         "waitTime":175,
         "receiveTime":318,
         "wireSize":44163,
         "agentId":35,
         "responseTime":717,
         "fetchTime":1036
       }
    ]
  }
}
```

###  /instant/web/page-load 

**Inputs:**

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| url | URL to retrieve | http://www.google.com |

**Example:**

```text
curl https://api.thousandeyes.com/instant/web/http-server.json?authToken={authToken} -d '{"agentId":35, "url":"http://www.google.com"}' -H "Content-Type: application/json"
```

**Outputs:**

```text
{
 "web": {
   "pageLoad": [
      {
        "agentName":"My Enterprise Agent",
        "countryId":"US",
        "connectTime":503,
        "sslTime":254,
        "waitTime":1469,
        "receiveTime":763,
        "agentId":97,
        "responseTime":384,
        "fetchTime":2739,
        "totalSize":365004,
        "numObjects":9,
        "numErrors":0,
        "domLoadTime":517,
        "pageLoadTime":1370
      }
   ]
  }
}
```

### /instant/web/transactions 

**Inputs:**

As with existing instant tests, transaction tests require a transaction to exist prior to executing it in an instant test:

| **Property** | **Description** | **Example** |
| :--- | :--- | :--- |
| agentId | ID of Enterprise Agent to run instant test from | 35 |
| testId | ID of the transaction test to run | 1234 |

**Example:**

```text
curl https://api.thousandeyes.com/instant/web/transactions.json?authToken={authToken} -d '{"agentId":35, "testId":255}' -H "Content-Type: application/json"
```

**Outputs:**

```text
{
 "web": {
   "transaction": [ 
     {
        "agentName":"My Enterprise Agent",
        "countryId":"US",
        "stepsCompleted":1,
        "totalSteps":1,
        "componentErrors":0,
        "agentId":35,
        "transactionTime":3074,
        "errorDetails":""
      }
    ]
  }
}
```

