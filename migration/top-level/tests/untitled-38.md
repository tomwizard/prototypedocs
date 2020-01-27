# Permitted Content-types for Page Load tests

When a web server responds to an HTTP request, typically the response contains a "Content-Type" field in the HTTP header.  A ThousandEyes Page Load test requires the target of the test \(the **URL** field of the configuration page\) to have a Content-Type of either "text/html" or "application/xhtml".  When saving a Page Load test's configuration, the ThousandEyes platform requests the URL and checks the response's Content-type to ensure that the Content-type is one of these values. If the target of the Page Load test does not have either of these values, the test configuration page displays an error upon attempting to save the configuration.  For example, if the target is a JPEG image, the test configuration page displays the following error:

> ```text
> URL's Content-Type: 'image/jpeg' is not allowed for this test type.
> It should be 'text/html' or 'application/xhtml' (web page)
> ```

The purpose of a Page Load test is to provide timings for loading a DOM object and the child objects. If you wish to time the loading of a single object, configure an HTTP Server test, instead.  HTTP Server tests are used to obtain the timings for targets such as multimedia files \(images, video or audio\), plain text, archive files or other files intended to be saved to storage rather than rendered in a browser.  Additionally, using an HTTP Server test benefits customers because HTTP Server tests have a lower cost in terms of [unit consumption](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmoKAC) than Page Load tests.

