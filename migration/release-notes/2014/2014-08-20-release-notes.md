# Release Notes: 2014-08-20

As our summer draws to a close, and the kids head back to school, we start to show off some of the impressive work our teams have been working on over the course of the summer. Below, find a few pointers to the things that have held our interest over this summer of 2014.

## Voice tests \(beta\)

Have you ever wondered why the quality of your VoIP service sounds so poor?  So have we.  We've expanded our testing capabilities to include unidirectional UDP+RTP tests, to be used for measuring the quality of voice services.  With Voice tests, you get standard VoIP metrics, including Loss, packet delay variation, and MOS scores, as well as the same X-layer capabilities \(Path Visualization, and BGP Visualization\) you've come to know and love.  Check out these articles for more details:

* [Voice tests overview](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmlKAC)
* [Using the Voice Metrics View](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmkKAC)
* [CLI Network Troubleshooting Utilities](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmoAKAS)

Our Voice testing capability is currently provided for existing under our Beta program, and will be further announced upon its exit from Beta. If you are interested in participating in our Beta program, [contact our Customer Success team](mailto:support@thousandeyes.com?subject=Voice%20Beta%20Request).

## HTTP Server test metrics: Throughput

We've updated the HTTP server test metrics available for selection in the interface. Prior to this change, the available metrics were Availability, Response time, and Fetch time. We have replaced the Fetch Time metric with Throughput, since this metric is more relevant for customers attempting to access larger objects.

IMAGE MISSING

Both Fetch Time and Throughput are still shown and available in the detailed metrics shown below the world map, as well as using the ThousandEyes API. It is important to note that Throughput metrics may in some circumstances not show a value; this may include instances where the target is so small that the receive time is insignificant. If you have a test configured for a target which shows this behavior, and throughput is an important metric for your use case, please [contact our Customer Success team](mailto:support@thousandeyes.com?subject=missing%20Throughput%20metric).

## Multi-homed agent connectivity

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>We&apos;ve been slowly changing the way that our Enterprise agents communicate
          with targets, in order to increase the ways that customers can leverage
          our agents. You can now configure a ThousandEyes agent to be attached to
          multiple networks, such that it can test targets in a private network,
          and communicate with ThousandEyes through another network connection. The
          only test type that does not support this capability is the Voice test,
          which requires that the Voice server be bound to a specific IP address.</p>
        <p>Prior to this change, the agent was bound to a specific IP address. Since
          this change has gone into effect, the agent now chooses the appropriate
          adapter to use, based on the routing tables of the agent.</p>
        <p>In the scenario shown in the inset image, the Enterprise agent has two
          network connections - one bound to the public internet, and one bound to
          the internal network, which is unreachable via the internet. The agent,
          configured to test a 10.0.0.x target, will now choose the second network
          adapter, and route the traffic targeted at the server, then collect its
          results, and communicate with the ThousandEyes agent collector over the
          interface bound to the Internet.</p>
      </th>
      <th style="text-align:left">IMAGE MISSING</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## CLI utilities

Our command line interface utilities have been updated, by removing the requirement to specify an interface or source IP address while testing. Check out this [document](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmoAKAS) on using our CLI utilities for troubleshooting.

## API changes

We've added the ability to update transaction tests via the API, as well as added alertRule data to the detailed tests endpoints \(/tests/{testId}\).  Check out the [ThousandEyes Developer Reference site](http://developer.thousandeyes.com/) for more details.

We've also updated our Developer reference site to show version-specific endpoint data, and changed our support policy for API versioning moving forward. The new versioning support policy states:

Support for the current and prior version of the ThousandEyes API will be provided at all times. Attempts to access the ThousandEyes API with no version specified will result in the current version being used. Attempts to access a deprecated version of the API will result in a response from the oldest supported version of the API.

New versions of the API will be released with a notification made available on our Developer reference site, and will be available using a version-specific endpoint call for a period of 90 days. After this 90-day period, the new version of the API will become the current version, and the oldest version of the API will be deprecated.

This means that the following timeline applies:

* Upon release of new API version v\(X\), for first 90 days:
  * Current version: v\(X-1\)
  * Supported versions: v\(X-2\)-v\(X\)
* After 90 days post-release of new API version:
  * Current version: v\(X\)
  * Supported versions: v\(X-1\)-v\(X\)

This versioning policy goes into effect upon release of version 5 of the ThousandEyes API, anticipated for release during Q4 of 2014.  Until this time, our existing version support policy is in place, supporting current plus 2 prior versions.

