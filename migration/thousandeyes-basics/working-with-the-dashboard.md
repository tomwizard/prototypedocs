# Working with the Dashboard

The Dashboard page is the starting point when you log in to the ThousandEyes platform. A Dashboard consists of one or more Dashboard widgets. Depending on the type\(s\) of widgets in a Dashboard configuration, your Dashboard can display a summary of your test results for the last 12 hours, a map of your Enterprise Agents and their status, an Alert Grid or a report created with the Reports feature. Widget configuration allows for filtering out or on specific elements, and other options. For information on configuring your Dashboard, see the ThousandEyes Knowledge Base article entitled [Customizing your Dashboard](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmcKAC).

The Dashboard page is configured to refresh every two minutes. Displaying the Dashboard page will prevent users from being logged out due to inactivity, making Dashboards suitable for kiosk or operations center displays.

## Dashboard Widget types

Widgets are categorized as "Report Widgets" and "Dashboard Widgets". All Report Widgets can be added to a Dashboard but Dashboard widgets cannot be used in a Report.

This section described all the available Dashboard Widgets: Alert List, Tests, Enterprise Agent Status, Alert Grid, and Color Grid. For details on all the Report Widgets click [here]().

#### Alert List

The Alert List widget displays alerts that are currently active or were active within the configured period of time:

IMAGE MISSING

Active alerts have an orange dot present on the left-hand side and their duration is displayed with orange-colored text as well. Clicking the link in the **Alert Source** column leads to the results view of the test that generated the alert. The **View All Alerts** link in the top right-hand corner of the widget leads to the [Alerts &gt; Alert List](https://app.thousandeyes.com/alerts/list/active) view, where a detailed alert data view is provided.

Consult the [How Alerts work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work-1476477151762) article for further information about ThousandEyes alerting capabilities.

#### Tests

The Tests Dashboard widget displays a list of tests configured in your Account Group or tests which have been shared to your Account Group via the Live Share feature. Grayed-out rows show disabled tests.

IMAGE MISSING

1. _Header bar_ – click a column name to sort the list of results by that column, or to toggle sort order between ascending and descending alphabetical order.
2. _Alert status_ – will show red for an alert that is currently running, or green for a healthy test. No color indicates either no Alert Rules assigned to the test or alerts are disabled on the test.
3. _Test name hyperlink_ – click to open the results page for that test. The default view will be opened, for a test type with multiple Views. See the table below for more information on Views.
4. _Trending values_ – default metrics for each test type, using values collected over the trailing 12 hours. Navigate to any test round by clicking on the desired point on the graph.
5. _Current values_ – default metrics for each test type, shows the most recent set of values collected when the page was last refreshed.
6. _Test configuration_ – click to open the test's configuration page. The gear icon will appear when you mouse over the row.

####  Agent Status

The Agent Status widget displays Agents that belong to your Account Group or have been shared with your Account Group on a global map. Locations are determined from IP address using the ThousandEyes geolocation database or using the **Country** and **Region** settings on an Agent \(overrides geolocation\). If the location cannot be determined exactly, then the Agent is placed on the correct country if the country can be determined, or placed in a neutral location on the map if no information is available.

Each dot on the map displays a number if more than one Agent is in that location. The color indicates the status of the Agent:

**Green:** indicates an Agent with up-to-date data uploads  
**Red:** indicates an Agent which has not uploaded data in the current round  
**Yellow:** indicates a mix of Agents that are and are not current in their data uploads  
**Clear**: indicates a disabled Agent

A summary legend of online, offline and disabled Agents is displayed in the upper-left corner. In the upper-right corner of the widget, zoom-in \(**+**\), zoom-out \(**-**\) and 100% zoom controls are available.

IMAGE MISSING

Mousing over an Agent dot displays a tooltip with the names, private and public IP addresses of the Enterprise Agents in that location or names and host Operating System information for Endpoint Agents. Clicking on the name of an Agent will open the Agent's configuration in the corresponding Agent Settings page.

#### Alert Grid

The Alert Grid widget displays alerts over the past 24 hours using a matrix with tests as rows, and either Enterprise Agents or BGP monitors as columns, depending on the Alert Grid configuration. Only one of Agents or Monitors may be displayed in a given Alert Grid widget. A test with an active alert is indicated by a red border around an orange dot, under the column of the Agent or Monitor that generated the alert. Alerts that are no longer active are borderless orange dots. The length of time the alert is/was active is proportional to dot size. Mousing over the dot will provide a tooltip with alert data.

IMAGE MISSING

For an Alert Grid widget configured with a filter, if no Alerts match the filter expression, the widget will display a "No active agent alerts" or "No active BGP monitor alerts" message, along with the number of alerts hidden due to the filter expression, if any:

IMAGE MISSING

#### Color Grid

The Color Grid widget displays an array of cards, where each card's color is determined by comparing the card's value to a predefined scale. Here is an example Color Grid widget showing data collected over the last 6 hours by two tests, with each test having 16 agents assigned to it:

IMAGE MISSING

The following remarks about this widget's configuration will explain why the data is displayed the way it is:

1. Cards visualize the `Median` value of the `Total Time` metric of the `Web - HTTP Server` tests running on `Cloud & Enterprise Agents`.
2. The `Agents` value is selected in the **Cards** drop-down menu makes each card display data from a specific agent.
3. Cards are grouped by `Tests`, meaning data from each test is displayed as a separate group of cards.
4. The configured **Scale** values determine card colors. Cards will be green when their value is lower than 200 ms. The color will progressively turn to red when the card's value approaches 270 ms.
5. Display two columns of card groups per row.

## Report widgets

Reports widgets allow users to configure a report for the Dashboard in the same manner that reports widgets are configured using the Reports feature. Every type of report widget that is available in the Reports feature can be used in a Dashboard. Consult the ThousandEyes Knowledge Base article [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS) for information on what each type of reports widget provides and how the widget is configured.

## Related information

The following resources provide further information:

* [Customizing your Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmcKAC_Customizing-your-Dashboard) article provides detailed configuration information for Dashboard-specific widgets.
* [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports) article guides you through the configuration of a Report, a feature similar to Dashboards but with additional abilities like \(periodic or instant\) report snapshot creation and [externally embeddable widgets](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnUKAS_Embedding-report-widgets-in-external-web-sites).

