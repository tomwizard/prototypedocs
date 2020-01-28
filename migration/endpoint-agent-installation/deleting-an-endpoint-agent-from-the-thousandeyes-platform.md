# Deleting an Endpoint Agent from the ThousandEyes platform

When an Endpoint Agent is installed on a computer with a supported Windows or Mac OS X operating system, the Agent registers with the ThousandEyes platform and then can be seen in the listing on the Endpoint Agents page, under the Account Group from which the Endpoint Agent Installer was downloaded. If an administrator removes an Endpoint Agent from its host computer, normally the administrator also would delete the Endpoint Agent from the ThousandEyes platform.

However, under some circumstances an administrator may only need to delete an Agent from the ThousandEyes platform. This article provides reasons for only deleting an Endpoint Agent from the ThousandEyes platform, information on the effect of deleting an Endpoint Agent from the ThousandEyes platform, and the steps to perform deletion.

Once an Endpoint Agent has been deleted from the platform, the Agent cannot be undeleted. Note, however, that data which has been uploaded to ThousandEyes platform by an Endpoint Agent will remain in the platform, regardless of whether the Agent which generated the data is deleted from the platform or from the computer on which the Agent was installed, or both.

## Reasons for deleting an Endpoint Agent from the platform

After installation, each Endpoint Agent receives a unique ID when it first contacts the ThousandEyes platform. Repeated installations of Endpoint Agent on the same host computer will generate a new ID per installation. Deleting an Endpoint Agent from the ThousandEyes platform will prevent the Endpoint Agent with that ID from uploading data to the platform. Additionally, when an Agent is deleted from the platform, the Agent will no longer count towards the number of Endpoint Agent licenses purchased by the organization, even when the Endpoint Agent software is running on the host computer.

Administrators may delete an Endpoint Agent from the platform if the administrator does not wish to receive the Agent’s data, such as when an Agent is installed from an Endpoint Agent Installer downloaded from the wrong ThousandEyes Account Group \(deleting the Endpoint Agent from the host computer would also prevent data from being sent, but ThousandEyes administrators may not have control over the host computer\). Note that disabling an Agent using the **Disable** button will also prevent data from being uploaded into the ThousandEyes platform and will also prevent the Agent from being counted towards the organization's Endpoint Agent license limit. So if the need to block an Agent is temporary, then disable the Agent rather than delete it.

Another common scenario for deleting an Agent in the platform occurs when an Agent and possibly the host computer may no longer exist, such as in the case of an Agent installed on a virtual machine which is then re-imaged or otherwise reverted to a state prior to installing Endpoint Agent.

In scenarios where multiple installations are performed on a computer with the same hostname, multiple entries in the Endpoint Agent page are created with the same Agent name, as in the image below:

IMAGE MISSING

If an administrator wishes to retain the current Agent while deleting prior instances, use the Last Contact time from the table in Endpoint Agents page to select the Agent with the most recent contact, ideally making certain that the Endpoint Agent and its host computer are currently running. If two Agents have a Last Contact time closer than 30 minutes, ThousandEyes recommends waiting for another update to the Last Contact time to ensure that the active Agent can be correctly identified.

## Deleting an Endpoint Agent from the platform

To delete an Endpoint Agent from the platform, navigate to the [Endpoint Agents page](https://app.thousandeyes.com/settings/agents/endpoint/?section=agents) \(**Settings &gt; Agents &gt; Endpoint Agents**\), expand the row of the Endpoint Agent to be deleted and click the Trash icon.

IMAGE MISSING

A confirmation dialog will appear:

IMAGE MISSING

Click the **Delete** button to confirm deletion.

