# Transactions \(Classic\) - Using the waitForCondition steps

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

Welcome to one of the \(arguably\) most important articles about transaction scripting. In this article, we'll explain what `waitForCondition` steps are, why they are necessary, where such steps should be placed and how to create them.

## From a user journey description to a working transaction

This section will guide you through an example user journey you might want to script and run as a transaction test. The purpose of such a transaction test is to make sure the tested application is working as expected and that the contracted service \(in this case we'll use Microsoft's login page as a fictional example\) is indeed functionally available to our users.

### User journey example

Let's consider the following user journey that we'll use throughout the rest of this article:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Step description</th>
      <th style="text-align:left">Screenshot</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Step #1:
        <br />- Open <a href="https://login.microsoftonline.com/">https://login.microsoftonline.com/</a>
      </td>
      <td style="text-align:left">IMAGE MISSING</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Step #2:
          <br />- Enter the username</p>
        <p>Step #3:
          <br />- Click the <b>Next</b> button (3)</p>
      </td>
      <td style="text-align:left">IMAGE MISSING</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Microsoft login interface redirects to organization&apos;s sign-in page.</p>
        <p>In this particular case, since in the previous step a ...@thousandeyes.com
          email was used, the redirect leads to the ThousandEyes-specific sign-in
          page.</p>
      </td>
      <td style="text-align:left">IMAGE MISSING</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>Step #4:
          <br />- Enter the username (again)</p>
        <p>Step #5:
          <br />- Enter the password</p>
        <p>Step #6:
          <br />- Click the <b>Sign In</b> button</p>
      </td>
      <td style="text-align:left">IMAGE MISSING</td>
    </tr>
  </tbody>
</table>Such a user journey could be scripted as follows:

IMAGE MISSING

There is nothing particularly wrong with the transaction script shown above - as far as a human is concerned, the script should work, provided that the steps are configured correctly \(they are\).

### Initial transaction run

Without further ado, let's give the transaction script above a go. Here are the results of the first run:

IMAGE MISSING

The transaction has reached 50% completion. How come only 50% completion? That's... well, it's a start.

The transaction failed at step \#4, which is an act of entering the username at the organization's sign-in page. The reported error \(2\) is stating that the element from transaction step \#4 \(the username input field\) does not exist.

Whenever the transaction test reports an error, a screenshot is provided. To view the screenshot, the agent must be selected. You can select an agent by either clicking on it in the map \(4\) or selecting it from the agent drop-down menu higher up in the view. Once the agent is selected, the **View Screenshot** link will appear \(3 above\).

Let's see what the error screenshot can tell us:

IMAGE MISSING

In the figure above it looks like the action from the previous step \(a click on the **Next** button\) is still being processed - the page is still being loaded. This brings us to the most important aspect of a transaction testing reliability - waiting for elements the transaction interacts with to become ready.

**Let's repeat that:**  
**If you want your transaction test to run reliably, it needs to wait for elements to become ready before interacting with them.**

Think of this as the first and the most important rule of transaction scripting. Because it is.

## Introducing the waitForCondition command

The solution to the problem outlined above comes in the form of a transaction command called `waitForCondition`. The operation of the `waitForCondition` command is fairly straightforward - it stalls the execution of a transaction until the specified condition is satisfied, or a timeout occurs.

### Waiting for elements to become ready

If there is one aspect of transaction scripting that customers should understand, it should be the speed of transaction test execution. Agents \(= computers\) running a transaction test are interacting with tested web application much faster than humans. Much faster. In the example we're working with here, the agent attempted to re-enter the username right after clicking the **Next** button, which is what caused the reported error.

To prevent such transaction errors, we must instruct the transaction to wait for the elements we want it to interact with to become fully available. This generally\* consists of two steps:

1. Making sure the element **exists** before verifying its visibility, and
2. Making sure the element **is visible** before interacting with it.

**1. Making sure the element exists:** This first condition makes sure the element that the transaction is trying to interact with actually exists in the context of the tested web page. This is especially important when working with dynamic elements. Dynamic elements are elements that are created on-the-fly when they are required. A good example of such element creation is any modern [single-page application](https://en.wikipedia.org/wiki/Single-page_application) where almost everything is loaded, instantiated and displayed dynamically. This first condition makes sure that the second condition \(described below\) does not fail with the "element not found" error message.

**2. Making sure the element is visible:** The second condition makes sure that the element is fully visible before the subsequent step will try to interact with it.

These two waiting conditions can be implemented with the `waitForCondition` Selenium command combined with the `selenium.isElementPresent()` and `selenium.isVisible()` functions.

\*Generally: There are applications that bind actions to element events well after said elements are instantiated and visible. Details about creating transaction tests targeting such applications are beyond the scope of this guide.

### How to create waitForCondition steps

Let's add waiting conditions for the username re-entry interaction. Such waiting conditions can be implemented as follows:

| Step | Name | Command | Target | Value |
| :--- | :--- | :--- | :--- | :--- |
| 4 | Wait to be present - Username input field | waitForCondition | selenium.isElementPresent\('`id=okta-signin-username`'\) | 10000 |
| 5 | Wait to become visible - Username input field | waitForCondition | selenium.isVisible\('`id=okta-signin-username`'\) | 5000 |
| 6 | Enter username again | type | `id=okta-signin-username` | \*\*\*\*\* |

In the table above, the expression for uniquely identifying the username input field \(`id=okta-signin-username`\) is highlighted for a reason - the same expression is used in all three steps:

* The first step makes the transaction wait until the targeted element is instantiated,
* The second step makes the transaction wait until the element is fully visible,
* The third step performs the actual interaction with the element.

### Getting to 100%

Now, let's give our updated transaction test another go:

IMAGE MISSING

Such. Beauty! :\)

There. We've successfully amended our transaction script to contain appropriate `waitForCondition` steps to make it reach the desired 100% completion. To conclude the story, here is the final version of the transaction script:

IMAGE MISSING

## Summary

We can summarize the content of this guide into the following suggestion:

**When creating transaction scripts, use appropriate waitForCondition steps in front of any step that interacts with the tested application. By not doing so you're making your transaction test prone to spurious errors. Such errors may occur due to modern web applications' non-deterministic resource loading.**

### Why do I want to use waitForCondition steps?

There are multiple reasons for why you should use proper waitForCondition steps. Let's outline the main ones:

* **To make your transaction test work in the first place:** You might be lucky and your tested application is architected in a way that makes transaction testing naturally work with it, without placing a single waitForCondition step in your scripts. If that's the case, good for you. However, if you are not that lucky \(like we weren't in our example above\) and if, like the majority of modern applications, your test target requires you to wait for specific elements before interacting with them, then you will need to use waitForCondition steps to make your transaction reach 100% completion.
* **To make your transaction test less prone to spurious errors:** Modern web applications are composed of many resources - cascading style sheets, JavaScript code, images, dynamic content fetched by XHR calls, and more. Depending on the architecture of the tested application, the order of loading of these resources might be deterministic, but most of the time it is not. Secondly, the loading of certain resources might stall, causing the order of resource loading to change dynamically. Such conditions are almost perfect for causing spurious errors in your transaction test. These errors will most certainly happen when you're not using appropriate waitForCondition steps. Therefore, it's best to not assume anything about the tested application and use proper waiting steps before doing any interaction with the application's elements.

### Where should I put my waitForCondition steps?

Short answer - in front of every interactive action such as click, text entry, mouse hovering, etc. However, read the following subsection.

#### Can some of these waitForCondition steps be omitted?

Short answer - it depends.

One example scenario where waitForCondition steps can be left out is in a transaction that is interacting with multiple elements of the same form. Often, all elements belonging to a common form are rendered at the same moment \(more or less\). This means that, while your transaction should definitely wait for presence and visibility of the first form element it wants to interact with, the second element that the transaction will interact with will already be waiting prepared by the time the transaction is done interacting with the first element.

We used this very approach in steps 4 through 7 in the [Getting to 100%]() section above, where the amended transaction only waits for the presence and visibility of the username input field, and then proceeds directly to entering a password, without explicitly waiting for the password input field to become present and visible.

Another example where waitForCondition steps can be omitted are web applications that stall the [onLoad](https://www.w3schools.com/jsref/event_onload.asp) browser event until all the resources are fully loaded and ready. For some applications, the browser does this automatically \(i.e. the ones that have all the HTML and JS code included in the main HTML content\). Agents stall transaction execution whenever the browser enters this "loading" mode. Transaction execution is resumed once onLoad event occurs. This is why our example didn't need waitForCondition steps in front of step \#2.

## Related information

The following resources provide related information:

* [Supported Selenium commands](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBwCAK_Transactions-supported-Selenium-commands) reference outlines all Selenium instructions supported by ThousandEyes transaction tests.
* [Using the Transactions view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmnKAC_Using-the-Transactions-View) article provides a guide through the main features of transaction test results view.
* [Using the ThousandEyes recorder](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000Cmn8KAC_Using-the-ThousandEyes-Recorder) guide demonstrates how to leverage a simple tool to help you create basic transactions by recording your actions in your browser.

