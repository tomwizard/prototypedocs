# Release Notes: 2018-09-26

Welcome to tonight's release! The first of the new season, to go along with explosions of green or multi-colored leaves, depending on your latitude. Ch-ch-ch-changes...

As we say goodbye to summer in the northern hemisphere, and to winter in the south, why not say "Hello" to ThousandEyes staff and fellow users at an event near you? 

IMAGE MISSING

### ThousandEyes Connect

We'll be having our next ThousandEyes Connect event in Dallas \(well, Irving\) Texas on October 11th at the Alamo Drafthouse. [Registration](https://www.thousandeyes.com/events/connect/dallas-2018) is free and open. Come swing by the Big D if you're living deep in the heart of Texas, or just visiting \(gotta visit at least one Alamo if you're in Texas, and the rental car counter doesn't count\).

No one named Bowie, Travis or Crockett at this event but our trio of distinguished speakers include Jim Metzler, a founder and Vice President of Ashton, Metzler and Associates and Lee Neel, the Director of Network Engineering at Sabre \(the folks who made possible your airline travel, should you be flying to Dallas\). Our Senior Product Marketing Manager, [Angelique Medina](https://blog.thousandeyes.com/author/amedina/) rounds out the lineup with a presentation on some recent DNS research. Don't miss out!

### NANOG

[NANOG 74](http://www.cvent.com/events/nanog-74/event-summary-72b86f62faad447c9c8a9d638dff8768.aspx) will be in Vancouver, Canada starting Monday, October 1st, with a [hackathon](http://www.cvent.com/events/nanog-74/custom-20-72b86f62faad447c9c8a9d638dff8768.aspx) starting the prior weekend. Our CEO, Mohit Lad will be leading the ThousandEyes contingent to NANOG, which will feature Angelique Medina presenting the aforementioned recent DNS research, if you didn't make it down to Big D.

And now for the release deets...

## Cloud Agents

We've got an explosion of new IPv6 Cloud Agents in this release cycle. You'll see them listed under the [Settings &gt; Cloud Agents page](https://app.thousandeyes.com/settings/agents/cloud/?section=agents) with the following names:

* Barcelona, Spain - IPv6
* Bogotá, Colombia - IPv6
* Orlando, FL - IPv6
* Guadalajara, Mexico - IPv6
* St. Petersburg, Russia - IPv6
* Kwai Chung, Hong Kong - IPv6

## BGP Route Visualization

We've updated the BGP Route Visualization view to be more scalable, easier to read and easier to interact with. The Route Visualization now has a linear layout with monitors \(diamonds\) on the left, transit ASNs \(blue ovals\) in the center and origin ASNs \(green ovals\) on the right. We also now visualize prefixes \(green circles\) on the far right.

IMAGE MISSING

Monitors can now be grouped by network or shown individually. Monitors are paginated, and pages are sorted by the selected Metric. For example, Monitors with path changes will be on the first page, when Path Changes is the selected metric. The **Undo** button allows the user to move back through the pagination or to remove any previous selection.

Transit nodes also now have the option to **Show only routes passing through this AS** in the tooltip that appears when mousing over the node. Filters now include **Paths active for more than**, which will help reduce the noise from short-lived BGP flaps.

## Reports

We've updated the interface for the Number widgets in reports, replacing the horizontal tabbed style of displaying the Card Descriptions with a vertical left-side listing.

IMAGE MISSING

## Roles

  
The [Roles tab](https://app.thousandeyes.com/settings/account/?section=roles) of the Account Settings page has been updated. Scrolling performance is improved, and we've added tooltips which provide descriptions of the individual Roles when hovering over the name of the Role.

IMAGE MISSING

Additionally, we've added features for ease of use, such as a drop-down filter which can quickly display groups of related permissions:

IMAGE MISSING

These filters work in conjunction with text entered in the search field.

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* On the Enterprise Agents settings page, we've added a bulk actions feature. Check the boxes next to Agents to perform enabling, disabling and deleting of all checked Agents.
* Creating a Web Layer test when the Username field has content, and the HTTP Authentication is switched to None now works.

## Questions and comments

Got feedback for us? Want to tell us your favorite [Jim Bowie](https://shannonselin.com/2015/08/jim-bowie-before-the-gaudy-legend/) legend / [David Bowie](http://time.com/4175275/david-bowie/) song / [Emily Dickinson](https://arcade.stanford.edu/blogs/my-life-withstood-yellow-rose) poem? [Send us an email](mailto:support@thousandeyes.com?subject=2017-09-26+Release+Update)!

