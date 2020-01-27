# ThousandEyes view layouts

This article describes how to navigate to and interact with the ThousandEyes Views.  This document describes the two primary View layouts \(standard and DNS+\) used throughout the user interface of the application, and makes reference to two other interactive Views.

## Navigation Bar and Menu

ThousandEyes uses a standard top navigation bar throughout the entire application. The top nav layout is documented in the figure below.

IMAGE MISSING

1. **Menu toggle:** Toggle displaying or hiding the Menu on the left side of the page.
2. **Page name:** Displays the current page name.
3. **Agent status:** Displays a drop-down list of all Enterprise Agents, along with their status.  The icon displays a circle with a count of Agent alerts.
4. **Notifications:** Displays a drop-down list of notifications, such as Live Shares awaiting your approval. The icon displays a red circle with a count of notifications. 
5. **Help & Support:** Displays a menu of help and support options:
   * Customer Success Center Knowledge Base articles and videos
   * Live Chat for live support via in-app chat during support hours 
   * Contact Support to submit a support ticket via web form, in a new browser tab or window
   * Page Tour to get context-sensitive information on the current page
6. **User menu:** Displays a list of Account Groups available, with the current Account Group initially visible.  Select an Account Group name to switch to that Account Group context.  Also displays your ThousandEyes name and login ID \(email address\) as well as a link to the Account Settings page and a logout link.
7. **Account Group:** Displays the name of the current Account Group context.

The Menu appears on the left side of the application window, unless your window width is below a minimum size, in which case it will be hidden until the Menu toggle \(\#1 above\) is clicked.  The Menu provides access to the top-level pages of the application for configuration of tests, displaying of test results, and other major functions.  The top-level entries on the Menu are described below.  
 

| IMAGE MISSING | **Cloud & Enterprise Agents:** Views of tests from, and settings for Cloud Agents, Enterprise Agents and BGP Monitors. |
| :--- | :--- |
| IMAGE MISSING | **Endpoint Agents:** Views of tests from, and settings for Endpoint Agents. |
| IMAGE MISSING | **Devices:** Views of data from, and settings for Monitored Devices. |
| IMAGE MISSING | **Dashboard link:** Dashboards in the current Account Group. |
| IMAGE MISSING | **Alerts:** Alert information for your Account Group and Alert Rule settings, including Suppression Windows. |
| IMAGE MISSING | **Reports:** Reports for your Account Group and Report Settings. |
| IMAGE MISSING | **Sharing:** Snapshots, Saved Events and Embedded Widgets for your Account Group. |
| IMAGE MISSING | **Account Settings:** Administrate User Profiles, Permissions, Account Groups.  Browse Usage, Billing, Quotas and view the Activity Log.  Administrate Organization security configurations including SCIM, SSO, Security Profile and Timezone configurations. |

## System Notifications

Occasionally, a system notification may appear, announcing major new features or changes, or other system information.  Each notification is only shown one time per user account, and can be dismissed either by clicking the link contained in the notification, or by clicking the X icon to the right of the notification.  Notifications are always linked to an article posted in the Customer Success Center, so don't worry--if you dismiss it accidentally, just log in to [https://support.thousandeyes.com](https://support.thousandeyes.com/) to get the current notification.  An example of a notification can be found below: 

IMAGE MISSING

## ThousandEyes standard layout

The ThousandEyes standard view is used across all Network, DNS, Voice and Web tests.  It provides a consistent layout when working with test results.  The ThousandEyes standard view layout is documented in the figure below, with numbered callouts.  Below the figure is a numbered list corresponding to the callouts, explaining each part of the layout. 

IMAGE MISSING

1. **Test selector:** Use this control to change which test is being displayed in the standard layout.  All tests of this type will be shown, including disabled tests.
2. **Views**: This menu lists views available for the test type selected.  When switching views, the test selected and date/time selected in the timeline \(\#5\) are persisted in the new view.
3. **Metric selector**: Use this control to change the context of the data shown in the timeline \(\#5\), Table tab \(\#7\) and averages \(\#8\) areas.
4. **Agent selector**: Use this control to select an Agent location. This selection changes the content shown on the timeline \(\#3\), detailed metrics \(\#7\), averages area \(\#8\) and world map \(\#9\).  All assigned locations are available for selection, and by default, the “All Agents” entry is selected.  When an individual location is selected, click the X button to the right of the Agent name, or click into a background area of the world map \(\#9\) to clear the location selection.
5. **Timeline:** By default, shows data for the lesser of 14 days or the length of time that the test has been enabled. When a location is selected \(see \#4\), charts the location’s values against the average computed across all locations.  To change the data displayed, either use the 24h \(trailing 24 hours\), 7d \(trailing 7 days\) or 14d \(trailing 14 days\) links, click the zoom out and latest buttons, or click and highlight the requested area of the map, and it will re-draw appropriately.  
6. **Current round:** Indicates the time and date of the currently selected round in the timeline. 
7. **Detailed Metrics tabs:** __In the lower section of the layout, one or more tabs are available to show the world map, detailed metrics and data specific to the selected test type. Refer to the knowledge base article [ThousandEyes Metrics: What do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean) for more information regarding each metric shown.
8. **Averages:** Based on the selected location, averages are computed for the selected metric for the time indicated by the date/time.  The content shown in the averages fvaries widely by view.
9. **World map:** Uses geo-location data for agents to place agents on the map. The world map is zoomable using the conrols to the right of the map or via mouse scrolling.  Individual agents can be selected using this view, having the same effect as the Agent selector \(\#4\). 
   * BULLET AND IMAGE MISSING
   * BULLET AND IMAGE MISSING
   * BULLET AND IMAGE MISSING
   * IMAGE MISSING
10. **Save button:** Click the **Save** button to permanently save a period of data of up to two days.
11. **Share button:** Click the **Share** button to create Share Links or export data in XML or JSON format.
12. **Run Now:** Run an Instant Test using this test as a base configuration. 

## ThousandEyes DNS+ layout

The ThousandEyes DNS+ view is used for all DNS+ tests.  DNS+ provides visibility into worldwide DNS data, from thousands of vantage points, in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The ThousandEyes DNS+ view layout is documented in the figure below, with numbered callouts by section.  Below the figure is a list of sections, with a numbered list corresponding to the callouts on the figure, explaining each section of the layout. 

IMAGE MISSING

1. **Test selector:** Use this control to change which test is being displayed in the DNS+ layout.  All tests of this type will be shown, including disabled tests.
2. **Views**: This menu lists views available for the test type selected.  When switching views, the test selected and date/time selected in the timeline \(\#6\) are persisted in the new view.
3. **Metric selector:** Use this control to change the context of the data shown in the timeline \(\#6\) and averages \(\#8\) areas.
4. **Country selector:** Use this control to select a specific country to display on the timeline and in the metrics.
5. **Mapping selector:** This control is only available in the DNS+ mappings view, and is used to select which value that maps back to the domain name used in the test configuration.  This can be very useful when viewing anycast datasets, or when attempting to troubleshoot DNS resolution problems from a specific network or geography.  Each mapping returned from a DNS query will be shown, with a percentage of worldwide resolvers shown in parentheses.
6. **Timeline:** By default, shows data for the lesser of 14 days or the length of time that the test has been enabled. When a location is selected \(see \#4\), charts the location’s values against the average computed across all locations.  To change the data displayed, either use the 24h \(trailing 24 hours\), 7d \(trailing 7 days\) or 14d \(trailing 14 days\) links, click the zoom out and latest buttons, or click and highlight the requested area of the map, and it will re-draw appropriately.  
7. **Current round:** Indicates the time and date of the currently selected round in the timeline. 
8. **Averages:** Based on the selected location, averages are computed for the selected metric for the time indicated by the date/time.  The content shown in the averages varies widely by view.
9. **World map**: unlike the standard layout, which marks agent locations on the map, the DNS+ view charts entire countries in color, according to either the response time, availability, or number of mapping density, based on their percentage of vantage points, using open resolvers available worldwide. World map is zoom interactive.  Individual countries can be selected using this view, having the same effect as \#4.
10. **Detailed metrics:** this list is somewhat more interactive than the list shown in the standard layout.  Each tab’s behavior is documented below:
    * **Countries tab** – this tab lists all countries, and shows the percentage of vantage points mapping to the selected mapping \(\#5\), and number of covered networks.  Number of networks is hyperlinked to open the network tab and select only those networks which are responsive to that metric.  Selecting a country by clicking on the map, or by using the country selector will have the following effects:
      * Change the color of the selected country \(yellow in mappings view, blue in availability and response time views\)
      * Change the chart shown in the timeline \(\#6 above\), to chart the selected country’s default measurement against the worldwide percentage of same.
      * Changes the computed averages section to be based on the selected country’s context
      * Reduces the number of networks shown in the network tab to only those contained within the selected country.
      * Hides other countries from the geography tab, and enables the View all countries button. 
    * **Network tab** – this tab lists all networks which are accessible, in the current context.  When a specific country is selected, only those networks contained within that country are shown.  Each network will show a mapping percentage statistic, and the number of vantage points, otherwise known as open resolvers, which reside on that network.  Each network shown is a registered Autonomous System, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below. IMAGE MISSING

## Other views

There are currently two other views being used within the platform, and they're sufficiently different enough to document them individually.

### BGP Route Visualization <a id="bgplayout"></a>

Since the BGP Route Visualization layout is used only in the BGP Route Visualization view, refer to the knowledge base article on How to work with BGP Route Visualization, located here: [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmpKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmpKAC)

### Path Visualization <a id="pathvislayout"></a>

Since the Path Visualization layout is used only in the Path Visualization view, refer to the knowledge base article on How to work with Path Visualization, located here: [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC)

## See also

The following table shows a list of tests and links to articles describing how to interact with the views for each test.  

| **View Name** | **Uses Layout** | **Applies to tests** | **Article link** |
| :--- | :--- | :--- | :--- |
| Overview | Standard | Agent to Server  Agent to Agent  FTP Server1  HTTP Server1  Page Load1   DNS Server1  SIP Server1 | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmtKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmtKAC) |
| Path Visualization | Path Visualization | Agent to Server  Agent to Agent  FTP Server1  HTTP Server1  Page Load1   DNS Server1  SIP Server1  RTP Stream1  Voice Call1 | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmiKAC) |
| BGP Route Visualization | BGP Visualization | Agent to Server  Agent to Agent  FTP Server1  HTTP Server1  Page Load1   DNS Server1  SIP Server1  RTP Stream1  Voice Call1 | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmpKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmpKAC) |
| DNS Domain Trace | Standard | DNS Domain Trace | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmmKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmmKAC) |
| DNS Server Metrics  | Standard | DNS Server | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmrKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmrKAC) |
| DNSSEC Trace  | Standard | DNSSEC Trace | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmqKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmqKAC) |
| HTTP Server | Standard | HTTP Server  Page Load  | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmvKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmvKAC) |
| Page Load | Standard | HTTP Server  Page Load  | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmuKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmuKAC) |
| Web Transaction | Standard | Web Transaction | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmnKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmnKAC) |
| FTP Server | Standard | FTP Server | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmWKAS](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmWKAS) |
| SIP Server | Standard | SIP Server, Voice Call | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnW8CAK](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmWKAS) |
| RTP Stream | Standard | RTP Stream, Voice Call | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmkKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmWKAS) |
| DNS+ Availability  | DNS+ | DNS+ Domain | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpkKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpkKAC) |
| DNS+ Resolution Time | DNS+ | DNS+ Domain | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpjKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpjKAC) |
| DNS+ Mappings  | DNS+ | DNS+ Domain | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpdKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpdKAC) |
| DNS+ Server Latency | DNS+ | DNS+ Server Latency | [https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpiKAC](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmpiKAC) |
| 1 When the **Perform network measurements** |  |  |  |

