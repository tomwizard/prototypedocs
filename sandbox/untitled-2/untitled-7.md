# Untitled

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The DNS+ Server Latency view leverages the ThousandEyes DNS+ layout, documented here: https://support.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmgKAC  This article highlights specifics shown in the DNS+ Server Latency view.

The example below shows DNS+ Server Latency View for a root nameserver. 

The DNS+ Server Latency view shows two different data views, depending on whether or not a country is selected.

## With no country selected

The computed averages area shows worldwide average server latency, calculated from the number of vantage points in different countries tested during the selected date/time.

![Screen\_Shot\_2015-07-07\_at\_7.17.03\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhE&feoid=00NE0000006OT0r&refid=0EME0000000DWaN)

Timeline shows average server latency, calculated globally over time. An example of a timeline with no country selected is shown below:

![Screen\_Shot\_2015-07-07\_at\_7.36.21\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhE&feoid=00NE0000006OT0r&refid=0EME0000000DWag)

The Detailed metrics section contains the following three tabs:

* Map: Shows worldwide average server latency measurements along with total number of vantage points available within all countries for the selected date and time. The map shows countries colored based on the server latency measurements obtained from all vantage points within those countries. Dark green color is used to indicate least average server latency, while dark red color indicates maximum average sever latency. 
* Countries: Tabulates for each country, average server latency measurements, number of networks, number of vantage points \(in those networks\), sorted by default in descending order of average server latency measurement.
* Networks: Tabulates for worldwide networks, AS number, server latency \(as computed across all vantage points in that network\), and number of vantage points, sorted by default in descending order of average server latency measurements.

To select a specific country, simply select a country from the world map, or choose a country from the Countries tab in the detailed metrics area or from the Country dropdown menu.

## With a country selected

The computed averages area computes the average server latency from vantage points tested in the selected country during the selected date/time.

![Screen\_Shot\_2015-07-07\_at\_7.32.35\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhE&feoid=00NE0000006OT0r&refid=0EME0000000DWaO)

The timeline shows average server latency measurements within the country as line graph plotted over the worldwide average server latency data. An example of a timeline with a country selected is shown below.

![Screen\_Shot\_2015-07-07\_at\_7.38.54\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhE&feoid=00NE0000006OT0r&refid=0EME0000000DWaR)

The Detailed metrics area, broken into two tabs shows the following:

* Map: Shows for the selected country, average server latency measurements along with number of vantage points for the selected date and time. The map shows countries colored based on the server latency measurements obtained from all vantage points within those countries. Dark green color is used to indicate least average server latency, while dark red color indicates maximum average sever latency. Selected country is shown in blue color.
* Countries: Tabulates for each country, average server latency measurements, number of networks, number of vantage points \(in those networks\), sorted by default in descending order of average server latency measurement. Selected country will be highlighted in blue.
* Networks: Tabulates for networks within the country, AS number, server latency \(as computed across all vantage points in that network\), and number of vantage points, sorted by default in descending order of average server latency measurements.

To clear a selected country, either click in background \(uncolored\) area of the world map, or click on 'x' from the Country dropdown menu.

Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

![Screen\_Shot\_2015-07-07\_at\_8.08.07\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJhE&feoid=00NE0000006OT0r&refid=0EME0000000DWaU)

