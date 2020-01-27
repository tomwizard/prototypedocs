# Release Notes: 2013-06-18

### Release update 2013-06-18

Tonight's release contains a few minor features, and some stability enhancements.  Check out the updates below.

## New Dashboard

We've converted our classic dashboard to a widget-based dashboard in tonight's release.  This new dashboard has several new features:

### New widget: All Tests

This is the same as the classic dashboard - lists each test, test type, alert status, trending and current values - just wrapped into a widget, rather than containing the entire dashboard page.  You'll also notice a gears icon, which appears when hovering over a test in the updated dashboard, for users with Account Admin privileges or higher.  As previously announced, the presence of the paperclip icon \(1\) beside a test name indicates a test shared by live share.  Click the gears icon \(2\) to jump to test settings, and edit the settings for that particular test.

IMAGE MISSING

### New widget: Enterprise Agent routes

This feature generates data used by the agent reference metrics data, released last week.  With the Enterprise Agent routes widget, you'll now see a path from each Enterprise Agent to the primary ThousandEyes agent collector for your account.  You'll see the very familiar path visualization view, for each agent testing connectivity to the primary agent collector, along with a summary of currently configured agents.  An example of the Enterprise Agent routes data is shown below.  Notice that this shows notification that one of my Enterprise Agents is offline.

IMAGE MISSING

### Dashboard configuration

The Dashboard Settings link, found on the upper right corner of the page, where the "Share this Screen" option normally sits, allows you to configure which components should be included on the dashboard.  Click the link \(1\) to expand a menu and choose the widgets you want included in the dashboard display \(2\).

IMAGE MISSING

In the near future, each widget will be configurable, and will show a link in the upper right corner of the widget to allow configuration of the widget's settings.

IMAGE MISSING

## API updates

We've made two minor revisions to the write methods to the ThousandEyes API, first announced in the [June 11, 2013 update](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmm4KAC):

### Response codes

* any successful _**new**_ request will now receive an HTTP/201 CREATED response.
* any successful _**delete**_ ****request will now receive an HTTP/204 NO CONTENT response.

### JSON structure change for network tests

The test structure for network tests now reflects a separate field for port number, in order to allow IPv6 addresses to be used in the server field.  The field is named port, and accepts integer responses.  The default for a network test is port 80.

Was:

```text
{
 "test": [
  {
     "enabled":1,
     "testName":"API network test addition for www.thousandeyes.com",
     "interval":300,
     "server":"www.thousandeyes.com:80",
     "agents":[]
   }
 ]
}
```

Changed to:

```text
{
 "test": [
  {
     "enabled":1,
     "testName":"API network test addition for www.thousandeyes.com",
     "interval":300,
     "server":"www.thousandeyes.com",
     "port":80,
     "agents":[]
   }
 ]
}
```

