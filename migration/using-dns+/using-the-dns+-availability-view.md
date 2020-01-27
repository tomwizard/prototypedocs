# Using the DNS+ Availability view

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Availability view leverages the ThousandEyes DNS+ layout, documented here: [https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).  This article highlights specifics shown in the DNS+ Availability view.

## Example

The example below shows a view of a DNS+ Availability test against the faluninfo.net domain's A record.

IMAGE MISSING

## View Specifics

The DNS+ Availability view shows two different data views, depending on whether or not a country is selected.

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>With no country selected</p>
        <p>The computed averages area computes the worldwide average availability,
          and shows the number of vantage points and number of countries tested during
          the selected date/time.</p>
        <p>IMAGE MISSING
          <br />Timeline shows average percentage availability for the test target, calculated
          globally over time. An example of a timeline with no country selected is
          shown below:
          <br />IMAGE MISSING</p>
        <p>The Detailed metrics section consists of the following tabs:</p>
        <ul>
          <li>Map: Shows worldwide average percentage availability measurements along
            with total number of vantage points available within tested countries for
            the selected date and time. The map shows countries colored based on the
            percentage availability measurements obtained from all vantage points within
            those countries. Dark green color is used to indicate least 100% availability,
            while dark red color indicates 0% availability.</li>
          <li>Countires: Tabulates for each country, average percentage availability
            measurements, number of networks, number of vantage points (in those networks)
            and response error code results, sorted by default in descending order
            of average availability measurements.</li>
          <li>Network: Tabulates for worldwide networks, AS number, average availability
            measurements (as computed across all vantage points in that network), and
            number of vantage points and response error code results, sorted by default
            in descending order of average availability measurements</li>
        </ul>
        <p>To select a specific country, simply select a country from the world map,
          or choose a country from the Countries tab in the detailed metrics area
          or from the Country dropdown menu.</p>
      </th>
      <th style="text-align:left">
        <p>With a country selected
          <br />The computed averages area computes the average availability, and shows
          the number of vantage points in the selected country, tested during the
          selected date/time.</p>
        <p>IMAGE MISSING
          <br />The timeline shows average percentage availability for test target within
          the country as a line graph plotted over the worldwide average percentage
          availability graph. An example of a timeline with a country selected is
          shown below.</p>
        <p>IMAGE MISSING</p>
        <p>The Detailed metrics section consisits of the following tabs:</p>
        <ul>
          <li>Map: Shows for the selected country average percentage availability measurements
            along with total number of vantage points available within the country
            for the selected date and time. The map shows countries colored based on
            the percentage availability measurements obtained from all vantage points
            within those countries. Dark green color is used to indicate least 100%
            availability, while dark red color indicates 0% availability. Selected
            country is indicated by blue color.</li>
          <li>Countires: Tabulates for country, average percentage availability measurements,
            number of networks, number of vantage points (in those networks) and response
            error code results, sorted by default in descending order of average availability
            measurements. Selected country is highlighted in blue color.</li>
          <li>Network: Tabulates for networks within the country, AS number, average
            availability measurements (as computed across all vantage points in that
            network), and number of vantage points and response error code results,
            sorted by default in descending order of average availability measurements.</li>
        </ul>
        <p>To clear a selected country, either click in background (uncolored) area
          of the world map, or click on &apos;x&apos; from the Country dropdown menu.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

IMAGE MISSING

