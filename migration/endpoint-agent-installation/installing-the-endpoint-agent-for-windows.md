# Installing the Endpoint Agent for Windows

The ThousandEyes Endpoint Agent is a browser extension application installed on a user's computer to collect web performance data for websites within configured domains and networks. This document outlines downloading the Endpoint Agent installer file, and installing and enabling the Endpoint Agent for a Windows user.

ThousandEyes Endpoint Agent requires Windows 7 or later, and Google Chrome or Internet Explorer 11+ installed on your machine. Complete operating system and browser support for Endpoint Agent is documented [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBp).

## Distribution of Installers

Endpoint Agent is custom-built for each account. Access to the Endpoint Agent installer from our site requires a ThousandEyes username and password. Customers will need to download the installer file, and distribute it internally to users without a ThousandEyes account. The MSI installer comes in two versions:

* x86 version for 32-bit processors \(but can be used with 64-bit processors\)
* x64 version for 64-bit processors

## Downloading the Endpoint Agent Installer

1. Navigate to [Endpoint Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents)
2. Click **Add New Endpoint Agent** IMAGE MISSING
3. Download the appropriate Installer file based on your operating system architecture. Click **Download - x86 Windows MSI** or **Download - x64 Windows MSI** to start downloading the MSI installer file. Depending on your security settings, you may see a warning that the file can harm your computer, per the image below. Clicking the **Allow anyone with the link to download** switch reveals public links to each installer file. Select the **Keep** option to continue the download. IMAGE MISSING
4. Once downloaded, double click the file in the receiving folder and select Run to start the installation. IMAGE MISSING

## Installing the Endpoint Agent  

1. Launch the installer.  You'll be guided by the wizard through the installation steps.  Click the **Next** button. IMAGE MISSING
2. Read the End-User License Agreement.  Click the checkbox to accept the terms and then click the **Next** button. IMAGE MISSING
3. Choose an installation folder.  Click the **Next** button. IMAGE MISSING
4. Install the Endpoint Agent. Click the **Install** button. IMAGE MISSING
5. You may receive a warning about the installation.  Check that the verified publisher is "ThousandEyes, Inc."  If so, click the **Yes** button or similar button to continue. IMAGE MISSING
6. Installation will complete. If you have Google Chrome installed, it will open and prompt to enable the extension in Chrome.  Click the **Add to Chrome** button to continue. \(If you do not have Google Chrome installed, proceed to step 9.\)   
   * Clicking on **Add to Chrome,** makes a request to Google Web Store. If access to Google Web Store is blocked, please allow the following URL to be available -- https://chrome.google.com/webstore/detail/thousandeyes-endpoint-age/ddnennmeinlkhkmajmmfaojcnpddnpgb IMAGE MISSING

  7. Acknowledge the security dialog and click the **Add extension** button to continue.  
IMAGE MISSING

  8. Once complete, a balloon will appear in the upper right corner of the page, indicating that the Endpoint Agent has been installed. Restart Chrome once this completes.  
IMAGE MISSING

9. Next, open Internet Explorer \(if installed\).  On first launch, it will prompt to enable the add-on. Click the Enable button in the banner at the bottom of the page to enable the add-on. If there is no such prompt, go to **Settings &gt; Manage Add-Ons** &gt; **right click on Start/Stop Recording with Endpoint Agent &gt; select Enable.**  
IMAGE MISSING

10. Restart Internet Explorer once the add-on is enabled, in order to add it to the appropriate context menus and toolbars.

11. Click the **Finish** button to complete the installation.  
IMAGE MISSING

## Collecting data using the Endpoint Agent

The Endpoint Agent installer is custom-built for each ThousandEyes account, and contains a built-in account key.  This account key is used to route the collected performance data into the right ThousandEyes account.

Two modes of data collection exist:

1. **Automatic data collection:** With the Endpoint Agent installed, if a user browses to a webpage whose domain is configured in a "Monitoring Profile" and the public IP address of the client machine is detected to be inside a "Monitored Network" for that domain, the Endpoint Agent will automatically gather web and network layer data associated with the user's browsing session.
2. **Manual data collection:** A user can initiate data collection by clicking the ThousandEyes Endpoint Agent extension button from the browser toolbar. While the Endpoint Agent is recording your browsing session, the top of the page will show a banner indicating that ThousandEyes Endpoint Agent is debugging this tab. To stop recording, simply click the same ThousandEyes extension button in the browser toolbar, or click the Cancel button on the banner.   

## Uninstalling Endpoint Agent

 The procedure to uninstall  the ThousandEyes Endpoint Agent from a Windows machine is illustrated in [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpeCCAS_Uninstalling-the-Endpoint-Agent-for-Windows).

## More Resources on Endpoint Agent

1. [Configuration Endpoint Agent setup](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBx)
2. [How does Endpoint Agent gather data?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpU)
3. [What information does Endpoint Agent collect?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmpb)

