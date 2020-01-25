# Release Notes: 2013-04-02

As always, we've been busy optimizing our code and adding new features to get you, our customer, what you're looking for.  Some of these updates have been highlighted below:

## ThousandEyes API learned a new language!

<table>
  <thead>
    <tr>
      <th style="text-align:left">IMAGE MISSING</th>
      <th style="text-align:left">
        <p>Our API now speaks JSON, do you?</p>
        <p>In order to simplify your code and reduce the amount of data being sent
          back to you on API calls, the ThousandEyes API can now respond in JSON
          format. For now, we&apos;ll continue outputting in XML format by default,
          but have made the JSON responses available to customers who wish to request
          it. The format and field content of a ThousandEyes API response will be
          identical to the XML-based response.</p>
        <p>To obtain JSON-formatted results, do one of three things:</p>
        <ol>
          <li>Add an accept: application/json header to your API request</li>
          <li>Include format=json argument to the request URI</li>
          <li>Append &apos;.json&apos; to your request (ie, https://api.thousandeyes.com/tests/basic-http.json)</li>
        </ol>
        <p>The legacy XML methods will remain in place (as the default) for the next
          month, at which time we will cut over to using JSON as the default. Once
          we move away from XML-based methods as a default, JSON will be returned
          for any API request. The ThousandEyes API documentation has been updated
          to reflect the combined XML and JSON responses.</p>
        <p>For those of you who wish to stick with XML, don&apos;t worry. Just append
          .xml to the URI (before the parameters), or pass a parameter &quot;format=xml&quot;
          along with the request, and we promise not to break anything.</p>
        <p>Read more on the ThousandEyes API at <a href="https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmo0KAC">this link</a>.</p>
        <p>We&apos;ve also updated the Nagios plugin code that was previously posted
          on our site, resolving some minor issues using the XML formatted methods.
          An update will be coming soon to provide the baseline plugin, compatible
          with JSON data.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>## ThousandEyes Virtual Appliance

We've added two new features to the ThousandEyes virtual appliance.  First, it will now automatically synchronize its clock with the pool.ntp.org group of servers.  This will prevent problems such as "Your agent's clock is X minutes behind", and some negative time errors shown as fixed below.  

## Alerts for agent connectivity

Beginning with this release, you will be notified when Enterprise Agents fail to contact the agent collector for 30 minutes.

## ThousandEyes SSL certificates updated

The app.thousandeyes.com and api.thousandeyes.com SSL certificates were updated with a new copy.  New certificates are valid through May 20, 2014, and are signed by GoDaddy.

## Bug Squashing

As usual, we've been doing housekeeping, lifting heavy furniture and and cleaning behind the appliances... and have found some bugs, which were squashed during the housekeeping process.

* Negative date intervals: in a case where the Enterprise Agent is running _ahead_ of our agent collector, certain circumstances could cause the date interval to show a negative number of minutes ago.  This has been corrected.
* BGP timeline: again, in a strange series of circumstances, the timeline didn't show the correct number of path changes.
* Path Visualization link delay: in some rare cases, link delays were shown with incorrect data.  This has been corrected.

## Join the community!

We're always looking for great ideas, and everybody has a question that needs to be answered.  In a lot of cases, you think you're asking a silly question.  Take it from me: I ask our senior developers and architects questions every day that I think are silly, but end up not being so bad.  Ask a question and get an answer!  We implemented our first community-requested feature in this release \(Origin and Next Hop alerts for BGP tests - see [here](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBqCAK_How-Alerts-work) for details\).  Provide a feature request and watch it get implemented!    
  
Everybody has a cool idea or two.  ServiceNow provided a baseline Nagios plugin which leverages the ThousandEyes API, and it's being used by other customers now as well.  If you've got something cool to share, please post it.  Each month, we'll send some free schwag to the most active members of our community.  Access the community forum [here](https://success.thousandeyes.com/PublicFeedItemContent).

