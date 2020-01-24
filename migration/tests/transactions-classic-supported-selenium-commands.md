# Transactions \(Classic\) - Supported Selenium commands

| Notice of obsolescence |
| :--- |
| This content is related to an older generation of ThousandEyes transaction test type, now renamed to **Transaction \(Classic\)**. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

Web Transaction tests in ThousandEyes allows a predefined script to interact with a browser from multiple locations simultaneously. Our transactions run in Chrome, using Selenium.

When creating a transaction, you have three options:

* Use the ThousandEyes Recorder to record a transaction, and export the transaction into ThousandEyes.  This is the simplest approach, because you're working with data created by one of our applications, and ingesting it using a method we've written.  
* Writing a script using Selenium, exporting it to a file, and importing that file into ThousandEyes
* Manually writing your own script execution using the test settings page.

This document covers the commands supported when using either of the last two methods, mentioned above.

Our agents **do not** support Webdriver, which is the second major release of Selenium, but they run in Selenium RC mode - meaning, they only accept commands which are available in the first major release of Selenium.

For information about Selenium versions, refer to the [SeleniumHQ website](http://docs.seleniumhq.org/). 

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Command</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
      <th style="text-align:left"><b>Required Parameters</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">addSelection</td>
      <td style="text-align:left">Add a selection to the set of selected options in a multi-select element
        using an option locator. Specify the multi-select element as the target,
        and the option as the value</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">altKeyDown</td>
      <td style="text-align:left">Presses the &apos;alt&apos; key down and holds until an altKeyUp command
        is sent, or a new page is loaded</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">altKeyUp</td>
      <td style="text-align:left">Releases the &apos;alt&apos; key</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">assignId</td>
      <td style="text-align:left">Temporarily sets the &quot;id&quot; attribute of the specified element,
        so you can locate it in the future using its ID rather than by Xpath. Target
        is the element, and value is the id</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">check</td>
      <td style="text-align:left">Check a toggle-button (checkbox/radio). Specify the element as the target</td>
      <td
      style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">click</td>
      <td style="text-align:left">Clicks on a link, button, checkbox or radio button. Specify the element
        as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">clickAt</td>
      <td style="text-align:left">Clicks on a link, button, checkbox or radio button. Specify the element
        as the target, and the coordinates (relative to the element) where to click
        on the element as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">chooseCancelOnNextConfirmation</td>
      <td style="text-align:left">By default, Selenium&apos;s overridden window.confirm() function will
        return true, as if the user had manually clicked OK; after running this
        command, the next call to confirm() will return false, as if the user had
        clicked Cancel.</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">chooseOkOnNextConfirmation</td>
      <td style="text-align:left">Undo the effect of calling chooseCancelOnNextConfirmation.</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">controlKeyDown</td>
      <td style="text-align:left">Presses the &apos;control&apos; key down and holds until a controlKeyUp
        command is sent, or a new page is loaded</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">controlKeyUp</td>
      <td style="text-align:left">Releases the &apos;control&apos; key</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">createCookie</td>
      <td style="text-align:left">
        <p>Create a cookie to be sent in subsequent HTTP headers. The <b>Target</b> field
          takes the cookie&apos;s name=value pair, the <b>Value</b> field takes the
          cookie&apos;s attributes. Multiple attributes are separated with commas
          in the <b>Value</b> field (NOT with semi-colons, which are delimiters for
          the Cookie header). Three types of attributes are allowed: Path, Domain,
          and Max-Age. Max-Age is an integer specifying a number of seconds. The
          cookie&apos;s Path and Domain is the current page path and domain if not
          explicitly set, and the Max-age is effectively -1 if not set.</p>
        <p> <b>Note: Cookies are automatically cleared upon completion of the test.</b>
        </p>
      </td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">deleteAllVisibleCookies</td>
      <td style="text-align:left"><a href="http://laughingsquid.com/wp-content/uploads/cookie-monster-20080603-133713.jpg">Deletes all cookies.</a> (image
        not used with permission)</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">deleteCookie</td>
      <td style="text-align:left">Delete a named cookie with specified path. Specify the cookie name as
        the target, and path as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">doubleClick</td>
      <td style="text-align:left">Double clicks on a link, button, checkbox or radio button. Specify the
        element as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">dragAndDrop</td>
      <td style="text-align:left">Drags an element a certain distance and then drops it. Specify the element
        as the target, and the coordinates as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">dynamicType</td>
      <td style="text-align:left">Similar to the <b>type</b> command, but instead of static text in the Value
        field, but accepts a JavaScript expression, the results of which are provided
        to dynamicType via the JavaScript return statement. The returned value
        must be a number or a string.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">fireEvent</td>
      <td style="text-align:left">Explicitly simulate an event, to trigger the corresponding &quot;on<em>event</em>&quot;
        handler. Specify the event as the target, and parameters as the value.</td>
      <td
      style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">focus</td>
      <td style="text-align:left">Move the focus to the specified element. Specify the element as the target.</td>
      <td
      style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">keyDown</td>
      <td style="text-align:left">Simulates a user pressing a key (without releasing it). Specify the element
        in which to press the key as the target, and the key as the value.</td>
      <td
      style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">keyPress</td>
      <td style="text-align:left">Simulates a user pressing and releasing a key. Specify the element in
        which to press the key type as the target, and the key as the value.
        <br
        /> <em>Use &apos;\10&apos; (LF) or &apos;\13&apos; (CR) strings to simulate pressing the Enter key.</em>
      </td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">keyUp</td>
      <td style="text-align:left">Releases a key. Specify the same target and value as the keyDown command.</td>
      <td
      style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">metaKeyDown</td>
      <td style="text-align:left">Presses the appropriate OS meta key (Windows Key / Command Key). Holds
        until a metaKeyUp command is sent, or a new page is loaded</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">metaKeyUp</td>
      <td style="text-align:left">Releases the meta key</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseOver</td>
      <td style="text-align:left">Simulates a user moving the mouse pointer over the target with the mouse.</td>
      <td
      style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseOut</td>
      <td style="text-align:left">Simulates a user moving the mouse pointer away from the specified element.</td>
      <td
      style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseDown</td>
      <td style="text-align:left">Simulates a user pressing the mouse button (without releasing it yet)
        on the specified element. Specify the element as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseDownAt</td>
      <td style="text-align:left">Simulates a user pressing the mouse button (without releasing it yet)
        at the specified location. Specify the element as the target and the coordinates
        in which to click (relative to the element) as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseMove</td>
      <td style="text-align:left">Simulates a user pressing the mouse button (without releasing it yet)
        on the specified element. Specify the element as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseMoveAt</td>
      <td style="text-align:left">Simulates a user pressing the mouse button (without releasing it yet)
        at the specified location. Specify the element as the target and the coordinates
        in which to click (relative to the element) as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseUp</td>
      <td style="text-align:left">Simulates the event that occurs when the user releases the mouse button
        (i.e., stops holding the button down) on the specified element. Specify
        the element as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">mouseUpAt</td>
      <td style="text-align:left">Simulates the event that occurs when the user releases the mouse button
        (i.e., stops holding the button down) at the specified location. Specify
        the element as the target and the coordinates at which to release the mouse
        button (relative
        <br />to the element) as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">open</td>
      <td style="text-align:left">Opens an URL in the test frame. This accepts both relative and absolute
        URLs. The &quot;open&quot; command waits for the page to load before proceeding,
        ie. the &quot;AndWait&quot; suffix is implicit.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">refresh</td>
      <td style="text-align:left">Simulates the user clicking the &quot;Refresh&quot; button on their browser.</td>
      <td
      style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">removeAllSelections</td>
      <td style="text-align:left">Unselects all of the selected options in a multi-select element. Specify
        the element as the target.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">removeSelection</td>
      <td style="text-align:left">Remove a selection from the set of selected options in a multi-select
        element using an option locator. Specify the element as the target, and
        the option locator as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">runScript</td>
      <td style="text-align:left">Creates a new &quot;script&quot; tag in the body of the current test window,
        and adds the specified text (specified as the target) into the body of
        the command.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">select</td>
      <td style="text-align:left">Select an option from a drop-down using an option locator. Specify the
        element as the target, and the option locator as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">selectFrame</td>
      <td style="text-align:left">Selects a frame within the current window. Specify the frame as the target.
        <br
        />Use <em>&apos;relative=up&apos;</em> to move to a parent frame or <em>&apos;relative=top&apos;</em> to
        move to the root frame.</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">selectWindow</td>
      <td style="text-align:left">Selects a popup window; once a popup window has been selected, all commands
        go to that window. Specify the window as the target. Empty target selects
        the first window in which the transaction started.</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">setTimeout</td>
      <td style="text-align:left">Specifies the amount of time that Selenium will wait for actions to complete,
        in milliseconds. Set this as the value.
        <br /> <em>Note: This will not affect the timeout of ThousandEyes transactions.</em>
      </td>
      <td style="text-align:left">value</td>
    </tr>
    <tr>
      <td style="text-align:left">shiftKeyDown</td>
      <td style="text-align:left">Presses the &apos;shift&apos; key down and holds until a shiftKeyUp command
        is sent, or a new page is loaded</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">shiftKeyUp</td>
      <td style="text-align:left">Releases the &apos;shift&apos; key</td>
      <td style="text-align:left">-</td>
    </tr>
    <tr>
      <td style="text-align:left">sleep</td>
      <td style="text-align:left">pause Test execution for definite time period
        <br /> <em>A step with the sleep command is considered completed at the start of the sleep duration. If transaction times out during the sleep duration, step is still displayed as completed.</em>
      </td>
      <td style="text-align:left">value</td>
    </tr>
    <tr>
      <td style="text-align:left">submit</td>
      <td style="text-align:left">Submits the form, specified as the target</td>
      <td style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">type</td>
      <td style="text-align:left">Sets the value of an input field, as though the user typed it in. Specify
        the element as the target, and the string to be entered as the value.</td>
      <td
      style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">typeKeys</td>
      <td style="text-align:left">Simulates keystroke events on the specified element, as though you typed
        the value key-by-key. Specify the element as the target, and the keys to
        be entered as the value.</td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">uncheck</td>
      <td style="text-align:left">Uncheck a toggle-button (checkbox/radio). Specify the element as the target</td>
      <td
      style="text-align:left">target</td>
    </tr>
    <tr>
      <td style="text-align:left">waitForCondition</td>
      <td style="text-align:left">Runs the specified check repeatedly until it evaluates to &quot;true&quot;.
        Specify the condition as the target, and the time to wait (in milliseconds)
        as the value.
        <br /> <em>See valid waitForCondition calls below, for snippets which can be used.</em>
      </td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">waitForDownload</td>
      <td style="text-align:left">
        <p>Waits for the specific file download to complete. Specify the final filename
          (as it appears in the browser&apos;s Downloads directory) as the target,
          and the time to wait (in milliseconds) as the value.</p>
        <p> <b>Tip:</b> If multiple files with an identical name are downloaded during
          the course of a single transaction run, the names of the files in the Download
          directory generated by the second and later downloads will contain a number
          suffix (i.e. <code>file.zip</code>, <code>file (1).zip</code> etc.).</p>
      </td>
      <td style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">waitForPageToLoad</td>
      <td style="text-align:left">Waits for a new page to load. Specify the time to wait (in milliseconds)
        as the value.</td>
      <td style="text-align:left">value</td>
    </tr>
    <tr>
      <td style="text-align:left">waitForPopUp</td>
      <td style="text-align:left">Waits for a popup window to appear and load up. Specify the windowID as
        the target, and the time to wait (in milliseconds) as the value.</td>
      <td
      style="text-align:left">target, value</td>
    </tr>
    <tr>
      <td style="text-align:left">windowFocus</td>
      <td style="text-align:left">Gives focus to the currently selected window</td>
      <td style="text-align:left">-</td>
    </tr>
  </tbody>
</table>## waitForCondition calls

The following boolean checks can be used in the value field of waitForCondition references.  As mentioned above, a waitForCondition call will repeatedly run the boolean check until it evaluates to true, or until the timeout expires.  If the timeout expires before true is returned, the transaction will fail.

| **Boolean expression** | **Description** | **Parameters** |
| :--- | :--- | :--- |
| isChecked | Gets whether a toggle-button \(checkbox/radio\) is checked | element |
| isConfirmationPresent | Has confirm\(\) been called? | - |
| isElementPresent | Verifies that the specified element is somewhere on the page. | element |
| isOrdered | Check if these two elements have same parent and are ordered siblings in the DOM. | element1, element2 |
| isPromptPresent | Has a prompt occurred? | - |
| isSomethingSelected | Determines whether some option in a drop-down menu is selected. | element |
| isTextPresent | Verifies that the specified text pattern appears somewhere on the rendered page shown to the user. | textPattern |
| isVisible | Determines if the specified element is visible. | element |

To negate a boolean check \(make a command that would evaluate to FALSE into TRUE or vice versa\), use an exclamation mark before the value in the target field.  For example, to check whether an element with an ID attribute of "foo" is NOT present, the command in Step 1 would be used:

| **Step** | **Name** | **Command** | **Target** | **Value** |
| :--- | :--- | :--- | :--- | :--- |
| 0 | Open page | open | / |  |
| 1 | Check for non-existent element | waitForCondition | !selenium.isElementPresent\('//\*\[@id="foo"\]'\) | 30000 |

When creating scripts using the Test Settings interface, available commands show using intellisense as they are typed.   Only those commands which are supported by the Selenium RC language are allowed.  When importing using the Script importer, a parsing error will be thrown if unsupported commands are used in a warning similar to that shown below:

_"The uploaded script contains one or more invalid commands"_

Contact the Customer Success team at support@thousandeyes.com if you have any questions.

Significant portions of selenium command descriptions borrow from the seleniumhq.org website.  See http://release.seleniumhq.org/selenium-remote-control/0.9.2/doc/java/com/thoughtworks/selenium/DefaultSelenium.html for details.

