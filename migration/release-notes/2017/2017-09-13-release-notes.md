# Release Notes: 2017-09-13

Welcome to the last release of the summer \(or winter, for our friends in the southern hemisphere\)!

If you're in the neighborhood of Sheffield, England, today was the start of the UK Network Operators Forum. If you're attending [UKNOF38](https://indico.uknof.org.uk/event/40/), ThousandEyes is a sponsor and presenter, so feel free to seek out one of our folks and say hello. If you missed it, the presentation slides for [Decoding Major Internet Outages in 2017](https://indico.uknof.org.uk/event/40/contribution/16) by ThousandEyes Solutions Engineer Nitin Nayar are available online. Click that link to see how ThousandEyes saw major events affecting Amazon Web Services, Marketo and other big logos.

No new ThousandEyes blog posts to talk up, this release. So we'll just take this space to extend best wishes to peoples around the world who've been affected by disasters natural or otherwise, and express our hopes for a quick return to safety and normalcy.

## Cloud Agents

Our Operations team has been working hard to bring new Cloud Agent locations online; see below for a list of new locations.

### IPv6

* Brisbane, Australia
* Cork, Ireland
* Oslo, Norway
* Osaka, Japan
* Salt Lake City, Utah, USA
* Vienna, Austria
* Zurich, Switzerland

### IPv4 and IPv6

* Brussels, Belgium \(replacing Bruges, Belgium\)

## New live chat

For those customers who enjoy communicating with our Customer Success team via chat, we’re proud to introduce a new in-app chat, which will provide our customers with a much richer support experience. This new platform will provide many new benefits, both now and in the future. Read all about it in the ThousandEyes Knowledge Base article [Using ThousandEyes Live Chat](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RwiCAE).

## API version changes

Per our API Change Policy, we will be changing the default version of the ThousandEyes API from version 5 to version 6, effective as of our release on September 27th, 2017. Timelines for deprecation and other policies governing API version changes can be found in the [Change Policy section](http://developer.thousandeyes.com/#/versioning) of our API documentation, along with instructions for specifying the API version in your query.

Users whose queries specify version 4 \(queries which begin with [https://api.thousandeyes.com/v4\](https://api.thousandeyes.com/v4\)\) will have 90 days from the date of the switch to make the necessary changes to their queries. After the 90-day transition period, version 4 will no longer be available. We recommend updating any v4-based queries to use the current version of the API \(no specification of version in the query\) in order to avoid the need for future changes.

## Dashboard widgets change

For customers who use Dashboard widgets on big displays in your NOC's and SOC's, note that in the next release on September 27th we will be making changes to widgets which may require that customers re-login, depending on the type of data that the widget displays. Be sure that someone knows how to log into the requisite account if your organization requires continual display of the information!

## TLS 1.0 deprecation

As part of our compliance with the Payment Card Industry \(PCI\) Security Council's [Data Security Standards](https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security) \(DSS\), ThousandEyes will be deprecating the use of TLS version 1.0 within our infrastructure. Customers who use older clients which cannot support these versions must upgrade the clients to support newer versions of TLS. Consult the ThousandEyes Knowledge Base article [TLS 1.0 Deprecation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009RwdCAE) for more information.

## Minor features and bug fixes

* A Dashboard Tests widget now allows filtering tests by test label \("Label ID" in the **Filter** and **Exclude** selectors\).
* The Virtual Appliance web server now supports 2048-bit Diffie-Hellman groups.
* Fixed an issue which prevented modification of BrowserBot test settings.
* Fixed a window-closing condition that would cause Transaction tests not to complete.
* Fixed a Transaction test issue that could cause a long error message displayed on the Map tab to be truncated.
* Fixed an issue on the Path Visualization that caused inconsistent coloration of the target icons for Agent to Agent tests.
* Fixed an issue which could cause an Active Alerts red dot icon to appear on the Active Alerts tab when no alerts were active.
* Fixed an API issue which caused the /agents endpoint not to return a value of "Disabled".

## Questions and comments

Want to tell us your opinion of our new live chat features, or what you'd like to see for new chat features in the future? [Send us an email](mailto:support@thousandeyes.com?subject=2017-09-13+Release+Update) \(or open a chat\).

