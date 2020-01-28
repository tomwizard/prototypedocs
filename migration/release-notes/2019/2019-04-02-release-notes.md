# Release Notes: 2019-04-02

Welcome to today's release! We hope your April Fool's Day was full of positive pranks, serious stealthy silliness and healthy humor.

Some big changes afoot in the ThousandEyes app to tell you about, but first, a rundown of the latest, no-fooling-around news from the ThousandEyes blog.

Our VP of Marketing, Alex Henthorn-Iwane, has a very sensible post with the existential-sounding title of [What is BGP Visibility, Really?](https://blog.thousandeyes.com/what-is-bgp-visibility-really) that discusses the relevance of BGP to monitoring the digital experience you provide your customers. Not even a little bit silly.

In addition to the new blog article, we have a new and only slightly silly article in our Knowledge Base that may be of interest to anyone requesting support from our Customer Success team. The article, [Getting support from ThousandEyes](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes), lists the ways customers can contact ThousandEyes \(spoiler: contacting us by carrier pigeon is an AFD joke, if a [time](https://tools.ietf.org/html/rfc1149)-[honored](https://tools.ietf.org/html/rfc2549) [one](https://tools.ietf.org/html/rfc6214)\) and information that the team will request \(as well as some types of information that we will never request\) when opening a support case.

And now for the details of today's release...

## New Navigation Menus

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>The big news: we&apos;ve updated the main menus used to navigate in the
          ThousandEyes app, in order to improve user experience and accommodate future
          enhancements.</p>
        <p>We&apos;ve created a short <a href="https://www.thousandeyes.com/resources/new-navigation-menu-tutorial">video tutorial</a> on
          the benefits of the new menus. A link to this video will appear in the
          new menu for each user during their first login after the menu update,
          as seen in the image to the right.</p>
        <p>We also have a new <a href="https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGaVCAW_Navigating-our-new-menus">Knowledge Base article</a> that
          describes exactly where that page you need went. And of course, you can
          always contact Customer Success for assistance.</p>
      </th>
      <th style="text-align:left">IMAGE MISSING</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## Endpoint Agent Lite

Customers can now measure and troubleshoot their end users' experiences with their applications via a new version of Endpoint Agent. Endpoint Agent Lite provides monitoring of web apps but without the Browser Sessions functionality, which simplifies installation and configuration. This product is intended for service providers and other customers who do not require Browser Session information or have security/privacy requirements which prevent installing the full Endpoint Agent. The Agent installation packages can be downloaded from publicly shareable links.

Endpoint Agent Lite can be deployed on Mac OS X 10.9 \(Mavericks\) and later, and Windows 7 or later.

## Window size configuration \(mobile browser emulation\)

For browser-based tests \(Page Load and Transaction tests\) we have added the ability to configure the frame buffer size \(length and width, in pixels\) of the virtual browser, allowing the test to emulate phones and tables. The **Window Size** pull-down menu will display a list of common devices and their screen dimensions \(custom dimensions can also be specified\).

IMAGE MISSING

Selecting one of the Phone or Tablet devices will also permit clicking on the icons for portrait or landscape orientation, to swap the length and width values.

IMAGE MISSING

## Updating Tests

After a test is created, key settings in a Test's configuration can now be updated. The following table details what setting can now be changed after a test is created:

| Test Type\(s\) | Setting\(s\) |
| :--- | :--- |
| HTTP Server, Page Load | URL |
| FTP Server | Domain, Port, Relative Path |
| DNS Server, DNS Trace, DNSSEC | Domain |
| RTP Stream, Voice Call | Target Agent |
| SIP Server | SIP Server, Protocol, Port |
| Agent to Server | Target, Protocol, Port |

## API

Two additions to the API...

### Enterprise Agent clusters

Enterprise Agent clusters can now be created, modified and deleted through the API. Check our [API documentation](https://developer.thousandeyes.com/) for the [/add-to-cluster](https://developer.thousandeyes.com/v6/agents/#/agent-cluster-add) and [/remove-from-cluster](https://developer.thousandeyes.com/v6/agents/#/agent-cluster-remove) endpoints, including the new memberId field \(within the clusterMembers field\).

### Reports details

The creator user ID, last modified date and last modifier user ID of a report are now available from the /reports endpoint. Check out the [Report details](https://developer.thousandeyes.com/v6/reports/#/report-detail) section of the API Documentation for more information.

## Bug fixes & minor features

Here are the bug fixes and minor features in this week's release:

* The filter for Tests settings now contains a "Shared with" option to filter based on tests which are shared with a specified Account Group\(s\)
* Fixed an issue causing users who are in the registration process to be deleted
* Fixed a billing issue generating an incorrect "You have reached your usage limit" message which prevented test editing
* Fixed issues involving disabled or offline Enterprise Agents' contributions to usage and projected usage
* After clicking the sign-up link in a new user's activation email, a blank page is no longer seen when using Internet Explorer
* Removing a Private BGP monitor using the BGP Monitors page's Test selector no longer disables the test's BGP data collection 
* Editing Proxy Settings under certain conditions no longer produces an "Unable to process your request. Please try again later." error

## Questions and comments

Got feedback \(real or prank\) for us? Want to tell us how you feel about the new menus? [Send us an email](mailto:support@thousandeyes.com?subject=2019-04-02+Release+Update)!

