# Installing the Endpoint Agent for Mac OS X

The ThousandEyes Endpoint Agent is a browser extension application installed on a user's computer to collect web performance data for websites within configured domains and networks.This document outlines downloading the Endpoint Agent installer file, and installing and enabling the Endpoint Agent for a Mac OS X user.

Endpoint Agent requires Mac OS X 10.9 \(Mavericks\) or later, and Google Chrome installed on your computer. Complete operating system and browser support for Endpoint Agent is documented [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBp).

## Distribution of Installers

Endpoint Agent is custom-built for each account. Access to the Endpoint Agent installer from our site requires a ThousandEyes username and password. Customers will need to download the installer file, and distribute internally to users without a ThousandEyes account that has access to the installer file.

## Downloading the Endpoint Agent installer

1. Navigate to [Endpoint Agents &gt; Agent Settings](https://app.thousandeyes.com/endpoint/agent-settings/?section=agents)
2. Click **Add New Endpoint Agent**
3. Click the **Download - Mac PKG** link to start downloading the PKG installer file. Clicking the **Allow anyone with the link to download** switch reveals public links to each installer file. Depending on your security settings, you may see a warning that the file can harm your computer, per the image below.  IMAGE MISSING
4.  Click the **Keep** button to continue the download. IMAGE MISSING
5. Once downloaded, double click the file in the receiving folder to start the installation.

## Installing the Endpoint Agent  

1. Launch the installer.  You'll be prompted by the wizard through the installation steps.  Click the **Continue** button. IMAGE MISSING
2. Read the End-user License Agreement and Terms of Use.  Click the **Continue** button. IMAGE MISSING
3. Accept the End-user License Agreement and Terms of Use.  Click the **Agree** button to continue.  IMAGE MISSING
4. Accept the default location for the software installation by choosing the _Install for all users of this computer_ option. Click the **Continue** button IMAGE MISSING
5. Next, you'll be shown how much disk space the ThousandEyes Endpoint Agent will consume.  Click the **Install** button. IMAGE MISSING
6. Your system will prompt for the username and password of an account with rights to install software.  Enter your username and password, then click the **Install Software** button. IMAGE MISSING
7. After installation completes \(it should take less than a minute to install\), you'll see an installation summary.  Click the **Close** button to Launch Google Chrome to complete the installation. IMAGE MISSING
8. Google Chrome will launch and prompt you to add the extension for Chrome.  Click the **Add to Chrome** button to add the extension.
   1. Clicking on **Add to Chrome,** makes a request to Google Web Store. If access to Google Web Store is blocked, please allow the following URL to be available -  [https://chrome.google.com/webstore/detail/thousandeyes-endpoint-age/ddnennmeinlkhkmajmmfaojcnpddnpgb](https://chrome.google.com/webstore/detail/thousandeyes-endpoint-age/ddnennmeinlkhkmajmmfaojcnpddnpgb) IMAGE MISSING
9. After you click the Add to Chrome button, Chrome will prompt you to accept the changes required by the Endpoint Agent.  Click the **Add extension** button to continue. IMAGE MISSING
10. Once added, the extension will show a notification next to the newly-added toolbar button in Chrome.  IMAGE MISSING

## Collecting data using the Endpoint Agent

The Endpoint Agent installer is custom-built for each ThousandEyes account, and contains a built-in account key.  This account key is used to route the collected performance data into the right ThousandEyes account.

Two modes of data collection exist:

1. **Automatic data collection:** With the Endpoint Agent installed, if a user browses to a webpage whose domain is configured in a "Monitoring Profile"  and the public IP address of the client machine is detected to be inside a "Monitored Network" for that domain, the Endpoint Agent will gather web and network layer data associated with the user's browsing session.
2. **Manual data collection:** A user can initiate data collection by clicking the ThousandEyes Endpoint Agent extension button from the browser toolbar. While the Endpoint Agent is recording your browsing session, the top of the page will show a banner indicating that ThousandEyes Endpoint Agent is debugging this tab. To stop recording, simply click the same ThousandEyes extension button in the browser toolbar, or click the Cancel button on the banner.

## Uninstalling ThousandEyes Endpoint Agent

 The procedure to uninstall  the ThousandEyes Endpoint Agent on Mac OS X is illustrated in [this article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpeHCAS_Uninstalling-the-Endpoint-Agent-for-Mac-OS-X).

## Refer following documents for more Endpoint Agent information

1. [Configuring Endpoint Agent](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBx)
2. [How does Endpoint Agent work?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmpU)
3. [What information does Endpoint Agent collect?](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmpb)

