# Using the DNS+ Mappings view

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Mappings view leverages the ThousandEyes DNS+ layout, documented here:[https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC).  This article highlights specifics shown in the DNS+ Mappings view.

## Example

The DNS+ Mappings view effectively takes each the IP address resolved by worldwide DNS resolvers, and shows how many resolvers worldwide respond to the domain trace using that IP address.  This allows visibility into Geographic Load balancing, content delivery networks, and DNS Cache Poisoning.  The example below shows a DNS+ Mappings view for thousandeyes.com MX.

IMAGE MISSING

## View Specifics

The DNS+ Mappings view has one control that others within the DNS+ family don't: the mappings selector.  This selector allows you to choose which mapping you wish to review.  Once a mapping is selected, the density of the mapping will be shown, based on the shade of blue in the map.  Countries shaded in dark blue show the densest concentration of resolvers responding on this IP, whereas light blue indicates light concentration.

As with other DNS+ views, the view is somewhat different depending on whether or not a country is selected.



<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>With no Country selected
          <br />The mapping selector will display for each mapping, the percentage of
          mapping from all vantage points globally.</p>
        <p>The computed averages area will show the percentage of vantage points
          mapping to the selected mapping, the number of vantage points used for
          the test at the date/time selected, and the number of mappings returned
          globally. When a domain trace returns more than 1 mapping, then either
          geographic load balancing, CDN-based delivery, or DNS cache poisoning is
          in play. Number of mappings is a valid alert criterion, and can be used
          to trigger alerts for DNS+ tests.</p>
        <p>IMAGE MISSING</p>
        <p>The timeline will show the percentage of worldwide vantage points mapping
          to the selected mapping over time.</p>
        <p>IMAGE MISSING</p>
        <p>The Detailed metrics area comprises of the following three tabs:</p>
        <ul>
          <li>Map: Shows worldwide percentage of vantage points returning the selected
            mapping, along with total number of vantage points available within all
            countries and total number of mappings for the target record type, for
            the selected date and time. The map shows countries colored based on the
            percentage of vantage points results for the selected mapping. White indicates
            least average server latency, while dark blue color indicates maximum average
            sever latency.</li>
          <li>Countries: Tabulates for each country, % of vantage points returning the
            selected mapping and number of networks, sorted by default in descending
            order of % of vantage points results.</li>
          <li>Networks: Tabulates for worldwide networks, AS number,% of vantage points
            returning the selected mapping and number of vantage points, sorted by
            default in descending order of % of vantage points results.</li>
        </ul>
        <p>To select a specific country, simply select a country from the world map,
          or choose a country from the Country tab in the detailed metrics area or
          from the Country dropdown menu. The selected country will turn yellow in
          the map view.</p>
      </th>
      <th style="text-align:left">
        <p>With a country selected
          <br />The mapping selector will display the list of mappings and percentage
          of country-based vantage points mapping to each address. All global mappings
          are shown, but the percentages in the list (when a country is selected)
          are based on the percentage of vantage points mapping to this address in
          country.</p>
        <p>The computed averages area shows the percentage of vantage points in the
          selected country mapping to the selected mapping, based on the total number
          of vantage points in that country.</p>
        <p>IMAGE MISSING</p>
        <p>The timeline will show the percentage of country-based vantage points
          mapping to the selected mapping over time, atop a global vantage point
          mapping chart. The country&apos;s value is charted in a line graph, whereas
          the global value is shown in an area graph.</p>
        <p>IMAGE MISSING</p>
        <p>The Detailed metrics area comprises of the following three tabs:</p>
        <ul>
          <li>Map: Shows for the selected country, percentage of vantage points returning
            the selected mapping, total number of vantage points available and total
            number of mappings for the target record type, for the selected date and
            time. The map shows countries colored based on the percentage of vantage
            points results for the selected mapping. White indicates least average
            server latency, while dark blue color indicates maximum average sever latency.
            Selected country is shaded in yellow color.</li>
          <li>Countries: Tabulates for each country, % of vantage points returning the
            selected mapping and number of networks, sorted by default in descending
            order of % of vantage points results. Selected country will be highlighted
            in blue.</li>
          <li>Network tab: Tabulates for networks within the country, AS number,% of
            vantage points returning the selected mapping and number of vantage points,
            sorted by default in descending order of % of vantage points results.</li>
        </ul>
        <p>To clear a selected country, either click in background (uncolored) area
          of the world map, click on &apos;x&apos; from the Country dropdown menu.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>