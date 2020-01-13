# HipChat

In order to integrate ThousandEyes Alerts into HipChat, you need to generate a URL and AuthToken for your HipChat room as follows:

1. Sign in to &lt;your\_domain&gt;.hipchat.com  
2. Navigate to https://&lt;your\_domain&gt;.hipchat.com/addons/  
3. Select a room, and click "Build your Own Integration"  
4. Enter a name for your integration and click Create  
5. Within the "Send messages to this room by posting to this URL" box, save the                                                                                                                 URL https://&lt;your\_domain&gt;.hipchat.com/v2/room/XXXXX/notification and the auth\_token=&lt;value&gt;

From ThousandEyes, under **Alert Settings**, expand the Alert rule you wish to integrate into HipChat, then click the **Notifications** tab. Click **Configure Integrations &gt; Add New Integration,** to open the below popup window. If you already have one or more integration services configured, click on **Edit Integrations &gt; Add New Integration**

![HipChat.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka044000000CwMN&feoid=00NE0000006OT0r&refid=0EM44000000DY0O)

1. **Type**: Choose your integration type.  
2. **Name**: Enter a name for your integration  
3. **URL**: Enter the HipChat room URL \(from step 5 above\)  
4. **Auth token**: Enter HipChat room auth\_token \(from step 5 above\)  
5. **Add New Integration**: Once all fields are  are finalized, click to add a new integration

A configured Hipchat integration example is shown below.

![HipChat.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka044000000CwMN&feoid=00NE0000006OT0r&refid=0EM44000000DY0Q)

Now when an alert is triggered, alert details will be posted as a message within the integrated channel, as shown below. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert start time.

![hipchat\_alert\_triggered.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka044000000CwMN&feoid=00NE0000006OT0r&refid=0EM44000000DY0P)

If you have the "**Send an email when clears**" box checked, under the Alert Rule &gt; Notifications tab, and Alert Rule conditions are no longer met by your test \(or the Alert Rule is updated such that the conditions no longer meet the criteria of the alert\), the Alert Rule cleared message will be posted within your HipChat room. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert cleared time.

![hipchat\_alert\_cleared.png](https://success.thousandeyes.com/servlet/rtaImage?eid=ka044000000CwMN&feoid=00NE0000006OT0r&refid=0EM44000000DY0R)

