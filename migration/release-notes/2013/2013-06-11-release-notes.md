# Release Notes: 2013-06-11

Editor's note: As we get closer and closer to launch, our feature list is growing as well.  This list really only accounts for a small portion of the actual effort that went into the release.  My hat is off to the development team for a monumental amount of effort this week.  

Without further ado, let's get on with the show.

## Live Sharing

Live sharing is now accessible to all accounts using the ThousandEyes platform.  First announced in our May 21, 2013 release notes \(find them [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmAKAS)\), you can now share a live view of a test with another ThousandEyes customer.  

## Test settings

### Multiple tests referencing the same URL

Due to popular demand, you can now create multiple tests referencing the same target URL.  This will facilitate creating region-specific alert rules against a particular test.  In instances where a second test is being created with the same target URL as another test, a warning will show, and if using the default name for the test, a number will be appended following the test.

The key idea behind this allows you to manage custom alert settings for different geographies: for example, alert when 2+ agents in North America have response time &gt; 100ms, vs 2+ agents in Asia/Pacific have response time &gt; 200ms.

### Allow test data to be shared with service provider

We are beginning preparations to enable customers to make their test data available to service providers, in order to facilitate troubleshooting activities between the service provider \(who is a ThousandEyes customer\), and the organization.  All tests will show an option in test settings, "Allow test data to be shared with service provider", which currently defaults to unchecked.  Once this option is checked, the service provider will see that there is additional test information available, and allows a representative of the service provider organization to request a live share of the data, in order to manage collaborative troubleshooting.

The process, as it is intended will be as follows:

1. Service provider registers certain authoritative domains
2. Admin from organization checks the 'allow test data to be shared with service provider' option on a test
3. Service provider searches for sharable data
4. Once found, a service provider representative requests access to the data
   1. Request is authorized by an account admin of the owning Organization
      * Live test data is shared using Live Sharing feature.  Access remains open until sharing is disabled.
   2. Request is denied by an account admin
      * Service provider does not see any data

### Page loads now have a configurable timeout

We've added a configurable timeout on page load tests.  To modify the timeout value, change the slider position.  Page load timeout must be higher than the target page load time, and target page load time must be higher than the target HTTP response time.  An excerpt of the settings can be found below.

IMAGE MISSING

## Timeline change: Cloud Agent reference metrics

Sometimes, an agent can trigger an alert, because the agent itself is experiencing connectivity problems.  This release we've added the concept of agent reference metrics, and are testing our own agent infrastructure with our own agent network.  When an agent fails to respond to the reference tests, a grey bar will be shown on the reference line below the timeline.  Hovering over this bar will show that a particular agent is having problems, and provide details around the specific agent.  A sample of the grey bar and detailed text can be found below:

IMAGE MISSING

## Alert rules 

### Email notification once alert clears

How about some good news for a change?  You can now modify your alerts to include email notification when an alert clears, and is returned to a non-triggered state.  To enable this option, check the check the option in alerts to notify when alert clears.

IMAGE MISSING

1. Notify when alert clears will send an email once the alert is returned to a healthy state.
2. Add personal notes which will be included in the alert.  This may include contact instructions for a NOC, or otherwise.  A sample of an alert email with notes included can be found below:

IMAGE MISSING

_Remember_: Default alert rules cannot be modified.  Default alert rules do not include notification when the system is returned to a known good state.

### New option: DNS Server Mapping alert

Alerts can now be configured to alert when a mapping returned by a DNS server test is not in a list of customer-provided mappings.  Enter each IP address in a separate entry for the alert condition, or specify an entire subnet, in the form 192.168.1.0/24.

IMAGE MISSING

### Prefix-based DNS+ Mapping alert

For DNS+ Domain tests, admins can now define alerts where the resultant mapping is not in a specific subnet, as opposed to a specific IP address, or group thereof.  Specify the alert criteria in a prefix format, such as 192.168.1.0/24.

## API changes!

As has become a common thread in recent releases, we've continued the development of the ThousandEyes API.  This release contains a number of additions, per the list below:

### API Versioning

Beginning today, we have begun versioning the ThousandEyes API. We will support the current and two previous versions of the API at all times. Today's release will begin v2 of the ThousandEyes API.

To access a specific version of the ThousandEyes API, provide the version number in the request URI:

```text
https://api.thousandeyes.com/v2/{endpoint}
```

* when specifying no API version, the latest version will be used
* when specifying a version that has been deprecated, the earliest available version will be used.

**Change Policy**

ThousandEyes may modify the attributes and resources available to the API and our policies related to access and use of the API from time to time without advance notice. ThousandEyes will use commercially reasonable efforts to notify you of any modifications to the API or policies through notifications or posts on the ThousandEyes Customer Success Center.  ThousandEyes also tracks deprecation of attributes of the API on the ThousandEyes API page, located here.

ThousandEyes will provide an update to the version of the API in circumstances where the structure of the API output substantively changes, format is modified, or code is deprecated.

Support for current and two prior versions of the ThousandEyes API will be provided at all times. Attempts to access the ThousandEyes API with no version specified will result in the latest version being used. Attempts to access a deprecated version of the API will result in a response from the oldest supported version of the API.

### API v2 release changes:

**Disallowed requests**

Requests with a parameter of window=0, or with parameters from= and to= set to the same value, will result in an http/400 error.  This was done since these requests do not return any data, and will prevent the inadvertent misuse of the API.

**Field changes**

Each endpoint which returns the information about a test will now include either two or four additional fields:

* _createdBy_ \(shows the name and email address of the user who created the test\)
* _createdDate_ \(shows the date and time that the test was created\)
* _modifiedBy_ \(only populated when the test has been modified, shows the name and login of the user who made the last change\)
* _modifiedDate_ \(only populated when the test has been modified, shows the date and time of the last modification to the test\)

**Addition of traceroute data endpoints**

**Traceroute Summary**

Two new endpoints are now available, and provide traceroute data to the requester.

```text
https://api.thousandeyes.com/v2/net/path-vis/{testId}
```

This endpoint will return the summary of the traceroute, and provide destination IP and list of endpoints, including a destination flag and total number of hops from the agent to the endpoint.  This endpoint supports both the window and from/to parameters, to return data related to a specific window.  A JSON sample of the output is shown below.  Note the array of 3 elements in the endpoints object - since the traceroute is run three times from each agent during each test, the information given indicates the final endpoint for each of the traceroutes run during the test round.

JSON sample:

```text
{
 "net": {
      "test": {
           "enabled": 1,
           "testId": 1158,
           "testName": "https://app.thousandeyes.com",
           "interval": 900,
           "url": "https://app.thousandeyes.com",
           "modifiedDate": "2013-06-06 22:53:53",
           "modifiedBy": "Dave Fraleigh (dave@thousandeyes.com)",
           "createdBy": "Dave Fraleigh (dave@thousandeyes.com)",
           "createdDate": "2013-03-29 19:58:42"
      },
      "pathVis": [
           {
           "agentName": "Palo Alto, CA",
           "countryId": "US",
           "date": "2013-06-11 16:00:09",
           "location": "San Francisco Area",
           "server": "app.thousandeyes.com:443",
           "serverIp": "208.185.7.120",
           "permalink": "https://app.thousandeyes.com/net/path-vis?__a=315&testId=1158&roundId=1370966400&serverId=1716&agentId=128",
           "agentId": 128,
           "roundId": 1370966400,
           "endpoints": [
                {
                     "numberOfHops": 5,
                     "ipAddress": "208.185.7.120",
                     "responseTime": 4
                },
                {
                     "numberOfHops": 5,
                     "ipAddress": "208.185.7.120",
                     "responseTime": 5
                },
                {
                     "numberOfHops": 5,
                     "ipAddress": "208.185.7.120",
                     "responseTime": 5
                }
           ]
      }
 }
```

**Detailed Traceroute**

We have also added a detailed traceroute endpoint, which is formatted in a similar structure to the summary endpoint.  The detailed traceroute endpoint requires both agentId and roundId, which can be obtained from the summary endpoint.  

```text
https://api.thousandeyes.com/v2/net/path-vis/{testId}/{agentId}/{roundId}
```

Similarly to the traceroute summary endpoint, the pathVis element contains two additional elements:

* A _routes_ object, which contains 3 routes, in an array.  
* Each of the arrays will contain an array of _hops_ taken by the traceroute.  
* Any traceroute returning a star \(\*\) will be skipped in output, and the hop count for the next element will increment by the number of stars transited.  

```text
{
 "net": {
      "test": {
           "enabled": 1,
           "testId": 1158,
           "testName": "https://app.thousandeyes.com",
           "interval": 900,
           "url": "https://app.thousandeyes.com",
           "modifiedDate": "2013-06-06 22:53:53",
           "modifiedBy": "Dave Fraleigh (dave@thousandeyes.com)",
           "createdBy": "Dave Fraleigh (dave@thousandeyes.com)",
           "createdDate": "2013-03-29 19:58:42"
           },
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

**Structure change**

The basic-http endpoints have been deprecated with this version 2 of the API.  They have been replaced with http-server endpoints.  These can be found in the list below:

| **Deprecated endpoint** |  | **Replacement endpoint** |
| :--- | :--- | :--- |
| /tests/basic-http |  | /tests/http-server |
| /web/basic-http/{testId} |  | /tests/http-server/{testId} |

**Agent data**

For any endpoint which includes an Agent component:

* Field label "locationName" has been changed to "agentName"
* added field agentId \(integer\)

**Addition of write API**

This release shows we've added a write-based API for tests in ThousandEyes.  Only users with Account admin privileges or higher have permission to use the write-based API.  Users without account admin privileges will receive an HTTP/403 error when attempting to post a write request.

The NEW, UPDATE and DELETE endpoints have been added to each test endpoint.  Content must be submitted using a POST request, and all POST requests must contain a "Content-Type: application/json" header.

```text
/tests/http-server/new
/tests/http-server/{testId}/update
/tests/http-server/{testId}/delete
```

To show a basic example of an add request, using cURL:

```text
curl https://api.thousandeyes.com/tests/network/new.json?authToken=<my_authToken> \
-d '{"interval": 300, "agents": [{"agentId": 113}], "testName": "API network test addition for www.thousandeyes.com", "server": "www.thousandeyes.com"}' \
-H "Content-Type: application/json"
```

this will return successfully once the test has been created:

```text
{
 "test": [
  {
     "enabled":1,
     "testId":1586,
     "testName":"API network test addition for www.thousandeyes.com",
     "interval":300,
     "server":"www.thousandeyes.com:80",
     "agents":[
       {
          "agentId":113,
          "agentName":"Bucharest, Romania",
          "location":"Bucuresti, Romania",
          "countryId":"RO",
          "ipAddress":"89.36.27.146",
          "prefix":"89.36.24.0/21",
          "network":"HOSTWAY ROMANIA SRL (AS 39756)",
          "public":1
       }
     ],
     "createdBy":"Dave Fraleigh (dave@thousandeyes.com)",
     "createdDate":"2013-06-12 01:22:40"
     }
  ]
}
```

I can then update the same request by modifying the JSON data:

```text
curl https://api.thousandeyes.com/tests/network/1586/update.json?authToken=<my_authtoken> \ 
-d '{"interval": 900, "agents": [{"agentId": 113}], "testName": "this is a new name and interval for my test"}' \ 
-H "Content-Type:application/json" 
```

Note that only certain fields can be updated in an update request:

* interval
* testName
* agents

```text
{
 "test": [
  {
     "enabled":1,
     "testId":1586,
     "testName":"this is a new name and interval for my test",
     "interval":900,
     "server":"www.thousandeyes.com:80",
     "agents":[
       {
          "agentId":113,
          "agentName":"Bucharest, Romania",
          "location":"Bucuresti, Romania",
          "countryId":"RO",
          "ipAddress":"89.36.27.146",
          "prefix":"89.36.24.0/21",
          "network":"HOSTWAY ROMANIA SRL (AS 39756)",
          "public":1
       }
     ],
     "createdBy":"Dave Fraleigh (dave@thousandeyes.com)",
     "createdDate":"2013-06-12 01:22:40",
     "modifiedBy":"Dave Fraleigh (dave@thousandeyes.com)",
     "modifiedDate":"2013-06-12 02:10:13",
     }
  ]
}
```

 Then, to delete the same test, run the following command:

```text
curl https://api.thousandeyes.com/tests/network/1586/delete.json?authToken=<my_authToken> \
-d '' \
-H "Content-Type:application/json" 
```

You'll get an empty JSON response back, and the test will be gone from the front end.

Our API documentation will be updated in the coming week to reflect these new additions.

