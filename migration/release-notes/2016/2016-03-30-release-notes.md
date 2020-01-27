# Release Notes: 2016-03-30

This release covers two major feature releases that our team has been working on for the last little while.  Let's get right to it!

## Docker support for enterprise agents

<table>
  <thead>
    <tr>
      <th style="text-align:left">IMAGE MISSING</th>
      <th style="text-align:left">
        <p>We&apos;re making a whale of a splash with Docker support for Enterprise
          Agents in this release.</p>
        <p>As part of our efforts to increase deployment options for Enterprise Agents,
          we will now support installation using Docker containers. Over the past
          months, our own operations team has been using Docker as a way to deploy
          agents in a low cost, resource efficient and easily automated manner. We
          will publishing a blog post of our experiences using Docker in the coming
          days, so be sure to keep an eye on the <a href="https://blog.thousandeyes.com/">ThousandEyes Blog</a> for
          updates!</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>If you're running a version of Linux that our agent doesn't natively support, fret not!  The Docker container-based approach will allow you to deploy an agent, using an Ubuntu-based container which is maintained and updated by the team at ThousandEyes, onto pretty much any supported server.  This means that it's literally minutes to deploy anything from 1 to dozens of enterprise agents.  Just download an image from the ThousandEyes repository on dockerHub, and start it!  

We've created an installation and deployment guide for installation of the enterprise agent container, located [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnXKAS).  Let us know if you have any questions, and we'll be happy to answer.

## Embedded report widgets

A request that we often receive from customers is on how to optimize the view of our report and dashboard widgets for large screens in network operations centers or external websites.  We've taken these requests to heart and introduced the ability to take our report widgets and embed them in these locations.  The new embeddded widget capability allows users to take a widget with a predetermined set of filters, provide a date scope, and then embed it on an external site.  This site can then be used by ThousandEyes and non-ThousandEyes users alike, to view the trends on test targets, filtered and aggregated as desired.  In fact, we've embedded a widget just below, covering the fetch time for http://cnn.com, broken down by component timing.

For more information on managing report widget embedding, check out [this article on Embedding widgets externally](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnUKAS).

This capability is being launched initially for Report widgets, however we'll be introducing support for dashboard widgets in due course.  Keep an eye on this channel for updates, and let us know if you're interested in doing the same for Dashboard widgets.

##  Groups support in API

We've added group support to versions 5 and higher of the ThousandEyes API.  Check out the [API change summary](http://developer.thousandeyes.com/#/changesummary) on our developer reference site for more details.

## Bugs squashed

As usual, we've identified and corrected a requisite number of bugs.  A summary list can be found below:

* Certain users had experienced problems while attempting to delete dashboard widgets using the context menu found on the widget in custom dashboards.  This has been corrected.
* Snapshot shares created from saved events will now be scoped to contain the entire saved event.  Prior to this release, it was possible to create a snapshot that only contained partial data from a saved event.
* We've corrected a problem that caused Agent to Agent tests to show an incorrect target IP address in the dashboard.
* Users are no longer able to associate cloud agents with Agent to Agent tests via the Settings &gt; Cloud Agents page.  This capability will be restored when the agent to agent tests feature is made generally available.
* We've corrected a problem that inadvertently allowed alerts to be triggered during a continuously repeating alert suppression window.  Prior to this release, if a test's data met alerting conditions while on the occurred on a boundary of a repeating 24 hour window, it was possible for an alert to be triggered despite the alert suppression window coverage.
* We've optimized our cloud agents for DNSSEC testing.  Prior to this release, it was possible to obtain false negative results for DNSSEC validity of a particular record if the agent was running a large number of DNSSEC tests.

## Feedback?

We're excited to bring you these, and other features.  If you have feedback, just [drop us a note](mailto:support@thousandeyes.com?subject=2016-03-30+release+update), any day, any time.  Feedback is always welcome!  

