# Release Notes: 2014-03-05

Short and sweet for the week, here's a quick preview of what our team has been working on for the last few weeks.

## Dashboard Template Editor facelift

Our dashboard has developed a penchant for plastic surgery, and our development team has been putting some extra cycles into optimizing the dashboard editor workflow.  This week's update adjusts the workflow for working with new templates, removing the modal dialog and replacing it with an inline editor.  To work with the template editor, follow these simple instructions:

IMAGE MISSING

1. Open the template editor
2. Create a new template
3. Duplicate or delete\(\*\) the currently selected template

Once the Template editor is open, the dashboard will show up with a striped background.  Work with the settings in the metadata section of the editor to modify the template name, and define it as private, or as a default:

IMAGE MISSING

1. Create a copy of the template under a new name
2. Deletes the template
3. Sets the template as only accessible to your user
4. Sets the template as your default template
5. Sets the template as the default template for all users in your account
6. Widgets - to add a widget, drag it from the list into the template body below.  When the target area goes dark grey, you can drop the widget onto the page.

All widget settings remain the same as in previous releases.  When you're done making changes, click the **Done Editing** button to commit your changes.

## Cloud Agents

Cloud Agents are now available in the following locations:

* _Dublin, Ireland_
* _Brisbane, Australia_
* _Seoul, South Korea_

The following locations are in the process of being replaced.  Watch our release notes for more information regarding the availability of new and/or replacement agents:

* _Newark, New Jersey_ agents are being replaced by new agent infrastructure in _New York, NY_.  
* _London, England_ agents are being replaced with a more reliable location. 

## New Product Beta: Private BGP peering

We're beginning the beta process for customers who wish to increase their eBGP visibility by creating private multi-hop peering with our route collector. This feature will allow internal monitor visibility into BGP reachability, path changes and updates for all monitored prefixes.  To request enrollment in the private BGP peering beta, contact the ThousandEyes Customer Success team by sending us an [email](mailto:support@thousandeyes.com?subject=eBGP%20Peer%20Beta%20Request).

Check out the how-to article on the topic in [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmjKAC).  Our CTO Ricardo Oliveira will be publishing a blog post on the new feature shortly, so watch the blog for updates.

## Bugs Squashed

* API-based instant transaction tests: we corrected a minor issue which caused any user input to be translated to star characters in execution of transactions using the instant test capability of the ThousandEyes API.  This could cause unpredictable and/or unexpected transaction results.

