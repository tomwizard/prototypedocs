# Release Notes: 2016-04-27

It's the end of April, and our next ThousandEyes Connect event is drawing ever nearer.   The event will occur on Thursday, May 19, 2016 in Bryant Park in New York, and we're excited to announce presenters from Nasdaq, AIM Specialty Health and VeriSign.  Registration is free; click [this link](https://www.thousandeyes.com/events/connect/new-york-2016) to register.

IMAGE MISSING

Also, in case you missed it, check out [Young Xu's](https://blog.thousandeyes.com/author/young/) latest blog post on making [Network Insights Accessible with Embedded Report Widgets](https://blog.thousandeyes.com/using-embedded-report-widgets/).  Given the new map widget detailed below - it may make sense to start thinking about embedding ThousandEyes in your own NOC.  Also, if you haven't read [Shashank Sahni's](https://blog.thousandeyes.com/author/shashank/) post on how we're leveraging docker at ThousandEyes, check it out here: [ThousandEyes Embraces Docker to Deploy Enterprise & Cloud Agents](https://blog.thousandeyes.com/thousandeyes-docker-enterprise-agents/).  Both are definitely worth the read.

## Map reports widget

Continuing along with expanding the feature set of our reporting, this week we've introduced the Map widget. Add the map widget to any report by entering Add/Remove Widgets mode, dragging the map icon in the widget selector into a report, and configuring the widget.  As a reminder, since the map shows results based on location, you can update the location of your enterprise agents by modifying the location field on the Settings &gt; Enterprise Agents page.

IMAGE MISSING

The Map widget has two different rendering styles, depending on how you choose to aggregate your data.

### By continent/country

When aggregating by either continent or country, the map will render the entire area according to the legend shown at the bottom and to the right of the widget.  Hover over the shaded area to obtain the detailed result.

IMAGE MISSING

### By agent

When aggregating by agent, the map will render a point in the location of the agent.  This is similar to the map view of most test results in our interface.

IMAGE MISSING

Multiple agents located in the same geography will be rendered as a point on the map with a number inside the point: hover over the point to obtain the detailed value for each agent, which will appear as a tooltip.

IMAGE MISSING

For more information on working with reports, please see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnTKAS).

## Retirement of legacy reports

As we've continued expanding our current reporting capabilities, we've begun the process to sunset the legacy reports feature of the platform. Effective today, customers can no longer schedule creation of legacy reports - in favor of using the current \(much more flexible\) reports infrastructure. If you need help working with our current reporting infrastructure, please [reach out to our Customer Success team](mailto:support@thousandeyes.com?subject=reports+transition+help), and we'll be happy to help you transition to the new version.

## Physical appliance installer

We've introduced the ability to download an enterprise agent installer, which can be used to image low-cost Intel NUC \(5th generation\) devices for deployment into locations where it's challenging to deploy server infrastructure. Available from the Settings &gt; Enterprise Agents page, click the Add new agent button, select the Appliance tab, and download the generic ISO, which that can be written to a USB disk for later installation.

IMAGE MISSING

Users can also prepare a customized Physical Appliance installer using the Custom Appliance tab, selecting Physical as the appliance type, and pre-entering details for a custom build.  

Keep in mind that this is an _installer_, rather than a working image.  Once you use this installer to create a new device, you have access to the same classic web-based configuration interface as the ThousandEyes Virtual Appliance.

Our supported hardware specifications and instructions for imaging these machines can be found in [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnOKAS). 

## Comments, questions?

You've got an opinion, and we want to hear it! [Drop us a note](mailto:support@thousandeyes.com?subject=2016-04-27+release+update) anytime - we'd love to hear what you have to say.

