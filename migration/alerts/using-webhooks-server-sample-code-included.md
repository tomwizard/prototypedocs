# Using Webhooks \(server sample code included\)

The ThousandEyes platform supports Webhooks as a notification mechanism when an Alert is raised. A **Webhook** is a user-defined HTTP callback \([Wikipedia](https://en.wikipedia.org/wiki/Webhook)\).  ThousandEyes makes POST requests in the event of an alerting event to a user-configured endpoint.

With this data, users can create a customized workflow for the handling of alerting events.  You'll now be able to do fun things with the alert, from submitting a request to your ticket management system, to sending customized emails, to posting into a group chat system, such as Slack.

In this Knowledge Base article, we'll describe the configuration of Alerts to use Webhooks. Additionally, for those unfamiliar with Webhooks or who will benefit from constructing a quick example, we provide information to [set up a test web service]() using [Heroku](https://www.heroku.com/).  For reference, we've also included [example POST body data]() at the end of this article.

## Configuring Webhook notifications

To configure notifications to a Webhook server, you'll need to define a Webhook in the Alert Rules interface \([Alerts &gt; Alert Rules](https://app.thousandeyes.com/settings/alerts/?tab=CloudAndEnterpriseAgent)\). Expand an Alert Rule and select the **Notifications** tab. Under the **Webhooks** section, click the **Configure Webhooks** link. If you already have configured Webhooks, click the **Edit webhooks** link:

IMAGE MISSING

Click the **Add New Webhook** link, then complete the New Webhook dialog:

IMAGE MISSING

Enter the **Name** of your Webhook, and the target **URL** \(note that HTTP redirects are not accepted, so be sure to provide the final URL\). Configure required [Authentication]() if required and click **Test** to check your configuration:

IMAGE MISSING  
**NOTE: Encoded HTML URLs are currently not supported for Webhook configuration, please enter the URL in decoded form.**

If the test succeeds, a Webhook test completed successfully message will be displayed:

IMAGE MISSING

Once you have tested your Webhook server successfully, click the **Add New Webhook** button, and select your Webhook from the list of configured Webhooks. 

## Webhook Authentication

 The Webhooks interface supports the use of [Token](), [OAuth]() and [Basic HTTP Authentication](). This is an optional configuration step and can be configured for a Webhook service if the target server requires authentication.

### Basic

A **Username** and ****corresponding **Password** are necessary to configure Basic HTTP Authentication:

IMAGE MISSING

### Token

 The Token Auth Type uses a **Bearer Token** to authenticate with the Webhook server:

IMAGE MISSING

### OAuth 

#### Webhook server-side configuration 

Create a new OAuth endpoint for ThousandEyes Alerts with [https://app.thousandeyes.com/webhooks-oauth-callback/](https://app.thousandeyes.com/webhooks-oauth-callback/) as **redirect/call back** URL. Grab the newly created **Client ID** and Authorization Endpoint URL \(**Auth URL**\) for Webhook server to configure ThousandEyes side authentication. Below is an example Client OAuth configuration from ServiceNow: 

IMAGE MISSING

**NOTICE:** Ensure token has a sufficient lifespan to avoid manual regeneration on timeout.

#### ThousandEyes-side configuration 

 Configure the Webhook **Name** and **URL** as explained in [Configuring Webhook notifications]() section. Click **OAuth** in **Auth Type.** Fill out the **Auth URL** and **Client ID** as per [Webhook server-side configuration]() section above. Click **Get Token**:

IMAGE MISSING

  
A new tab will be opened requesting for a consent to authorize ThousandEyes. Below is a snippet from ServiceNow application which we are using in this guide as an example:

IMAGE MISSING  
Once the authorization is complete, a Token retrieved successfully message will be displayed, as shown in the following figure:

IMAGE MISSING

  
Now click the **Test** button to verify operability of your new Webhook:

IMAGE MISSING

## Setting up a Webhook server

If you visit [Heroku](https://www.heroku.com/), you can deploy a free web application to demonstrate the behavior.  We'll deploy a simple web service that accepts posts in JSON format, to show what requests from ThousandEyes look like.  If you're new to either node.js, or to Heroku, it's worth running through their instructional tutorials to understand how the deployment process works.

Follow these instructions to deploy a simple version of your web service.

1. Install the Heroku command line interface \(CLI\)  Go to https://devcenter.heroku.com/articles/getting-started-with-nodejs\#set-up, and follow the instructions to download the Heroku CLI for your operating system.   
2. Clone the simple-webhook-server repository and move to the directory created

   ```text
   $ git clone https://github.com/thousandeyes/simple-webhook-server.git
   Cloning into 'simple-webhook-server'...
   remote: Counting objects: 26, done.
   remote: Total 26 (delta 0), reused 0 (delta 0), pack-reused 26
   Unpacking objects: 100% (26/26), done.

   $ cd simple-webhook-server

   ```

3. Create a Heroku remote in your git repository

   ```text
   $ heroku create
   Creating app... done, vast-shore-1766
   https://vast-shore-1766.herokuapp.com/ | https://git.heroku.com/vast-shore-1766.git

   ```

4. Push your content to the Heroku remote.  This will build the application.

   ```text
   $ git push heroku master
   Counting objects: 12, done.
   Delta compression using up to 4 threads.
   Compressing objects: 100% (9/9), done.
   Writing objects: 100% (12/12), 3.31 KiB | 0 bytes/s, done.
   Total 12 (delta 0), reused 0 (delta 0)
   remote: Compressing source files... done.
   remote: Building source:
   remote:
   remote: -----> Node.js app detected
   remote:
   remote:        PRO TIP: Specify a node version in package.json
   remote:        See https://devcenter.heroku.com/articles/nodejs-support
   remote:
   remote: -----> Defaulting to latest stable node: 0.10.33
   remote: -----> Downloading and installing node
   remote: -----> Exporting config vars to environment
   remote: -----> Installing dependencies
   remote:        npm WARN package.json webhook-server@0.1.0 No repository field.
   remote:        body-parser@1.0.2 node_modules/body-parser
   remote:        ├── qs@0.6.6
   remote:        ├── raw-body@1.1.7 (string_decoder@0.10.31, bytes@1.0.0)
   remote:        └── type-is@1.1.0 (mime@1.2.11)
   remote:
   remote:        express@4.10.2 node_modules/express
   remote:        ├── merge-descriptors@0.0.2
   remote:        ├── utils-merge@1.0.0
   remote:        ├── fresh@0.2.4
   remote:        ├── cookie@0.1.2
   remote:        ├── escape-html@1.0.1
   remote:        ├── range-parser@1.0.2
   remote:        ├── cookie-signature@1.0.5
   remote:        ├── finalhandler@0.3.2
   remote:        ├── vary@1.0.0
   remote:        ├── media-typer@0.3.0
   remote:        ├── methods@1.1.0
   remote:        ├── parseurl@1.3.0
   remote:        ├── serve-static@1.7.1
   remote:        ├── content-disposition@0.5.0
   remote:        ├── path-to-regexp@0.1.3
   remote:        ├── depd@1.0.0
   remote:        ├── qs@2.3.2
   remote:        ├── on-finished@2.1.1 (ee-first@1.1.0)
   remote:        ├── proxy-addr@1.0.3 (forwarded@0.1.0, ipaddr.js@0.1.3)
   remote:        ├── etag@1.5.0 (crc@3.0.0)
   remote:        ├── debug@2.1.0 (ms@0.6.2)
   remote:        ├── send@0.10.1 (destroy@1.0.3, ms@0.6.2, mime@1.2.11)
   remote:        ├── accepts@1.1.3 (negotiator@0.4.9, mime-types@2.0.3)
   remote:        └── type-is@1.5.3 (mime-types@2.0.3)
   remote: -----> Caching node_modules directory for future builds
   remote: -----> Cleaning up node-gyp and npm artifacts
   remote: -----> No Procfile found; Adding npm start to new Procfile
   remote: -----> Building runtime environment
   remote: -----> Discovering process types
   remote:        Procfile declares types -> web
   remote:
   remote: -----> Compressing... done, 5.7MB
   remote: -----> Launching... done, v3
   remote:        https://vast-shore-1766.herokuapp.com/ deployed to Heroku
   remote:
   remote: Verifying deploy... done.
   To https://git.heroku.com/vast-shore-1766.git
    * [new branch]      master -> master

   ```

5. Open the site to confirm the target location.  This will open a web browser in the context of your Heroku application.

   ```text
   $ heroku open

   ```

6. Open a console to review the logs of the target server.  In this window, you'll see POST requests hitting your server.

   ```text
   $ heroku logs --tail
   2014-11-11T20:33:42.767724+00:00 heroku[api]: Deploy e5d1a07 by dave@thousandeyes.com
   2014-11-11T20:33:42.767753+00:00 heroku[api]: Release v15 created by dave@thousandeyes.com
   2014-11-11T20:33:43.724332+00:00 heroku[web.1]: State changed from up to starting
   2014-11-11T20:33:46.814245+00:00 heroku[web.1]: Starting process with command `node webhook-server.js`
   2014-11-11T20:33:50.439787+00:00 heroku[web.1]: State changed from starting to up
   2014-11-11T20:33:50.347118+00:00 app[web.1]: Webhook Server started... port: 30490
   2014-11-11T20:33:59.586785+00:00 heroku[router]: at=info method=GET path="/" host=sleepy-mesa-2108.herokuapp.com request_id=228650f8-d810-477e-858b-b61235766260 fwd="54.90.223.146" dyno=web.1 connect=2ms service=10ms status=200 bytes=266
   ```

## Webhook POST content

Webhooks use events to signify activity. Our system is configured today to support the following types of events:

* **WEBHOOK\_TEST** - sent when a user clicks the Test Webhook link in ThousandEyes Webhook configuration.
* **ALERT\_NOTIFICATION\_TRIGGER** - sent when an alert is triggered
* **ALERT\_NOTIFICATION\_CLEAR** - sent when an alert is cleared, the alert rule is deleted, or the alert rule is removed from a test while in an active alerting status.
* **AGENT\_ALERT\_NOTIFICATION\_TRIGGER** - sent when an agent notification triggers - may be related to clock offset, version number, or agent online status
* **AGENT\_ALERT\_NOTIFICATION\_CLEAR** - sent when the agent notification clears

Note: All `eventIds` are unique. To correlate two events \(for example, an alert trigger and clear,\) reference the `alertId`, which is unique per generated alert.

##  Sample Webhook event payloads

Each event type shown below contains a sample JSON payload, which is posted to the target server.  The Alert notification data corresponds to alerting data from the ThousandEyes API, wrapped in an event wrapper.  See the [ThousandEyes Developer Reference site](http://developer.thousandeyes.com/v4/alerts/#/alertdetail) for more information on data returned via the API.

#### WEBHOOK\_TEST

```text
{  
   "eventType":"WEBHOOK_TEST",
   "eventId":"1415733887743"
}
```

#### ALERT\_NOTIFICATION\_TRIGGER

```text
{  
   "eventType":"ALERT_NOTIFICATION_TRIGGER",
   "eventId":"49-35541",
   "alert":{  
      "ruleId":173,
      "alertId":35541,
      "testId":5370,
      "testName":"http://www.thousandeyes111.com",
      "ruleExpression":"Page Load is incomplete",
      "dateStart":"2014-08-24 01:01:47",
      "violationCount":2,
      "ruleName":"Default Page Load Alert Rule",
      "agents":[  
         {  
            "dateStart":"2014-08-24 01:01:47",
            "active":1,
            "metricsAtStart":"Page load: Incomplete",
            "metricsAtEnd":"Page Load: Incomplete",
            "agentId":108,
            "agentName":"Boston, MA",
            "locationName":"Boston, MA",
            "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541&agentId=108"
         },
         {  
            "dateStart":"2014-08-24 01:00:51",
            "active":1,
            "metricsAtStart":"Page load: Incomplete",
            "metricsAtEnd":"Page Load: Incomplete",
            "agentId":107,
            "agentName":"Vancouver, Canada",
            "locationName":"Vancouver, Canada",
            "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541&agentId=107"
         }
      ],
      "type":"Page Load",
      "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541",
      "apiLinks":[  
         {  
            "rel":"related",
            "href":"http://api.thousandeyes.com/tests/5370"
         },
         {  
            "rel":"data",
            "href":"http://api.thousandeyes.com/web/page-load/5370"
         }
      ]
   }
}
```

#### ALERT\_NOTIFICATION\_CLEAR

```text
{  
   "eventType":"ALERT_NOTIFICATION_CLEAR",
   "eventId":"49-35546",
   "alert":{  
      "ruleId":173,
      "alertId":35541,
      "testId":5370,
      "testName":"http://www.thousandeyes111.com",
      "ruleExpression":"Page Load is incomplete",
      "dateStart":"2014-08-24 01:01:47",
      "dateEnd":"2014-08-24 01:09:51",
      "violationCount":2,
      "ruleName":"Default Page Load Alert Rule",
      "agents":[  
         {  
            "dateStart":"2014-08-24 01:01:47",
            "dateEnd":"2014-08-24 01:09:47",
            "active":0,
            "metricsAtStart":"Page load: Incomplete",
            "metricsAtEnd":"Page Load: Complete",
            "agentId":108,
            "agentName":"Boston, MA",
            "locationName":"Boston, MA",
            "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541&agentId=108"
         },
         {  
            "dateStart":"2014-08-24 01:01:51",
            "dateEnd":"2014-08-24 01:09:51",
            "active":0,
            "metricsAtStart":"Page load: Incomplete",
            "metricsAtEnd":"Page Load: Complete",
            "agentId":107,
            "agentName":"Vancouver, Canada",
            "locationName":"Vancouver, Canada",
            "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541&agentId=107"
         }
      ],
      "type":"Page Load",
      "permalink":"https://app.thousandeyes.com/alerts/list?__a=11&alertId=35541",
      "apiLinks":[  
         {  
            "rel":"related",
            "href":"http://api.thousandeyes.com/tests/5370"
         },
         {  
            "rel":"data",
            "href":"http://api.thousandeyes.com/web/page-load/5370"
         }
      ]
   }
}
```

#### AGENT\_ALERT\_NOTIFICATION\_TRIGGER

```text
{
    "eventType":"AGENT_ALERT_NOTIFICATION_TRIGGER",
    "eventId":"164522-5744505",
    "agentAlert":{
        "agentRuleId":43587,
        "agentNotificationId":5744505,
        "agentId":25694,
        "hostname":"TE-AGENT1.local.lan",
        "agentName":"Packet1",
        "ipAddress":"147.75.199.171",
        "active":1,
        "ruleExpression":"Clock Offset ≤ 60 seconds",
        "ruleName":"Default Agent Clock Offset Notification",
        "dateStart":1476987748,
        "metricsAtStart":"Clock Offset: 20 seconds",
        "metricsAtEnd":""
    }
}
```

#### AGENT\_ALERT\_NOTIFICATION\_CLEAR

```text
{
    "eventType":"AGENT_ALERT_NOTIFICATION_CLEAR",
    "eventId":"164534-5003852",
    "agentAlert":{
        "agentRuleId":43587,
        "agentNotificationId":5003852,
        "agentId":13558,
        "hostname":"cluster-agent2",
        "agentName":"cluster-agent2",
        "ipAddress":"10.100.20.110",
        "active":0,
        "ruleExpression":"Clock Offset ≤ 60 seconds",
        "ruleName":"Default Agent Clock Offset Notification",
        "dateStart":1467175574,
        "dateEnd":1476987748,
        "metricsAtStart":"Clock Offset: 130 seconds",
        "metricsAtEnd":"Clock Offset: 130 seconds"
    }
}
```

##  Firewall exception requirements

If your web server only allows requests from whitelisted senders, you will need to whitelist requests from ThousandEyes web servers, which come from the network 192.150.160.0/24.

## Related Articles

* The [How Alerts Work](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work-1476477151762) article is a detailed guide to ThousandEyes Alerts.
* For a guide on creating your own Alert rules consult the [Creating and editing Alert Rules](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmhKAC_Creating-and-editing-Alert-Rules) article.

