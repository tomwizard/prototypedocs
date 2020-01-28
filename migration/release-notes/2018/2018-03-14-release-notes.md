# Release Notes: 2018-03-14

Welcome to tonight's release! We had a release last week, but we're sneaking an extra release into our normal bi-weekly release schedule, in honor of  [Pi Day](https://en.wikipedia.org/wiki/Pi_Day). We'll revert to the usual every-other-week release, hereafter. Next release: March 26th.

IMAGE MISSING

## ThousandEyes Connect

A quick reminder that our next ThousandEyes Connect event will take place in London on March 21st, and an update that our Chief Technology Officer, Ricardo Olivera, will join his ThousandEyes co-founder and CEO Mohit Lad at the speaker's podium. Check out the [full details](https://www.thousandeyes.com/events/connect/london-2018) and register for free!

## ThousandEyes Blog

Since last week, our Marketing team has been busy on the blog front. Technical Marketing Manager Ameet Naik has a new post that digs deeper into the [Amazon Web Services outage](https://blog.thousandeyes.com/amazon-aws-outage-lesson-managing-cloud-first-risks/) on March 2nd. Ameet looks at those AWS customers most affected, and asks [Does AWS Direct Connect Guarantee Cloud Performance?](https://blog.thousandeyes.com/does-aws-direct-connect-guarantee-cloud-performance/) A good read for those interested in understanding the pro's and con's of private connections to cloud providers.

As mentioned in previous Release Udpates, we have been adding Cloud Agents in broadband ISP providers. Our Senior Product Marketing Manager, Angelique Medina, explains the rationales behind these new broadband ISP-based Cloud Agents and does an ISP performance comparison, in her article entitled [Introducing Broadband ISP Cloud Agents](https://blog.thousandeyes.com/introducing-broadband-isp-cloud-agents/).

And speaking of broadband ISP Cloud Agents... The details of the release.

## Cloud Agents

We've added two new providers, Comcast and Verizon, to the list of broadband ISP Cloud Agents available in San Jose, CA. See how Silicon Valley measures up!

## Trial Account changes

Going forward, we are changing our handling of Trial accounts. Enterprise Agents installed in Trial accounts will now use a "metered" billing model. Previously, Enterprise Agents were billed based on one of two \(Standard or Pro\) flat rates per month. With the metered billing model, Enterprise Agents will use the Pro feature set only, and will be charged on a per-test basis using the same units as Cloud Agents. The cost will be capped when the usage reaches the level of the previous flat rate of Pro Agents. This model provides cost savings for customers who have low levels of usage on their Enterprise Agents, and allows for spreading usage across more Enterprise Agents without increased cost.

While Trials are free of charge, this change will allow Trial customers to experiment with the new model, which should provide more value to customers than the previous way of licensing Enterprise Agents.

Additionally, when a Trial account expires, we will no longer be changing the account to a Lite account. Expired Trial accounts will remain accessible but will stop collecting test data from all Agents.

If you have questions about Trial accounts, contact your ThousandEyes Account Manager for more information.

## Minor features and bug fixes

* Changed a number of error messages to be warning messages
* Fixed a Device Layer issue for scheduling a Device Discovery with Notifications enabled
* Duplicating a test now creates the new test with the original's Alert Rules, rather than default Alert Rules
* Improved the positioning of the Tooltip in a Dashboard Alert Grid widget
* Appliances no longer display an error in the Diagnostics tab of the Web Console when using a large proxy PAC file
* Custom Time Range now allows new settings for existing Reports
* Fixed an issue with Endpoint Data which caused no data to be displayed on the timeline when filtering by user
* Fixed an issue which could cause repositioned Reports widgets not to be saved in their new positions

## Questions and comments

Having pie on Pi Day? Got a favorite π pun you'd like to share with us?  [Send us an email](mailto:support@thousandeyes.com?subject=2018-03-14+Release+Update)!

