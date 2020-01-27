# Release Notes: 2014-06-04

Our team has been busy, and the changes we've been alluding to in the last couple of releases have come to fruition.  Check out the specific comments below, and let us know if you have any questions.

Thanks and enjoy the update!  
 

## Agent groups

As the first step in changing how we're grouping objects in the system, we've changed how you interact with agents. Admins can define groups of agents, which can be used to quickly select which agents get assigned to tests. You can use these groupings in test assignment today, as well as other areas \(including reports and alerts\) in the future.

To manage your groups, browse to **Settings** &gt; **Groups**, and create groups for your agents. We've rolled out some built-in agent groups \(for _IPv4_, _IPv6_, _Public_ and _Enterprise Agents_\) to allow you to quickly select the appropriate group of agents to assign to a test.

IMAGE MISSING

### Creating a group:

1. On the right hand side of the page, find the text "Group name..." and enter a name for your group
2. Choose a color by clicking the teal circle, and selecting a color from the context menu that pops up
3. Click the + button or hit enter
4. Search for or select agents from the main list.  Select multiple agents by clicking their names.
5. Drag the required agents into your group

Once your agents have been assigned to groups, these groups can be used to quickly assign agents to tests. Check out the test settings update below.

If you make a mistake, and need to remove an agent from a group, simply find the agent in the main list, and click the x on the right side of the group label.  

IMAGE MISSING

Groups can be renamed or deleted by clicking the pencil icon beside the group name, then either renaming and clicking the checkmark, or clicking the trash can and confirming.

IMAGE MISSING

Click the checkmark to confirm your change, or the trash can to remove the group

IMAGE MISSING

### Working with groups

Working with groups is pretty simple.  You can search using the search box above the agent list, and filter by agent group.  Filters and searches are **BOTH** applied, so only the items which meet all selected criteria will be shown.

IMAGE MISSING

1. Search for agents using the search box.  This case-insensitive search interface will search based on the agent's display name.  Agents which match on display name will be shown in the list below.
2. Select a group, to _**filter**_.  Agents which don't meet the search criteria \(1\) AND the filters \(2,3\) will be suppressed from the list
3. Multiple groups can be used for filtering.  Filters are ANDed together, so agents must match all filters in order to be displayed.
4. When a group is selected, that group will be highlighted on the agent's display.
5. To add an agent to another group, select \(the agent's name will be highlighted in teal\), and drag it into the new group; an "_Assign X agents to group_" will be shown \(see below\) IMAGE MISSING

## New test settings interface

Our test settings interface has undergone a pretty significant facelift as well. Primarily done in light of codebase and performance optimization, we've slightly changed how the test settings interface works.

### New Tests

We've shifted away from the tab-based mechanism, and moved to a button-based approach. You'll select the \(1\) layer you wish to test \(select from **Network**, **DNS**, **DNS+**, **Web**\), then \(2\) choose a test type, and complete the fields just as you would in the previous test settings interface. This release optimizes the data entry flow somewhat, reducing the overall time required in order to add data.

IMAGE MISSING

The Basic Configuration and Advanced Settings tabs now contain the content previously contained in the main test settings page, as well as the advanced options section of each test.  Basic Configuration contains your test target, testing interval, agent selection and alerting selections. Advanced Settings allows access to timeouts, target times, and other optional settings for the selected test type.

The agent selector has also changed, in order to take advantage of agent groups. In the agent selector, you can now search for agents, and filter based on one or more agent groups. Search by agent name \(using the search box\) and select groups from the right in order to filter your criteria. The total number of agents selected for the test will show up when you click outside the agent selection dialog.  See above for details on using the agent groups interface.

Depending on the test type and advanced settings configured for your test, you will see different lists of views enabled for the test, found on the right hand side of the page, beside the test settings.  As options specified in the test change the projected usage of the test, you will be notified regarding cloud agent unit usage changes. Usage details will be shown for both the current period, and the next full period.

IMAGE MISSING

1. **Views Enabled for This Test**: shows a list of the various views available to the end user.
2. **Projected Usage \(This Month\)**: takes current consumption for the monthly period, and projected usage based on currently enabled tests, as well as this new test.  
3. **Projected Usage \(Next Month\)**: takes only the currently configured tests, and the newly configured test, then extrapolates total monthly usage for a full calendar month.

NOTE: Keep note of both projected usage values.  A test which is under 100% on this month's usage may cause your organization to exceed Cloud Agent usage in the subsequent month.

### Working with Existing Tests

The image below lays out working with existing tests.  The numbered list below identifies actions associated with specific UI elements:

IMAGE MISSING

1. **Search** for tests, using name, type or target.
2. The **Basic Configuration** tab identifies targets, test intervals, assigned agents, and alert status / rule selection.
3. The **Advanced Settings** tab allows configuration of items such as browser authentication, headers, timeouts, and which test layer measurements are included.  Each test type has different advanced settings.
4. **Views Enabled for This Test** contains clickable links which will take you directly to the selected view for the selected test.
5. **Last Change** date and last user to modify the test is shown.
6. Click the **Enabled** checkbox to toggle the status of the test.  Checking this box takes effect immediately, and does not require a subsequent save.
7. Click the **trash** can to delete the test.  You will be prompted to confirm a deletion request.
8. Don't forget to click the **Save** button if you've made changes to any of the editable fields on a test.

## Test settings changes

###  HTTP Server

We've changed our HTTP Server test to allow users to control the timeout. In previous releases, the test was set by the system at 10 seconds. New tests will default to a 5-second timeout, but users can configure timeouts between 5 and 30 seconds by modifying the timeout, specified in the Advanced Settings interface.

IMAGE MISSING

### Transactions

Our maximum transaction timeout has been increased from 120s to 180s, in order to accommodate long-running transactions.  To change the timeout of a Web Transaction test, open the Advanced Settings tab and set the timeout.  Values range from 5 seconds to 180 seconds.

### Alerting decoupled from alert rule assignment

Prior to this release, the action of disabling alerts on a test would clear the list of alert rules assigned to the test.  Conversely, enabling alerts would automatically pull in the default alert rules for each test type included in your test.  Effective this release, alert rules have been decoupled from the enabled/disabled state of alerting on a test, allowing users to temporarily disable alerting on a test, then re-enable alerting without changing the list of alert rules assigned.  Simply check the Enabled checkbox.

This update lends itself well to configuration of maintenance windows, and can leverage the ThousandEyes API in order to make the change.  To update a test's alerting status,  use the appropriate test update endpoint, and set alertsEnabled = 0 \(for disabled\), or 1 \(for enabled\). Customers who have a periodic scheduled maintenance window can create and run a script to toggle alerting status during a maintenance period. Check out our developer reference [here](http://developer.thousandeyes.com/).

## API changes

### Set alerts to enabled/disabled

See "Alerting decoupled from alert rule assignment", above.

### Multiple tests against same target

We've corrected a minor issue with the ThousandEyes API, where users were unable to create multiple tests of the same type, targeting the same target.  Prior to this release, upon attempt to create a test with the same target as another test in your account, users would receive an HTTP/400 error.  This was not consistent with what was allowed via the user interface, and has thus been changed.  
 

## ThousandEyes Virtual Appliance

We've updated our Virtual Appliance package to alert when either the primary or secondary DNS server specified in the network configuration for your appliance was not functioning. An improperly configured DNS could result in false negatives when attempting to run DNS Trace queries.  Beginning with tonight's release, users will see the following error when configuring a virtual appliance with a non-responsive DNS server:

IMAGE MISSING

### Proxy settings change

Proxy configuration settings have been moved from the Agent tab to the Network tab in the Virtual Appliance configuration site. We've added an option to configure a separate proxy for operating system updates, and updated the interface used to enter targets onto the proxy bypass list.  This new interface will alert when an incorrectly configured target is added to the list, prompting for correction.  
 

## Single Sign-On default settings change

The Single Sign-On \(SSO\) configuration page has been updated to use a default value for the Service Provider Issuer field, of http://www.thousandeyes.com.  This entry can be overridden, but must match the authentication provider's settings.  This change was made to facilitate the integration of ThousandEyes with Okta for SSO.

