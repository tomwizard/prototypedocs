# Navigating Waterfall Charts for Page Load and Transaction Tests

ThousandEyes Page Load and Transaction tests provide a waterfall chart for insight into how a browser interacts with web page objects. This article will explain how data is presented within waterfall charts.

| Notice |
| :--- |
| In this article, Transaction-related content refers to an older generation transaction test type that is now called **Transaction \(Classic\)**. Current generation transactions provide conceptually similar, but visually and functionally improved waterfall charts. We encourage you to start using the more powerful, JavaScript-based current generation of transactions. For more information about the current generation transaction testing, head over to the [Transaction Scripting Guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UFYvCAO_Transaction-Scripting-Guide). |

## What is a Waterfall Chart

A waterfall chart is a time-based representation of data which displays the relationship between events.

Browserbot, the application which performs Page Load and Transaction tests, generates a .har file upon completion of each test. The .har file contains metrics about each object downloaded during the test. This information is then represented in the form of a waterfall chart.

IMAGE MISSING

Properly understanding results requires familiarity with the test types, the Document Object Model, and the ThousandEyes user interface. An introduction to each is provided below.

## The Page Load Waterfall Display

Page Load tests are navigated using a timeline pane and an informational pane. Selecting a single agent, from the agent drop-down menu, enables a waterfall chart which documents each object loaded by the agent's browser.

IMAGE MISSING

An explanation of how to navigate page load test results is [available here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmuKAC_Using-the-Page-Load-view).

An explanation of ThousandEyes test results is [available here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics:-What-do-your-results-mean?).

## The Transaction Test Waterfall Display

Transaction tests are navigated using a timeline pane and an informational pane. Selecting a single agent, from the agent drop-down menu, enables a waterfall chart which documents each object loaded by the agent's browser.

IMAGE MISSING

An explanation of how to navigate Transaction test results is [available here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmnKAC_Using-the-Transactions-View).

An explanation of ThousandEyes test results is [available here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmzKAC_ThousandEyes-Metrics:-What-do-your-results-mean?).

## The Document Object Model

Understanding waterfall charts requires familiarity with the Document Object Model.

Upon receiving a browser request for a web page, an HTTP server locates the site "Directory Index" file and provides an HTML formatted document to the requesting browser.  HTML \(HyperText Markup Language\) instructs the browser regarding how information should be displayed.

The Document Object Model describes HTML structure as a series of objects called nodes. A diagrammed HTML document resembles an ancestral tree; hence the terms "parents" and "children" are used to describe the relationship between nodes. While some nodes, such as text and scripts, may be included within the root HTML document, others must include links to resources which a browser downloads separately.

IMAGE MISSING

Downloaded objects, such as javascript and css files, may in turn reference other objects that the browser must download to prior to page load completion.

IMAGE MISSING

These objects are often sourced from multiple domains.

IMAGE MISSING

## DOM Object Statistics

Each Page Load Object requires an independently completed HTTP transaction.

IMAGE MISSING 

**Waterfall Charts provide metrics for the following HTTP transaction activities:**

**BLOCKED:** The time that a browser waits for an already established connection to become available. Web browsers are designed to allow a maximum number of concurrent connections per domain. 

**DNS**: The duration to resolve a domain record to an IP address. By default, Browserbot does not cache DNS records at startup. 

**CONNECT:** The time to establish a TCP handshake with the Target Server. 

**SSL:** The duration of SSL/TLS negotiation. 

**SEND:** The duration in which the browser successfully sends a request to the server. 

**WAIT:** The duration between the completion of a browser's SEND request and receipt of the first byte of a server's response. 

**RECEIVE:** The time between the first byte of the server response to the last byte of the data payload. 

  
**Aggregate Metrics include:** 

**DOM LOAD TIME:** Transaction time from the beginning of the first object load to the end of the final object load. 

**PAGE  LOAD TIME:** The time from the initial request to when the page is fully rendered. 

##  Navigating the Page Load Waterfall Chart

The transaction test waterfall chart displays DOM load metrics for a target web page.

By default, the waterfall chart displays objects in chronological order. Selecting table headers will reorder rows by either Object Name, Domain, Response Code, Provider, Size, or Waterfall Chronology.

IMAGE MISSING

Hovering over a multi-colored download bar will display object and load metrics.

IMAGE MISSING

Hovering over the blue and red load completion markers will display aggregate load metrics.

IMAGE MISSING

If "save object headers" was selected under the test's advanced settings, a link to view headers will be included within the Waterfall "Response Code" column.

IMAGE MISSING

Selecting a header link opens a light-box which includes both the Request and Response Headers.

IMAGE MISSING

## Navigating the Transaction Test Waterfall Chart

The transaction test waterfall chart displays DOM load metrics for each page loaded during a transaction test.

By default, the waterfall chart displays objects in chronological order. Selecting table headers will reorder rows by either Object Name, Domain, Response Code, Provider, Size, or Waterfall Chronology.

IMAGE MISSING

The Transaction test waterfall traverses multiple pages. A chronological view selector is used to focus on specific portions of the DOM load history.

IMAGE MISSING

Hovering over a multi-colored download bar will display object and load metrics.

IMAGE MISSING

Hovering over the blue and red load completion markers will display aggregate load metrics.

IMAGE MISSING

If "save object headers" was selected under the test's advanced settings, a link to view headers will be included within the Waterfall "Response Code" column.

IMAGE MISSING

Selecting the headers icon will open a light-box which includes both the Request and Response Headers.

IMAGE MISSING

In some cases objects will not have Response Headers one example of this is an object with the Cancelled designation.  If there is no Response Code for an object the word "Cancelled" is shown for an incomplete object.  In the size field of the waterfall a triangular logo with an exclamation point will appear and "Object Incomplete \(cancelled\)" will appear in the hover menu for that logo.  Selecting the Header link will only show a Request Header.  The Response Header section will not show information since there is none.

