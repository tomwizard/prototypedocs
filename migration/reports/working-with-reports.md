# Working with Reports

The ThousandEyes platform contains a reporting engine which provides both on-demand reports and scheduling of automatically generated reports.  Data from tests can be organized into highly customized layouts, presented numerically or in tables or graphs, and sent via email to users.

A report consists of one or more report widgets. We currently provide ten types: Numbers, Tables, Multi-metric Tables, Pie Chart, Stacked Bar/Column Chart, Grouped Bar/Column Chart, Time Series, Time Series Stacked Bar Chart, Map and Box-and-Whiskers.  You create a report by selecting the widgets appropriate for the data you wish to include, and then configuring the parameters of the widgets.  Widget parameters allow for operations on the raw test data such as statistical calculations \(e.g. means, medians or percentiles\), data trends, and tabular views of the data. Widget configuration also permits arrangement of the numbers, tables and time series graphs on the page.  Once configured, reports permit the user to select a time frame of interest, and the report page will then be populated with that period's test data according to the report configuration.

With each report you can take report snapshots. Report snapshots are analogous to test view snapshots.  The snapshot represents a specific time range of the report’s data. Report snapshot creation can be scheduled at regular intervals.  Additionally, the report snapshot can be automatically emailed to a list of recipients.

Report data can also be shared through embedded widgets, which allow a report's widgets to be included in customer web pages such as kiosk displays or network operations center dashboards.  For more information on embedded report widgets, see the ThousandEyes Knowledge Base article [Embedding Reports report widgets in external web sites](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnUKAS_Embedding-report-widgets-in-external-web-sites).

## Configuring Reports

The Reports page \(Reports &gt; Reports\) allows you to create, modify and delete reports, and create and schedule snapshots of existing reports. The figure below and the following list describe the Reports configuration tool on the Reports page.  Below the list is the [Creating a New Report]() section with steps for creating a report.

IMAGE MISSING

1. **Recent Snapshot Selector:** This drop-down menu provides a list of most recent snapshots for each report in account group.
2. **Report selector:** This drop-down menu provides a list of existing reports, along with a Search field to search the list.  Select a report to view by clicking the report name. A watch icon  \(IMAGE MISSING\) next to the name of a report indicates that report has scheduled snapshots. A shared by icon \(IMAGE MISSING\) next to the name of report indicates that report has been shared with other account groups in the same organization. A shared with icon \(IMAGE MISSING\) next to name of report signifies the report belongs to a different account group in same organization. An option to perform **Bulk Actions** enables creating multiple report snapshots or deleting multiple reports at once.
3. **Report Time Range selector:** Quickly select relative time ranges \(eg: Last 7 days, This Month\) or configure a custom time range. Time Ranges will be displayed using the time zone configured within the User's profile. By default, data for last 7 days is displayed. Widgets with configured **Fixed Time Span** option are unaffected by the Time Range selector.
4. **Snapshots menu** provides the following options:
   * **Save a Snapshot:** The currently selected report will be saved as a snapshot, using the time range configured in the Time Range selector.
   * **Schedule a Snapshots:** The currently selected report can be saved as a snapshot on a daily, weekly or monthly basis.
5. **Add/Manage Widgets:** Opens the widget manager. New widgets can be added to the report, or existing widgets can be modified or removed.
6. **Options button** provides the following options:
   * **Create New Report:** Creates a new blank report to be named and populated with widgets
   * **Duplicate Report:** Creates a copy of the currently viewed report, to be renamed and modified
   * **View Report Details:** Allows a user to edit the currently viewed **Report Name**, **Account Group Visibility** and meta-data. The **Related Snapshots History** section shows list of most recent snapshots as seen in below screenshot. IMAGE MISSING

* **Download as PDF:** Download the report as a PDF file. Timestamps will be displayed using the time zone configured for the Organization.
* **Download as CSV:** Download the report as a CSV file. Timestamps will be displayed using the time zone configured for the Organization.
* **Delete Report:** Delete the currently viewed report.

### Creating a New Report

Follow these steps to create a new report:  

IMAGE MISSING

1. On the Reports page, click on the **Options** button and select **Create New Report.**
2. Enter a report name in the **Report Name** field.
3. Enter appropriate **Report Description**.
4. Configure desired **Account Group Visibility**, below are available options:
   * **All account groups:** make report visible to all account groups in current organization.
   * **Only current account group:** hide report from other account groups.
   * **Specific account groups:** make report visible to desired account groups which can be selected from resulting drop-down menu.
5. **Set as my default:** Check this box to make this report the default report displayed for the current user.
6. **Sat as default for account group:** Check this box to make this report the default report displayed for the current Account Group.  User Default takes priority over Account Group Default.
7. Click **Create Report** to open up widget manager. IMAGE MISSING

Reports are created in the widget manager which can also be used to modify a report.  Invoke the widget manager by clicking the **Add/Manage Widgets** button from the Reports page. The figure below and the following list describe the features of the widget manager.

IMAGE MISSING

1. **Widget picker:** Select a widget to add to your report by clicking on the type of widget desired and dragging it to the location within the report layout where you wish the data to appear. 
2. **Widget name:**  The name of your widget, which will appear in your reports and snapshots.
3. **Widget Settings:** Click the gear icon to toggle displaying or hiding the widget’s settings \(available inside or outside the widget manager\).  
4. **More Actions:** Click the More Actions icon to delete, duplicate, [embed](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnUKAS_Embedding-report-widgets-in-external-web-sites) or rename the widget \(available inside or outside the widget manager\) or download a PNG or JPG image of the widget.
5. **Widget handle:** Click the widget handle to change the size of the widget to either half or full page width \(available only in the widget manager\).
6. **Return to Report:** Click this button to exit the widget manager and return to the Reports page. 

To add widgets to the report, drag them down from the widget picker. Widgets can be dragged to different positions within the overall report page whenever the mouse pointer is moved over the header of a widget, causing the pointer to be displayed as a hand: 

IMAGE MISSING

Once the widget is added to the report, select appropriate values for each available option. Changes made in the widget manager are immediately saved, allowing for exit of the widget manager at any time with a single click.

### Working with Report Widgets

Reports provide ten widget types: Numbers, Tables, Multi-metric Tables, Pie Chart, Stacked Bar/Column Chart, Grouped Bar/Column Chart, Time Series and Time Series Stacked Area Chart, Map and Box-and-Whiskers:

* Number widgets display a single scalar quantity, such as an average of packets lost or page load times, or a number of alerts.
* Table widgets permit a breakdown of numbers by rows and columns.  Either rows or columns can list by test, country, continent, or data source \(agents or BGP monitors\) or the aggregate of those \("All"\).
* Multi-metric Table widgets allow for the same configuration as Table widgets, but can have columns with different Metrics, rather than a single metric for the entire table.
* Stacked Bar/Column Chart widgets provide horizontal histogram bars with multiple values, which are useful for composite metric data \(such as HTTP response or fetch time\) and for comparing values between multiple tests, or comparing values on a per-country basis. Bars can be oriented horizontally or vertically as columns.
* Grouped Bar/Column Chart widgets are similar to stacked bar chart widgets, but represent multiple values as single bars in a group of bars.  Bars can be oriented horizontally or vertically as columns.
* Pie Chart Widgets are similar to stacked bar chart widgets, representing multiple values as proportionally sized segments of a pie.
* Time Series widgets are line plots with time on the horizontal axis, and the selected quantity on the vertical axis.
* Time Series Stacked Area widgets are line plots with time on the horizontal axis, and the selected quantities on the vertical axis.  They are used similarly to Stacked Bar Charts but showing values over time.
* Map widgets display data on a world map, based on location of the testing systems \(Agents or BGP monitors\). Data can be displayed per country, per continent, or per Agent \(if a non-BGP metric is displayed\).
* Box-and-Whiskers widgets plot data values versus time on the horizontal axis, with the vertical axis displaying the median, minimum and maximum data points per time value, along with a bar for the range of values represented by the second and third quartiles.

Adding widgets to a report is done by clicking the **+Add/Manage Widgets** button on the Reports page to enter the widget manager. Modifying an individual widget's settings can be done from the Reports page by clicking the gear icon. Details of the settings for each widget type are below, along with examples.

#### Number widget

The image below shows an unconfigured Number widget.

IMAGE MISSING

Number widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts is also a category of choices for Metrics.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** choices available depend on the **Metric** setting, but will come from the following list:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* _Maximum:_ The maximum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the latency times of a Network test over the time period of the report.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were from 0 to 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\)
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\)

**Show Comparison to Previous Timespan:** When checked, the report displays the difference between the current data set and the previous data set of the same length as the reporting interval. The comparison numbers are shown as an additional row of cells below the principle row, in red or green font color along with an up-arrow or down-arrow indicating a numerical increase or decrease.  The combination of color and arrow direction changes based on the Metric setting.  For some settings of Metric, a numeric increase is a change for the better and thus is rendered in green. For other metrics a numeric increase is a change for the worse and rendered in red.  For some metrics, the situation may be ambiguous; those metrics are rendered in grey font. 

"N/A" is displayed in place of the comparison numbers when sufficient data from the previous reporting interval is not currently available for a comparison \(such as when a test is first configured but hasn't accumulated a full timespan of data\).  A "-" \(single dash\) is displayed in place of the comparison numbers when no data is present and will not ever be present, such as when a agent is not assigned to the test.

By default, the timespan of the past data set is the timespan prior to the current data set's time span, which is specified by the **From** and **To** fields of the report's date and time selector.  If the **Fixed Time Span** box is checked, then the timespans of the data sets are specified by the **Fixed Time Span** setting's date selector.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Card Description:** For Number widgets, each number is contained on a card, which can be given its own description which will appear in the number box when viewing the report.  Configuration of this setting is optional.

**Tests:** Names of tests which will provide the data to the report. Select one or more tests that is appropriate to your **Metric** setting \(e.g. if the **Metric** is Packet Loss, select one or more Network tests or tests with included Network Metrics; if the **Metric** is Response Time, select an HTTP Server or Page Load test\).

**Sources:** Filter sources from which the data will be taken. The column heading changes based on which **Metric** is set, and will be one of the following:

* _Alert Rules:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Alert Rules.
* _Agents:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agents.
* _Agent Labels:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agent Labels \(Built-in or Custom\).
* _Tests:_  For any **Metric**, a list of Tests.
* _Test Labels:_ For any **Metric**, a list of Test Labels \(Built-in or Custom\).
* _Monitors:_ If the **Metric** is a BGP test or alert, a list of ThousandEyes BGP monitors.
* _Countries:_ If the **Metric** is a DNS+ test or alert, a list of countries.

#### Example Number widget

Below is an example of a configured Number widget and the resulting report output.

IMAGE MISSING

The configuration shows the widget configured with three numbers:

1. Maximum Packet Loss for selected Agent to Server test.
2. Total number of Alerts triggered across all tests.
3. Maximum Packet Loss observed by Endpoint Agents across all browser sessions.

#### Table widget

The image below shows an unconfigured Table widget.

IMAGE MISSING

Table widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts also have Metrics. For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean) Depending on your choice of **Metric**, the names of the widget settings may change, or additional settings may appear.  For example, selecting any of the Alerts metrics will result in the Alert Rules setting appearing in the widget.

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* Maximum: The maximum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* Minimum: The minimum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\)
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\)

**Show Comparison to Previous Timespan:** When checked, the report displays the difference between the current data set and a past data set, shown as an additional row of cells below the principle row, with the comparison numbers in red or green along with an up-arrow or down-arrow indicating a numerical increase or decrease.  The combination of color and arrow direction changes based on the Metric setting.  For some settings of Metric, a numeric increase is a change for the better and thus is rendered in green. For other metrics a numeric increase is a change for the worse and rendered in red.  For some metrics, the situation may be ambiguous; those metrics are rendered in grey font without accompanying arrows. 

"N/A" is displayed in place of the comparison numbers when sufficient data is not currently available for a comparison \(such as when a test is first configured but hasn't accumulated a full timespan of data\).  A "-" \(single dash\) is displayed in place of the comparison numbers when no data is present and will not ever be present, such as when a test error prevented a round of data collection.

By default, the timespan of the past data set is the timespan prior to the current data set's time span, which is specified by the **From** and **To** fields of the report's date and time selector.  If the **Fixed Time Span** box is checked, then the timespans of the data sets are specified by the **Fixed Time Span** setting's date selector.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Limit To:** When checked, the table rows will display at most the number you set in the selector.  When more rows exist than are displayed, the **Sort By** order determines which rows are displayed.

**Rows:** 

* _Agent:_ Data from all agents are aggregated by Agent.  A row is displayed for each Agent that has data from at least one test.
* _All:_ Data from all sources are aggregated into a single row.
* _Continents:_ Data from all sources are aggregated by continent.  A row is displayed for each continent that has data from at least one source.
* _Countries:_  Data from all sources are aggregated by country.  A row is displayed for each country that has data from at least one source.
* _Test:_  Data from all tests are given their own rows.
* _Test Labels:_ Data from all test labels are given their own rows. 
* _Agent Labels:_ Data from all agents aggregated based on Agent Labels.

**Columns:**

* _Agent:_ Data from all agents are aggregated by Agent.  A column is displayed for each Agent that has data from at least one test.
* _All:_ Data from all sources are aggregated into a single column.
* _Continents:_ Data are aggregated by continent.  A column is displayed for each continent that has data from at least one source.
* _Countries:_ Data are aggregated by country.  A column is displayed for each country that has data from at least one source.
* _Test:_ Data from all sources are aggregated by test.  A column is displayed for each test that has data from at least one source.

**Sort By:** For tables containing multiple rows, the Sort By setting will determine in what order the rows appear.  That is, the value of the Sort By setting is applied to the value in the Rows setting.

* _Default:_ Sort rows optimally, based on the settings for Metric and Show Comparison. The metric which is optimal for your settings is shown in parentheses.
* _Alphabetical:_ Sort rows by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort rows by ascending alphabetical order.
* _Greatest Decrease:_ Sort rows by greatest decrease between current and past measurements of a row's **Metric** value. This setting is meaningful only when the **Show Comparison** box is checked.
* _Greatest Increase:_ Sort rows by greatest increase between current and past measurements of a row's **Metric** value. This setting is meaningful only when the **Show Comparison** box is checked.
* _Highest:_  Sort rows by highest value first.
* _Lowest:_ Sort rows by lowest value first.

**Tests:** Names of tests which will provide the data to the report. Select one or more tests that are appropriate for your selection of **Metric** setting \(e.g. if the **Metric** is Packet Loss, select one or more Network tests or tests with included Network Metrics; if the Metric is Availability, select a Web test, etc..\)

**Sources:** Filter the sources from which the data will be taken.  This setting's name and the corresponding column heading change once the **Metric** is set, and will be one of the following:

* _Alert Rules:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Alert Rules.
* _Agents:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agents.
* _Agent Labels:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agent Labels \(Built-in or Custom\)
* _Tests:_  For any **Metric**, a list of Tests. 
* _Test Labels:_ For any **Metric**, a list of Test Labels \(Built-in or Custom\).
* _Monitors:_ If the **Metric** is a BGP test or alert, a list of ThousandEyes BGP monitors.
* _Countries:_ If the **Metric** is a DNS+ test or alert, a list of countries.

#### Example Table widget

Below is an example of a configured Table widget and the resulting output.

IMAGE MISSING

1. The configuration shows Cloud & Enterprise Agents set as Data Source with Latency of Agent to Agent tests set as a reported Metric for the table. The widget is set to visualize Standard Deviation of a Latency metric in the Source To Target direction.
2. Data is set to visualize with Tests forming the Rows and Agents forming the columns. Rows are sorted by a reported value, in the ascending order.
3. The filter is set to include 2 of 3 available Agent to Agent Tests. The “+” icon can be used to put on additional filters.

#### Multi Metric Table widget

The images below show an unconfigured Multi Metric Table widget.  The first image displays the Rows tab, and the second image displays the Column tab.

IMAGE MISSING

#### Rows tab

The Multi Metric Table widget's Rows tab has the following settings:

**Rows:** Select the property that will be used for the rows in the table.  Rows will be one of the following:

* _All:_ Any property which is relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Tests:_ Tests relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Test Labels:_ Test Labels relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Agents:_ Agents relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Monitors:_ Monitors relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Agent Labels:_ Agent Labels relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Servers:_ Servers relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Countries:_ Servers relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.
* _Continents:_ Continents relevant to the criteria in the Column\(s\) tab\(s\) will be used as a row.

**Sort By:** For tables containing multiple rows, the Sort By setting will determine in what order the rows appear.  That is, the value of the Sort By setting is applied to the value in the Rows setting.

* _Default:_ Sort rows optimally, based on the settings for Metric and Show Comparison. The **Metric** which is used for each column shows the column's **Measure** in parentheses.
* _Alphabetical:_ Sort rows by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort rows by ascending alphabetical order.
* _Greatest Decrease:_ Sort rows by greatest decrease between current and past measurements of a row's **Metric** value. This setting is meaningful only when the **Show Comparison** box is checked.
* _Greatest Increase:_ Sort rows by greatest increase between current and past measurements of a row's **Metric** value. This setting is meaningful only when the **Show Comparison** box is checked.
* _Highest:_  Sort rows by highest value first.
* _Lowest:_ Sort rows by lowest value first.

**Show Comparison to Previous Timespan:** When checked, the report displays the difference between the current data set and a past data set, shown as an additional value in the cells below the principle value, with the comparison numbers in red or green along with an up-arrow or down-arrow indicating a numerical increase or decrease.  The combination of color and arrow direction changes based on the Metric setting.  For some settings of Metric, a numeric increase is a change for the better and thus is rendered in green. For other metrics a numeric increase is a change for the worse and rendered in red.  For some metrics, the situation may be ambiguous; those metrics are rendered in grey font without accompanying arrows. 

"N/A" is displayed in place of the comparison numbers when sufficient data is not currently available for a comparison \(such as when a test is first configured but hasn't accumulated a full timespan of data\).  A "-" \(single dash\) is displayed in place of the comparison numbers when no data is present and will not ever be present, such as when a test error prevented a round of data collection.

By default, the timespan of the past data set is the timespan prior to the current data set's time span, which is specified by the **From** and **To** fields of the report's date and time selector.  If the **Fixed Time Span** box is checked, then the timespans of the data sets are specified by the **Fixed Time Span** setting's date selector.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Limit To:** When checked, the table rows will display at most the number you set in the selector.  When more rows exist than are displayed, the **Sort By** order determines which rows are displayed.

**Sources:** Filter sources from which the data will be taken.  This setting's name and the corresponding column heading change once the **Metric** is set, and will be one of the following:

* _Alert Rules:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Alert Rules.
* _Agents:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agents.
* _Agent Labels:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agent Labels \(Built-in or Custom\)
* _Tests:_  For any **Metric**, a list of Tests. 
* _Test Labels:_ For any **Metric**, a list of Test Labels \(Built-in or Custom\).
* _Monitors:_ If the **Metric** is a BGP test or alert, a list of ThousandEyes BGP monitors.
* _Countries:_ If the **Metric** is a DNS+ test or alert, a list of countries.
* _Servers:_ For any Metric, a list of servers being tested.
* _Location:_ For any Metric, a list of locations being tested. IMAGE MISSING

####  Columns tab

The Multi Metric Table widget's Columns tabs have the following settings:

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts also have Metrics. For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean) Depending on your choice of **Metric**, the names of the widget settings may change, or additional settings may appear.  For example, selecting any of the Alerts metrics will result in the Alert Rules setting appearing in the widget.

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* Maximum: The maximum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* Minimum: The minimum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\)
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\)

To add a column, click on the **Add New Column** link.  To delete a column, click the tab of the column you wish to delete, then click the **X** in the column's header.

#### Example Multi Metric Table widget

Below is an example of a configured Multi Metric Table widget entitled “HTTP Server statistics” and the resulting output.

IMAGE MISSING

The **Rows** setting is set to "Tests", indicating that the table's rows will be individual test names, and the **Sources** is set to filter on "Tests", where 3 tests of 501 are selected, creating a two-row table with the first column containing those two selected tests. Column 1 has "Availability" selected as the **Metric** and "Mean" as the Measure.  Each test row will display the mean of availability in the first column. Column 2 has "Response Time" selected as the **Metric** and "Maximum" as the Measure.  Each test row will display the largest of all response time values in the round, in the second column.

Sort by is set to  "Default \(Tests\)", meaning that the sorting order of the rows will be the default \(the first column that's set by the **Rows**\).  The dark switch with the white up-arrow indicates that the value of the **Sort by** field will be sorted from low to high, alphabetically in this case.  The **Show Comparison** box is checked, producing the second, lower set of numbers along with up or down arrows to indicate whether the value rose or dropped, and a color code to indicate whether that rise or drop is an improving change from the previous period \(green\), a degrading change \(red\) or is ambiguous \(gray\).  **Fixed Time Span** is unchecked, indicating that the report uses the time frame that is set  at the top of the Reports page.  Limit To is set to 2 rows, thereby preventing one of the three tests from being displayed.

#### Time Series widget

The image below shows an unconfigured Time Series widget.

IMAGE MISSING

Time Series widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts also have Metrics.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* _Maximum:_ The maximum value in the set of measurements, such as the response times of an HTTP Server test in a test round.
* _Minimum:_ The minimum value in the set of measurements, such as the response times of an HTTP Server test in a test round.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\)
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\)

**One Chart per Line:** When checked, the widget will create a chart for each member of the setting specified in the **Group By** column.  For example, if **Group By** is set to "Agent", then a chart will be created for each Agent, rather than one chart graphing all of the lines.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Group By:**

* _Single Line:_ Data from all Sources and Tests are aggregated together into a single line.
* _Test:_  Data from all Sources and Tests are aggregated together into a single line.
* _Agent:_  Data from all Agents are given their own chart lines.
* _Continents:_ Data are aggregated by continent.  A chart line is displayed for each continent that has data from at least one source.
* _Countries:_  Data are aggregated by country.  A chart line is displayed for each country that has data from at least one source.
* _None:_ Data are not aggregated.
* _All:_ Group all the data as a single chart line.
* _Test Labels:_ Data from each Test Label is given their own chart lines.
* _Sources:_ Data from each source is given their own lines on chart.
* _Agent Labels:_ Data from each Agent Label is given their own chart lines.
* _Servers:_ Data aggregated based on servers. Each server would  have a dedicated chart line.
* _Visited Sites:_ Endpoint Data from each visited site is given their own chart lines.
* _Private Networks:_ Data from each private network is given their own lines on chart.
* _Users:_ Data is aggregated based on user, each user gets their own chart lines.
* _Platforms:_ Data from each platform Windows/Mac is given their own chart lines.
* _Connections:_ Data for each connection is given their own lines on chart.
* _Networks:_ Data aggregated based on networks, each network gets their own chart lines.
* _Domains:_ Data aggregated based on visited domain, each domain would have a dedicated chart line.
* _Endpoint Agent Labels:_ Data from each Endpoint Agent Label gets their own line on chart.
* _Device:_ Data from each Device is given their own chart lines.
* _Device Types:_ Data from each Type of Device  is given their own chart lines.
* _Interfaces:_ Data from each Device Interface is given their own chart lines.
* _Interface Types:_ Data from each Device Interface Type is given their own chart lines.

**Note:** If the Group By field's setting is the same as the Source field type \(e.g. Group By is "Test" and Source type is "Test", Group By is "Countries" and Source type is "Countries", or Group By is "Monitors" and the Source type is "Monitors"\) then the Source field takes precedence.

For example, if Group By is "Countries" and Source type is "Tests", then all selected Tests will have their data grouped by all countries found from those Tests's results.  Each country will have its own graph.  However, if Group By is "Countries" and Source type is "Countries", then only those countries selected in the Source selector will have their own graph.

**Tests:** Names of tests which will provide the data to the report. Based on your selection of **Metric** setting, the Tests menu will display only those tests which are relevant \(e.g. if the **Metric** is Packet Loss, the Test menu displays Network tests and other tests which use an included Network test; if the Metric is Availability, the Test menu displays a Web test, etc...\).

**Sources:** Filter sources from which the data will be taken.  The selections change based on which **Metric** is set, and will be one of the following:

* _Alert Rules:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Alert Rules.
* _Agents:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agents.
* _Agent Labels:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agent Labels \(Built-in or Custom\).
* _Tests:_  For any **Metric**, a list of Tests.
* _Test Labels:_ For any **Metric**, a list of Test Labels \(Built-in or Custom\).
* _Monitors:_ If the **Metric** is a BGP test or alert, a list of ThousandEyes BGP monitors.
* _Countries:_ If the **Metric** is a DNS+ test or alert, a list of countries.

#### Example Time Series widget

Below is an example of a configured Time Series widget  and the resulting output.

IMAGE MISSING

1. The above widget visualizes Maximum Packet Loss detected by an Agent to Server test. Data Source is configured to Cloud & Enterprise Agents.
2. The data is aggregated by agent, resulting in each agent's data rendered on an indivudual chart line.
3. The “Show Overall Maximum” box is checked and therefore the first displayed chart shows the overall maximum, across all agents.
4. “One Chart per Line” checkbox results in each line being rendered in a separate chart.
5. Configured to visualize data from 1 of 16 available tests.

#### Stacked Bar Chart widget

The image below shows an unconfigured Stacked Bar Chart widget.

IMAGE MISSING

Stacked Bar Chart widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For a Stacked Bar Chart widget, the Metrics provided \(Response Time, Total Fetch Time and Total Error Count\) are composites of metrics found in an HTTP Server test.  For example, Response Time consists of four distinct metrics: DNS resolution time, connect time, SSL time and wait time.  Each of the four metrics are presented in a single stacked bar.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive \(Total Error Count only\):_ The percentage of measurements with non-zero error counts. 
* _% zero_ \(Total Error Count only\): The percentage of measurements with error counts equal to zero.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Maximum:_ The maximum value in the set of measurements, such as the response times of an HTTP Server test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the response times of a HTTP Server test over the time period of the report.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Response Time" would indicate that the average value of the response time in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Response Time" would indicate that the value of 50 ms is the middle value in the range of all values of the response time in the reporting period.
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the response times, over the time period of the report.
* _Total \(Total Error Count only\)_: The total number of errors in the reporting period.

**Axis:** Arrange the data into bars by the following criteria, and orient the label\(s\) on the axis displayed :

* _All:_ Produces a single bar with all data.
* _Agent:_ Produces bars for each Agent.
* _Continents:_ Produces bars for each continent/continental region \(North America, Europe/EMEA, Asia/APAC, etc...\).
* _Countries:_ Produces bars for each country.
* _Test:_ Produces bars for each test.
* _Test Labels:_ Each test label would get their own bar.
* _Sources:_ Produces dedicated bars for each source.
* _Visited Sites:_ Each visited side would have their own bar.
* _Private Networks:_ Each private network gets their own bar.
* _User:_ Each user gets their own bar.
* _Connection:_ Each connection gets a dedicated bar.
* _Network:_ Produces bars for each network.
* _Domain:_ Each visited domain gets their own bar.
* _Location:_ Each location would have a dedicated bar.
* _Endpoint Agent Labels:_ A separate bar is produced for each Endpoint Agent Label.
* _Endpoint Tests:_ Each Endpoint Test gets their own bar.
* _Devices:_ Each device is dedicated a bar on graph.
* _Interfaces:_ Device Interfaces would have dedicated bars.
* _Device Types:_ Separate bars produced for each type of device.
* _Interface Types:_ Each  interface type would have dedicated bars.

Either **X-Axis** or **Y-Axis** is displayed, based on the **Orientation** selected. 

**Orientation:** The orientation of the bars--either horizontal or vertical. Selecting horizontal or vertical orientation sets the associated pull-down menu label to **X-Axis** or **Y-Axis.**

**Sort By:** For charts containing multiple bars, the Sort By setting will determine in what order the bars appear.  That is, the value of the Sort By setting is applied to the value in the X-Axis/Y-Axis setting.

* _Default \(Highest\):_ Sort bars optimally, based on the settings for Metric and Show Comparison. The metric which is optimal for your settings is shown in parentheses.
* _Alphabetical:_ Sort bars by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort bars by ascending alphabetical order.
* _Highest:_  Sort bars by highest value first.
* _Lowest:_ Sort bars by lowest value first.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Limit To:** When checked, the chart will display at most the number of groups you set in the selector.  When more groups exist than are displayed, the **Sort By** order determines which rows are displayed.

**Sources:** Filter on names of tests or Agents which will provide the data to the report. To filter by both tests and Agents, click the **+** icon to the right of the pull-down menu.

#### Example Stacked Bar Chart widget

Below is an example of a configured Stacked Bar Chart widget and the resulting output.

IMAGE MISSING

1. The configured widget visualizes mean Response Time for HTTP Server tests based on Cloud & Enterprise Agents.
2. Graph is configured to be oriented to extend from left to right with Y axis as Servers sorted alphabetically.
3. The “Show Labels” box is checked and as a result Response Time labels can be seen in the graph.
4. This widget is visualizing 4 out of 5 available HTTP Server tests.

#### Grouped Bar Chart widget

The image below shows an unconfigured Grouped Bar Chart widget.

IMAGE MISSING

Grouped Bar Chart widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts also have Metrics.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Maximum:_ The maximum value in the set of measurements, such as the response times of an HTTP Server test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the response times of a HTTP Server test over the time period of the report.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the response times, over the time period of the report.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.

**Axis:** Arrange the data into bars by the following criteria, and orient the label\(s\) on the axis displayed :

* _All:_ Produces a single bar with all data.
* _Source:_ Produces bars for each source of data \(test or Agent\).
* _Continents:_ Produces bars for each continent/continental region \(North America, Europe/EMEA, Asia/APAC, etc...\).
* _Countries:_ Produces bars for each country.
* _Test:_ Produces bars for each test.
* _Test Labels:_ Each test label would get their own bar.
* _Sources:_ Produces dedicated bars for each source.
* _Visited Sites:_ Each visited side would have their own bar.
* _Private Networks:_ Each private network gets their own bar.
* _User:_ Each user gets their own bar.
* _Connection:_ Each connection gets a dedicated bar.
* _Network:_ Produces bars for each network.
* _Domain:_ Each visited domain gets their own bar.
* _Location:_ Each location would have a dedicated bar.
* _Endpoint Agent Labels:_ A separate bar is produced for each Endpoint Agent Label.
* _Endpoint Tests:_ Each Endpoint Test gets their own bar.
* _Devices:_ Each device is dedicated a bar on graph.
* _Interfaces:_ Device Interfaces would have dedicated bars.
* _Device Types:_ Separate bars produced for each type of device.
* _Interface Types:_ Each  interface type would have dedicated bars.

Either **X-Axis** or **Y-Axis** is displayed, based on the **Orientation** selected. 

**Orientation:** The orientation of the bars--either horizontal or vertical. Selecting horizontal or vertical orientation sets the associated pull-down menu label to **X-Axis** or **Y-Axis.**

**Group By:** One or more sets of bars are produced for each of the values in the **Axis** setting, based on the value of the Group By setting.  The available settings will be among the following:

* _All:_ All data aggregated into one bar
* _Test:_  Data from all Sources and Tests are aggregated together into a single line.
* _Source:_  Data from all tests or Agents are given their own bars.
* _Continents:_ Data are aggregated by continent.  A chart line is displayed for each continent that has data from at least one source.
* _Countries:_  Data are aggregated by country.  A chart line is displayed for each country that has data from at least one source.
* _Test Labels:_ Data from each Test Label is aggregated into a single line.
* _Sources:_ Data from each source is aggregated into a single line.
* _Agent Labels:_ Data from each Agent Label is aggregated into a single line.
* _Servers:_ Data aggregated based on servers in a single line.
* _Visited Sites:_ Endpoint Data from each visited site is aggregated into a single line.
* _Private Networks:_ Data from each private network is aggregated into a single line.
* _Users:_ Data is aggregated based on user into a single line.
* _Platforms:_ Data from each platform Windows/Mac is aggregated into a single line.
* _Connections:_ Data for each connection is aggregated into a single line.
* _Networks:_ Data aggregated based on networks  into a single line.
* _Domains:_ Data aggregated based on visited domain into a single line.
* _Endpoint Agent Labels:_ Data from each Endpoint Agent Label is aggregated into a single line.
* _Device:_ Data from each Device is aggregated into a single line. 
* _Device Types:_ Data from each Type of Device  is aggregated into a single line.
* _Interfaces:_ Data from each Device Interface is aggregated into a single line.
* _Interface Types:_ Data from each Device Interface Type is aggregated into a single line.

**Sort By:** For charts containing multiple bars, the Sort By setting will determine in what order the bars appear.  That is, the value of the Sort By setting is applied to the value in the X-Axis/Y-Axis setting.

* _Default:_ Sort bars optimally, based on the settings for Metric and Show Comparison. The metric which is optimal for your settings is shown in parentheses.
* _Alphabetical:_ Sort bars by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort bars by ascending alphabetical order.
* _Highest:_  Sort bars by highest value first.
* _Lowest:_ Sort bars by lowest value first.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Limit To:** When checked, the chart will display at most the number of groups you set in the selector.  When more groups exist than are displayed, the **Sort By** order determines which rows are displayed.

**Sources:** Filter on names of tests or Agents which will provide the data to the report. To filter by both tests and Agents, click the **+** icon to the right of the pull-down menu.

#### Example Grouped Bar Chart widget

Below is an example of a configured Grouped Bar Chart widget and the resulting output.

IMAGE MISSING

1. The chart is configured to visualize Mean Receive Time from HTTP Server tests based on Cloud & Enterprise Agents.
2. Graph is configured to extend horizontally with Servers as Y axis grouped by Agent Labels and sorted in a descending order.
3. The “Show Labels” box is checked and as a result Receive Time labels are visible.
4. Widget is configured to visualize 4 out of 5 tests.

#### Pie Chart widget

The image below shows an unconfigured Pie Chart widget.

IMAGE MISSING

Pie Chart widgets have the following settings:  
 

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For a Map widget, the Metrics provided \(Response Time, Total Error Count and Total Fetch Time\) are composites of metrics found in an HTTP Server test.  For example, Response Time consists of four distinct metrics: DNS resolution time, connect time, SSL time and wait time.  Each of the four metrics are presented in a single pie chart.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** types available depend on the **Metric** setting, and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Maximum:_ The maximum value in the set of measurements, such as the response times of an HTTP Server test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the response times of a HTTP Server test over the time period of the report.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the response times, over the time period of the report.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.

**Group By:** One or more pie charts are produced based on the value of the Group By setting.  The available settings will be among the following:

* _All:_ All data aggregated into one pie chart.
* _Agent:_  Data from all Agents are aggregated into a single pie chart.
* _Continents:_ Data are aggregated by continent.  A pie chart is displayed for each continent that has data from at least one test.
* _Countries:_  Data are aggregated by country.  A pie chart is displayed for each country that has data from at least one test.
* _Test:_  Data from all Tests are aggregated into a single pie chart.
* _All:_ Group all the data as a single chart.
* _Test Labels:_ Data from all associated Test Labels are aggregated in a single pie chart.
* _Sources:_ Data from each source is given their own pie charts.
* _Agent Labels:_ Data from each Agent Label is given their own pie chart.
* _Servers:_ Data aggregated based on servers. Each server would  have a dedicated pie chart.
* _Visited Sites:_ Endpoint Data from each visited site is given their own pie chart.
* _Private Networks:_ Data from each private network is given their own pie chart.
* _Users:_ Data is aggregated based on user, each user gets their own pie chart.
* _Platforms:_ Data from each platform Windows/Mac is given their own pie chart.
* _Connections:_ Data for each connection is given their own pie chart.
* _Networks:_ Data aggregated based on networks, each network gets their own pie chart.
* _Domains:_ Data aggregated based on visited domain, each domain would have a dedicated pie chart.
* _Endpoint Agent Labels:_ Data from each Endpoint Agent Label gets their own pie chart.
* _Device:_ Data from each Device is given their own pie chart. 
* _Device Types:_ Data from each Type of Device  is given their own pie chart.
* _Interfaces:_ Data from each Device Interface is given their own pie chart.
* _Interface Types:_ Data from each Device Interface Type is given their own pie chart.

**Filter:** Names of Tests or Agents which will be the source of the data to the report. To filter by both tests and Agents, click the **+** icon to the right of the pull-down menu.

#### Example Pie Chart widget

Below is an example of a configured Pie Chart widget and the resulting output.

IMAGE MISSING

1. The widget is configured to visualize Mean Page Load Time of Browser Sessions - Web collected by Endpoint Agents.
2. Group By field is set to Networks and as a result data from each network is visualized as a separate pie chart.
3. The data is not filtered and as a result all available data is visualized.

#### Map widget

The image below shows an unconfigured Map widget.

IMAGE MISSING

Map widgets have the following settings:  
 

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts is also a category of choices for Metrics.  For more information on ThousandEyes metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. **Measure** choices available depend on the **Metric** setting, but will come from the following list:

* _% positive:_ The percentage of measurements greater than zero.  For example, the percentage of time when a Network alert was active.
* _% zero: ****_The percentage of measurements equal to zero.  For example, the percentage of time when a Network alert was active.
* _Maximum:_ The maximum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the latency times of a Network test over the time period of the report.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99.  98% is the default.  For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were from 0 to 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements.  For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\)
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\)

**Group By:** Sets the Map widget to display results grouped by:

* _Agent:_  Agents are displayed with circles on the map at their geographic location.  Enterprise Agents use the geographic location listed in the Agent's row of the Enterprise Agents page \(Settings &gt; Enterprise Agents\). Agents are colored based on the value of the data, per the colored legend and associated scale from the **Fixed Scale** setting, as described below.
* _Countries:_  Data are aggregated by country.  Countries are colored based on the value of the data, per the colored legend and associated scale from the **Fixed Scale** setting, as described below.
* _Continents:_ Data are aggregated by continent.  Continents are colored based on the value of the data, per the colored legend and associated scale from the **Fixed Scale** setting, as described below.

**Sort By:** Available only for a **Group By** setting of "Agents". Orders multiple entries in the Tooltips that are displayed when mousing over circles with multiple Agents.

* _Default:_ Sort bars optimally, based on the settings for Metric and Show Comparison. The metric which is optimal for your settings is shown in parentheses.
* _Alphabetical:_ Sort bars by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort bars by ascending alphabetical order.
* _Highest:_  Sort bars by highest value first.
* _Lowest:_ Sort bars by lowest value first.

**Scale:** Specify the range of values for the colored legend in the map. By default, the low end is set to 0. Not available for metrics with non-arbitrary values \(i.e. percent metrics\).

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Filter:** Names of Tests, or Agents or servers which will be the source of the data to the report. To filter by multiple criteria, click the **+** icon to the right of the pull-down menu.

#### Example Map widget

Below is an example of a configured Map widget  and the resulting output.

IMAGE MISSING

1. The widget is configured to visualize Mean Packet Loss observed in an Agent to Server tests with Cloud & Enterprise Agents as Data Source.
2. Group By field is set to Countries and hence data is aggregated based on Countries and coloured on the map accordingly.
3. Widget is configured to visualize data from all 16 available tests.

Note in the upper-right corner the magnification selector, which allows you to zoom in or out on the map.  Also note in the lower-right corner the colored legend, with a range of the Metric \(Availability\) which starts at 0% and ends at 100%.

#### Box-and-Whiskers widget

The image below shows an unconfigured Box-and-Whiskers widget.

IMAGE MISSING

Box-and-Whiskers widgets have the following settings:

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes test has its own Metrics. For example, Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency and Packet Loss. In addition to each of the ThousandEyes test types, Alerts is also a category of choices for Metrics.  For more information on ThousandEyes Metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Group By:**

* _Single Chart:_ Data from all Sources and Tests are aggregated together into a single plot.
* _Test:_  Data from all Tests are aggregated together into a single line.
* _Agent:_  Data from all Agents are given their own chart lines.
* _Continents:_ Data are aggregated by continent.  A chart line is displayed for each continent that has data from at least one source.
* _Countries:_  Data are aggregated by country.  A chart line is displayed for each country that has data from at least one source.
* _None:_ Data are not aggregated.
* _All:_ Group all the data as a single chart.
* _Test Labels:_ Data aggregated based on Test Labels,  each Test Label gets their own chart.
* _Sources:_ Data from each source is given their own charts.
* _Agent Labels:_ Data from each Agent Label is given their own chart.
* _Servers:_ Data aggregated based on servers. Each server would  have a dedicated chart.
* _Visited Sites:_ Endpoint Data from each visited site is given their own chart.
* _Private Networks:_ Data from each private network is given their own chart.
* _Users:_ Data is aggregated based on user, each user gets their own chart.
* _Platforms:_ Data from each platform Windows/Mac is given their own chart.
* _Connections:_ Data for each connection is given their own chart.
* _Networks:_ Data aggregated based on networks, each network gets their own chart.
* _Domains:_ Data aggregated based on visited domain, each domain would have a dedicated chart.
* _Endpoint Agent Labels:_ Data from each Endpoint Agent Label gets their own chart.
* _Device:_ Data from each Device is given their own chart. 
* _Device Types:_ Data from each Type of Device  is given their own chart.
* _Interfaces:_ Data from each Device Interface is given their own chart.
* _Interface Types:_ Data from each Device Interface Type is given their own chart.

**Note:** If the Group By field's setting is the same as the Source field type \(e.g. Group By is "Test" and Source type is "Test", Group By is "Countries" and Source type is "Countries", or Group By is "Monitors" and the Source type is "Monitors"\) then the Source field takes precedence.

For example, if Group By is "Countries" and Source type is "Tests", then all selected Tests will have their data grouped by all countries found from those Tests's results.  Each country will have its own chart.  However, if Group By is "Countries" and Source type is "Countries", then only those countries selected in the Source selector will have their own chart.

**Fixed Time Span:** When checked, a date selector will appear, allowing selection of a range of days different than the one specified for the entire report. The widget will display data in that range.

**Sources:** Filter sources from which the data will be taken.  The selections change based on which **Metric** is set, and will be one of the following:

* _Alert Rules:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Alert Rules.
* _Agents:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agents.
* _Agent Labels:_ If the **Metric** is a Network, Web, DNS or Voice test or alert metric, a list of Cloud and Enterprise Agent Labels \(Built-in or Custom\).
* _Tests:_  For any **Metric**, a list of Tests.
* _Test Labels:_ For any **Metric**, a list of Test Labels \(Built-in or Custom\).
* _Monitors:_ If the **Metric** is a BGP test or alert, a list of ThousandEyes BGP monitors.
* _Countries:_ If the **Metric** is a DNS+ test or alert, a list of countries.

**Scale:** Configure scaling of shown metric. By default, the low end is set to 0. Not available for metrics with non-arbitrary values \(i.e. percent metrics\).

#### Example Box-and-Whiskers widget

Below is an example of a configured Box-and-Whiskers widget entitled  and the resulting report output.

IMAGE MISSING

The configuration shows the widget's Metric as “Throughput".  The Group By selector is set to "Agents", which displays Cloud and Enterprise Agents on the map in their respective locations.  The source filter is set to "Tests" and "1 of 188 included", indicating that one test's data is being displayed.

For each time on the horizontal axis, dots representing minimum and maximum values for that round of data are plotted, along with a dot for the median of all values in that round.  Additionally, a blue bar starts below the median at the value representing the end of the first quartile of the data, and extends above the median to the value representing the end of the third quartile.  Mousing over the points or bars will display a tooltip with the numeric values:

IMAGE MISSING

At 2019-01-27 we see that the data from all Agents had the following distribution:

* One quarter of the measurements fell into the range of 8.78 mbps to 42.65 mbps \(minimum dot to bottom of the bar\)
* One quarter of the measurements fell into the range of 42.65 mbps to 88.18 mbps \(bottom of the bar to the median dot\)
* One quarter of the measurements fell into the range of 88.18 mbps to 98.67 mbps \(median dot to the top of the bar\)
* One quarter of the measurements fell into the range of 98.67 mbps to 139.85 mbps \(top of the bar to the maximum dot\)

Position of the median dot relative to the ends of the bar indicates the spread of the values in the data for the quartile above and below the median.

## Report Snapshots

Snapshots are reports that are saved with a fixed time period of data.  Snapshots can be created on demand, or created automatically according to a schedule.

### Creating a new Report Snapshot

To create an on-demand report snapshot, select the desired report in the Report name pull-down on the Reports page.  Then select the **Snapshot &gt; Save a Snapshot** link from the Reports page. The **Save a Snapshot** side pane will appear.  The dialog allows you to name the snapshot.  The current date range in the report date selector's To and From fields will be used to select the data in the snapshot. Options to anonymize data that can reveal a user's identity and creating a public share-link are also available here.

IMAGE MISSING

Report snapshots can be automatically generated at periodic intervals, such as each week or month.  To create or edit a snapshot schedule, select the desired report in the Report name pull-down on the Reports page.  Then select the **Snapshot &gt; Schedule Snapshots** link. The **Schedule Snapshots** side pane will appear, and allow you to select settings for the snapshot's schedule.

IMAGE MISSING

The following settings are available:

* **Snapshot Name:** Enter a name for the snapshot, which will appear in the listing under Reports &gt; Report Snapshots.
* **Repeat Interval:** Select the frequency with which to create snapshots. You may select from the following values:
  * None: Creates a single report at the specified time.
  * Daily
  * Weekly
  * Bi-Weekly
  * Monthly
  * Quarterly \(3 Months\)
  * Custom: Allows you to select an integer number of days, weeks or months.
* **Timezone:** Select the desired timezone
* **Next Repeat On:** Shows the time of the next scheduled snapshot.
* **Contains:** Select the number of days or weeks of data that the snapshot will cover, going back from the creation date of the snapshot.
* **Emails:** Displays addresses to which the ThousandEyes platform will email each snapshot. The recipients on the email list will receive an HTML-formatted version of the Snapshot and a link to the snapshot in the ThousandEyes platform, once the new snapshot is generated. Add addresses using the **Edit Emails** link.
* **Auto Share Snapshots:** When enabled, the report snapshots will automatically be shared via a public link \(see **Sharing Report Snapshots**, below\). The link will be included in email if the Subscriber Emails \(above\) is configured. You can stop sharing the existing report snapshots at any time. To stop automatic creation of the report snapshots, uncheck the **Auto Share Snapshots** box.
* **Anonymize data that identifies users:** All data that could reveal user's identity are anonymized.
* **Include a PDF attachment of the Report:** Attaches a PDF version of the report snapshot when sending out report snapshot notification emails.

A report with an associated snapshot schedule will have a watch icon beside its name in the Report name pull-down menu.

To remove the scheduled creation from a report, select the  schedule, select the desired report in the Report name pull-down on the Reports page, then select **Snapshot &gt; Cancel Schedule** link.

**Note:** Changing the report layout that generated a scheduled snapshot will not change existing scheduled snapshots. Only future snapshots will be affected by a the change to the report layout.

### Working with Report Snapshots

To view existing on-demand and scheduled snapshots, navigate to the **Reports &gt; Report Snapshots** page.  A table of Snapshots will be displayed, showing information about each Snapshot.  Snapshots created from a schedule will have a watch icon next to the snapshot name.  The report which generated the snapshot is listed, along with creation date and the number of days of data in the snapshot.

Clicking on the link of a snapshot will display the snapshot.  The snapshot may be saved as a file to your drive by using your browser's **File** menu. Snapshots can be deleted by clicking on the trash can icon in the row of the snapshot on the **Reports &gt; Report Snapshots** page.  Existing snapshots cannot be edited.

**Note:** When creating a new report using the **New from this Report** link, the newly created report will not inherit the schedule for creating snapshots from the original report.

### Sharing Report Snapshots

Snapshots of reports can be manually shared via a publicly accessible URL, similar to Snapshot Sharing of test data. To share a snapshot of a report, navigate to the desired Report and click on the gear icon on the right-hand side to open the report snapshot's additional options menu.

IMAGE MISSING

Here, click the **Link Share** switch and the public URL for viewing this report snapshot will be presented. You may copy the link to your clipboard and paste it into a document, an email, a chat or any other medium.

You may stop sharing the report snapshot at any time by unchecking the **Shared** checkbox shown above.

## Related information

The following resources provide further information:

* [Working with the Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmdKAC_Working-with-the-Dashboard) article provides basic information about Dashboards, a feature similar to Reports but tailored for usage in [NOCs](https://en.wikipedia.org/wiki/Network_operations_center) and similar operational environments.
* [Embedding report widgets in external web sites](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnUKAS_Embedding-report-widgets-in-external-web-sites) article will guide you through the process of creating chunks of HTML code that display individual report widgets and can be instantly added to your existing NOC dashboards.

