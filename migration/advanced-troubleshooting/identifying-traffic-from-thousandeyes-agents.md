# Identifying traffic from ThousandEyes Agents

Users may need to identify traffic from ThousandEyes Agents in order to separate monitoring traffic in their web metrics or web server logs, allow traffic that would otherwise be blocked by web application firewalls or intrusion detection/prevention systems, handle the traffic in ways different from production traffic or for other reasons.

Two methods of identifying ThousandEyes-generated traffic are available: an HTTP header in the web request or the source IP address of the Agent sending the web request. Using an HTTP header provides a per-test option for Web Layer test types.  In contrast, the source IP address method identifies all Agent traffic from any test type.

## HTTP Headers

The following HTTP request headers are available to customers:

* The ThousandEyes-specific header
* A custom HTTP header
* The User-Agent header

Each header's configuration is described below, along with instructions for viewing the request headers sent in your test data.

The ThousandEyes-specific header, a custom header or a User-Agent header can be used by mechanisms that parse an HTTP header to make filtering decisions.  Note that if a request is using SSL/TLS \(an https:// URL\) then the mechanism must be able to see the unencrypted HTTP traffic, as an HTTP header is encrypted when sent by a client \(the ThousandEyes Agent, in this scenario\).

### ThousandEyes Header

ThousandEyes adds the following header to all HTTP requests of any Web Layer test type:

```text
X-ThousandEyes-Agent: yes
```

This header cannot be removed via test configuration.  This header is the best choice for users wishing to filter on an HTTP header.

### Custom Header

Users may add any custom header of their own choosing with the **Custom Headers** field.  The field is available in the Advanced Settings tab of the test configuration.  Enter the name of the header, a colon and a space, followed by the value of the header.  In the example below, the header name is "X-My-Custom-Header" and the value is the string "Hello World!".

IMAGE MISSING

Multiple headers can be entered by typing the Enter/Return key when you are finished entering the first header.

**NOTE:** Custom Headers in Page Load and Transaction tests are only inserted into the request for the test's target page.  Subsequent requests for objects in the DOM or other pages \(Transaction tests\) will not use the **Custom Header** field's contents. To identify the subsequent requests, some other session-based method would be required.

### User-Agent

By default, the User-Agent in an HTTP header from Web layer tests does not uniquely identify ThousandEyes Agents.  HTTP Server tests send a User-Agent string based on the "curl" program, for example:

```text
User-Agent: curl/7.48.0-DEV
```

By default, Page Load and Transaction tests send the User-Agent string associated with the Chromium browser and operating system running the Agent, for example:

```text
User-Agent: Red Hat Enterprise Linux/CentOS 7.x: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36
```

These defaults can be changed by selecting the Advanced Settings tab on the test configuration page, and setting the **User Agent** selector to a different value than "Default".  To use a custom string, select "Custom", then enter your desired User-Agent string in the text field \(other settings in the selector represent User-Agent strings of standard browsers\).

**NOTE:**  Page Load tests include an HTTP Server test for the HTTP Server View, so by default the two default User-Agent strings are sent, separately.  However, configuring a non-default **User-Agent** value will set both the Page Load and HTTP Server test User-Agents to the same string.

### Viewing Request Headers

A test's HTTP request headers can be displayed in test results:

IMAGE MISSING

#### HTTP Server test

To view the request headers of an HTTP Server test, navigate to the on the test results page, then click on the **View Headers** link on the Map tab, or click on the **\[Headers\]** link in the Response Code column of the Table tab:

IMAGE MISSING

To see the **View Headers** link, an Agent must be selected.  The Table tab does not require Agent selection before displaying the **\[Headers\]** link:

IMAGE MISSING

#### Page Load and Transaction tests \(BrowserBot\)

To view the request headers in a Page Load or Transaction test, first select the **Show HTTP headers in waterfalls** checkbox in the Advanced Settings tab of the test configuration:

IMAGE MISSING

then mouse over the Headers icon in the Waterfall tab of the test results page:

IMAGE MISSING

## Agent IP Addresses

Identification of traffic can be performed using the source IP addresses of ThousandEyes Agents. Lists of Agent IP addresses can be obtained in the app.thousandeyes.com application user interface, or through the application programming interface \(API\).  For Enterprise Agents, the former method is quick and easy.  For obtaining Cloud Agent IP addresses, large numbers of Enterprise Agent IP addresses or for obtaining a list of both Cloud and Enterprise Agent addresses, the application programming interface \(API\) is preferable.

With a comprehensive list of Agent IP addresses, whitelists or filters can then be constructed for web analytics programs, firewall rulesets, intrusion detection systems and other purposes.

### Application User Interface

To obtain the IP address of an Enterprise Agent, log into your ThousandEyes account and go to the SETTINGS &gt; Agents &gt; Enterprise Agents page.  Under the Agents tab, expand the row with the Enterprise Agent.  In the **General Info** section, note the IP address from either the **Private IP Address** or **Public IP Address**, depending on which address will be seen by your filtering mechanism.

If your Enterprise Agent is part of an Enterprise Agent Cluster, be certain to add the IP addresses of all cluster members in order to ensure that any test assigned to the cluster is filtered. Changes to the configuration of an existing cluster can cause a test to be re-assigned to a different cluster member. Under the Clusters tab of the Enterprise Agents page, expand the row with a cluster and note the Enterprise Agents listed in the **Cluster Members** field. Obtain all members' IP addresses using the method in the previous paragraph.

### Application Programming Interface

A listing of current IP addresses of all Cloud and Enterprise Agents available to your account can be obtained by querying the ThousandEyes API. Consult the ThousandEyes Knowledge Base article [Obtaining IP Addresses of ThousandEyes Agents](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnuKAC) for instructions.

Obtaining Cloud Agent IP addresses via API is preferable because of the large number of Cloud Agents.  Each Cloud Agent geographic location contains multiple Agent instances, each with a unique IP address.  Furthermore, tests can be assigned to any instance within a geographic location and can change without notice.  Therefore, whitelisting or filtering a single Cloud Agent location requires using all IP addresses from the geographic location.

