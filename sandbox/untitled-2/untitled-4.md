# Untitled

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Mappings view effectively takes each the IP address resolved by worldwide DNS resolvers, and shows how many resolvers worldwide respond to the domain trace using that IP address.  This allows visibility into Geographic Load balancing, content delivery networks, and DNS Cache Poisoning.  The example below shows a DNS+ Mappings view for thousandeyes.com MX.

The DNS+ Mappings view has one control that others within the DNS+ family don't: the mappings selector.  This selector allows you to choose which mapping you wish to review.  Once a mapping is selected, the density of the mapping will be shown, based on the shade of blue in the map.  Countries shaded in dark blue show the densest concentration of resolvers responding on this IP, whereas light blue indicates light concentration.

As with other DNS+ views, the view is somewhat different depending on whether or not a country is selected.

## With no country selected

The mapping selector will display for each mapping, the percentage of mapping  from all vantage points globally.

The computed averages area will show the percentage of vantage points mapping to the selected mapping, the number of vantage points used for the test at the date/time selected, and the number of mappings returned globally. When a domain trace returns more than 1 mapping, then either geographic load balancing, CDN-based delivery, or DNS cache poisoning is in play.  Number of mappings is a valid alert criterion, and can be used to trigger alerts for DNS+ tests.

![Screen\_Shot\_2015-07-07\_at\_8.28.36\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhD&feoid=00NE0000006OT0r&refid=0EME0000000DWac)

The timeline will show the percentage of worldwide vantage points mapping to the selected mapping over time.

![Screen\_Shot\_2015-07-07\_at\_8.29.25\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhD&feoid=00NE0000006OT0r&refid=0EME0000000DWae)

The Detailed metrics area comprises of the following three tabs:

* Map: Shows worldwide percentage of vantage points returning the selected mapping, along with total number of vantage points available within all countries and total number of mappings for the target record type, for the selected date and time. The map shows countries colored based on the percentage of vantage points results for the selected mapping. White indicates least average server latency, while dark blue color indicates maximum average sever latency. 
* Countries: Tabulates for each country, % of vantage points returning the selected mapping and number of networks, sorted by default in descending order of % of vantage points results.
* Networks: Tabulates for worldwide networks, AS number,% of vantage points returning the selected mapping  and number of vantage points, sorted by default in descending order of % of vantage points results.

To select a specific country, simply select a country from the world map, or choose a country from the Country tab in the detailed metrics area or from the Country dropdown menu. The selected country will turn yellow in the map view.

## With a country selected

The mapping selector will display the list of mappings and percentage of country-based vantage points mapping to each address.  All global mappings are shown, but the percentages in the list \(when a country is selected\) are based on the percentage of vantage points mapping to this address in country.  

The computed averages area shows the percentage of vantage points in the selected country mapping to the selected mapping, based on the total number of vantage points in that country.  

![Screen\_Shot\_2015-07-07\_at\_8.30.17\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhD&feoid=00NE0000006OT0r&refid=0EME0000000DWaf)

The timeline will show the percentage of country-based vantage points mapping to the selected mapping over time, atop a global vantage point mapping chart.  The country's value is charted in a line graph, whereas the global value is shown in an area graph.

![Screen\_Shot\_2015-07-07\_at\_8.33.52\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhD&feoid=00NE0000006OT0r&refid=0EME0000000DWad)

The Detailed metrics area comprises of the following three tabs:

* Map: Shows for the selected country, percentage of vantage points returning the selected mapping, total number of vantage points available and total number of mappings for the target record type, for the selected date and time. The map shows countries colored based on the percentage of vantage points results for the selected mapping. White indicates least average server latency, while dark blue color indicates maximum average sever latency. Selected country is shaded in yellow color.
* Countries: Tabulates for each country, % of vantage points returning the selected mapping and number of networks, sorted by default in descending order of % of vantage points results. Selected country will be highlighted in blue.
* Network tab: Tabulates for networks within the country, AS number,% of vantage points returning the selected mapping  and number of vantage points, sorted by default in descending order of % of vantage points results.

To clear a selected country, either click in background \(uncolored\) area of the world map, click on 'x' from the Country dropdown menu.

