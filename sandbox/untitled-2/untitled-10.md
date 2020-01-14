# Untitled

DNS+ provides visibility into worldwide DNS data, from thousands of vantage points in the form of open resolvers present on the Internet.  DNS+ is an optional module that is built to provide DNS visibility over and above the agent-based insight provided by the ThousandEyes platform, and as such, not all organizations will have access to the DNS+ test suite.  

The example below shows a view of a DNS+ Availability test against the faluninfo.net domain's A record.

The DNS+ Availability view shows two different data views, depending on whether or not a country is selected.

## With no country selected

The computed averages area computes the worldwide average availability, and shows the number of vantage points and number of countries tested during the selected date/time. 

![Screen\_Shot\_2015-07-07\_at\_10.25.40\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh4&feoid=00NE0000006OT0r&refid=0EME0000000DWaW)

  
 Timeline shows average percentage availability for the test target, calculated globally over time. An example of a timeline with no country selected is shown below:  


![Screen\_Shot\_2015-07-07\_at\_10.26.16\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh4&feoid=00NE0000006OT0r&refid=0EME0000000DWaM)

The Detailed metrics section consists of the following tabs:

* Map: Shows worldwide average percentage availability measurements along with total number of vantage points available within tested countries for the selected date and time. The map shows countries colored based on the percentage availability measurements obtained from all vantage points within those countries. Dark green color is used to indicate least 100% availability, while dark red color indicates 0% availability.
* Countires: Tabulates for each country, average percentage availability measurements, number of networks, number of vantage points \(in those networks\) and response error code results, sorted by default in descending order of average availability measurements.
* Network: Tabulates for worldwide networks, AS number, average availability measurements \(as computed across all vantage points in that network\), and number of vantage points and response error code results, sorted by default in descending order of average availability measurements

To select a specific country, simply select a country from the world map, or choose a country from the Countries tab in the detailed metrics area or from the Country dropdown menu.

## With a country selected

The computed averages area computes the average availability, and shows the number of vantage points in the selected country, tested during the selected date/time.

![Screen\_Shot\_2015-07-07\_at\_10.26.51\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh4&feoid=00NE0000006OT0r&refid=0EME0000000DWaZ)

  
 The timeline shows average percentage availability for test target within the country as a line graph plotted over the worldwide average percentage availability graph. An example of a timeline with a country selected is shown below.

![Screen\_Shot\_2015-07-07\_at\_10.27.12\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh4&feoid=00NE0000006OT0r&refid=0EME0000000DWaY)

The Detailed metrics section consisits of the following tabs:

* Map: Shows for the selected country average percentage availability measurements along with total number of vantage points available within the country for the selected date and time. The map shows countries colored based on the percentage availability measurements obtained from all vantage points within those countries. Dark green color is used to indicate least 100% availability, while dark red color indicates 0% availability. Selected country is indicated by blue color.
* Countires: Tabulates for country, average percentage availability measurements, number of networks, number of vantage points \(in those networks\) and response error code results, sorted by default in descending order of average availability measurements. Selected country is highlighted in blue color.
* Network:  Tabulates for networks within the country, AS number, average availability measurements \(as computed across all vantage points in that network\), and number of vantage points and response error code results, sorted by default in descending order of average availability measurements.

To clear a selected country, either click in background \(uncolored\) area of the world map, or click on 'x' from the Country dropdown menu. 

Any view of a network, or Autonomous System \(AS\) is based on a list of registered Autonomous Systems, or telecommunications provider present in that country.  Autonomous System \(AS\) details can be seen by hovering over the AS link, shown in the network name column of the network tab.  An example of this AS information can be found below, showing Telecom Argentina S.A., AS 7303.

![Screen\_Shot\_2015-07-07\_at\_10.46.43\_PM.png](https://thousandeyes--c.na98.content.force.com/servlet/rtaImage?eid=ka044000000UJh4&feoid=00NE0000006OT0r&refid=0EME0000000DWaa)

