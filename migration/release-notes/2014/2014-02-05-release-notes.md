# Release Notes: 2014-02-05

Short and sweet, leading up to Valentine's day, please find below a list of updates for our February 5, 2014 release.

## Custom Virtual Appliance

Released in Beta in the last quarter of 2013, the Custom Virtual Appliance builder allows companies to generate custom versions of the ThousandEyes Virtual Appliance, for use as a Enterprise Agent.  Extremely useful for widescale Enterprise Agent deployment, or deployment into client sites, the Custom Virtual Appliance allows organizations to pre-fill the account token used by the agent to communicate with ThousandEyes, as well as proxy and advanced access settings, including SSH keys.

Check out our Custom Virtual Appliance article at this [link](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnYKAS).

##  BGP Covering and Covered Prefixes

Under the BGP Route Visualization view, if your tested prefix has another test running for a covered or covering prefix, links to the BGP view for the covered/covering prefixes will be shown, just above the Quick Selection area of the page.  An example of each is shown below.  

What are covered and covering prefixes?

* A **covered prefix** is a prefix, for which a shorter prefix \(shorter subnet mask\) is being monitored, which contains the covered prefix.  For example, 8.8.8.0/24 is covered by 8.8.0.0/16.
* A **covering prefix** is exactly the opposite of a covered prefix: it's a shorter prefix which contains the covering prefix.  For example, 8.8.0.0/16 is a covering prefix for 8.8.8.0/24.

IMAGE MISSING

## Register your domain

We've granted access to the My Domains and Networks settings interface, which was previously in Beta.  Using this interface, organizations can register their domain names, such that users using the live share capability of the platform can share results with your domain, rather than a specific user, as well as in some upcoming features.  

To access the domain registration interface, click **Settings** &gt; **My Domains & Networks**.  Click the **Domains** tab, and enter the domain name you wish to register.  There are two methods of registration: using DNS and using Email.

* To register a domain using DNS, you'll need to place a TXT record into DNS for domain, according to the instructions that appear on the screen
* To register a domain using Email, we look up data from the whois information associated with your domain, and pull a list of technical and administrative contacts.  You can pick the address to whom the email will be sent from this list.  Once chosen, an email containing a verification link will be sent to this address, confirming ownership of the domain.  

Domains are registered at the account level, rather than the organization level.  If you have multiple accounts in an organization requiring that the same domain is registered, please contact support.

We strongly recommend that organizations _validate_ _their primary email domain_, in order to ensure prompt delivery of live share requests.

##  Proxied agents

Proxied agents now show an icon IMAGE MISSING beside the agent in detailed test results, to help distinguish them from agents which are not behind a proxy.  Hovering over the proxy icon shows the name of the proxy.

## API Changes

Saved event data is now available in the API.  Saved events are listed under the /tests/ endpoint, with a property of savedEvent = 1, and can be accessed using the same method as the equivalent /tests/ response.

