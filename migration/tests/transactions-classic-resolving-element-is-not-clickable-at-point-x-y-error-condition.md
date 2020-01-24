# Transactions \(Classic\) - resolving "Element is not clickable at point \(X, Y\)" error condition

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

## Problem analysis

Let's start with an assumption that your transaction is properly constructed and [leverages waitForCondition statements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFeUCAW_Transactions-Classic-Using-the-waitForCondition-steps) in all the appropriate places, yet still reports the following error:

IMAGE MISSING

Let's display the error message in a more readable manner:

```text
Element <A> is not clickable at point (<X>, <Y>).
Other element would receive the click: <B>.
```

Before delving into the details of this error, let's review what this transaction test is trying to achieve.

### Transaction scenario used in this article

Our transaction here is testing a Salesforce instance. The initial steps that deal with login-related tasks are absent from the table below, as we will only be focusing on the relevant part of the transaction - the part where the error condition occurs, which is step \#17. In the table below, however, some additional \(earlier\) steps are included as well, to provide sufficient context for understanding the issue:

| Step number | Description | Screenshot indicating exact transaction flow |
| :--- | :--- | :--- |
| \#8 - \#10 | Wait for and click the **Edit** button | IMAGE MISSING |
| \#11 - \#14 | First, wait for text **Edit S-CS-0100299** to appear.  Then wait for and click the **Cancel** button | IMAGE MISSING |
| \#15 - \#17 | Wait for and click the **Change Owner** button | IMAGE MISSING |

The entire transaction script looks like this:

IMAGE MISSING

This script, despite being constructed as per [recommendations for proper usage of waitForCondition steps](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFeUCAW_Transactions-Using-the-waitForCondition-steps), still produces an unexpected error at step \#17. Time to investigate further.

### Dissecting the error message

The error message from step \#17 comprises of two parts. The first part \(slightly abbreviated\) says this:

```text
Element <div ...>Change Owner</div> is not clickable at point (594, 171).
```

The target element is not clickable - that is... weird? We used proper waiting conditions right before this step, meaning the target element is definitely present and visible.

The second part of the error message reveals the first clue:

```text
Other element would receive the click: <div class="slds-form-element slds-form-element_readonly slds-grow slds-hint-parent override--slds-form-element" data-aura-rendered-by="1154:0">...</div>
```

How can an element be visible, but when clicked on, some other element would receive the click event?

### Screenshot analysis

A much clearer clue is revealed in the screenshot of the error:

IMAGE MISSING

In the figure above, the **Change Owner** button is already visible, but only partially - the editing dialog and the semi-transparent overlay element from the previous step have not yet disappeared entirely, due to a gradual transition from fully visible to invisible. This explains how a visible element is unable to receive a click event.

### Analytical conclusion

Any matching and fully or partially visible element will satisfy the `selenium.isVisible()` condition. An element is partially visible when it is covered by another element and the covering element is semi-transparent.

## Solving the issue

Solving the issue at hand is often not an exact science, especially not for users who are not intimately familiar with the internal structure of the tested application. A certain amount of creativity and trial-and-error experimentation can be expected.

### Theory

A theoretical solution that works around the `Element A is not clickable at point (X, Y). Other element would receive the click: B` issue is rather simple and consists of two steps:

1. Finding the XPath locator of the element obstructing the click
2. Making the transaction wait until the offending element is either gone or becomes invisible

The theory is simple, right? Well, determining what exactly these two steps should be might prove a bit more challenging.

### Locating the offending overlay element

The basic information about the offending overlay element is already given in the second part of the error message:

```text
Other element would receive the click: <div class="slds-form-element slds-form-element_readonly slds-grow slds-hint-parent override--slds-form-element" data-aura-rendered-by="1154:0">...</div>
```

There is a good chance that the following `<div>` element locator \(created by just adjusting the content of the error message above\) is what we're looking for:

```text
//div[@class="slds-form-element slds-form-element_readonly slds-grow slds-hint-parent override--slds-form-element"]
```

Such element locator is a good start. However, at this point, it is often beneficial to leverage [web development tools](https://en.wikipedia.org/wiki/Web_development_tools) integrated into your web browser to inspect the relevant overlay elements manually.

### Waiting for the overlay element to disappear

When the offending overlay element is implemented in a way that makes it completely disappear from the DOM structure before further interactions with the tested application are possible, the following transaction step will make sure the overlay element is gone before the transaction is allowed to continue:

| \# | Step name | Command | Target | Value \(timeout in ms\) |
| :--- | :--- | :--- | :--- | :--- |
| 17 | Wait for the overlay to disappear | `waitForCondition` | `!selenium.isElementPresent('<OVERLAY-LOCATOR>')` | `10000` |

Notice the `!` character in front of the `selenium.isElementPresent` in the target column above - this is a negation operator. Instead of waiting for the presence of the specified element, the command above makes the transaction wait for the absence of said element.

### Waiting for the overlay element to become invisible

When the offending overlay element is constructed in a manner that makes it always be present in the DOM structure but only visible when needed, the following transaction step can provide the necessary waiting condition:

| \# | Step name | Command | Target | Value \(timeout in ms\) |
| :--- | :--- | :--- | :--- | :--- |
| 17 | Wait for the overlay to become invisible | `waitForCondition` | `!selenium.isVisible('<OVERLAY-LOCATOR>')` | `10000` |

### Waiting for the overlay element to either disappear or become invisible

Yet another approach is to wait for any of the events that may happen to the offending overlay element - either to have it disappear from the DOM entirely or to wait until it becomes invisible:

| \# | Step name | Command | Target | Value  |
| :--- | :--- | :--- | :--- | :--- |
| 17 | Wait for the overlay to disappear | `waitForCondition` | `!selenium.isElementPresent('<OVERLAY-LOCATOR>') || !selenium.isVisible('<OVERLAY-LOCATOR>')` | `10000` |

### Using sleep

Potentially 100% successful yet a rather rudimentary approach to solving the issue at hand is to simply make the transaction stall for a fixed amount of time. This can be achieved using the `sleep` command like this:

| \# | Step name | Command | Target | Value \(sleep in milliseconds\) |
| :--- | :--- | :--- | :--- | :--- |
| 17 | Sleep | `sleep` |  | `2000` |

The `sleep` command can certainly make the transaction wait long enough for the offending overlay element to disappear. The downside is the fixed amount of time your transaction will spend doing nothing. While the transaction itself is not doing anything during sleep, the induced delay does contribute to either [Enterprise Agent utilization](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnjgCAC_Enterprise-Agent-Utilization) or [Cloud Agent unit consumption](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmoKAC_How-Unit-consumption-works) \(or both\). Additionally, such an artificial delay makes the transaction time metric less precise.

### Other approaches

The approaches above are not the only available and be-all-end-all solutions. Because there are many ways of manipulating DOM content to create overlay elements, there are many methods for finding them and waiting for their disappearance. As stated in the initial paragraph of this section, a certain level of creativity can be expected.

### Making our example work

While working on the example used in this guide, three iterations had to be performed and each revealed a new element that needed to be waited out. Eventually, the right `waitForCondition` step was constructed and the transaction has been running smoothly ever since:

IMAGE MISSING

In our case, the step that successfully made the transaction stall until the overlay element disappears was this one:

| \# | Step name | Command | Target | Value \(timeout in ms\) |
| :--- | :--- | :--- | :--- | :--- |
| 17 | Wait for the overlay to disappear | `waitForCondition` | `!selenium.isElementPresent('//div[@class="slds-form-element slds-form-element_readonly slds-grow slds-hint-parent override--slds-form-element"]')` | `10000` |

## Related information

The following resources provide further information on related subjects:

* [Using the waitForCondition steps](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFeUCAW_Transactions-Classic-Using-the-waitForCondition-steps) guide details where and how transaction waiting conditions should be used.
* [Navigating the waterfall charts](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CpebCAC_Navigating-Waterfall-Charts-for-Page-Load-and-Transaction-Tests) article provides an overview of how to review transaction test result details.
* [Using the Transactions \(Classic\) view](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmnKAC_Using-the-Transactions-Classic-View) article provides a guide through the main features of the transaction test results view.

