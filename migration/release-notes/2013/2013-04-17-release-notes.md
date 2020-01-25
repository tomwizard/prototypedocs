# Release Notes: 2013-04-17

As usual, our team has been burning the midnight oil bringing you some new and fun stuff!

## A test by any other name...

Since there's nothing basic about our HTTP Server test, we've changed its name from Basic HTTP to HTTP Server. Any label which included the term Basic HTTP has been updated to reflect the new name. We have added the API endpoints for the new server name, which are documented below:

```text
/tests/http-server.json
/alerts/http-server.json
```

These requests will return the same data as their legacy equivalent \(/tests/basic-http.json and /alerts/basic-http.json\). The by-test listing has also been updated, but the individual results are returned using an httpServer object, as opposed to a basicHttp object. The individual test listing can be found at the following URI:

```text
/web/http-server/{testId}.json
```

The legacy API entrypoints have been maintained, and will continue to operate for the next 30 days. Any API calls should be updated to reflect the new entrypoints.

## Interface grouping

Many customers use routers which contain multiple interfaces. Due to this, we've added a new feature to path visualization to allow users to create interface groups, to handle multiple interfaces on a single piece of physical hardware, such as a router with multiple interfaces. This allows users to simplify path visualization, and allowing paths to converge, allowing identification of a single device where applicable. This is the first iteration of the interface grouping.

With managed interfaces, the concept is very simple: create a grouping of IP addresses which are represented as a single node on a path visualization. This would allow us to converge three IP addresses into a single element on the path visualization.

IMAGE MISSING

When multiple interfaces are grouped together, they appear as a slightly larger version of a node in path visualization, and allow a simplified path visualization view, similar to the image below.

IMAGE MISSING

The interface grouping management can be turned on or off, by using the group interfaces feature, which is now checked by default. This can be found above the origin and endpoint complexity controls on the path visualization page. Click [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmiKAC) to view the article on working with the path visualization layout.

## Pass the SSH please

Our Virtual Appliance now supports SSH! This means it'll be easier to debug situations where the agent has network connectivity problems. Don't worry, it's safe; to enable SSH, you need to provide an SSHv2 public key, then log in with the passphrase used to generate the SSH key. To work with the SSH controls, simply open the "Appliance Access" tab of the page, copy in an SSH public key. Instructions for generating, adding and using the SSH key can be found at this [article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnrKAC).

IMAGE MISSING

## Agent connectivity notification

With this release, we have expanded agent connectivity notification: see this [article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cml2KAC) for details on managing agent alerts. When alerts are enabled, alerts will be generated on the following timeframe:

* 30 minutes after losing connectivity with the agent collector
* 2 days after losing connectivity with the agent collector
* 7 days after losing connectivity with the agent collector
* After connectivity has been restored to the agent collector
* If a clock offset of more than 1 minute from the time on the collector is detected

## A little help from my friends

<table>
  <thead>
    <tr>
      <th style="text-align:left">IMAGE MISSING</th>
      <th style="text-align:left">
        <p>We&apos;re changing the style of the help interface! Click the Help? icon
          in the lower right of any page in the interface to initiate an online chat
          session, view and interact with the community, or get helpful tips &amp;
          tricks based on the context you&apos;re in. We&apos;ve combined the contents
          of the page guide and help &amp; support icons.</p>
        <p>The page guide provides helpful information for navigating using interface
          hints.</p>
        <p>Live chat allows you to interact live with members of the ThousandEyes
          customer success team.</p>
        <p>Finally, direct links into the customer success center! This is the same
          as the former help button, but this will take you into the Customer Success
          Center. We&apos;ve also hand picked some relevant articles that may be
          useful to you, in your current view.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## A few minor enhancements

Of course, no release would be complete without some bug squashing and minor enhancements.

* "No routes" message - When you enter path visualization, a "no routes" method could appear under certain circumstances, while the path visualization data is rendered.  This has been replaced to show a message indicating that the visualization is being generated.
* Internet Explorer 10 - We have resolved several issues related to compatibility with Internet Explorer 10.
* Enterprise Agent map placement - under a strange series of circumstances, when multiple Enterprise Agents detect the same location and are later corrected, an agent could show up in the wrong part of the world map.  This has been corrected to ensure that these agents show in the correct location
* BGP data - beginning with this release, we will only retain BGP data for the trailing 14 days.

