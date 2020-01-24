# Working with Test settings

The ThousandEyes platform enables customers to test networked assets owned by the organization, and test SaaS-based assets to which the organization subscribes.  This article describes how to create and work with tests using the Tests Settings page.

Click on the [**Cloud & Enterprise Agents &gt; Test Settings**](https://app.thousandeyes.com/settings/tests/?tab=settings), where you can view a list of the tests that have been configured in the Account Group.

## Without Tests configured

Upon initial login into a new ThousandEyes account, no test will have yet been created and an empty Dashboard will be displayed:

IMAGE MISSING

## Adding tests

To begin adding tests, select [**Cloud & Enterprise Agents &gt; Test Settings**](https://app.thousandeyes.com/settings/tests/?tab=settings) in the left-hand navigation pane.  The Tests Settings page will appear, with the **Add New Test** section visible:

IMAGE MISSING

Highlighted areas on the page are documented in the following list:

**1\) Test Layer:** Available test layers are shown in a ribbon at the top of the page.  Only test layers which are available to your organization will be shown.  Each category is documented in the section below entitled Test Details.

**2\) Test Type:** Test types for the highlighted test layer. 

**3\) Basic / Advanced Settings:** This set of tabs allows users to toggle between Basic and Advanced test settings

**4\) Agents:** This drop-down lists the ThousandEyes Cloud Agents and Enterprise Agents available to your account.  Select one or more agents to assign them to this test.

**5\) Alerts:** When the Enable box is checked, the alert rules selected in the drop-down list will be active for the test. You can select alert rules with the drop-down list, and create, modify and delete alert rules with the Edit Alert Rules link.

**6\) Views Enabled for This Test:** This panel shows which views will be available, given the current test type and configuration selections.

**7\) Projected Usage**: This meter shows projections of the number of test units consumed once the test configured, as a percentage of the organization's monthly unit allotment.  Two projected values are shown:

This Month: The percentage of the organization's current monthly unit consumption that will be used once this test is added

Next Month: The percentage of the organization's monthly unit consumption that will be used in a full month once this test is added.

Refer to the ThousandEyes Knowledge Base article [How Unit consumption works](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmoKAC_How-Unit-consumption-works) regarding unit consumption.  
**NOTE:** The Projected Usage panel appears once the user selects one or more Cloud Agents from the Agents selector. Selecting Enterprise Agents will not cause the meter to appear.

**NOTE:** Some panels may not appear if your user account is not assigned a role with the appropriate permissions.  Check your account's roles on the **Profile** tab of the [Account Settings](https://app.thousandeyes.com/settings/account) page.  Other users' roles can be viewed on the **Users** tab. Check the permissions assigned to each role on the **Roles** tab.  For more information on roles and permissions, see the ThousandEyes Knowledge Base article [Role-Based Access Control explained](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained).

Once you click the **Create New Test** button, the test will be added and will begin collecting its first set of data.

## With tests configured

If the account has at least one Agent available, then the interface will show a list of tests configured under the account. The image below shows a sample list of tests:

IMAGE MISSING

Each test entry in a list depicted above can be expanded. When expanded, the test's configuration is revealed. Here is an example of a Page Load test configuration:

IMAGE MISSING

A user with appropriate privileges is able to enable or disable any test listed under the Account Group.  Disabling a test will not delete the test data, but the data will expire on a daily rolling basis \(see the ThousandEyes Knowledge Base article [How long does ThousandEyes retain customer data?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn0KAC) for more information about data retention periods\). Disabled tests do not consume [Cloud Units](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmoKAC).

Clicking the "..." icon will show you additional test options. You can delete the test from that menu by clicking the **Delete** button.

IMAGE MISSING

The deleted tests are available to be recovered for 31 days after deletion. They can be found in the [Cloud & Enterprise Agents &gt; Test Settings](https://app.thousandeyes.com/settings/tests/?tab=settings) page, then clicking the Trash Bin icon highlighted in the following image:

IMAGE MISSING

Deleted tests can be recovered by clicking on the **Recover** button, as shown below.

IMAGE MISSING

## Filtering Tests

Use the "Add a filter" link to filter the test listing by various criteria. The screenshot example below illustrates how to filter by tests that are not Enabled or in other words displaying disabled tests.  After Navigating to [Cloud & Enterprise Agents &gt; Test Settings &gt; Tests Tab](http://app.thousandeyes.com/settings/tests/?tab=settings):

1. Select "Add a filter" link 
2. Select "Enabled" from the drop down menu
3. A new drop down will appear with the options Yes/No \(It is possible to select either or both\)
4. For the purposes of this example Select "No" to show tests that are disabled. IMAGE MISSING IMAGE MISSING

##  Updating Tests

After a test is created, the settings of the test configuration can be updated. There are some exceptions, the table below lists the parameters that cannot be edited in specific test types:  
 

| Test Type | Immutable setting |
| :--- | :--- |
| BGP | Prefix |
| Transaction | Target |
| Transaction \(Classic\) | Target |
| DNS+ Domain | Domain |
| DNS+ Server Latency | DNS Server |

##  Test Details

The following lists each of the test types, including inputs, outputs and measurements.

### Network Layer tests

The Network layer provides two test types: Agent to Server and Agent to Agent. Both test types contains two views.  The Overview view shows data on packet loss, latency, jitter \(the standard deviation of the latency\), path MTU, \(Agent to Server and Enterprise Agents only\) bandwidth and \(Agent to Agent only\) throughput. Path Visualization view is a traceroute-like map of each router in the path from agent to target.

**Inputs**

* **Test Type:** Agent to Server or Agent to Agent.
* **Test Name:** This optional parameter gives the test a label.  When no label is provided, then the values in the **Target** and \(if the **Protocol** is TCP\) the **Port** fields will be combined to comprise the **Test Name.** A Test name cannot exceed 255 characters.
* **Interval:** How frequently the test will be run.
* **Alerts:** When the **Enable** box is checked, the Alert Rules and Alert Suppression Windows selected in their respective drop-down list will be active for the test. You can create, modify and delete Alert Rules with the **Edit Alert Rules** link.

**Agent to Server Test Basic Configuration tab**

* **Target:** Domain name or IP address.
* **Protocol:** The protocol used when sending packets to the target.
* **Port:** The port number on the target to which the test sends packets, if the Protocol selected is TCP.
* **Agents:** ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account. Select one or more Agents to assign them to this test.

**Agent to Server Test Advanced Settings tab**

* **Perform bandwidth measurements:** Check this box to perform bandwidth measurements. Only applies to Enterprise Agents.
* **Perform MTU measurements:** Check this box to determine path maximum transmission unit measurements in the Path Visualization View.
* **Collect BGP data:** Check this box to enable the BGP Path Visualization View. The "BGP Public Monitors" option button allows users to choose whether ThousandEyes' public BGP Monitors should be used for monitoring target prefixes. The "Private BGP Monitors" drop-down box allows users to select which private BGP Monitors should be used for monitoring target prefixes. By default, all public and private monitors are selected.

   Note that some monitors are IPv4 monitors and some are IPv6 monitors.  Tests with IPv4 targets will display only IPv4 monitors in the BGP Path Visualization; similarly, tests with IPv6 targets display only IPv6 monitors in the BGP Path Visualization.

* **Transmission Rate:** Select the checkbox to “Enforce fixed packet rate”. This will reveal a slider bar that offers the option to reduce rate packets are sent to measure the network in packets per second.
* **No. of Path Traces:** Three path trace packets are used by each Agent by default to discover each hop in the Path Visualization to the target.  Uncheck the box to display a slider which allows selection of 1 - 10 packets.  To learn more about Path Traces refer to this [article](http://https//success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RslCAE_What-is-Path-Trace).
* **Ping Payload Size:** Payload size \(not total packet size\) for the End-to-End metric's probes.  When set to "Manual", ping payload size allows values from 0 to 1400 bytes.  When set to "Auto", payload sizes are 0 bytes for ICMP-based tests and 1 byte for TCP-based tests.  Noted that these values can be set only on Agent-to-Server tests, and not on included network metrics of other tests, such as HTTP Server, Page Load or DNS Server tests.
* **DSCP selector:** Set the Differentiated Services Code Point \(DSCP\) field of the IP header for probe packets, in order for the packets to be handled by quality-of-service \(QoS\) devices. The default value is DSCP=0 \(best effort\).

**Agent to Agent Test Basic Configuration tab**

* **Target Agent:** Select a ThousandEyes Enterprise Agent  available to your account.
* **Agents:** ThousandEyes Enterprise Agents agents that are available to your account. Select one or more Agents to assign them to this test.
* **Direction**: Select the direction of network and \(optionally\) throughput measurements between Agents as follows:
  * **Source to Target:** All selected Agents will perform network measurements to Target Agent.
  * **Target to Source:** Target Agent will perform network measurements to each Agent selected under Agents tab.
  * **Both Directions:** Network measurements are performed from each selected Agent to Target Agent and from Target Agent to each selected Agent.
* **Protocol:** The protocol used when sending packets to the target.
* **Enable Throughput:** Check this box to perform throughput measurements in selected direction.
  * **Duration:** Use the slider to set time period for throughput measurements.
  * **Maximum Rate:** Agents send packet for set duration as fast as possible.
  * **Specified Rate:** Input sending rate of throughput packets.

**Agent to Agent Test Advanced Configuration tab**

* **Server Port:** The port number on the Target Agent to which Agents send packets.
* **MSS:** Set the Maximum Segment Size to Auto or Manually specifying the number in bytes to avoid fragmentation.  The range of manual sizes that will be accepted as valid to create or save this setting in a test is between 30-1400 bytes.   
* **Collect BGP data:** Check this box to enable the BGP Path Visualization View.The "BGP Public Monitors" option button allows users to choose whether ThousandEyes' public BGP Monitors should be used for monitoring target prefixes. The "Private BGP Monitors" drop-down box allows users to select which private BGP Monitors should be used for monitoring target prefixes. By default, all public and private monitors are selected.

   Note that some monitors are IPv4 monitors and some are IPv6 monitors.  Tests with IPv4 targets will display only IPv4 monitors in the BGP Path Visualization; similarly, tests with IPv6 targets display only IPv6 monitors in the BGP Path Visualization.

* **Transmission Rate:** Select the checkbox to “Enforce fixed packet rate”. This will reveal a slider bar that offers the option to reduce rate packets are sent to measure the network in packets per second.
* **No. of Path Traces:** Three path trace packets are used by each Agent by default to discover each hop in the Path Visualization to the target.  Uncheck the box to display a slider which allows selection of 1 - 10 packets.  To learn more about Path Traces refer to this [article](http://https//success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RslCAE_What-is-Path-Trace).
* **Payload Size:** Size of the packets for network and \(optionally\) throughput measurements:
  * **Auto:** Packet size is determined based on Path MTU
  * **Manual:** Packet size is IP header size + TCP or UDP header size + &lt;input value&gt; bytes.
* **DSCP selector:** Set the Differentiated Services Code Point \(DSCP\) field of the IP header for probe packets, in order for the packets to be handled by quality-of-service \(QoS\) devices. The default value is DSCP=0 \(best effort\).

#### Outputs

**Agent to Server** tests provide these two views:

1. **End-to-End Metrics** provides data on packet loss, latency, jitter \(the standard deviation of the latency\), path MTU and \(Enterprise Agents only\) bandwidth.
2. **Path Visualization** displays a router-by-router view of the nodes in the path from the Agents to the target, along with IP, MPLS and routing information about each node and link between nodes.

**Agent to Agent** tests provide these two views:

1. **End-to-End Metrics** provides data on packet loss, latency, jitter \(the standard deviation of the latency\), and throughput.
2. **Path Visualization** displays router-by-router view of the nodes in the path from the Agents to the target, along with IP, MPLS and routing information about each node and link between nodes. Arrows indicated direction of packet through the intermediate nodes.

### Routing Layer tests

The Routing layer provides one test type, BGP, which has a single view: the BGP Route Visualization. The BGP Route Visualization displays an autonomous system-by-autonomous system view of the nodes in the path from the BGP monitors to the target.

#### **Inputs**

* **Test Type:** BGP
* **Test Name:** This optional parameter gives the test a label.  When no label is provided, then the value in the **Prefix** field will be used. A Test name cannot exceed 255 characters.
* **Prefix:** A BGP prefix and prefix length in CIDR notation \(dotted-quad network address, a slash then integer netmask\).
* **Include covered prefixes:** When this box is checked, provide test results for covered prefixes of the netblock in the **Prefix** field.
* **Public BGP Monitors:** This option button allows users to choose whether ThousandEyes' public BGP Monitors should be used for monitoring target prefixes.
* **Private BGP Monitors:** This drop-down box allows users to select which private BGP Monitors should be used for monitoring target prefixes.

Note that some monitors are IPv4 monitors and some are IPv6 monitors.  Tests with IPv4 targets will display only IPv4 monitors in the BGP Path Visualization; similarly, tests with IPv6 targets display only IPv6 monitors in the BGP Path Visualization.

* **Alerts:** When the **Enable** box is checked, the Alert Rules selected in drop-down list will be active for the test. You can select Alert Rules with the drop-down list, and create, modify and delete alert rules with the **Edit Alert Rules** link.

#### Outputs

BGP tests provide the following view:

* **BGP Route Visualization** displays an autonomous system-by-autonomous system view of the nodes in the path from the monitors to the target, along with routing and geographical information about each node and link between nodes.

### DNS Layer tests

DNS Trace tests run queries against target DNS resource records, while DNS Server tests run queries against target servers. The tests measure resolution time and availability for the target.  DNSSEC tests provide keychain verification in a bottom-up manner.

#### Inputs

* **Test type:** _****_DNS trace, DNS Server, or DNSSEC.
* **Test Name:** This optional parameter gives the test a label.  When no label is provided, the value in the **Domain** field will be used as the test name. A Test name cannot exceed 255 characters.
* **Domain:** Domain name, record type, and \(DNS Server only\) class of the record in the test query.
* **Interval:** How frequently this test will be run.
* **Agents**: This drop-down lists the ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account.  Select one or more agents to assign them to this test.
* **DNS Servers:** \(DNS Server only\) The DNS servers that are queried for the domain name in the **Domain** field.  Click the **Lookup Servers** button to automatically populate the **DNS Servers** field with the authoritative name servers for the domain name in the **Domain** field.
* **Alerts:** When the Enable box is checked, the alert rules selected in drop-down list will be active for the test. You can select alert rules with the drop-down list, and create, modify and delete alert rules with the **Edit Alert Rules** link.
* **Advanced Settings:** \(DNS Server only\) Provides configuration of an associated Network test for the target server\(s\), per the [Network Test Advanced Settings tab](), and provides the **Send Recursive Queries** check box to request recursive queries be sent to the target server\(s\). The default is to send queries without recursion.

#### Outputs

* DNS Domain Trace and DNSSEC tests return a map of locations showing availability by location for the DNS record requested, returning the average query time.
* DNS Server tests query the authoritative nameservers from each location, showing availability and resolution time by location.  In addition to these metrics, network measurements can be enabled on DNS Server tests, which provides access to network measurement details \(and outputs\) against each authoritative nameserver specified in the test.

### DNS+ Layer tests

DNS+ Tests are only available to premium ThousandEyes accounts.  DNS+ tests query a list of open resolvers throughout the world for DNS information, and display a world map of DNS availability for the target domain, showing global and country-based list of mappings \(by mapping percentage\) and resolution time.

#### Inputs

* **Test type:** DNS+ Domain or DNS+ Server Latency
* **Test Name:** This optional parameter gives the test a label.  When no label is provided, the value in the **Domain** field will be used as the test name.
* **Domain:** \(DNS+ Domain\) Domain name and record type.
* **DNS Server:** \(DNS+ Server Latency only\) DNS server domain name or IP address.
* **Interval:** How frequently this test will be run.
* **Alerts:** When the Enable box is checked, the alert rules selected in drop-down list will be active for the test. You can select alert rules with the drop-down list, and create, modify and delete alert rules with the **Edit Alert Rules** link.

#### Outputs

* DNS+ Domain tests display a world map with countries colored according to availability, along with mapping and resolution time details.
* DNS+ Server Latency tests display a world map with countries colored according to latency.

### Web Layer tests

Web tests target a web server, and measure availability, response time, throughput, redirects, and response codes \(HTTP Server\) or time to load page objects \(Page Load\), including component count and providing a waterfall view of all page objects. Transaction tests perform a sequence of scripted actions from within an actual browser process, returning waterfall views of all the objects and pages loaded.  FTP Server tests target an FTP and measure availability, response time, throughput, and reply codes.

#### HTTP-based Inputs

* **Test type:** HTTP Server, Page Load, Transaction or Transaction \(Classic\) ****
* **Test Name:** This optional parameter gives the test a label.  Where no label is provided, the value in the **URL** field will be used as the test name, along with a protocol \("http://" by default\) prepended.
* **URL:** A URL, domain name or IP address, including TCP port. If a domain name or IP address is used \(i.e. protocol specification is not provided\) then "http://" is assumed.
* **Interval:** How frequently this test will be run.
* **Agents:** This drop-down lists the ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account.  Select one or more agents to assign them to this test.
* **Alerts:** When the Enable box is checked, the alert rules selected in drop-down list will be active for the test. You can select alert rules with the drop-down list, and create, modify and delete alert rules with the **Edit Alert Rules** link.
* **Transaction Script:** Transaction tests execute custom Selenium WebDriver-based scripts written in JavaScript language to simulate user interaction with web page elements.
* **Script commands:** Transaction \(Classic\) tests execute Selenium script commands to simulate user interaction with web page elements.
* **Advanced Settings:** Provides configuration of an associated Network test for the target server\(s\), per the [Network Test Advanced Settings tab](), and provides the following settings for either the selected test type or an associated HTTP Server View, as indicated below:
  * **HTTP Server Timing/Page Load Timing/Transaction Timing**
    * _Timeout:_ Seconds until the test type terminates due to an unresponsive target server. Defaults and maximum values vary by type of Web test:
      * For HTTP Server test, the default timeout is 5 seconds. The maximum timeout value is 60 seconds.
      * For Page Load test, the default timeout is 10 seconds. The maximum timeout value is either 0.25 \* interval \(in seconds\) or 60 seconds, whichever is lower.
      * For Transaction tests, the default timeout is 30 seconds. The maximum timeout value is either 0.25 \* interval \(in seconds\) or 180 seconds, whichever is lower.
    * _Target Time for View:_ Sets the color legend on the global map, and the corresponding font colors for the Agent results table.  For example, Response Time for an HTTP Server test sets the range of the legend from 0 seconds \(green end\) to 2x the Target Time for View \(red end\).  Colors for results up to .5x the Target Time for View will be green; between .5x and 1x will be yellow.
  * **HTTP Authentication**
    * _Username:_ The username for the account being accessed by the HTTP request\(s\).
    * _Password:_  The password for the account being accessed by the HTTP request\(s\).
    * _Scheme:_ The following are available
      1. HTTP Basic Authentication
      2. NTLMv2 \(a.k.a. Windows Integrated\) Authentication. NTLMv2 authentication is supported for HTTP Server tests only.
      3. Kerberos
      4. OAuth \(HTTP Server only\), two Initial Authentication Schemes supported with OAuth as under:
         1. Basic Authentication
         2. NTLM 
  * **HTTP Request**

    * HTTP Version: Select the HTTP version for requests:
      * Prefer HTTP/2: Attempt HTTP/2 and fallback to HTTP/1.1  if HTTP/2 is not available.
      * HTTP/1.1 Only: Send request\(s\) using HTTP/1.1 only, no attempt is made to utilize HTTP/2.
    * Window Size \(Page Load and Transaction tests only\): Select size and orientation \(phone or tablet\) from the various `Desktop`, `Phone` and `Tablet` options available, or configure a custom size. Defaults to `Desktop Small (1024x768)`.
    * _Request Method:_ \(HTTP Server only\) Select the HTTP request method--either GET or POST.  If POST is selected, you may specify data in the **POST Body** field.  The default is GET.
    * _SSL Version:_ Select the version of the SSL/TLS protocol to offer in the SSL Client Hello.  This will set the maximum version of SSL/TLS that the connection can use, but a lower version may be negotiated by the server.  The options are the following:
      * SSLv3: Use SSL version 3.0. No lower version can be negotiated.
      * TLSv1.0: The Agent will start the TLS negotiation at version 1.0.
      * TLSv1.1: The Agent will start the TLS negotiation at version 1.1.
      * TLSv1.2: The Agent will start the TLS negotiation at version 1.2.
      * Auto: The Agent will start the TLS negotiation at the highest version of TLS supported by its operating system.  Currently the highest version is TLS 1.2  Contact [support@thousandeyes.com](mailto:support@thousandeyes.com) if you require confirmation of the current version.
    * _Verify SSL certificate:_ By default, certificate-related errors will result in a test error.  Uncheck this box to ignore certificate errors during SSL/TLS negotiation.
    * _Custom Headers:_ Enter one or more HTTP header strings in the form &lt;stringname&gt;: &lt;value&gt;.  Note the whitespace between the literal colon character and the placeholder &lt;value&gt;.  The custom header\(s\) will be transmitted with the target page request \(Page Load test\) or each page request \(Transaction test\) but not for objects within a page. When adding multiple headers, delineate between individual headers using a line break.
    * _Override DNS:_ \(HTTP Server only\) Instead of using standard DNS resolution, allows you to specify the IP address to which the target's domain name will resolve.  Useful for targeting a specific server within a cluster, or when testing HTTPS URLs which require a Server Name Indication \(SNI\) in the TLS negotiation that is different from the domain name-to-IP address mapping required to access the URL.
    * _Client Certificate:_ \(HTTP Server only\) Configure a client-side certificate, which will be sent in the SSL handshake to the web server to authenticate the client.  Check the **Enable** box, then copy your client certificate \(both the private key and the public certificate\) in PEM format and paste into the **Client Certificate** field.

      If your certificate is in PKCS\#12 format \(.pfx file extension\), you may use the openssl utility to create a PEM version.  For example, the openssl command for a client certificate "mycert.pfx" with a password would be:

    ```text
    openssl pkcs12 -in mycert.pfx -out clientcert.pem -nodes -passin pass:<password>
    ```

    Then edit the output file "clientcert.pem" using a text editor to remove any text before, after or in between the certificate and private key.  The file should look like:

    ```text
    -----BEGIN RSA PRIVATE KEY-----
    MIIEpQIBAAKCAQEAtjjpbonL7xK2AiVPo7/n0uQiwjk3hN0B3bAR0wVPt6UYLc2h
    L+T5UOOU5xlNu1ydz2iyxbcV8sn6rtT4NGyRgeh91A+GvCRzR2GMH5vocNMNSuYh
    <lines omitted for brevity>
    Nx6ZWZekTlYrelnIM6FsUVUplwlYxU9UqBWeYcLx6BkrKKzoohFSTstI4PhuzE4P
    lSD/opYrkwCYiNmNX4Z8SU136fbz43FhFUNzmEePNEVLJ2mF0f2Y+ek=
    -----END RSA PRIVATE KEY-----
    -----BEGIN CERTIFICATE-----
    MIIEGzCCAwOgAwIBAgIJAOUXm6K8B9tnMA0GCSqGSIb3DQEBCwUAMIGjMQswCQYD
    VQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTEWMBQGA1UEBwwNU2FuIEZyYW5j
    <lines omitted for brevity>
    T4QRFKjtQiTzkGl4NT+wiLi+JLS3sQVpsmfqJ5cBLf91GOpFWQs65Kc7JdUfezs=
    -----END CERTIFICATE-----
    ```

    **NOTE:** The private key must be placed first, then the certificate.

  * **HTTP Headers**
    * _Show HTTP headers in waterfalls:_ \(Page Load and Web Transaction\) Make available HTTP request and response header information for each object in the waterfall displays.
  * **HTTP Response**
    * _Desired Status Code:_ \(HTTP Server and Page Load\) Sets the HTTP status code returned by the server that is defined as a successful test \(i.e. no errors will be displayed in the test table results, no response code-based alerts generated, etc...\). By default, either a 200-level or 300-level status code is considered a successful return code.  Uncheck the box and enter a response code in the field below to use a different response code.
    * _Verify Content:_ \(HTTP Server only\) Search the HTTP response headers and body \(similarly to a "curl -i" command\) for text matching a given [POSIX regular expression](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnCKAS_POSIX-Extended-Regular-Expression-Syntax). Headers and body are searched separately. If no match occurs, the test shows an error condition. **Note**: the HTTP Server test does not execute any JavaScript code, therefore the content generated by JavaScript cannot be verified by this feature. JavaScript generated content can be matched using a Web Transaction test.
    * _Limit Download Size:_ \(HTTP Server only\) Load only the first number of kiloBytes \(kB\) specified in the field below the Enable box.  The result is not guaranteed to be exactly the number specified, but can be slightly more--but always within a few percent, or less as the size of the download is increased.  Note that this function does not use an HTTP Range header, so the HTTP response code should not be affected \(i.e. success is a 200 OK response, not a 206 Partial Content response\).

  
 **FTP Server Basic Settings tab**

* **URL:** Specify
  * Protocol \(FTP, SFTP or FTPS\)
  * Domain name and port number of the server, separated by a colon.  If the port number is omitted, the defaults are:
    * FTP: 21
    * FTPS: 990
    * SFTP: 22
  * Path to the file \("Download" and "Upload" Request Types\) or directory on the server \("List" Request Type\).  Depending on the protocol, you will need either an absolute path \(starting point is the root directory, "/"\) or a relative path \(starting point is relative to the user's home directory or other directory per the server configuration\). FTP and FTPS use relative paths. SFTP uses an absolute path or a relative path.  
* **Username/Password:** Enter the username and password for the FTP account.  To perform anonymous FTP, please enter “anonymous” as the username.  The username field is required. The password field may be left blank, or you may enter an email address for the password, depending on the server requirements on anonymous access.   
* **Request Type:** Select “Download” to retrieve a file from the FTP server.  Select “Upload” to send a file to the FTP server.  Select “List” to retrieve a listing of the files in the directory specified by your **URL** setting. Downloads and uploads use "Image" \(binary\) transfer; listings use "ASCII" transfer.

   Note: The Upload setting will use a random sequence of bytes as the contents of the file upload. The remote filename will be taken from the **URL** field. It is not possible to specify the file contents, but the size of the file can be specified by the **Upload File Size** selector.

* **Limit Download Size/Upload File Size:** The number of kilobytes \(kB\) at which to stop the transfer.  Useful for transfers of large files, particularly with slow transfer rates which could result in reaching the test’s **Timeout** setting prior to completion.

   **NOTE:** Do not use the **Limit Download Size** or **Upload File Size** settings in combination with the **Desired Reply Code** setting.

* **Verify Content:** \(List Request Type only\) Check the **Enable** box and enter a regular expression in the field below to verify that a filename or other string\(s\) is present in your directory listing.

**FTP Server Test Advanced Settings tab**

* **Request Mode:** Select “Passive” or “Active” mode FTP.  The request mode governs the whether the client or server initiates the data channel’s TCP connection.  Passive mode is the more common mode, and is the mode used by web browsers when retrieving files via FTP. Active mode requires an inbound TCP connection to port 20 on the Agent performing the test.  If your Agent is an Enterprise Agent, then ensure that the firewall or packet filter rules allow this connection if you have selected Active FTP request mode.   
* **Desired Reply Code:** Enter the reply code that will represent successful test completion. An FTP command can generate multiple reply codes; the Desired Reply Code setting checks the last reply code in the response. For a list of FTP reply codes, consult [RFC 959](https://www.ietf.org/rfc/rfc959.txt).

   **NOTE:** Do not use the **Desired Reply Code** setting in combination with the **Limit Download Size** or **Upload File Size** settings.

#### Outputs

* HTTP Server tests provide a world map containing availability, and on location-by-location basis, the response code served by the target web page, and number of redirects from URL requested until the final page was served.
* Page Load tests provide all the content from an HTTP Server test, along with a page load table, showing the breakdown of the data received by domain and provider, as well as a waterfall chart, which shows the load time, source and provider for each component of the page.  The Page Load test also provides access to DOM load and page load times, which provide elapsed times from the request start.
* Transaction tests provide page load detail for each page visited in a transaction, timing information for custom defined markers, screenshots \(if configured\) as well as overall transaction time and completion percentage, on an agent-by-agent basis.
* Transaction \(Classic\) tests provide page load detail for each page visited in a transaction, as well as transaction time and completion percentage, on an agent-by-agent basis.  Unlike Page Load tests, network measurements are not available for Web Transaction tests.
* FTP Server tests provide availability, response time and throughput metrics, as well as FTP reply codes for an FTP session. 

### Voice Layer test

The Voice layer provides the following test types: RTP Stream and SIP Server. Each test type has a single corresponding view: the Voice Metrics view and the SIP Server view.

An RTP Stream test establishes a point-to-point connection from the sender \(VoIP call initiator\) to the receiver \(VoIP call endpoint\). A stream of voice packets is sent between the endpoints to measure Mean Opinion Score \(MOS\), packet loss, discards, latency and Packet Delay Variation \(PDV\). The RTP Stream test also provides a choice in the Differentiated Services Code Point \(DSCP\) and codec values.

A SIP Server test performs a SIP registration with the target SIP server. Optionally it can verify response status code and whether response headers match a configured regular expression. Both test types also provide a traceroute-like visualization of the network route and can optionally provide the BGP Route Visualization view showing a map of connections between autonomous systems in the route from each BGP monitor to the target.

#### RTP Stream Basic Settings tab

* **Test type:** RTP Stream.
* **Test Name:** __This optional parameter gives the test a label.  When no label is provided, the the values in the **Target** and the **Server Port** field will be combined to comprise the Test Name. A Test name cannot exceed 255 characters.
* **Target:** Enterprise Agent or Cloud Agent.
* **Interval:** How frequently the test will be run.
* **Agents:** This drop-down lists the ThousandEyes Cloud Agents and \(optionally\) Enterprise Agents agents that are available to your account.  Select one or more Agents to assign them to this test.
* **Alerts:** When the **Enable** box is checked, the Alert Rules selected in drop-down list will be active for the test. You can select Alert Rules with the drop-down list, and create, modify and delete Alert Rules with the **Edit Alert Rules** link.

#### RTP Stream Advanced Settings tab

* **Server Port:** The port number that the server uses for incoming RTP sessions.
* **Codec:** The codec name \(and associated bit rate\) used for the RTP session.
* **Duration:** The length of time the test will run, in seconds.
* **De-jitter Buffer Size:** The size of the de-jitter buffer, in seconds. De-jitter buffers store traffic in order to eliminate the effects of delay variations. Having too small or too large a buffer size can result in audio gaps perceived by the call recipient.
* **Collect BGP data:** Check this box to enable BGP Path Visualization View. The "BGP Public Monitors" option button allows users to choose whether ThousandEyes' public BGP Monitors should be used for monitoring target prefixes. The "Private BGP Monitors" drop-down box allows users to select which private BGP Monitors should be used for monitoring target prefixes. By default, all public and private monitors are selected.
* **No. of Path Traces:** Three path trace packets are used by each Agent by default to discover each hop in the Path Visualization to the target.  Uncheck the box to display a slider which allows selection of 1 - 10 packets.
* **DSCP:** The Differentiated Services Code Point \(DSCP\) value for the IP packet headers of the RTP session.  DSCP allows for prioritization of voice traffic in a network.

#### RTP Stream Outputs

* RTP Stream tests enable access to the Voice Metrics, Path Visualization and BGP Route Visualization views.

#### SIP Server Basic Settings tab

* **SIP Server:** Specify domain name or IP address of the SIP server.
* **SIP Proxy:** Checkbox to enable the use of SIP Proxy, and text field to enter Proxy's IP address.
* **Protocol:** Select either "TCP" or "UDP".
* **Port:** TCP or UDP port number on which the SIP service is listening.

#### SIP Server Test Advanced Settings tab

* **Perform SIP Register:** Enable/disable SIP registration as part of the test.
* **User:** Username for SIP registration.
* **Auth User:** Alternative username when performing authentication \(the "authuser" setting\).
* **Password:** Password or secret for authentication.
* **Desired status code:** Sets the SIP status code returned by the server which will be considered a successful test \(no errors will be displayed in the test table results, no response code-based alerts generated, etc...\). By default, either a 200-level or 300-level status code is considered a successful status code. Uncheck the box and enter a code in the field below to use a different status code.
* **Verify Headers:** Search SIP response headers for text which matches the expression in the **Verify Headers** field. The expression can be literal text or a POSIX regular expression. If no match occurs, the test shows an error.

#### SIP Server Outputs

* SIP Server tests enable access to the SIP Server metrics, End-to-End Metrics, Path Visualization and BGP Route Visualization views.

## Related articles

* To learn more about ThousandEyes metrics please see [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean).
* To understand how a test results can be shared, visit [Sharing Test Data](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmyKAC_Sharing-Test-Data)

