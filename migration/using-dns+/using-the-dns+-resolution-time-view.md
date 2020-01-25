# Using the DNS+ Resolution Time view

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Resolution Time view leverages the ThousandEyes DNS+ layout, documented here: https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC  This article highlights specifics shown in the DNS+ Resolution Time view.

## Example

The example below shows DNS+ Resolution View of a DNS+ Domain Trace test against thousandeyes.com MX record.

IMAGE MISSING

## View Specifics

The DNS+ Resolution Time view shows two different data views, depending on whether or not a country is selected.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>With no country selected</p>
        <p>The computed averages area computes the worldwide average resolution time,
          and shows the number of vantage points and number of countries tested during
          the selected date/time.</p>
        <p>IMAGE MISSING</p>
        <p>The timeline area plots average response time, calculated globally over
          time, as shown below.</p>
        <p>IMAGE MISSING</p>
        <p>The Detailed metrics area, broken into two tabs shows the following:</p>
        <ul>
          <li>
            <ul>
              <li>Map: Shows worldwide average resolution time results, along with total
                number of vantage points available within all tested countries, for the
                selected date and time. The map shows countries colored based on the resolution
                time measurements obtained from vantage points within those countries.
                Dark green color indicates least resolution time while dark red color indicates
                maximum resolution time.</li>
              <li>Countries: Tabulates for each country, average resolution time measurements,
                number of networks, number of vantage points (in those networks), sorted
                by default in descending average resolution time measurements results.</li>
              <li></li>
              <li>Networks: Tabulates for worldwide networks, AS number, resolution time
                (as computed across all vantage points in that network), and number of
                vantage points, sorted by default in descending order of average resolution
                time measurements</li>
            </ul>
          </li>
        </ul>
        <p>To select a specific country, simply select a country from the world map,
          or choose a country from the Countries tab in the detailed metrics area
          or from the Country dropdown menu.</p>
      </th>
      <th style="text-align:left">
        <p>With a country selected</p>
        <p>The computed averages area computes the average resolution time, and shows
          the number of vantage points in the selected country tested during the
          selected date/time.</p>
        <p>IMAGE MISSING</p>
        <p>The timeline area plots the average resolution time results for the selected
          country as a line graph over the plot for the average resolution time results
          from countries worldwide.</p>
        <p>IMAGE MISSING</p>
        <p>The Detailed metrics area, broken into two tabs shows the following:</p>
        <ul>
          <li></li>
          <li>Map: Shows for the selected country, average resolution time measurements
            along with number of vantage points for the selected date and time. The
            map shows countries colored based on the resolution time measurements obtained
            from vantage points within those countries. Dark green color indicates
            least resolution time while dark red color indicates maximum resolution
            time. Selected country is shown in blue color.</li>
          <li>Countries: Tabulates for each country, average resolution time measurements,
            number of networks, number of vantage points (in those networks), sorted
            by default in descending average server latency measurement. Selected country
            will be highlighted in blue.</li>
          <li>Networks: Tabulates for networks within the country, AS number, resolution
            time (as computed across all vantage points in that network), and number
            of vantage points, sorted by default in descending order of average resolution
            time measurements.</li>
          <li>To clear a selected country, either click in background (uncolored) area
            of the world map, or click on &apos;x&apos; from the Country dropdown menu.</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

IMAGE MISSING

