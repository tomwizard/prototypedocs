# Release Notes: 2013-09-05

### Release update 2013-09-05

Welcome to September!  Time flies when you're having fun and working hard - and our teams have been toiling on some long awaited features.  Check out the release contents below.

## Dashboard: Instant filter

The tests widget in the dashboard now supports the use of an instant filter, to allow users to quickly reduce the number of tests shown.  Enter a search string, which searches the test name column \(combining the test name and target\), and the contents of your results widget will be instantly filtered based on the search criteria. 

IMAGE MISSING

Note: filtered results do not persist, but can be configured using either the Widget Settings or Dashboard Settings links.

## POSTing data using HTTP Server test

We've expanded our HTTP Server test sets to support POSTing data to a target site.  Prior to today's release, the only request method available was an HTTP GET request.  

To create an HTTP Server test using the POST request method, simply expand the advanced options section of the new test interface, and change the request method to POST.  Next, insert the application/x-www-form-urlencoded POST body into the field which appears for this use.  A sample image showing the instant test interface can be found below:

IMAGE MISSING

Note, this feature is not yet supported by the ThousandEyes API, however it is supported by both the HTTP Server test interface, and by HTTP server instant tests.

## API changes

### Basic authentication now supported

Beginning with this week's release, users can now use either the token-based authentication method, or a basic authentication \(username/password\) to obtain data using the ThousandEyes API.  Using Basic authentication increases the security of your token, by not including it in the URL  As a reminder, your authToken is the same as a password, and personally identifies you with our system. All actions taken using your authToken are logged under your specific user account, so your authToken should never be disclosed to \(or shared with\) anyone, including ThousandEyes personnel.

IMAGE MISSING

When prompted, your User name is the email address you use to log in to ThousandEyes, and your password is your authToken.  This applies to both organizations using Single Sign On \(SSO\), and to those using traditional authentication.

**Using cURL:**

```text
Shazenfreude:~ dave$ curl -u {username}:{authToken} https://api.thousandeyes.com/{endpoint}
```

### New endpoint: /agents

We've added an endpoint to pull up a list of agents assigned to each organization.  To access this data, please use the following URL:

```text
https://api.thousandeyes.com/v2/agents.json
```

This will return a list of agent IDs, locations, country and whether or not the agent is public or private, per the example below.

```text
{
    "agents": [
        {
            "agentId": 108,
            "agentName": "Boston, MA",
            "location": "Boston Area",
            "countryId": "US",
            "public": 1
        },
        {
            "agentId": 421,
            "agentName": "vm-dave-dev-1",
            "location": "San Francisco Area",
            "countryId": "US",
            "ipAddress": "192.168.2.102",
            "prefix": "72.67.0.0/16",
            "network": "Verizon Business/UUnet (AS 701)",
            "public": 0
        }
     ]
```

Please note: IP address, prefix and network information is not exposed for Cloud Agents, since requests may be served from multiple physical servers in a single location.  Note: the ipAddress field contains the server's private IP address, whereas the prefix information applies to the public address.  We will augment this information in the future to include the public IP address as well.

To obtain the IP address, prefix and network information of a Cloud Agent assigned to a specific test, use the /tests/{testId} endpoint.

If you have any questions regarding these notes, please contact our Customer Success team by emailing support@thousandeyes.com.

