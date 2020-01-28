# Transactions \(Classic\) - Using the ThousandEyes Recorder

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

This article describes how to install and use the ThousandEyes Recorder browser plugin to assist in creating Transaction test scripts.

## What is the ThousandEyes Recorder?

ThousandEyes leverages Selenium to play scripted transactions from private and Cloud Agents. The ThousandEyes Recorder allows you to record your interactions with a web page in the form of a Selenium script, which can be further developed. The script is particularly useful for testing target sites that implement forms-based authentication. A basic transaction would be to connect to a target site, enter the username and password, and then click the login button, then wait for the page to load.

## Which browsers are supported?

Currently, the ThousandEyes Recorder is supported by Chrome for Windows, Mac OS X, and Linux.

## How do I install the ThousandEyes Recorder?

You can install the ThousandEyes Recorder from the [Chrome Store](https://chrome.google.com/webstore/detail/thousandeyes-recorder/hnmekclmbdhoicblhbcloiemofnengnn). Additionally, a manual installation is possible if installation from the Chrome Store cannot be performed. Please contact the [ThousandEyes Customer Success](mailto:support@thousandeyes.com) team for information on manual installation.

When you install the Recorder from the Chrome Store, you'll see a confirmation request on adding the new extension:

IMAGE MISSING

Click the **Add** button. Another confirmation will indicate the Recorder has been added:

IMAGE MISSING

The ThousandEyes End-User License Agreement will appear in a separate browser window. Read to the bottom of the page. If you agree to the terms, click the **I Agree** button. The installation will complete.

## Updating the Recorder

The ThousandEyes Recorder uses the [extension auto-updating feature](https://developer.chrome.com/extensions/autoupdate) of Chrome. When a new version of the ThousandEyes Recorder is released to the Chrome Store, your extension will be automatically updated. No user interaction is required \(beyond having Chrome running\) in order for the update to occur.

## Running the ThousandEyes Recorder

After installation, your new extension will display a button to the right of the address bar. Click the button to begin recording a transaction, and then interact with the target page. When the Recorder is recording, the icon will change from the at rest icon, to an icon showing that recording is in progress. During playback, the icon changes to a green play icon - see the three screenshots below:

IMAGE MISSING

## How does the Recorder work?

The ThousandEyes Recorder records your clicks and keyboard inputs into a replay-able Selenium script.

1. When you click the **Record** button, the Base URL field in the Recorder will auto-populate with the URL of the current page.
2. Each mouse click will be captured according to the target of the click.
3. Each keyboard interaction will be captured--both the target input field, as well as the typed content.

## What does the output look like?

In general, the output is pretty simple. It's a selenium script, which identifies ordered steps, and actions taken by each step. You can export the script as HTML, which exports the content into a table-formatted HTML page, or exports it directly into ThousandEyes, which will create a new Web Transaction test based on the content found in the Recorder. The screenshots below show a script captured in the Recorder, as well as both HTML and direct-to-ThousandEyes output. Note that form inputs \(keyboard\) are masked in the ThousandEyes test management interface to prevent inadvertent disclosure of username and password values.

ThousandEyes Recorder interface:

IMAGE MISSING

ThousandEyes Recorder "Export to File" output:

```text
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
   <head profile="http://selenium-ide.openqa.org/profiles/test-case">
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
      <link rel="selenium.base" href="https://app.thousandeyes.com/" />
      <title></title>
   </head>
   <body>
      <table>
         <tbody>
            <tr>
               <td>open</td>
               <td>&#x2F;login</td>
               <td></td>
            </tr>
            <tr>
               <td>type</td>
               <td>id=email</td>
               <td>user@company.com</td>
            </tr>
            <tr>
               <td>type</td>
               <td>id=password</td>
               <td>mypassword</td>
            </tr>
            <tr>
               <td>click</td>
               <td>id=submit-button</td>
               <td></td>
            </tr>
            <tr>
               <td>waitForPageToLoad</td>
               <td></td>
               <td>30000</td>
            </tr>
         </tbody>
      </table>
   </body>
</html>
```

ThousandEyes Recorder "Export to TE" output:

IMAGE MISSING

## Supported Commands

The ThousandEyes Recorder is effectively a Selenium script generator, so most commands available through Selenium are available here as well. If you type a letter into the command pane input, a list of available commands will auto-populate based on the letter typed, similar to the following image. A command with invalid syntax will show in red until it is correctly completed. Check [this article link](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBwCAK_Transactions-supported-Selenium-commands) for a list of all supported commands.

IMAGE MISSING

## Tips and tricks

Keep in mind that the ThousandEyes Recorder is intended to be a framework generator for your transactions. It will work well with most target sites, but keep in mind that a proofread and testing of your transaction should be done before inserting into the system, to prevent transaction failures. Following these guidelines will help you develop your transactions in as seamless an approach as possible:

* Never use the Enter/Return key to operate a button. Always click the button using the mouse, otherwise the Recorder may not capture the event.
* Do not use form filler extensions to fill in the fields of a form. Turn off form filler extensions and similar automation tools when recording the steps of a Transaction test. Otherwise, the Recorder may not capture the event.
* Always test on a browser with cookies cleared; ThousandEyes executes every transaction with all cookies and cache cleared, in order to give as accurate a picture as possible when providing transaction times.
* Use XPath syntax to specify targets if possible. The Recorder will typically record target elements using CSS syntax. However, playback by Agents can sometimes fail unless the target element is specified with XPath syntax.
* To validate the final output, add a waitForElementPresent step at the end of the transaction, targeting the element on the page you wish to load. This will ensure that the target content is loaded. Without adding a condition at the end of the transaction, transactions may indicate successful completion, when the actual result was not the desired one.

## Troubleshooting

Recording scripted transactions against web servers can be a tricky business, because it's difficult to identify specific elements in the page sometimes \(due to the use of iframes\), so you'll likely have to tweak the settings of a recording on a reasonably frequent basis. It's best to think of the recorder as something that develops a framework for you to work within, and then flesh out that framework. You can use the Recorder as an actual editor, and add and remove lines within the script as appropriate, using the **Command**, **Target** and **Value** fields in the Recorder.

As always, feel free to [contact the Customer Success](mailto:support@thousandeyes.com?subject=Selenium%20Assistance) team at ThousandEyes. We're happy to help.

## License

ThousandEyes Recorder is an extension for Google Chrome that records user actions and produces a resulting Selenium script.

Copyright © 2012 – 2018 ThousandEyes, Inc.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or \(at your option\) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see [http://www.gnu.org/licenses/](http://www.gnu.org/licenses/).

If you have questions or comments, please send them to [opensource@thousandeyes.com](mailto:opensource@thousandeyes.com).

