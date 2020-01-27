# Release Notes: 2013-10-02

Welcome to the October 2013 release update!  We've got changes in various areas of the application for you today - from transparent proxy detection for Virtual Appliances, to a recycle bin for deleted tests, to a process to make your alert notifications more relevant.  Check out the list below, and see what you think; we're psyched to hear your feedback.

## Path Visualization changes

### Show on Timeline

We've updated the timeline component in the Path Visualization and BGP views, to be more consistent with the other views of ThousandEyes.  With this release, you can overlay an agent's \(or monitor's\) measurements for the view atop the aggregate values across all agents.

IMAGE MISSING

To add an agent values to the timeline, click the **Show on Timeline** link from the information box that appears when hovered over an agent \(or monitor, in BGP view\). To remove the agent overlay, hover over the agent, and click **Remove from Timeline**, or select a different agent. The agent selection carries over between views, so if you're looking at data for London in the Page Load view, it will carry over into the Path Visualization view.

IMAGE MISSING

IMAGE MISSING

Note: the timeline can only accommodate a single agent's values at a time, so choosing to Show on Timeline for any other agent will override the agent data being shown.

### Run Path Visualization test

It's now also possible to run an instant Path Visualization test by clicking the "Run Test" link from the information box that appears when hovered over an agent in path visualization view.  This will open the Instant Test page, pre-populate the form and target with your agent selection, and run the test.

## New! Recycle Bin for recently deleted tests

Historically, if you've deleted a test, then added it back, the test would be added, and would reference previously gathered data, with a measurement gap between when it was deleted and re-added. This behavior is changed as of today's release.

When you delete a test, measurements will stop being collected, and it will move into the Recycle Bin.  To find the Recycle Bin, go to the [test settings](https://app.thousandeyes.com/test-settings/) page, and note the link for "**X recently deleted tests**".  Clicking the link causes a pane to open showing a list of deleted tests, categorized by test type.  Recently deleted tests are available for 14 days, after which they are permanently purged from test results.

IMAGE MISSING

Clicking the Recover link opens the Add New Test dialog, and will allow you to change the test name, agent settings, interval and other options, then re-enable your test.  The test will show a measurement gap between when it was deleted and when it was re-enabled, but legacy measurements for the test will be maintained.

IMAGE MISSING

Creating a new test with the same target will no longer pull in previously gathered data for that test, and will instead begin gathering data anew.

## Alerts

### Agents with Local Problems excluded from Alert calculation

Our team has been making a concerted effort around improving the accuracy of alerts, to make alerts more timely and relevant for our users. In our [June 11, 2013 release](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmm4KAC), we introduced the concept of _Local Agent Problems_, which is measured using an internal agent-to-agent reference measurement test.  When an agent is experiencing local problems, a mark appears on the event timeline, indicating when a specific Cloud Agent is reporting problems.  We've taken this data and added it into the alerts notification system, such that when an agent is experiencing local problems, it will be suppressed from the number of agents used in reporting problems, which triggers the alert.

If you have a minimal number of agents assigned to your tests, you should review alert rules in order to ensure that minimum thresholds for agents are updated accordingly.

### New DNS+ Domain Alerts option: Reference metrics

We've added a new option to the alert rules interface, specifically for DNS+ availability metrics. When creating a DNS+ Alert rule for the availability metric, the rule will now include a reference availability component.  Create a rule which shows availability dipping below a certain percentage, while reference availability remains above this percentage.

IMAGE MISSING

When selecting this option, the Reference availability metrics \(as well as the Availability metrics\) for countries violating the alert rule will be provided in the alert notification.  Existing DNS+ Availability based rules will remain unchanged, however they will be updated if users attempt to change the metric upon which the rules are based.

## Virtual Appliance Changes

### Transparent Proxy detection

Effective with Virtual Appliance version 0.22, the system will now detect the presence of a transparent web proxy. When a web proxy is detected during the agent validation process, an error will be thrown during diagnostics, indicating the presence of a proxy, and the error message which occurs during an attempt to communicate with the ThousandEyes API.

### De-activating Virtual Appliance configuration website

The Virtual Appliance can now be configured to run without exposing the configuration website on external IPs. To activate this option, at least one valid SSH public key must be assigned to the server; activate this option using the te-va-configure command from inside an SSH session against the server. 

## API

From an API perspective, there are two minor updates to this week's release.

### Record sort order

We've updated our API to sort records by roundId \(which refers to the starting epoch time for a round\) in ascending order.  This will prevent records from shifting position between pages of results, for paginated query results \(any query result which exceeds 1 hour of data\).  This sorting was introduced to correct a behavior observed by querying a large period of data over an incomplete round.

### Public IP information for Enterprise Agents

Prior to this release, public IP information was not available when querying the API for agent information on Enterprise Agents. With today's release, for agents which have a different public IP address which differs from the private IP, a new field will be available in the &lt;agents&gt; UI. Keep in mind that the prefix and network information refers to the public address space, and not the private space.

```text
{
    "agents": [
        {
            "agentId": 5492,
            "agentName": "Italy-VA",
            "location": "Emilia-Romagna, Italy",
            "countryId": "IT",
            "ipAddress": "192.168.1.51",
            "publicIpAddress": "79.35.247.235",
            "prefix": "79.35.0.0/16",
            "network": "Telecom Italia S.p.a. (AS 3269)",
            "public": 0
        }
    ]
}
```

##  Bug Fixes

What release would be complete without a squashed bug or two?  We've solved the following customer-reported issues, identified below:

* Introduced when we changed the behavior of the dashboard to only show completed rounds, the current values shown in the dashboard were one round old. After this update, the dashboard will show current values for tests, if loaded after the completion of a testing round.
* We've also corrected a problem where agents shared between accounts in an organization couldn't be used for instant tests by users in accounts with whom those agents were shared. Prior to this fix, the agents would report "Invalid Agent ID" when attempting to run an instant test.

