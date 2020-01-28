# Release Notes: 2014-10-15

The fall rollout continues! See notes below related to tonight's release, and as always, let us know to the extent that you have any questions.

## New Cloud Agent locations

* Barcelona, Spain
* Sofia, Bulgaria

## Updated Agent Settings interface

We've given our agent settings interface a makeover.  With the new agent settings interface, users have access to more information both about Enterprise Agents, and about Cloud Agents.  Click [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmsKAC) to review the new article on working with agent settings.

## Test Groups

Similar to the Agent groups capability added in the [June 6, 2014 release](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmloKAC), we've introduced test groups in this week's release.  Check out [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmfKAC) for more information.  A quick look can be found in the image below.

IMAGE MISSING

## Path Visualization updates

We've added two new options to the Path Visualization interface.

* **Traceroute-style output**: to obtain a traceroute-style output from the path visualization interface, hover over an agent, and click the 'Show Traceroute-style Output' link in the information window that opens.  This will open a dialog that shows the results from a Path trace from a particular agent to the destination.  This can be used to provide information to service providers who insist on having classic traceroute responses during diagnosis.

  IMAGE MISSING  
  IMAGE MISSING

* **Forwarding loss packet count added** to intermediate nodes showing loss.  In addition to showing the percentage loss allocated to each hop found in the Path Visualization interface, we now show the number of packets dropped at each intermediate node.  In the image example below, the packet count \(6 of 9 packets\) used in calculation of loss is added. IMAGE MISSING

## Alert Settings

We've added a new operator for the Mappings field of DNS-based alert rules: DNS+ Alerts, as well as DNS Trace and Server tests will now allow the use of the "in" operator.

## MTU Measurements for SSL targets

We've disabled MTU measurements \(found in the advanced settings interface for tests\) on tests targeting known SSL ports.  This includes ports on the following list:

* 443, 465, 563, 636, 695, 989, 990, 992, 993, 994, 995

This is due to common issues encountered while attempting to use our MTU interrogation method against SSL targets.  This is only a default setting, and can be overridden by navigating to Advanced Settings and checking the **Perform MTU Measurements** checkbox.

## API Updates

We've updated the list of parameters accepted in the HTTP Server and DNS Server Instant Test endpoints.  We've also introduced the APIv5 preview, which provides access to new methods, including Page Load and Transaction component detail, as well as BGP Route endpoints.  Please note that APIv5 is currently in preview mode and subject to change without notice until its release.  Check out our [Developer Reference site](http://developer.thousandeyes.com/) for more details.

