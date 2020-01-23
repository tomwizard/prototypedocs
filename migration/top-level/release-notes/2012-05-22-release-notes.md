# Release Notes: 2012-05-22

What's new in this release:

* **"Jump to" menu** - This release we added a feature that makes it lightning fast to move between application delivery layers while keeping context. Next to each test selector in the views, you'll find a menu with links to different views. When jumping to another view, as always, the context is kept \(including time, location, and test\). However, the "Jump to" menu only contains the views that are relevant for the selected test. For example, from the _Web -&gt; Basic HTTP_ view, _Web -&gt; Page Load_ will only be shown if you enabled page load testing for the current URL. Similarly, network layer views will only be visible if you enabled network testing for the current URL. The menu will be disabled if there's no other related view to switched to. This way, when diagnosing a problem, you can quickly see what other views may have relevant data.
* **Partial data warning** - if a round of data collection is not completed at the current time, we now show a _Partial Data_warning close to the date; also the world map will contain the locations that didnt collected data yet as light gray circles.
* **Run Test widget** - instant tests can now be triggered from a single place in the interface.
* **Permalinks in API** - API results have a new attribute called _permalink_ that has the URL of the view representing the API data. This can be used in user scripts to provide links to the ThousandEyes UI for visualization or further investigation.
* **BGP data now visible in API** - we added a new API endpoint to show BGP data for a given test. It can be also be further filtered by prefix: _/net/bgp-metrics/{testId}/{prefixId}_

