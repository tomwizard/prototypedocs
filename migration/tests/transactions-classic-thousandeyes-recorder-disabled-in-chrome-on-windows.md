# Transactions \(Classic\) - ThousandEyes Recorder disabled in Chrome on Windows

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

This article describes a current limitation for Windows users with the [ThousandEyes Recorder browser plugin](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn8KAC) when the plugin was not installed from the Chrome Store.  The last version of the Recorder which was not available from the Chrome store is version 0.60.  If your version of the Recorder is greater than 0.60, then you should not be affected by this issue.

## ThousandEyes Recorder installation

The ThousandEyes Recorder is installed into a user's Chrome browser on Windows or MacOS.  The installation was previously performed by downloading the CRX file from the ThousandEyes web site, rather than downloading from the Chrome Store.  After installation, the text "Not from Chrome Web Store" will appear in the Recorder's entry on the Extensions page \(go to **Settings &gt;  Tools &gt;  Extensions**, or enter the URL chrome://extensions into your browser\).

## Google policy on disabling extensions

Recently, Google announced that they will disable Chrome extensions which were not downloaded from the Chrome Store, for Windows platforms only.  The official announcement can be found here:

[Protecting Windows users from malicious extensions](http://blog.chromium.org/2013/11/protecting-windows-users-from-malicious.html)

This action was taken by Google due to security and privacy concerns caused by installation of undesired extensions and plugins from non-Chrome Store sources. If your Recorder becomes disabled and you cannot re-enable it, this may be due to Google's policy.  However, it is also possible that your organization has implemented their own security measures which disable some or all Chrome extensions.

**NOTE:** Extension disabling is not universally implemented at this time. Windows users may be able to user the Recorder for an indefinite time, depending on a variety of factors.

## Solution and Workarounds

As of June 25th, 2014, the ThousandEyes Recorder is available from the [Chrome Store](https://chrome.google.com/webstore/detail/thousandeyes-recorder/hnmekclmbdhoicblhbcloiemofnengnn).  Please install the latest version of the Recorder from the Chrome Store.

If you are unable to install from the Chrome Store, and your ThousandEyes Recorder becomes disabled on your Windows platform, you should be able to re-enable it by checking the **Developer Mode** box on the Extensions page \(**Settings &gt;  Tools &gt;  Extensions**, or browse to chrome://extensions\).

Additionally, Selenium commands can be entered into a ThousandEyes Transaction Test directly, or can be imported from a script file that has been created manually or by a third-party Selenium scripting tool.

**NOTE:** Please be aware when creating Selenium scripts that ThousandEyes supports Selenium RC syntax.  We do not currently support Webdriver syntax. Refer to the Knowledge Base article [Transactions - Supported Selenium Commands](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBwCAK_Transactions-supported-Selenium-commands) for more information.

Contact the ThousandEyes Customer Success Center to discuss your options, if needed.

Currently, the ThousandEyes Recorder installs from the Chrome Store and from local CRX file and functions normally, when running on MacOS.  At some future date, Google may require Chrome Store installation for MacOS versions.

