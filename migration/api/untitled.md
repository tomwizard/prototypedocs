# Create/Update/Delete tests using the ThousandEyes API

The ThousandEyes API supports creating, editing, and deleting tests programmatically.  

This feature is restricted to users with Account Admin privileges or higher.  Users without account admin privileges will receive an HTTP/403 error when attempting to post a write request.

The NEW, UPDATE and DELETE endpoints have been added to each test endpoint.  Content must be submitted using a POST request, and all POST requests must contain a "Content-Type: application/JSON" header.

```text
/tests/network/new
/tests/network/{testId}/update
/tests/network/{testId}/delete

/tests/dns-trace/new
/tests/dns-trace/{testId}/update
/tests/dns-trace/{testId}/delete

/tests/dns-server/new
/tests/dns-server/{testId}/update
/tests/dns-server/{testId}/delete

/tests/dns-dnssec/new
/tests/dns-dnssec/{testId}/update
/tests/dns-dnssec/{testId}/delete

/tests/http-server/new
/tests/http-server/{testId}/update
/tests/http-server/{testId}/delete

/tests/page-load/new
/tests/page-load/{testId}/update
/tests/page-load/{testId}/delete

/tests/transactions/{testId}/update
/tests/transactions/{testId}/delete
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

