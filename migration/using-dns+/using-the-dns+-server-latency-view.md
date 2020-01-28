# Using the DNS+ Server Latency view

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Server Latency view leverages the ThousandEyes DNS+ layout, documented here: https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC  This article highlights specifics shown in the DNS+ Server Latency view.

## Example

The example below shows DNS+ Server Latency View for a root nameserver. 

IMAGE MISSING

## View Specifics

The DNS+ Server Latency view shows two different data views, depending on whether or not a country is selected.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>With no country selected
          <br />The computed averages area shows worldwide average server latency, calculated
          from the number of vantage points in different countries tested during
          the selected date/time.
          <br />IMAGE MISSING</p>
        <p>Timeline shows average server latency, calculated globally over time.
          An example of a timeline with no country selected is shown below:
          <br />IMAGE MISSING</p>
        <p>The Detailed metrics section contains the following three tabs:</p>
        <ul>
          <li>Map: Shows worldwide average server latency measurements along with total
            number of vantage points available within all countries for the selected
            date and time. The map shows countries colored based on the server latency
            measurements obtained from all vantage points within those countries. Dark
            green color is used to indicate least average server latency, while dark
            red color indicates maximum average sever latency.</li>
          <li>Countries: Tabulates for each country, average server latency measurements,
            number of networks, number of vantage points (in those networks), sorted
            by default in descending order of average server latency measurement.</li>
          <li>Networks: Tabulates for worldwide networks, AS number, server latency
            (as computed across all vantage points in that network), and number of
            vantage points, sorted by default in descending order of average server
            latency measurements.</li>
        </ul>
        <p>To select a specific country, simply select a country from the world map,
          or choose a country from the Countries tab in the detailed metrics area
          or from the Country dropdown menu.</p>
      </th>
      <th style="text-align:left">
        <p>With a country selected
          <br />The computed averages area computes the average server latency from vantage
          points tested in the selected country during the selected date/time.
          <br
          />IMAGE MISSING</p>
        <p>The timeline shows average server latency measurements within the country
          as line graph plotted over the worldwide average server latency data. An
          example of a timeline with a country selected is shown below.
          <br />IMAGE MISSING</p>
        <p>The Detailed metrics area, broken into two tabs shows the following:</p>
        <ul>
          <li>
            <ul>
              <li>Map: Shows for the selected country, average server latency measurements
                along with number of vantage points for the selected date and time. The
                map shows countries colored based on the server latency measurements obtained
                from all vantage points within those countries. Dark green color is used
                to indicate least average server latency, while dark red color indicates
                maximum average sever latency. Selected country is shown in blue color.</li>
              <li>Countries: Tabulates for each country, average server latency measurements,
                number of networks, number of vantage points (in those networks), sorted
                by default in descending order of average server latency measurement. Selected
                country will be highlighted in blue.</li>
              <li>Networks: Tabulates for networks within the country, AS number, server
                latency (as computed across all vantage points in that network), and number
                of vantage points, sorted by default in descending order of average server
                latency measurements.</li>
            </ul>
          </li>
        </ul>
        <p>To clear a selected country, either click in background (uncolored) area
          of the world map, or click on &apos;x&apos; from the Country dropdown menu.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

IMAGE MISSING

