# Release Notes: 2014-07-09

Hard to believe, but we're already halfway through the year!  Some interesting updates have come through, but as Mr. Sinatra once said, the best is yet to come... We've made some changes in the product in this week's release; check out the list below.

## Agent nomenclature change

Per the email notification that went out on July 7, we've made some terminology changes for our agents:

* **Enterprise Agents** are now known as **Enterprise Agents**
* **Cloud Agents** are now known as **Cloud Agents**
* Our Agent **collector** is now called a **Collector**

Built-in Agent groups have been updated to reflect the new agent Labels. This doesn't impact any of the features provided by either Cloud or Enterprise agents, but will impact our documentation and labels in the user interface.

## BGP options

We've added the ability to toggle BGP data collection on or off for tests which include network measurements. Previously, BGP data collection was enabled for all tests which include network measurements, unless the target was a CDN-hosted domain. With tonight's change, you can now select whether or not you want BGP data to be collected against your target domain - and can individually select which BGP monitors will be polled for reachability, path changes and updates. This flag will default to enabled for all tests, with the exception of those testing CDN-hosted targets. CDN-hosted targets will have the option disabled by default, but can be overridden.  

IMAGE MISSING

As a reminder, BGP data is not collected from ThousandEyes Agents; we aggregate information from public BGP aggregators, or private BGP peers, and monitor the availability of your target prefixes from each of those peers.

## HTTP Server content verification

The content verification option on HTTP server tests will run content verification of response headers, in addition to the response content.  We have done an analysis on tests which include content verification, and notified customers we believe will be affected by this change.

## Alert Rules

An option to validate DNS mappings has been added to alert rule options for DNS Trace, DNS Server and DNS+ Domain tests. Mappings can now match on specific IP lists, wildcarded domains, or on network prefixes. Sample valid options are shown below:

Mapping is not in 1.2.3.0/30  
Mapping is not in 2.3.4.1, 2.3.4.2  
Mapping is not in \*.mydomain.com  
Mapping is not in myserver.otherdomain.com, myserver2.otherdomain.com

Text-based options \(\*.mydomain.com, myserver.otherdomain.com\) should only be used in cases where a string record \(such as CNAME or TXT\) is being requested. Also, note that the asterisk character will only be treated as a wildcard if it is the first character in the string.

## Agent package changes

### Ubuntu 14.04 LTS Support

We've released our Enterprise Agent code for Ubuntu 14.04 LTS Server. To install a ThousandEyes Enterprise agent on Ubuntu 14.04, simply follow the instructions on the [Add Agent](https://app.thousandeyes.com/agent-settings?s=1) page, under the Linux Package Installation option.

### Browserbot dependencies updated

We've updated our package dependencies for the ThousandEyes Enterprise Agent.  The Browserbot package will now require te-chromium, instead of te-google-chrome.  No action is required on behalf of our customers; these packages will self-update.

In the next two weeks, we will be releasing recursive dependency lists for both the te-agent and te-browserbot packages, across all supported operating systems for our enterprise agents.

## API Changes

Version 4 of our API has been released, and version 1 is now deprecated. Check out the [change summary](http://developer.thousandeyes.com/#/changesummary) on our [developer reference site](http://developer.thousandeyes.com/) for a list of updates.

