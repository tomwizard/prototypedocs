# How to generate a HAR file

Occasionally, we encounter a site that doesn't load the waterfall view in page load very nicely.  This won't happen often, but when it does, it's important that we obtain diagnostic information so that we can resolve the issue, and make your interaction with the ThousandEyes platform as enjoyable and seamless as possible.

When this happens, and the interaction is with a site behind your own firewall, we may request that you generate a HAR file of your interaction with the site; this is easiest done in either Firefox or Chrome.  Instructions are below for each platform:

## Using Firefox

In Firefox, you'll need to use the Firebug plugin to export a HAR file.  Installation and usage instructions can be found below:

### Installation of plugins

First, download firebug.  Firebug can be downloaded by using the Tools menu &gt; Add-ons browser, and searching for Firebug, or by browsing to https://getfirebug.com.  After installing the plugin, you will need to enable it.

Next, download the NetExport plugin.  This is available at the following URL: https://getfirebug.com/releases/netexport/.  After downloading the .xpi file, you will need to enable the plugin, and restart your browser.

Once the plugins are installed, you will likely need to restart your browser.

### Generating a HAR file

Once the browser is restarted, click the firebug icon in the upper right hand corner of the browser to enable the plugin.  The firebug panel will open \(by default, in the bottom of your browser\).  Click the Net tab, and open the website you wish to profile.  If you need to enter any authentication information, please do so in order to open the site.  The example below shows google.com being accessed.

IMAGE MISSING

Once the page finishes loading, in the Firebug UI, click the Net tab, and then click the Export button, and click Save As... this will allow you to save a .HAR file for the interaction with this site.  The resulting HAR file should then be emailed to support@thousandeyes.com for analysis.  An example of the .HAR file's contents are attached, \(www.google.com.har-firefox\) for interaction with www.google.com.

If the Export button is not shown while the Net tab is selected, this is an indication that the NetExport plugin has not been installed.

## Using Chrome

Using Chrome, you'll be leveraging the developer tools built into the browser to export a timeline.  No additional plugins are required.  

### Generating a HAR file

From the Chrome Menu, click tools &gt; developer tools.  This will either launch the developer tools in a separate window, or be docked at the bottom of your browser page.  Clicking the  icon in the lower corner of the developer tools window will toggle the behavior of the developer tools window \(dock / pop out\).  Next, click the Network tab, then click the black circle in the toolbar at the bottom of the window.  This will start recording a page load, and will change the black circle into a red circle.  Open the website you wish to record, and enter any authentication information that is required.  Once complete, click the record button again, and the recording will stop.  Once the recording is complete, right-click anywhere in the developer console and select "Save as HAR with Content"\).  This will create a HAR file in the location you specify.  As with the Firefox example above, an example of www.google.com is shown below. 

IMAGE MISSING

An example HAR file \(www.google.com.har-chrome\) is attached showing the content of this exported HAR.

If you have any questions regarding how this information is being used, or how to generate the content, please contact support@thousandeyes.com.

