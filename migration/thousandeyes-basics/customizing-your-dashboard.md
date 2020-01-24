# Customizing your Dashboard

In ThousandEyes, you can configure your Dashboard page to meet your own individual needs. If you have a role with the appropriate permissions, you can configure a Dashboard and make it available for other users in your own Account Group. It's pretty simple to customize as needed - just check out the details below.

## Dashboard configuration

To view or configure new or existing Dashboards, start at the top of your Dashboards page.

IMAGE MISSING

1. Use the selector to choose one of the Dashboards shared within your Account Group or private dashboards you've created for yourself.
2. Displays time since current dashboard was last refreshed.
3. Click the **Add/Manage Widgets** button to edit the widgets of the current Dashboard.
4. Click the **Options** button ****to reveal a drop down menu with below options:

* **Create New Dashboard** creates a new blank dashboard to be named and populated with widgets.
* **Duplicate Dashboard** Creates a copy of current dashboard.
* **View Dashboard Details** Opens a side modal where the report title, description and sharing options within the account groups of the organization can be configured.
* **Delete Dashboard** deletes the currently viewed dashboard.

### Settings

 Select **View Dashboard Details** from Options menu to configure current Dashboard's settings:

IMAGE MISSING

* The **Dashboard Name** box displays the name of the Dashboard . Click in the box to edit the Dashboard name. The name of a Dashboard is shown when the Dashboard is used on the Dashboard page.  
* The **Account Group Visibility** setting allows setting below sharing options:
  * **All account groups:** Share current dashboard with all account groups in organization.
  * **Only Current account group:** Do not share current dashboard with other account groups.
  * **Specific account groups:** Share current dashboard with specific account groups selected in resulting drop-down list. 
* The **Set as private** checkbox indicates that this Dashboard will be viewable by only you. If this box is unchecked, the Dashboard is available to anyone from the Account Group in which the user created the Dashboard.
* The **Set as my default** checkbox indicates that this Dashboard will be your default Dashboard--the one that appears when the Dashboard page is opened \(you can still select and view other Dashboards using the **Current** selector on the Dashboard page\).  The user's default Dashboard is displayed as "Default \(Dashboard name\)" in the **Current** selector to indicate its status as the default.  If this box is unchecked, the Dashboard page displays Dashboard which is the Account Group Default.  
* The **Set as default for account group** checkbox indicates that this Dashboard will be used as a default for all users in the current Account Group.  A User Default supersedes an Account Group default.   Only users with a role having the _Set dashboard template as account group default_ permission can set an Account Group default.
* Click the **Save Changes** button when finished editing to return to the Dashboard page.

#### Widgets

Click the **Add/Manage Widgets** button to open the current Dashboard's widgets for configuration \(settings can also be configured\).

At the top of the page, the available widget types will be shown in the **Add New Widgets** panel:

IMAGE MISSING

Click the **Dashboard Widgets** to display just the widgets which are available in Dashboards only:

IMAGE MISSING

Click the **Report Widgets** to display just the widgets which are common to Reports and Dashboards:

IMAGE MISSING

## Widget configuration

Widgets can be added to the Dashboard by clicking and dragging the widget's icon from the Add New Widgets panel to the page below. Once a widget is dragged into the configuration, it can be configured. To reposition a widget within the Dashboard, drag it above or below another widget.

Click the **Settings** \(gear icon\) to expand or close a widget. Click the **More Actions** menu \(three vertical dots icon\) to rename, delete or duplicate the widget. Click the chevron \(&lt; or &gt; icon, if present\) to change the widget to full or half the page width. 

Once your configuration is complete, click the **Return to Dashboard** button. Be careful when editing a Widget's settings, since all changes are immediately applied for all users using the Dashboard.

Configuration specific to each widget type follows.

#### Alert List

Alert List widgets display a list of active and recently cleared alerts.

IMAGE MISSING

**Alert Type:** Configure the types of alerts to show. Various combinations can be configured, from BGP Routing, Cloud and Enterprise Agents, Devices, and Endpoint Agent classes of alert types.

**Limit to:** Number of alerts to show. If the amount of alerts to show exceeds the configured limit, a **Show more alerts** link is provided.

**Active within:** Limit the age of alerts shown. Only alerts that are currently active, or were active during the outlined period, are shown by the widget. The currently active alerts are listed first.

**Filters:** Just like with [report-based widgets](), additional filters can be configured to narrow down displayed alerts, by specific Tests, Labels, Agents, Alert rules, etc.

#### Alert Grid

Alert Grid widgets display alerts from tests, broken down by Agent or BGP Monitor.

IMAGE MISSING

**Alert Type:** Agents will display the Account Group's Agents across the top of the Alert Grid.  BGP will display BGP Monitors.

**Filter all/any:** Enter one or more filter criteria.  Filter criteria will be displayed when you place focus on the text field.  With "all" the filter displays matches of the criteria that meet all the criteria in the text field.  With "any" the filter displays matches if any of the criteria are met.  For example, two Test Name criteria of "ThousandEyes" and "Support" would match the tests "My ThousandEyes", "ThousandEyes Support site" and "Linux support website" if the selection were "any".  If the selection were "all", then the only match would be "ThousandEyes Support site".

**Exclude all/any:** Identical to **Filter all/any** above, except matches cause exclusion from display in the widget.

#### Agent Status

Enterprise Agent Status widgets display Enterprise Agents on a world map, using the Agent IP address with the ThousandEyes geolocation database, or manually configured geographical information to place the Agent in the correct location on the map.

IMAGE MISSING

**Agents**: This selector allows the widget to display either Enterprise Agents or Endpoint Agents  
**Show:** Owned Agents displays only those Agents that belong to the user's current Account Group \(i.e. Agents installed using the Account Group's token\).  All Assigned Agents\(Enterprise Agents only\) displays owned Agents plus any Agents shared to your Account Group from another Account Group in your Organization.

**Filter:** Allows for the selection of specific Agents or Agent Groups.

#### Tests

 Tests widgets display a list of tests.  Each test lists the name the test type, the test's alert status and a 12-hour trend graph of key metrics relevant to that test type.

IMAGE MISSING

**Filter all/any:** Enter one or more filter criteria.  Filter criteria will be displayed when you place focus on the text field.  With "all" the filter displays matches of the criteria that meet all the criteria in the text field.  With "any" the filter displays matches if any of the criteria are met.  For example, two Test Name criteria of "ThousandEyes" and "Support" would match the tests "My ThousandEyes", "ThousandEyes Support site" and "Linux support website" if the selection were "any".  If the selection were "all", then the match would only be "ThousandEyes Support site".

**Exclude all/any:** Identical to Filter all/any above, except matches cause exclusion from display in the widget.

#### Color Grid

The Color Grid widget shows an array of colored cards, where each card's color depends on the configured scale.

IMAGE MISSING

**Data Source:** The data source indicates which platform service will be referenced within the widget. Current options include:

* Alerts: Data is obtained from Platform Alerts
* Cloud & Enterprise Agents: Data is obtained from Scheduled Tests performed by Cloud & Enterprise Agents
* Devices: Data is obtained from Device Layer reporting
* DNS+: Data is obtained from DNS+ Tests
* Endpoint Agents: Data is obtained from Scheduled Tests & Monitored Domain metrics
* Routing: Data is obtained from BGP tests

**Metric:** Each type of ThousandEyes Data Source has its own Metrics. For example, Cloud and Enterprise Agents data from Agent to Server tests have five Metrics: Available Bandwidth, Capacity, Jitter, Latency, and Packet Loss. In addition to each of the ThousandEyes test types, Alerts also have Metrics.  For more information on ThousandEyes Metrics, see the ThousandEyes Knowledge Base article [ThousandMetrics: what do your results mean?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics-What-do-your-results-mean)

**Measure:** A statistical measurement. Measure types available depend on the Metric setting and will be one or more of the following:

* _% positive:_ The percentage of measurements greater than zero. For example, the percentage of time when a Network alert was active.
* _% zero:_ The percentage of measurements equal to zero. For example, the percentage of time when a Network alert was active.
* _Maximum:_ The maximum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _Minimum:_ The minimum value in the set of measurements, such as the latency times of a Network test over the time period of the report.
* _nth Percentile:_ The value of the Metric which contains n% of the measurements. When "nth Percentile" is selected, a text box will appear, allowing you to specify an integer for the percentile value from 1 to 99. 98% is the default. For example, a 98th Percentile whose value is 500 ms for a **Metric** of "Response Time" would indicate that 98% of the measurements of the response time were between 0 and 500 ms.
* _Mean:_ The value of the arithmetic mean \(i.e. average\) of the measurements. For example, a **Mean** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the average value of the latency in the reporting period was 50 ms.
* _Median:_ The value of the median measurement. For example, a **Median** of 50 ms for a **Metric** of "Latency" for one or more Network tests would indicate that the value of 50 ms is the middle value in the range of all values of the latency in the reporting period.
* _Total:_ The total number of measurements. For example, a **Metric** set to "Alerts" and **Tests** set to a DNS+ test indicate the total number of DNS+ alerts received in the reporting period.
* _Active Time:_ The amount of time an Alert Rule\(s\) was active. \(Alerts Metrics only\).
* _Inactive time:_ The amount of time an Alert Rule\(s\) was inactive. \(Alerts Metrics only\).
* _Standard Deviation:_ The population standard deviation of a set of measurements, such as the latency times of a Network test over the time period of the report.

**Cards:**

* _All:_ Data from all sources are aggregated into a single card.
* _Test:_ Data from all tests are given their own card based on group cards configuration.
* _Test Labels:_ Data from all test labels configured in **Settings &gt; Labels** are given their own card based on group cards configuration.
* _Agents:_ Data from all agents are given their own card based on group cards configuration.
* _Agent Labels:_ Data from all agent labels configured in **Settings &gt; Labels** are given their own card based on group cards configuration.
* _Servers:_ Data from all Target servers are given their own card, and the card is displayed for each Target server.
* _Continents:_ Data from all sources are aggregated by continent. A card is displayed for each continent that has data from at least one source.
* _Countries:_ Data from all sources are aggregated by country. A card is displayed for each country that has data from at least one source.

**Group Cards By:**

* _All:_ Data from all sources are grouped by **Cards** drop-down menu configuration.
* _Test:_ Data from sources configured in Cards are grouped by Test name.
* _Test Labels:_ Data from sources configured in Cards are grouped by Test Labels.
* _Agents:_ Data from sources configured in Cards are grouped by Agent name.
* _Agent Labels:_ Data from sources configured in Cards are grouped by Agent Labels name.
* _Servers:_ Data from sources configured in Cards are grouped by Target Servers name.
* _Continents:_ Data from sources configured in Cards are grouped and aggregated by Continent.
* _Countries:_ Data from sources configured in Cards are grouped and aggregated by Country.

**Sort Cards By:** For cards displayed in multiple rows, the **Sort By** setting will determine in what order the cards appear. That is, the value of the **Sort Cards By** setting is applied to the value in the **Cards** setting:

* _Alphabetical:_ Sort rows by ascending alphabetical order.
* _Alphabetical \(Reverse\):_ Sort rows by descending alphabetical order.
* _Value:_ Sort rows by highest value first.
* _Value \(Reverse\):_ Sort rows by lowest value first.

**Time Span:** Select a number of minutes, hours or days. The widget will display data for the time span configured in Time setting.

**Scale:** Select a number range on how cards will be colored. Select the maximum metric value for a card to be colored green and the minimum metric value for a card to be colored red.  

**Columns:** Select a number of group of cards displayed per column, the dashboard can allocate up to two columns on the widget.

**Limit To:** When checked, the cards in a group will be displayed up to the number you set in the selector. When more cards exist than are displayed, the **Sort Cards By** order determines which cards are displayed.

#### Report widgets

Report widgets display a report for the Dashboard in the same manner that reports widgets are configured using the Reports feature.  Every type of report widget that is available in the Reports feature can be used in a Dashboard. Consult the ThousandEyes Knowledge Base article [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS) for information on what each type of reports widget provides and how the widget is configured.

## Related information

The following resources provide further information:

* [Working with the Dashboard](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmdKAC_Working-with-the-Dashboard) article provides basic information about Dashboards feature.
* [Working with Reports](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnTKAS_Working-with-Reports) article guides you through the configuration of a Report, a feature similar to Dashboards but with additional abilities like \(periodic or instant\) report snapshot creation and [externally embeddable widgets](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnUKAS_Embedding-report-widgets-in-external-web-sites).

