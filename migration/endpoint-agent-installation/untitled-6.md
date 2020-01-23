# Uninstalling the Endpoint Agent for Mac OS X

The ThousandEyes Endpoint Agent is a browser extension application installed on a user's computer to collect web performance data for websites within configured domains and networks. The Endpoint Agent  installation for Mac OS X is illustrated in [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBvCAK_Installing-the-Endpoint-Agent-for-Mac-OS-X).

This document outlines the procedure to uninstall  the ThousandEyes Endpoint Agent from a Windows machine.

## Uninstalling ThousandEyes Endpoint Agent

1. Open the Applications folder of your computer, and drag the ThousandEyes Endpoint Agent to the trash or right-click and select the "Move to Trash" option.
2. Remove the extension from Google Chrome by locating the Endpoint Agent button in the browser toolbar, right-clicking and selecting the Remove from Chrome... option.
3. Delete the Endpoint Agent from Settings &gt; Agents &gt; Endpoint Agent &gt; expand Agent tab
4. Once the Endpoint agent has been removed, no more data will be collected.  To remove all traces of the Endpoint Agent from your system, open Finder and press SHIFT+COMMAND+C to open the computer view, then remove the following file

* /Library/Application Support/ThousandEyes
* /Users/&lt;username&gt;/Library/Application Support/ThousandEyes

