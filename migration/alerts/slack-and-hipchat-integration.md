# Slack and HipChat Integration

The ThousandEyes platform integrates with the popular messaging applications Slack and HipChat. When an Alert is raised, notification can be sent to a channel automatically.

## Slack Integration

In order to integrate ThousandEyes Alerts into Slack, you need to generate a webhook URL for your Slack channel as follows:

1. Sign into &lt;your-domain&gt;.slack.com  
2. Click the option to add an **Incoming Webhooks** integration \(https://my.slack.com/services/new/incoming-webhook/\)  
3. Choose a channel you want Alert notifications to be posted  
4. Get the Webhook URL from the integration settings.

From ThousandEyes, under **Alert Settings**, expand the Alert rule you wish to integrate into Slack, then click the **Notifications** tab. Click **Configure Integrations &gt; Add New Integration,** to open the below popup window. If you already have one or more integration services configured, click on **Edit Integrations &gt; Add New Integration**

IMAGE MISSING

1. **Type**: Choose your integration type.  
2. **Name**: Enter a name for your integration  
3. **URL**: Enter the channel Webhook URL \(per step 4 above\)  
4. **Channel**: Enter the channel name  
5. Add New Integration: Once all fields are  are finalized, click to add a new integration

A configured Slack integration example is shown below.

IMAGE MISSING

Now when an alert is triggered, the alert details will be posted as a message within the integrated channel, as shown below. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert start time.

IMAGE MISSING

If you have the "**Send an email when clears**" box checked, under the Alert Rule &gt; Notifications tab, and Alert Rule conditions are no longer met by your test \(or the Alert Rule is updated such that the conditions no longer meet the criteria of the alert\), the Alert Rule cleared message will be posted within your Slack channel. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert cleared time.

IMAGE MISSING

## HipChat Integration 

In order to integrate ThousandEyes Alerts into HipChat, you need to generate a URL and AuthToken for your HipChat room as follows:

1. Sign in to &lt;your\_domain&gt;.hipchat.com  
2. Navigate to https://&lt;your\_domain&gt;.hipchat.com/addons/  
3. Select a room, and click "Build your Own Integration"  
4. Enter a name for your integration and click Create  
5. Within the "Send messages to this room by posting to this URL" box, save the                                                                                                                 URL https://&lt;your\_domain&gt;.hipchat.com/v2/room/XXXXX/notification and the auth\_token=&lt;value&gt;

From ThousandEyes, under **Alert Settings**, expand the Alert rule you wish to integrate into HipChat, then click the **Notifications** tab. Click **Configure Integrations &gt; Add New Integration,** to open the below popup window. If you already have one or more integration services configured, click on **Edit Integrations &gt; Add New Integration**

IMAGE MISSING

1. **Type**: Choose your integration type.  
2. **Name**: Enter a name for your integration  
3. **URL**: Enter the HipChat room URL \(from step 5 above\)  
4. **Auth token**: Enter HipChat room auth\_token \(from step 5 above\)  
5. **Add New Integration**: Once all fields are  are finalized, click to add a new integration

A configured Hipchat integration example is shown below.

IMAGE MISSING

Now when an alert is triggered, alert details will be posted as a message within the integrated channel, as shown below. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert start time.

IMAGE MISSING

If you have the "**Send an email when clears**" box checked, under the Alert Rule &gt; Notifications tab, and Alert Rule conditions are no longer met by your test \(or the Alert Rule is updated such that the conditions no longer meet the criteria of the alert\), the Alert Rule cleared message will be posted within your HipChat room. Clicking on the Alert message link will open ThousandEyes Views webpage at the alert cleared time.

IMAGE MISSING

