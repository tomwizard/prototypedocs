# Custom User-Agent strings in a Web test

The User-Agent string in an HTTP request header specifies the type of client which sent the HTTP request.  ThousandEyes Web layer tests send a default User-Agent string based on the test type, but you may instead configure a custom User-Agent string.

## Default User-Agent strings

By default, a ThousandEyes Web layer test \(HTTP Server, Page Load or Transaction test\) will send the following:**HTTP Server test**A ThousandEyes HTTP Server test will send a User-Agent string that is based on the curl program:

```text
User-Agent: curl/7.51.0-DEV
```

 **Page Load and Transaction tests**A ThousandEyes Page Load or Transaction test will send a User-Agent string associated with the Chrome browser:

```text
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36
```

The exact User-Agent string can change periodically, as ThousandEyes updates the components that run these test types. You can check the current values by displaying the test's request headers using the methods listed below.

## Custom User-Agent strings

Customers may wish to specify your own User-Agent string in a ThousandEyes Web test, rather than accept the default string. For example, an application may differentiate desktop from mobile clients via the User-Agent string and redirect those clients to content formatted for the appropriate display. A ThousandEyes Web test allows you to set a custom HTTP User-Agent string using the **User Agent** selector in the **HTTP Request** section, under the Advanced Settings tab of the test's configuration page.

IMAGE MISSING

The User Agent selector contains predefined User-Agent strings and a "Custom" option to enter your own.  Select "Custom" and a text box will appear beneath the selector to allow you to enter your custom User Agent string.

### Verification

You can verify the User-Agent string being sent by clicking on an Agent in the results table of the test's result's page.  For an HTTP Server test, click **Headers** link.  Under the **Request Headers** tab, you can see the User-Agent string that was sent.

IMAGE MISSING

For Page Load and Transaction tests, check the **Show HTTP headers in waterfalls box** in the Advanced Settings tab of the test configuration to enable HTTP header data for the test:

IMAGE MISSING

then click the Headers icon to the right of the Object name in the Waterfall tab of the results table.  The Headers icon appears when you mouse over the row belonging to the Object, between the Object's name and the Provider name.

IMAGE MISSING

## Additional Information

Additional information on identifying HTTP requests coming from ThousandEyes Agents can be found in the ThousandEyes Knowledge Base article [Identifying traffic from ThousandEyes Agents](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnyKAC).  User-Agent strings are often used by web analytics packages such as Google Analytics.  If you wish to filter out ThousandEyes HTTP Server test requests from your analytics, see this discussion on [Filtering Agent requests from Google Analytics](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnxKAC) for additional information.

For information about Web test settings, see the ThousandEyes Knowledge Base article [Working with Test settings](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC).

