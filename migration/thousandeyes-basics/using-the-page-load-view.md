# Using the Page Load view

When you create Page Load test, you get access to the Page Load view.  The Page Load view leverages the ThousandEyes standard layout, documented here: [https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).  

This article highlights specifics shown in the Page Load view.

## Example

This example shows the result of a globally distributed Page Load test against christianmingle.com, a dating site.

IMAGE MISSING

## View Specifics

 As with most pages in the ThousandEyes platform, the Page Load view shows two different views, depending on whether or not a location is selected.  Differences are shown below:

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><b>Without a location selected</b>
        </p>
        <p>The computed averages area on this view is more complex than most others.
          When in the global view (no location selected), it will show the average
          DOM Load and average Page Load times, followed by a warning if the page
          load was incomplete from any locations.</p>
        <p>If the test obtains a DOM Load time but no Page Load time from one or
          more locations, the DOM Load time will be incorporated into the average
          DOM Load, while the average Page Load will have one fewer measurement per
          incomplete location. Thus, average DOM Load can be greater than average
          Page Load, even though DOM Load time is always less than Page Load time.</p>
      </th>
      <th style="text-align:left">
        <p><b>With a location selected</b>
        </p>
        <p>The computed averages area on this view is more complex than most others.
          When in the location view (with a location selected), it will show the
          DOM load and Page Load times, followed by a warning if the page load was
          incomplete from any locations.</p>
        <p>If the test obtains a DOM Load time but no Page Load time, the DOM Load
          time will be displayed.</p>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">IMAGE MISSING</td>
      <td style="text-align:left">IMAGE MISSING</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>In addition to this, a tabbed interface allows the user to switch between
          breakdowns of timing between domain and by provider. This can be helpful
          when troubleshooting a slow page load which is dependent on components
          from other domains.</p>
        <p>Without a location selected, the timeline shows the average page load
          time, calculated from all locations globally. Note that the averageThe
          following image shows an example of a timeline for the page load view:</p>
        <p>IMAGE MISSING</p>
        <p>The detailed metrics area shows a tabular view of by-location metrics
          for each of the locations used in the test. This includes Location name,
          date/time that the data was collected, Total Wire Size (calculated as the
          sum of the size of all component sizes as sent on the wire, where compression
          can be used), throughput (measured by total wire size/fetch time), number
          of objects, component errors, and DOM and Page load times.</p>
      </td>
      <td style="text-align:left">
        <p>In addition to this, a tabbed interface allows the user to switch between
          breakdowns of timing between domain and by provider. This can be helpful
          when troubleshooting a slow page load which is dependent on components
          from other domains. The only difference from the global view is the number
          of objects is included is shown.</p>
        <p>With a location selected, the timeline shows a chart showing page load
          time for that location, charted against the global average page load times.
          The following image shows a sample for the page load times with a location
          selected. As you can see, the agent&apos;s data is charted in a blue line,
          whereas the global data is charted as an area.</p>
        <p>IMAGE MISSING</p>
        <p>Detailed metrics when a location is selected in this view is different
          from the global view. When a location is selected, the page load waterfall
          is shown, which includes the object name, domain, provider, size, and a
          waterfall, including start/end time, and fetch time breakdown for each
          component loaded. To access the waterfall detail, hover over a specific
          object&apos;s chart, and view the contents.</p>
        <p>IMAGE MISSING</p>
        <p>If an object is being indicating an error, it can be directly opened by
          clicking the pop-out icon to the right of the name of the object.</p>
        <p>A page load waterfall example is shown below.</p>
      </td>
    </tr>
  </tbody>
</table>## Waterfall example

IMAGE MISSING

