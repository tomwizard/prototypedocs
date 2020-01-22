# Uninstalling the Endpoint Agent for Windows

The ThousandEyes Endpoint Agent is a browser extension application installed on a user's computer to collect web performance data for websites within configured domains and networks. The Endpoint Agent  installation for Windows is illustrated in [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBuCAK_Installing-the-Endpoint-Agent-for-Windows).

This document outlines the procedure to uninstall  the ThousandEyes Endpoint Agent from a Windows machine.

## Uninstalling ThousandEyes Endpoint Agent

1. Close any open Internet Explorer or Google Chrome browser windows.
2. Open Add/Remove Programs on the machine you wish to uninstall the ThousandEyes Endpoint Agent.
3. Find the ThousandEyes Agent entry on the list.
4. Click Uninstall.
5. Acknowledge that you are uninstalling the Endpoint Agent.
6. If you have Google Chrome installed, and the extension is enabled there, you will be prompted to confirm removal of the extension from Google Chrome. Acknowledge this prompt.
7. A reboot may be required.
8. Delete the Endpoint Agent from Settings &gt; Agents &gt; Endpoint Agent &gt; expand Agent tab.
9. Once the application has been removed, the following folders may be left on the file system.  To completely remove all filesystem remnants, remove the following folders \(and all contents\):

* c:\Documents and Settings\All Users\ThousandEyes\
* c:\Documents and Settings\USERNAME\AppData\Local\Application Data\ThousandEyes\
* c:\Documents and Settings\USERNAME\AppData\Local\ThousandEyes\
* c:\Documents and Settings\USERNAME\AppData\LocalLow\ThousandEyes\
* c:\ProgramData\Application Data\ThousandEyes\
* c:\ProgramData\ThousandEyes\
* c:\Users\All Users\ThousandEyes\
* c:\Users\USERNAME\AppData\Local\Application Data\ThousandEyes\
* c:\Users\USERNAME\AppData\Local\ThousandEyes\
* c:\Users\USERNAME\AppData\LocalLow\ThousandEyes\
* c:\Users\USERNAME\Local Settings\ThousandEyes\

