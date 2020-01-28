# Troubleshooting Endpoint Agent issues

In the event that the ThousandEyes Endpoint Agent does not install or function correctly, review the following information:

## Endpoint Agent installed on Windows

### ThousandEyes Endpoint Agent button is missing from Chrome

1. First, verify that the ThousandEyes Endpoint Agent is installed on your system. Go to **Add/Remove Programs** and scroll down to the entry for `ThousandEyes Endpoint Agent`. If the package is not installed, contact your system administrator, or follow the instructions for [installing the Endpoint Agent on Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBuCAK_Installing-the-Endpoint-Agent-for-Windows).
2. If the package is installed, open the Chrome extensions page by going to **Tools &gt; Extensions**. Find the `ThousandEyes Endpoint Agent` in the list, and ensure that it is enabled.
3. If the package is installed but the extension is missing, browse to [https://app.thousandeyes.com/install/endpoint-agent](https://app.thousandeyes.com/install/endpoint-agent). This will allow you to add the ThousandEyes Endpoint Agent to Google Chrome.

### Start/Stop Recording is missing from Internet Explorer

1. First, check to ensure that you are running a compatible version of Internet Explorer. We currently support Internet Explorer version 11 and higher on Windows 7, Windows 8.x, Windows 10, Windows Server 2008, and Windows Server 2012. For versions of Windows which ship with the Metro UI, we only support the use of the Endpoint Agent in Desktop mode.
2. Next, make sure the Endpoint Agent is installed on your system. Go to **Add/Remove Programs**, and scroll down to the entry for `ThousandEyes Endpoint Agent`. If the package is not installed, contact your system administrator, or follow the instructions for [installing the Endpoint Agent on Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBuCAK_Installing-the-Endpoint-Agent-for-Windows).
3. If the package is installed, try restarting Internet Explorer. If Internet Explorer hasn't been restarted since the package was installed, then the application won't have hooks into IE.
4. After you've restarted Internet Explorer, if the plugin is still missing, go to **Tools &gt; Manage add-ons**:
   1. Under the **Add-on Types** menu, select **Toolbars and Extensions**.
   2. Find the item with the name **Start/Stop Recording** and check the status to ensure that it is enabled.

### Inspect Endpoint Agent logs

1. Agent logs are available under the `C:\ProgramData\ThousandEyes\Endpoint Agent\log` directory.
2. BrowserHelper logs are available under the `C:\Users\$user\AppData\Local\ThousandEyes\Endpoint Agent\log` directory.

### Share data with ThousandEyes Support

1. Navigate to the `C:\Program Files (x86)\ThousandEyes\Endpoint Agent\` directory and run the `te-diagnostics.exe` program. A file named `TE Endpoint Agent - Diagnostics Results.zip` will be created on your desktop. The folder contains all relevant Endpoint Agent logs. Share this file with [support@thousandeyes.com](mailto:support@thousandeyes.com).
2. Additionally, send to [support@thousandeyes.com](mailto:support@thousandeyes.com) a share link of the Endpoint Agent View encompassing the issue. You can create a share link by pressing the **Share** button, as outlined in the following figure: IMAGE MISSING

## Endpoint Agent installed on Mac OS X

### ThousandEyes Endpoint Agent button is missing from Chrome

1. First, verify that the ThousandEyes Endpoint Agent is installed on your system using the Mac OS X's builtin search tool Spotlight. Open Spotlight by pressing Command+Space keys, then type `kind:app ThousandEyes Endpoint Agent`. If `No results` message is displayed the package needs installing. Please contact your system administrator, or follow the instructions for [installing the Endpoint Agent on Mac OS X](http://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBvCAK_Installing-the-Endpoint-Agent-for-Mac-OS-X-1476477152096).
2. If the package is already installed, open the Chrome extensions page by typing the following text into the Chrome address bar `chrome://extensions`. Find the `ThousandEyes Endpoint Agent` in the list, and ensure that it is enabled.
3. If the package is installed but the extension is missing, browse to [https://app.thousandeyes.com/install/endpoint-agent](https://app.thousandeyes.com/install/endpoint-agent). This will allow you to add the ThousandEyes Endpoint Agent to Google Chrome.
4. If after these steps you are still unable to see the Endpoint Agent button or access the Start/Stop recording options, contact our Customer Success team.

### Recording is working, but no data is appearing

1. Ensure that the domain the user is accessing is configured within a monitoring profile from the agent’s current network. Refer to [Settings &gt; Endpoint Agents](https://app.thousandeyes.com/settings/agents/endpoint/) for more information
2. Validate that the user is connecting from a monitored network. Refer to [Settings &gt; Endpoint Agents](https://app.thousandeyes.com/settings/agents/endpoint/) for more information
3. Validate that the user is able to access the Internet by opening a website and browsing to [http://www.thousandeyes.com](http://www.thousandeyes.com/)

### Inspect Endpoint Agent logs

1. To view the Endpoint Agent log files, open Spotlight by pressing the Command+Space keys, then type in `kind:folder /Library/Application Support/ThousandEyes/Endpoint Agent/log/`.
2. To view the BrowserHelper log files, open Spotlight by pressing the Command+Space keys, type in the following text but replace USERNAME with your actual username: `kind:folder /Users/<USERNAME>/Library/Application Support/ThousandEyes/Endpoint Agent/log` then press Return.

### Share data with ThousandEyes Support

1. To run the ThousandEyes Endpoint Agent Diagnostics Tool, open Spotlight by pressing the Command+Space keys, type `kind:app ThousandEyes Endpoint Agent`. In the popup dialogue box click **Run Diagnostics**. You will be prompted with the file name and the location of your diagnostic test results. Please share this file with [support@thousandeyes.com](mailto:support@thousandeyes.com).
2. Additionally, send to [support@thousandeyes.com](mailto:support@thousandeyes.com) a share link of the Endpoint Agent View encompassing the issue. You can create a share link by pressing the **Share** button, as outlined in the following figure: IMAGE MISSING

## Further assistance

If you have an issue not listed here or need further help, please contact ThousandEyes Support via Live Chat or email at [support@thousandeyes.com](mailto:support@thousandeyes.com).

