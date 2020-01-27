# Release Notes: 2018-09-12

Welcome to tonight's release! A light night for new features, but some other heavy-hitting items to watch out for.

First, a quick heads-up for...

IMAGE MISSING  
IMAGE MISSING

Whether you're in [Minnesota](https://www.thousandeyes.com/events/connect/twin-cities-2018) or [Texas](https://www.thousandeyes.com/events/connect/dallas-2018), or fancy a visit to either, come be a star at ThousandEyes Connect! We'll be skating into the Twin Cities on September 19th with a great lineup of speakers, and in the Big D on October 11th with another band of all-star speakers. For you Connect rookies: registration is free, you'll get to rub elbows with other ThousandEyes users from a wide range of companies, there's lots of great ThousandEyes t-shirts given away during intermission and you're guaranteed a great seat that's close to the action!

From the ThousandEyes blog, we have some great new posts that we hope will put a twinkle in your eyes. First up, Senior Product Marketing Manager Angelique Medina has a one-two punch of articles for those who are responsible for delivering SaaS-based services to their users: [The Building Blocks of SaaS are Also Risks](https://blog.thousandeyes.com/the-building-blocks-of-saas-are-also-risks/) and [Five Operational Habits of Successful SaaS Delivery](https://blog.thousandeyes.com/five-operational-habits-successful-saas-delivery/). This checklist of best practices, useful suggestions and general philosophies will help guarantee that your users are your biggest fans.

Next, our VP of Product Marketing, Alex Henthorn-Iwane, shares what ThousandEyes has learned about the IT landscape and cloud computing adoption in the [land of the rising sun](https://en.wikipedia.org/wiki/Names_of_Japan), in his post [Solving Cloud Migration Visibility Pains in Japan](https://blog.thousandeyes.com/solving-cloud-migration-visibility-pains-in-japan/). Lots of interesting data and other information pertaining to the role of SaaS in the Japanese market.

And finally, a blast from this past summer's ThousandEyes Connect in Silicon Valley. Senior Product Marketing Manager Archana Kesavan gives us the highlights of a great presentation by Benjamin McAlary, Principle Network Engineer at Atlassian Software. Benjamin's talk was entitled [How ThousandEyes Saved the Sanity of the Atlassian Network Team](https://blog.thousandeyes.com/how-thousandeyes-saved-sanity-atlassian-network-team/), and drew big claps from those in attendance. Check out his slides--maybe they'll help save your team's sanity, too.

And now for tonight's lineup of features and fixes...

## Path Visualization changes

Previously, the Path Visualization had a **Grouping** option to group **Agents by** "IP Address", for Agent-to-Agent tests. This was the default grouping for Agents. We are removing this option to simplify the rendering of the path. Setting the **Grouping** for Agents to "by Agent" \(the new default\) will show one node per Agent with details for all interfaces via the tooltip.

We've also improved the Path Visualization's ability to handle different nodes with the same private IP address. We now render separate nodes rather than a single node, based on location. So if every one of your offices' Enterprise Agents have a default gateway of 192.168.1.254, you should see all of the default gateways rendered on the Path Visualization with separate nodes, each with a single Location in the tooltip.

## Minor enhancements & bug fixes

Here are the minor enhancements in this week's release:

* When expanding a row on the Enterprise Agents page, the General Info section has been reorganized to better display Appliance version and lock status.
* Improved the display time for Labels on the Agent and Test settings pages. 
* Fixed an issue where Alerts were not being displayed in the Quick Selection menu and Agent mouseover.
* Fixed an issue which caused an Enterprise Agent to be displayed twice in Path Visualization.

## Questions and comments

Got feedback for us? Got an idea for a new feature you'd like to pass our way? [Send us an email](mailto:support@thousandeyes.com?subject=2018-09-12+Release+Update)!

