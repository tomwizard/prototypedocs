# Working with the Activity Log

The Activity Log provides a history of actions by the ThousandEyes users in your organization. Activity data is retained for 2 years.  The Activity Log is accessed from the **Activity Log** tab under the [Account Settings](https://app.thousandeyes.com/settings/account/?section=activityLog) menu. Events such as test creation, updates, deletions, login, logout, and other activities are tracked. Timeout events \(i.e. when a user's login session times out\) are not tracked by the Activity Log. Timestamp and User metadata are also displayed for each event.

## Activity Log

The following figure shows an example of what you might see when accessing the Activity Log:

IMAGE MISSING

There are three main components in this view:

1. [Activity Table]()
2. [Time Range Selector]()
3. [Filters]() 
4. [Download the Activity Log as a list]()

 The following sections provide details about each listed component.

### **1\)** **Activity Table**

For each event the following information is logged:

1. Timestamp in coordinated universal time \(UTC\)
2. Account Group in which the action was performed
3. User performing the activity
4. Event type
5. Component accessed by the User
6. Description of the event

The entries displayed in your view of the Activity Log depend on your role within the organization:

* Users having the Org Admin role will see activities from all users across all accounts in the organization.
* Users having the Account Admin role will see activities from users in your account only.
* If you are a Regular User, you will see a history of your logins and logouts.

### **2\) Time Range Selection**

The Time Range Selector allows you to set the period for which you wish to view events in the table. As can be seen in the following screenshot, there are quick selectors for the `Last 24 hours, Last 7 days, Last 1 month`, etc.

IMAGE MISSING

You may also select a specific range of time with the Custom Time Range box. The following screenshot shows the Custom Time Range:

IMAGE MISSING

Clicking inside the gray box under Custom Time Range \(1\) will display a dialog. You can select a range of time using the **From** and **To** fields. Once you have specified your desired range, click the **Apply** button to display the results.

### 3\) Filters

Filters allow you to select specify what information you wish to see in the Activity Log. The following filters are available:

* **Event Type** - The category of the logged activity, such as Administration, System, Operation, Exception, etc.
* **Component** - The module of the platform which was affected by the logged activity.
* **Account Group** - The Account Group from which the logged activity originated.
* **User** - The user who initiated the logged activity.
* **IP Address** - The IP address from which the logged activity originated.
* **Event** - Short description of the logged activity.

 When selected, each filter type will populate with selections which are available in the Activity Log for that particular filter:

IMAGE MISSING

As can be seen in the above screenshot, when selecting the **Event** filter type you will get a list of the available Events in the Activity Log. Selecting one of these Events will display only the Events in the Activity Log which meets these criteria. You can also add additional filters using the **Add a filter** link

**4\)**  **Download a the Activity Log as a list**

To export the Activity log as a listing, click the **Download** Button and select **Download as a CSV** file.

IMAGE MISSING

## Advanced Topics

### Using Filters on Specified Time Ranges

 When applying filters on specific time ranges, the filters are locked to that specific time range. Any additional filters added will continue to show results from the specified time range. If you change the time range, the filters will continue to show data from the previous time range you had selected. In order to show data which corresponds to your newly selected time range, you will need to remove and reapply all filters after the new time range has been selected.

### How Sign-On Settings Affect the Activity Log

If your organization has Single Sign-On enabled, this can affect how logout events are tracked by the Activity Log. Unless your organization has Single Logout configured through your SSO provider, logout events will not be tracked the Activity Log.

## Related Information

* [Role-based Access Control](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnLKAS_Role-Based-Access-Control-explained) discusses the model for user and user group management utilized by the ThousandEyes platform.
* [Working with Account settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnGKAS_Working-with-Account-settings) explains how to manage your own user account, security settings, contact information, and information about your organization.

