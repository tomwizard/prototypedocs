# Release Notes: 2015-07-08

This week's release is chock full of updates, including a new user interface, and many other improvements.  Below, find a summary of these updates.

## ThousandEyes has a fresh new look

Last week, we sent out an email to users, indicating that a revised UI was about to be released. It's here, and we want to tell you a bit about it: Our primary goal was to improve the user experience of the main views within the product by unifying them in a single interface.  By doing this, the views now reload only the data necessary and fetch new data as soon it is available. The experience is snappier, the data is fresh and it’s easier to navigate around various metrics and layers. 

### Menus and Navigation

Starting with navigation, we've reorganized our menus and settings to make the options more prominent and easily accessible. The new menu, found on the left hand side of the page, can either be pinned to the left, or configured to auto-hide.  You'll find settings grouped at the bottom, with data at the top.

We've also reorganized the user menu, mini-dashboard icons and the help and support section into the top navigation bar. You'll now see your account group name in the upper right corner.  Click here to access account settings, to change your current account context, or to log out.

### Views

IMAGE MISSING

All of your test results can now be found in the Views menu item.

1. To open your test results, click Views, and select your test from the picker in the upper left of the page.  As you navigate between tests, the view you currently have selected will be maintained.
2. We've split each section of the views into a tab: where you'd have to scroll down in the legacy UI layout, you can now choose between seeing the world map, and the table of detailed results.  The currently selected tab will be indicated by a blue line underneath the tab name.
3. Changing context is now much easier. We've enhanced navigation between the various layers by showing which layers are available for each test. Click the view name to change context.

Refresh no more: Views will now seamlessly auto-refresh every 2 minutes.

We've also added an enhanced search interface to the Path Visualization and BGP Route Visualization interfaces. Using this interface, users can now search not only by network and country, but also by IP address, rDNS name, or network prefix.

IMAGE MISSING

### Dashboard and Reports

Our new dashboard incorporates a responsive design: it now takes up the full size of your browser window, auto-expanding widgets to take up the full width of the page.  The dashboard, along with Reports, is among the application's first pages to do so.

### Sharing and Saved Events

A save button for saving an event \(1\), and a share button \(2\) for sharing a snapshot are now at the top of the views page.

IMAGE MISSING

To control live sharing \(sharing either with another account in your organization \(1\), or with another ThousandEyes customer \(2\)\), go to Test settings and pick recipients from the sharing panel on the right hand side of the page.

IMAGE MISSING

### Getting Help & Support

If you're looking for help, don't worry: our team is here for you. Navigate to the question mark icon in the top navigation menu to access Help & Support. From the enhanced Page Guide, to the Customer Success center, we're working to provide you with all the resources you need.

IMAGE MISSING

If you need to engage our team to ask a question, just open a live chat and we'll be happy to assist.

## New cloud agent location

This week, we've added a new cloud agent in Cadiz, Spain.

This agent is immediately available to paying customers. Please note that access to these agents is not included in trial subscriptions.

## New features and improvements

### Reduced minimum testing interval

We now support using a 2-minute test interval for Voice, DNS Trace, DNS Server and DNSSEC tests.  Prior to the update, the minimum interval was 5 minutes on these test types.

### Single-sign-on settings

We've added the ability to test a service-provider initiated single-sign-on attempt to the Security & Authentication tab found in advanced settings. This will send a request to the configured identity provider and report back results.

### Adding new users

We've added better error logging when adding new users.  When attempting to add multiple users at once, if a user already exists in another account, an error message will indicate which user was unable to be added, and why.

IMAGE MISSING

### Custom virtual appliance

Users can now generate a custom virtual appliance with both a preseeded SSH key and the web server enabled. Prior to this release, these options were mutually exclusive.

## Questions and comments?

We really do love hearing from our users, especially after a big change like this. If you have any questions or comments, please [drop us a note](mailto:support@thousandeyes.com?subject=2015-07-08+Release+Comment).

