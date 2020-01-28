# Resetting an Enterprise Agent

Occasionally, customers may need to reset an Enterprise Agent. Resetting may be needed to repair incorrect behavior, or as the first step in reassigning the Agent to a different Account Group.

The ThousandEyes application allows sharing of Enterprise Agents across Account Groups in the same organization \(see the **Account Groups** setting for each Agent, under the **Basic Configuration** tab of the [Agent Settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmsKAC#Agent_Settings) page\). However, the one Account Group to which an Agent belongs cannot be changed through a setting in the ThousandEyes app. To change an Enterprise Agent's Account Group, the Agent must be reset and then reconfigured with the new Account Group's token.

This article provides instructions for resetting Enterprise Agents, according to the type of installation \(such as Virtual or Physical Appliance, Linux package or Docker container\). The article also provides instructions for optionally reassigning the Enterprise Agent to belong to a new Account Group. Prior to these instructions, the article explains where to find the Account Group token for an Agent, and how to remove an Agent from the ThousandEyes app, which is important for purposes of counting towards the number of licenses purchased. These steps are optional but may be needed depending on the reason for resetting the Agent.

**Important:**  Resetting an Enterprise Agent removes all configuration belonging to the existing Account Group, and creates a new instance of the Agent in the ThousandEyes app. The new Agent will not automatically assign itself to any existing tests or alerts. Test and alert assignment must be done manually after the reset. Some configuration that is local to the Agent and not specific to Account Groups is retained.

## Account Group token

If resetting an Enterprise Agent to change the Account Group, the Agent will need to be configured with the new Account Group's installation token. The token can be found on the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page. Select the **+Add New Agent** form. Under the **Appliance** view, click the **Show Account Group Token for Installation** link to display the token.

IMAGE MISSING

Copy the Account Group token for later use:

IMAGE MISSING

The Linux Package and Docker settings will also display the token, in the text of their installation instructions.

Access to the Account Group token requires a user account with a role that has the View agents in account group and Edit agents in account group permissions.

## Removing old Agent entries

Resetting an Enterprise Agent will assign the Agent a new, unique ID number in the ThousandEyes application, and will create a new entry in the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page, in the Agent's Account Group.

To avoid using an additional Enterprise Agent license, as well as avoiding confusion and accumulating out-of-date information, the entry for the Agent should be removed from the Enterprise Agents Settings page before resetting an Enterprise Agent, unless a specific reason to keep the entry exists. Resetting an Agent without deleting the old Agent's entry in the ThousandEyes app could result in an extra license used in the billing cycle, as the ThousandEyes app does not know that the Agent has been reset; only that the old Agent hasn't reported to ThousandEyes and a new Agent has been created.

On the Enterprise Agents Settings page, expand the entry for the Agent and click the Delete dropdown option.

IMAGE MISSING

If the old entry is not removed before the Agent is reset, and the Agent is not being reassigned to a new Account Group, then the new Agent will be created with a name which has the new Agent's unique numerical ID appended to the name, in order to have a unique name. For example, resetting the Agent called "superteva" without first deleting the entry in the Settings page will result in the new Agent having a name "superteva-XXXXX" where XXXXX is the new Agent ID.

If the entry is not deleted prior to reset, and the new Agent name appears with the appended ID, the old Agent entry can be deleted, and then the new Agent name edited to return to the old name, if desired. Simply edit the **Agent Name** field and click the **Save Changes** button. Note however that using the existing name will not preserve test or alert configuration that the reset deletes.

## Resetting an Appliance

Resetting a Virtual or Physical Appliance is done using the web console of the Appliance. Access to the Appliance's web console is done using the IP address of the Appliance. The IP address can be found by accessing the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page, or by opening a console connection to the Appliance. In the console, the IP address and login credentials will be shown as per the example below:

IMAGE MISSING

1. Browse to http://&lt;Appliance\_IP\_address&gt; then log in to the web console
2. Open the **Advanced Settings** tab IMAGE MISSING
3. Click the **Reset Agent State** button
4. Confirm the reset operation

The user will be logged out of the Appliance. Log back in using the same credentials. The Agent will display the Setup wizard:

IMAGE MISSING

The Agent may now be set up using the instructions for configuring a new Appliance. If configuring the Agent for a new Account Group, provide the new Account Group's installation token during step 4, and make any other changes on the Appliance if needed. Once the Setup wizard has completed, navigate to the Status tab to ensure that the Agent is running, and return to the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page for the appropriate Account Group to confirm that the Agent is present.

### Troubleshooting

If the Appliance does not appear on the Enterprise Agents Settings page after reset, check the following:

* Run diagnostics from the web console's Diagnostic tab 
* Log into app.thousandeyes.com with a username which can access the Agent's current Account Group, view the installation token \(see instructions above\) and compare to the installation token on the web console's Agent tab
* Check the **Show agents not assigned to this account group** box on the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page and search for the Agent in the listing
* Check the Agent Log under the web console's Diagnostic tab \(or log into the Agent's command line using SSH and view /var/log/te-agent.log\) for indications of an Agent ID change. An Agent will normally show a log line at startup like:  
  

  ```text
  2018-05-01 20:42:26.300 INFO  [537197c0] [te.agent.main] {} Found id 56567
  ```

  If the Agent has been reset and has obtained a new ID, the log will show a line at startup like:

  ```text
  2018-05-16 22:20:45.231 INFO  [d349e7c0] [te.agent.main] {} No agent id found, attempting to obtain one from sc1.thousandeyes.com
  ```

## Resetting a Linux package Agent

To reset an Enterprise Agent that has been installed on a [supported Linux operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) with the Linux package, log into the command line of the Linux system running the Agent, using an account which has sudo privileges. Issue the following commands:

1. Stop the Agent process by running:

   ```text
   sudo systemctl stop te-agent
   ```

2. Delete the .sqlite files located in the /var/lib/te-agent/ directory:

   ```text
   sudo rm /var/lib/te-agent/*.sqlite
   ```

3. Optionally, if you wish to change the Account Group of the Agent, edit the configuration file /etc/te-agent.cfg and change the value of the **account-token** setting to use the new Account Group token.
4. Restart the Agent process:

   ```text
   sudo systemctl start te-agent
   ```

### Troubleshooting

If the Linux package-based Agent does not appear on the Enterprise Agents Settings page after reset, check the following:

* Log into app.thousandeyes.com with a username which can access the Agent's current Account Group, view the installation token \(see instructions above\) and compare to the installation token in the  /etc/te-agent.cfg file
* Check the **Show agents not assigned to this account group** box on the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page and search for the Agent in the listing
* Check the Agent logs /var/log/te-agent.log for indications of an Agent ID change. An Agent will normally show a log line at startup like:  
  

  ```text
  2018-05-01 20:42:26.300 INFO  [537197c0] [te.agent.main] {} Found id 56567
  ```

  If the Agent has been reset and has obtained a new ID, the log will show a line at startup like:

  ```text
  2018-05-16 22:20:45.231 INFO  [d349e7c0] [te.agent.main] {} No agent id found, attempting to obtain one from sc1.thousandeyes.com
  ```

## Resetting a Docker container Agent

To reset an Enterprise Agent that has been installed via a Docker container, log into the command line of the system running Docker \(Docker host\), using an account which has sudo privileges. Issue the following commands:

1. Stop the container:

   ```text
   sudo docker stop <container_name>
   ```

2. Delete the persistent storage directory which was created with the -v option of the docker run command:

   ```text
   sudo rm -rf <persistent_volume_directory>/thousandeyes/<container_name>
   ```

    **Note:** If you wish to retain any files in the directories for the Docker Agent, such as Agent or BrowserBot logs, copy them to another location before running the rm command.

3. Optionally, if you wish to change the Account Group of the Agent, re-run the docker run command which was used to create the container, and use the new Account Group token when specifying the following option:

   ```text
   -e TEAGENT_ACCOUNT_TOKEN=<new_Account_Group_token>
   ```

4. If not performing step 3, then restart the container:

   ```text
   sudo docker start <container_name>
   ```

### Troubleshooting

If the Docker container-based Agent does not appear on the Enterprise Agents Settings page after reset, check the following:

* Log into app.thousandeyes.com with a username which can access the Agent's current Account Group, view the installation token \(see instructions above\) and compare to the installation token used in the TEAGENT\_ACCOUNT\_TOKEN option
* Check the **Show agents not assigned to this account group** box on the [Enterprise Agents Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page and search for the Agent in the listing
* Check the Agent logs in &lt;persistent\_volumen\_directory&gt;/thousandeyes/&lt;container\_name&gt;/log on the Docker host for indications of an Agent ID change. An Agent will normally show a log line at startup like:  
  

  ```text
  2018-05-01 20:42:26.300 INFO  [537197c0] [te.agent.main] {} Found id 56567
  ```

  If the Agent has been reset and has obtained a new ID, the log will show a line at startup like:

  ```text
  2018-05-16 22:20:45.231 INFO  [d349e7c0] [te.agent.main] {} No agent id found, attempting to obtain one from sc1.thousandeyes.com
  ```

