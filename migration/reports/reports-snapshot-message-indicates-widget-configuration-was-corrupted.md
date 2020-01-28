# Reports Snapshot message indicates widget configuration was corrupted

As 9/14/2016, we have fixed an issue which affected Reports with configurations that used grouping selectors such as “Group By" with a setting of "All".  The list of affected grouping selectors and their widget types:

| Selector | Found in these widget types |
| :--- | :--- |
| Group By | Time Series, Time Series Stacked Area Chart, Stacked Bar Chart, Grouped Bar Chart, Pie Chart, Box-and-Whiskers, Map |
| Columns | Table, Multi-metric Table |
| X/Y-Axis | Grouped Bar Chart, Stacked Bar Chart  |

These Reports behaved as though the value of the selector was "Tests" rather than "All".  When using certain values of Measure, this issue caused the data returned to be incorrect, based on the way data was aggregated to optimize \(minimize\) data requests between front-end and back-end systems.  The list of affected Measures:

* Median
* nth Percentile
* % positive
* % zero
* Standard Deviation

If the Report used the other Measures \(Mean, Total, Maximum, Minimum\) then the Report data was not affected by this issue.  Additionally, if the Report did use an affected Measure but the results were the same due to conditions such as having only one test as source, then "Tests" is equivalent to "All" and the Report data was not affected by this issue.

Reports are now displaying data correctly but some Report Snapshots that were generated with the issue still contain incorrect data. To address this issue, ThousandEyes has created a warning displayed on already-existing Reports Snapshots that display bad data.  The following warning appears on your widget:

"This snapshot widget’s configuration was corrupted.  The data displayed is not aggregated as originally specified."

IMAGE MISSING

This indicates that the data was aggregated by "Test" rather than by "All" even though the Report configuration was using the latter setting. 

