# Alerts

The ThousandEyes platform allows customers to configure highly customizable Alert Rules and assign them to tests, in order to highlight or be notified of events of interest. For customers who want simplicity in alert configuration and management, the ThousandEyes platform ships with default Alert Rules configured and enabled for each test.

{% hint style="info" %}
**For Mac OS Catalina Users**: Test text

**sdjfkl;asdfjlk;sdfj jksld;f** 

1. _**fsdfsdf**_
2. _**jklsdjlkflksdflk** sdfsdfsdfsdfsdfsdfsdfsdf_
{% endhint %}

## Viewing alerts

Current and past alerts can be viewed on the Alerts page.  The Alerts page has two tabs:

* **Active Alerts:** List of alerts currently active for any test within your Account Group.
* **Alerts History:** List of alerts no longer active from tests in your Account Group, shown chronologically on a timeline, and with a table whose entries contain details on each alert.

### Active Alerts

![Active\_Alerts.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQmC&feoid=00NE0000006OT0r&refid=0EM44000000DYFe)

The Active Alerts tab shows all alerts currently active in your Account Group. The Active Alerts tab will auto-refresh every two minutes.

1. **Search**:  Search for alerts based on the following criteria: **Alert ID, Alert Rule Name,  Alert Type, Test ID, Test Name, Test Type or Status**. Entering text followed by the return/enter key will execute a search and display results in the table below. To filter events by more than one criteria, click either **All** or **Any** links to specify whether the table rows must match all \(AND\) or any \(OR\) of the selected criteria.  
2. **Alert Status:** 
   * A **red** colored box indicates that the Alert Rule is currently active for that Test. 
   * A **green** colored box indicates that the Alert was recently cleared for the test. A cleared Alert will be shown under Alert History tab.
   * A **grey** colored box indicates that the Alert Rule was disabled for that Test
3. **Alert Rule Name**: Name of the Alert Rule currently active. Expand an Alert Rule for more detailed information by Agent, BGP monitor, Start/End Time, Metrics at Alert Start, Metrics at Alert End and Duration for which the Alert was active.
4. **Test Name**: Name of the Test for which the Alert Rule is currently active
5. **Alert ID**: When gathering details for an Alert via ThousandEyes API, use the Alert ID to reference a particular Alert.

### Alert History

![Alert\_History.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQmC&feoid=00NE0000006OT0r&refid=0EM44000000DYFa)

The Alerts History tab tabulates triggered Alerts which are currently in "cleared" or "inactive" state or are "disabled". To interact with the Alert History page,

1. **Date and Time slider**: Input the date endpoints to view Alerts active during that timespan.  Click and drag on either the start or end bars and drag to the desired date.  Your selection will update the **From** and **To** date and time fields automatically. 
2. **Date and Time selector:** The **From** and **To** fields allow manual input of the date and time endpoints to display Alerts active at that time.  Clicking in the date field will both allow manual entry of dates and display a clickable calendar to select a date. Click on the calendar arrows to navigate in the current view \(default is the month view\). To change to a view of months in a year or a range of years, click the current title \(month, year or year range\) at the top-middle of the calendar.  The view will cycle to the next timeframe: month -&gt; months -&gt; years.
3. **Search for alerts**.  By entering text into the search box, you will search for alerts matching based on the following criteria: **Alert ID, Alert Rule Name,  Alert Type, Test ID, Test Name, Test Type or Status**. Entering text followed by the return/enter key will execute a search and refine the table below. To filter events by more than one criteria, click either **All** or **Any** links to specify whether the table rows must match all \(AND\) or either \(OR\) of the selected criteria.
4. **Alert Rule Name**: Expand an Alert Rule for more detailed information by Agent, BGP monitor, Start/End Time, Metrics at Alert Start, Metrics at Alert End and Duration for which the Alert was active.
5. **Test Name**: Name of the Test for which the Alert Rule was triggered.
6. **Duration**: Length of time for which the Alert Rule was active for that test.
7. **Alert ID:** When gathering details for an Alert via ThousandEyes API, use the Alert ID to reference a particular Alert.

## Default alerting rules

Default Alert Rules are defined according to the following list.  Within the Account Group, Default Alert Rules can be changed by any user having a role with the _View alert rules_ and _Edit alert rules_ permissions, such as the built-in Account Admin or Organization Admin roles.  Default rules can be configured with zero or more alert rules representing the default alert rule for each type.

| Name | Criteria | Minimum Locations |
| :--- | :--- | :--- |
| Default Network Alert Rule | Packet loss ≥ 20% | 2 locations |
| Default DNS Trace Alert Rule | Error is present | 2 locations |
| Default DNS Server Alert Rule | Error is present | 2 locations |
| Default DNSSEC Alert Rule | Error is present | 2 locations |
| Default DNS+ Domain Alert Rule | Availability ≤ 90% and Reference Availability ≥ 90% | 2 countries |
| Default DNS+ Server Alert Rule | Resolution time ≥ 100ms | 1 country |
| Default HTTP Alert Rule | Error type is any | 2 locations |
| Default Page Load Alert Rule | Page load is incomplete | 2 locations |
| Default Transaction Alert Rule | Error is present | 2 locations |
| Default BGP Alert Rule | Reachability &lt; 100% | 2 locations |
| Default Voice Alert Rule | Error is present | 1 location   |

## Additional Information

Cloud Agents displaying a _Local Problems_ message on a test results page are excluded from alert calculations:

![User-added image](https://success.thousandeyes.com/servlet/rtaImage?eid=ka02R000000UQmC&feoid=00NE0000006OT0r&refid=0EM44000000IhG4)

This is equivalent of having the Alert Rule's Agents field set to "All agents except" the Cloud Agent with the _Local Problems_ message.

