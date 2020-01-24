# Transaction Scripting Reference

This article contains a reference of all namespaces, classes, modules and methods that are available for creating [transaction tests](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-scripting-guide).

## Example scripts

For quicker orientation, there is a comprehensive collection of script examples provided by the [transaction scripting examples repository in our GitHub account](https://github.com/thousandeyes/transaction-scripting-examples).

## Controlling the browser

ThousandEyes provides a wrapper of the Selenium WebDriver library for JavaScript. It contains methods for controlling the browser that is used to execute the test.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>driver</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { driver } from &apos;thousandeyes&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>await driver.get(&apos;https://google.com&apos;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>actions( options )</code>
          </li>
          <li><code>executeAsyncScript( script, ...args )</code>
          </li>
          <li><code>executeScript( script, ...args )</code>
          </li>
          <li><code>findElement( locator )</code>
          </li>
          <li><code>findElements( locator )</code>
          </li>
          <li><code>get( url )</code>
          </li>
          <li><code>getAllWindowHandles()</code>
          </li>
          <li><code>getCurrentUrl()</code>
          </li>
          <li><code>getPageSource()</code>
          </li>
          <li><code>getTitle()</code>
          </li>
          <li><code>getWindowHandle()</code>
          </li>
          <li><code>manage()</code>
          </li>
          <li><code>navigate()</code>
          </li>
          <li><code>sleep( ms )</code>
          </li>
          <li><code>switchTo()</code>
          </li>
          <li><code>wait( condition, timeout, message )</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_WebDriver.html">https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_WebDriver.html</a>
      </td>
    </tr>
  </tbody>
</table>## Interacting with page elements

A set of methods for interacting with elements. Once the element is located and retrieved \(by using the `findElement()` function or similar\), it can be managed using the following methods.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>selenium-webdriver</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>WebElement</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Find an element</b>
      </td>
      <td style="text-align:left"><code>const element = await driver.findElement(By.css(&apos;.someClass&apos;))</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>clear()</code>
          </li>
          <li><code>click()</code>
          </li>
          <li><code>getAttribute( attributeName )</code>
          </li>
          <li><code>getCssValue( cssStyleProperty )</code>
          </li>
          <li><code>getId()</code>
          </li>
          <li><code>getText()</code>
          </li>
          <li><code>sendKeys( ...args )</code>
          </li>
          <li><code>submit()</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_WebElement.html">https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_WebElement.html</a>
      </td>
    </tr>
  </tbody>
</table>### Waiting for events

Defines common conditions for use with WebDriver wait.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>selenium-webdriver</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>until</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { until } from &apos;selenium-webdriver&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>await driver.wait(until.alertIsPresent(), 10 * 1000, &apos;Alert did not appear within 10 seconds!&apos;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>ableToSwitchToFrame( frame )</code>
          </li>
          <li><code>alertIsPresent()</code>
          </li>
          <li><code>elementIsDisabled( element )</code>
          </li>
          <li><code>elementIsEnabled( element )</code>
          </li>
          <li><code>elementIsNotSelected( element )</code>
          </li>
          <li><code>elementIsNotVisible( element )</code>
          </li>
          <li><code>elementIsSelected( element )</code>
          </li>
          <li><code>elementIsVisible( element )</code>
          </li>
          <li><code>elementLocated( locator )</code>
          </li>
          <li><code>elementTextContains( element, substr )</code>
          </li>
          <li><code>elementTextIs( element, text )</code>
          </li>
          <li><code>elementTextMatches( element, regex )</code>
          </li>
          <li><code>elementsLocated( locator )</code>
          </li>
          <li><code>stalenessOf( element )</code>
          </li>
          <li><code>titleContains( substr )</code>
          </li>
          <li><code>titleIs( title )</code>
          </li>
          <li><code>titleMatches( regex )</code>
          </li>
          <li><code>urlContains( substrUrl )</code>
          </li>
          <li><code>urlIs( url )</code>
          </li>
          <li><code>urlMatches( regex )</code>
          </li>
          <li><code>elementTextMatches( element, regex )</code>
          </li>
          <li><code>elementsLocated( locator )</code>
          </li>
          <li><code>stalenessOf( element )</code>
          </li>
          <li><code>titleContains( substr )</code>
          </li>
          <li><code>titleIs( title )</code>
          </li>
          <li><code>titleMatches( regex )</code>
          </li>
          <li><code>urlContains( substrUrl )</code>
          </li>
          <li><code>urlIs( url )</code>
          </li>
          <li><code>urlMatches( regex )</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/lib/until.html">https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/lib/until.html</a>
      </td>
    </tr>
  </tbody>
</table>### Generating keyboard events

Representations of pressable keys that aren't text.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>selenium-webdriver</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>Key</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { Key } from &apos;selenium-webdriver&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>await driver.findElement(By.css(&apos;.form-input&apos;)).sendKeys(Key.RETURN);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>Key.chord( ...keys )</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Values</b>
      </td>
      <td style="text-align:left">See the reference below.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_Key.html">https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/index_exports_Key.html</a>
      </td>
    </tr>
  </tbody>
</table>### Taking screenshots

| **Namespace** | `thousandeyes` |
| :--- | :--- |
| **Module** | `driver` |
| **Method** | `takeScreenshot()` |
| **Used Like** | `await driver.takeScreenshot();` |
| **Description** | Takes a screenshot of the current page and stores it in memory. These screenshots will be collected at the end of the test. A maximum of 3 screenshots are allowed, new screenshots will override the old ones in case that this limit is exceeded. |
| **Parameters** | None |
| **Returns** | None |

### Handling credentials

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>credentials</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { credentials } from &apos;thousandeyes&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>credentials.get(&apos;MyPasswordName&apos;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>get( credentialName )</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Gets the stored credential value matching the supplied name.</p>
        <p>Only works if you have already associated the credential with the current
          test (Test settings page).</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left"><code>credentialName</code> (string) The name of the credential to fetch</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">(string) The password or sensitive value associated with the supplied
        credential name</td>
    </tr>
  </tbody>
</table>### Handling downloads

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>downloads</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { downloads } from &apos;thousandeyes&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>await downloads.waitForDownload(&apos;myFilename.txt&apos;, 10 * 1000);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>waitForDownload( fileName, timeout )</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Waits for a download matching the supplied filename to appear and then
          to finish.</p>
        <p>If a file matching the supplied name has previously been downloaded, this
          function will complete immediately.</p>
        <p>If no file matching the supplied name has been or is currently downloading,
          it will wait for the supplied timeout amount of time for the file to appear
          and finish downloading.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>fileName</code> (string) The name of the file to wait for</li>
          <li><code>timeout</code> (number) The max number of milliseconds to wait for
            download completion. Defaults to 60 seconds</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">None, if the download is successful, else will throw an error</td>
    </tr>
  </tbody>
</table>## Measuring transaction time\(s\)

ThousandEyes transactions support two types of measuring time:

* [Markers]()
* [Overall transaction time]()

## Markers

Markers are custom time delimiters, enabling precise time measurements of smaller sections of the transaction.

Start a marker:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>markers</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>start( markerName )</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Starts a marker with the supplied name.</p>
        <p>This marker can later be stopped by calling the <code>stop</code> function
          with the same name.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left"><code>markerName</code> (string) The name of the marker</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">None. Will throw an error if attempting to start a previously started
        marker.</td>
    </tr>
  </tbody>
</table>Stop a marker:

| **Namespace** | `thousandeyes` |
| :--- | :--- |
| **Module** | `markers` |
| **Method** | `stop( markerName )` |
| **Description** | Stops the marker matching the supplied name. |
| **Parameters** | `markerName` \(string\) The name of the marker |
| **Returns** | None. Will throw an error if attempting to stop a marker that hasn't been started yet or one that was already stopped. |

Set a marker:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>markers</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>set( markerName )</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Creates a marker that spans from transaction start time to the time this
          method is called.</p>
        <p>Calling <code>set</code> implicitly closes the marker, so there is no need
          to later close it.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left"><code>markerName</code> (string) The name of the marker</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">None.</td>
    </tr>
  </tbody>
</table>### Overall transaction time

Running a transaction test implicitly causes the overall transaction time measurement, spanning from the moment the transaction test run starts and to the end of the transaction. However, if customization of overall transaction time's start and stop moments is required, the following methods can be used to such effect.

Set the overall transaction time **start** moment:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>transaction</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>start()</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Sets the start time of the transaction.</p>
        <p>If not called, the transaction start time will default to the script start
          time.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
  </tbody>
</table>Set the overall transaction time **end** moment:

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>thousandeyes</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>transaction</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left"><code>stop()</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Sets the end time of the transaction.</p>
        <p>If not called, the transaction end time will default to the script end
          time.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Parameters</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Returns</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
  </tbody>
</table>## Element locators

Provided is a set of mechanisms dedicated to locating elements on the page.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>selenium-webdriver</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Class</b>
      </td>
      <td style="text-align:left"><code>By</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import { By } from &apos;selenium-webdriver&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>await driver.findElement(By.css(&apos;#myId&apos;));</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported static methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>By.className( name )</code>
          </li>
          <li><code>By.css( selector )</code>
          </li>
          <li><code>By.id( selector )</code>
          </li>
          <li><code>By.js( script, ...var_args )</code>
          </li>
          <li><code>By.linkText( text )</code>
          </li>
          <li><code>By.name( name )</code>
          </li>
          <li><code>By.partialLinkText( text )</code>
          </li>
          <li><code>By.xpath( xpath )</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/lib/by_exports_By.html">https://selenium.dev/selenium/docs/api/javascript/module/selenium-webdriver/lib/by_exports_By.html</a>
      </td>
    </tr>
  </tbody>
</table>## Assertions

The `assert` module provides a set of assertion functions for verifying invariants.

**NOTE:** Only strict mode is supported.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Namespace</b>
      </th>
      <th style="text-align:left"><code>assert</code>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Module</b>
      </td>
      <td style="text-align:left"><code>assert</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Import Syntax</b>
      </td>
      <td style="text-align:left"><code>import assert from &apos;assert&apos;;</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Used Like</b>
      </td>
      <td style="text-align:left"><code>assert(url === &apos;https://wikipedia.org&apos;, &apos;Assertion failed: not on wikipedia!&apos;)</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Supported methods</b>
      </td>
      <td style="text-align:left">
        <ul>
          <li><code>assert( value[, message] )</code>
          </li>
          <li><code>deepEqual( actual, expected[, message] )</code>
          </li>
          <li><code>doesNotReject( asyncFn[, error][, message] )</code>
          </li>
          <li><code>doesNotThrow( fn[, error][, message] )</code>
          </li>
          <li><code>equal( actual, expected[, message] )</code>
          </li>
          <li><code>fail( [message] )</code>
          </li>
          <li><code>ifError( value )</code>
          </li>
          <li><code>notDeepEqual( actual, expected[, message] )</code>
          </li>
          <li><code>notEqual( actual, expected[, message] )</code>
          </li>
          <li><code>ok( value[, message] )</code>
          </li>
          <li><code>rejects( asyncFn[, error][, message] )</code>
          </li>
          <li><code>throws( fn[, error][, message] )</code>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Reference</b>
      </td>
      <td style="text-align:left"><a href="https://nodejs.org/api/assert.html">https://nodejs.org/api/assert.html</a>
      </td>
    </tr>
  </tbody>
</table>## Further information

For further information about transaction testing head back to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide).

If you have any questions, reach out to [reach out to ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes).

