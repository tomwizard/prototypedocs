# Untitled

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Resolution Time view leverages the ThousandEyes DNS+ layout, documented here: https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC  This article highlights specifics shown in the DNS+ Resolution Time view.

The example below shows DNS+ Resolution View of a DNS+ Domain Trace test against thousandeyes.com MX record.

The DNS+ Resolution Time view shows two different data views, depending on whether or not a country is selected.

## With no country selected

The computed averages area computes the worldwide average resolution time, and shows the number of vantage points and number of countries tested during the selected date/time. 

![Screen\_Shot\_2015-07-07\_at\_9.23.05\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh3&feoid=00NE0000006OT0r&refid=0EME0000000DWap)

The timeline area plots average response time, calculated globally over time, as shown below.

![Screen\_Shot\_2015-07-07\_at\_9.23.43\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh3&feoid=00NE0000006OT0r&refid=0EME0000000DWan)

The Detailed metrics area, broken into two tabs shows the following:

* Map: Shows worldwide average resolution time results, along with total number of vantage points available within all tested countries, for the selected date and time. The map shows countries colored based on the resolution time measurements obtained from vantage points within those countries. Dark green color indicates least resolution time while dark red color indicates maximum resolution time.
* Countries: Tabulates for each country, average resolution time measurements, number of networks, number of vantage points \(in those networks\), sorted by default in descending average resolution time measurements results.
* Networks: Tabulates for worldwide networks, AS number, resolution time \(as computed across all vantage points in that network\), and number of vantage points, sorted by default in descending order of average resolution time measurements

To select a specific country, simply select a country from the world map, or choose a country from the Countries tab in the detailed metrics area or from the Country dropdown menu.

## With a country selected

The computed averages area computes the average resolution time, and shows the number of vantage points in the selected country tested during the selected date/time. 

![Screen\_Shot\_2015-07-07\_at\_9.24.20\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh3&feoid=00NE0000006OT0r&refid=0EME0000000DWam)

The timeline area plots the average resolution time results for the selected country as a line graph over the plot for the average resolution time results from countries worldwide.

![Screen\_Shot\_2015-07-07\_at\_9.24.53\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh3&feoid=00NE0000006OT0r&refid=0EME0000000DWaL)

The Detailed metrics area, broken into two tabs shows the following:

* Map: Shows for the selected country, average resolution time measurements along with number of vantage points for the selected date and time. The map shows countries colored based on the resolution time measurements obtained from vantage points within those countries. Dark green color indicates least resolution time while dark red color indicates maximum resolution time. Selected country is shown in blue color.
* Countries: Tabulates for each country, average resolution time measurements, number of networks, number of vantage points \(in those networks\), sorted by default in descending average server latency measurement. Selected country will be highlighted in blue.
* Networks: Tabulates for networks within the country, AS number, resolution time \(as computed across all vantage points in that network\), and number of vantage points, sorted by default in descending order of average resolution time measurements.
* To clear a selected country, either click in background \(uncolored\) area of the world map, or click on 'x' from the Country dropdown menu.

Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

