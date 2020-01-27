# Release Notes: 2014-03-19

### Release update 2014-03-19

As we near the end of March, check out some of the updates our team has been working on over the past couple of weeks.  Just a quick note: we'll be releasing next week as well, in order to get some critical components released before end of quarter.  Remember to check out ThousandEyes Operations on Twitter [@thousandeyesOps](http://www.twitter.com/thousandEyesOps) for maintenance updates.

## DNS Server tests now support recursion

We've updated our DNS Server tests to allow users to target non-authoritative DNS servers.  This feature was introduced for organizations to target internal DNS servers, in the event that they are experiencing problems resolving requests.  This effectively updates the dig equivalent from:

```text
dig <domainname> <recordtype> @<server> +norec
```

to 

```text
dig <domainname> <recordtype> @<server>
```

To target a non-authoritative server, simply check the _Send recursive queries_ checkbox when creating a new test, otherwise the test will fail.

IMAGE MISSING

## Dashboard Updates

A few productivity-driving updates for our dashboard consumers this week:

### Tests widget: Exclude filter

We've updated our Tests widget to allow users to exclude certain tests from a list.   When configuring your Tests widget, be sure to remember that criteria are ANDed together, which means that the test must meet both the inclusion and exclusion filter, in order to be included.

IMAGE MISSING

### Alert Grid: link to alerts page

Our alert grid's summary \(shown at the bottom, X tests alerting in the last 24 hours\) will now link to the main alerts page, as a shortcut for users wishing to open the alerts interface.  You can still click through an individual alert cell, to be taken to the test \(and agent\) where the alert first triggered.

IMAGE MISSING

## Path Visualization

We've added more information, and quick selection options into the Path Visualization interface, to allow users to see TCP MSS and Minimum Path MTU values for each agent's path to the target.  The availability of this information is controlled by the _Enable MTU measurements_ checkbox, found under the Network test options in the Test Settings interface.  Hover over an agent to show information about the Agent, including the Minimum Path MTU and TCP MSS values for that agent's connection to the target \(shown in the bottom right of the pop-up\)

IMAGE MISSING

In addition to the availability of these values, our system will now alert when TCP MSS is configured for abnormal values.  Our CTO, Ricardo Oliveira, published a blog entry this morning, which walks through [Troubleshooting Path MTU and TCP MSS problems,](http://blog.thousandeyes.com/troubleshooting-path-mtu-tcp-mss-problems/) explaining the feature in more depth.

## Agent notification emails

In an attempt to reduce the number of agent communication email notifications, our team has updated our notification system to In the event that your agents are unable to contact their specified agent collector.  Emails will be aggregated into a single notification, for agents losing connectivity within the same 5-minute window.  We've also updated some of our internal nightly maintenance processes, which were causing agent communication failure notifications to be sent around 11pm PT on certain nights.  We'll be watching agent communication emails closely over the coming few weeks, to continue tuning the processes which cause the checkin failures.

## API

Two significant releases on the ThousandEyes API for this release.  First, we've added the ability to show request and response headers on HTTP server test responses.  This information can be accessed by appending a headers=1 parameter to an http-server request.  We've also resolved an issue with the generic /alerts endpoint, which could result \(in certain circumstances\) in transaction alerts not being shown in the response.  

This information is also included in the HTTP Server view, when clicking on the headers link.

IMAGE MISSING

Check out our [Developer Reference site](http://developer.thousandeyes.com/) for more information on API updates.

## Live Sharing update

A quick update to our live sharing interface, for Organization Admin users.  Tests shared by users with Organization Admin privileges with another account inside the same Organization, will now be automatically accepted \(and exempted from the email acceptance process\) into the target account inside their organization.  Prior to this update, all live shares required approval, even those shared within the same organization, by a user with administrative control over multiple accounts.

