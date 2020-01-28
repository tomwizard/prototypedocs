# Release Notes: 2013-03-20

Our team has been hard at work over the last month working to bring you improvements on across the platform! A few of the bigger updates can be found below:

## Browserbot changed to use Chrome

We've updated our agent codebase to use Chrome for the Browserbot, instead of Firefox. This is a good thing: it's faster, more stable, and less buggy; Chrome will alleviate some of the concerns people have raised, mostly in relation to our Enterprise Agents. A list of key features affected by this will change is below.

* Page Loads now show the waterfall with mixed case URLs
* NTLM authentication works, in addition to basic authentication
* Browser session cleared after each page load / transaction test completes
* Better interaction with Selenium \(used in web transactions\)

This will affect customers with Enterprise Agents deployed in their infrastructure. We continuously update our agent codebase, and push these changes to all agents, seamlessly upgrading agents during periods of inactivity. The te-chrome package will be installed on all Enterprise Agents, and te-firefox will be removed. Users monitoring their logs and wanting to exclude the BrowserBot can continue to do so by filtering on Chrome version 99, rather than Firefox. We do not anticipate any deployment hiccups during this process, and as always, agents will continue collecting data during any period of downtime or upgrade. We'll monitor our agent deployment carefully, so as to avoid any unforeseen downtime.

## Minor bugs squashed

We've also optimized code and resolved some minor UI errors reported by our customers. This includes the following:

* Using the views menu to open BGP View would sometimes result in a server error.
* The location selector in DNSSEC view would sometimes not update when a different location was selected from either the world view, or the detailed metrics table.
* Certain links in the DNS+ views were not functioning correctly

## Documentation available!

Since we released our updated Customer Success Center last release, we've been hard at work developing some basic documentation for our knowledge base. Articles are now available for each of the major areas and views in the platform. This includes items like the [Getting Started Guide](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmaKAC), as well as sections on each major view of the product. Have a look, ask questions as needed, suggest updates and/or needed documentation.... we're happy to answer and here to make you successful.

We've also launched a contact number for customers experiencing critical issues: +1 \(415\) 237-EYES.

