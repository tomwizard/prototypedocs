# Transactions - Executing custom JavaScript code

The flow of a ThousandEyes transaction test is defined with JavaScript code. Similarly, frontends of modern web applications are also implemented using JavaScript code. The evident similarity intuitively can lead to an incorrect conclusion that execution contexts of transaction test control code and of tested web application are somehow interlinked, which is not exactly the case.

This article briefly discusses differences between two main JavaScript code execution contexts and provides instructions on how to implement a transaction that executes custom JavaScript code in the context of the tested web application.

## BrowserBot vs. Chromium web browser

ThousandEyes Cloud and Enterprise Agents utilize [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-BrowserBot) component for running transaction \(and page load\) tests. To be precise, the BrowserBot component actually consists of two parts:

* The **BrowserBot** itself is the control center of the transaction test execution - when the agent requires a transaction test to be executed, the task is dispatched to BrowserBot. The BrowserBot, upon receiving a new transaction test execution task, runs the received task and controls the browser as specified by the transaction test code. You could think of BrowserBot as a human, sitting behind a computer on which a web browser is running, using that browser to navigate web applications as instructed by a transaction script.
* **Chromium web browser** is the web browser that the BrowserBot is "driving around" by performing transaction steps such as mouse clicks, keyboard inputs, waiting conditions, etc.

To summarize, BrowserBot and Chromium web browser \(and a few other bits\) are separate pieces of software that constitute the entire BrowserBot component. These pieces of software talk to each other through a set of well-defined interfaces and should not, at least for the purpose of this discussion, be thought of as one monolithic application.

## Transaction control execution context

ThousandEyes transaction test is defined using JavaScript code. Here is an example of a very simple transaction test implementation:

```text
import { driver } from 'thousandeyes';

runScript();

async function runScript() {

    // Load page
    await driver.get('https://google.com');

    // Take a screenshot
    await driver.takeScreenshot();
}
```

This transaction does the following:

1. First, it opens the [https://google.com](https://google.com/) website;
2. Then it takes a screenshot.

This code runs in what we call a **transaction control execution context** - an isolated, [Node.js](https://nodejs.org/)-powered environment. To simplify, one can imagine that transaction code runs inside the BrowserBot and tells the BrowserBot how to interact with the Chromium web browser. The available methods of interaction with the web browser are described in detail in the [Transaction Scripting Reference](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000UIORSA4_Transaction-Scripting-Reference).

Results from a transaction test using the code above can be observed here: [https://jrxnpmt.share.thousandeyes.com](https://jrxnpmt.share.thousandeyes.com/)

## Web application \(browser\) execution context

This execution context takes place in a web browser. One of the simpler ways to explain this execution context is by showing an equivalent way of executing custom JavaScript code inside the web application context - by using the **Console** tab of the [Chrome/Chromium browser developer tools](https://developers.google.com/web/tools/chrome-devtools/).

Using your web browser, navigate to the target web application \(in our case [https://google.com](https://google.com/)\) and open the browser developer tools. Switch to the **Console** tab and enter the custom code to be executed in the application context.

Here is an example of using custom code to trigger an alert dialog:

IMAGE MISSING

## Executing custom JavaScript in target web application

Let's suppose that we want to add a big text to the application that we are testing. Here is a sample JavaScript code that enables us to achieve that:

```text
var h = document.createElement("h1");
var t = document.createTextNode("ADDING THIS TEXT ELEMENT TO THE PAGE, JUST FOR FUN");
h.appendChild(t);
document.body.appendChild(h);
```

While you can quickly test the above code in your browser developer tools, this code cannot simply be added to the transaction test control code, as transaction control execution context has no `document` reference available.

Instead, the `executeScript()` method of the `driver` object of the `thousandeyes` module enables passing custom JavaScript code into the web application \(browser\) context and executing it there:

```text
import { driver } from 'thousandeyes';

runScript(); 

async function runScript() {

    // Load page
    await driver.get('https://google.com');

    // Inject custom code
    await driver.executeScript(
        'var h = document.createElement("h1"); ' +
        'var t = document.createTextNode("ADD THIS <h1> TEXT ELEMENT TO THE PAGE, JUST FOR FUN"); ' +
        'h.appendChild(t); ' +
        'document.body.appendChild(h);'
    );

    // Take a screenshot
    await driver.takeScreenshot();
}
```

It is important to note that the custom code to be executed in the web browser context is passed to the `executeScript()` method **as a string** \(regular text\).

The added code above results in the following transaction screenshot:

IMAGE MISSING

Test results of the example above can be observed here: [https://yxlwlwf.share.thousandeyes.com](https://yxlwlwf.share.thousandeyes.com/)

## Related information

This article is part of the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide).

If you have any questions, [reach out to ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

