# Release Notes: 2018-11-13

Welcome to tonight's release. The holiday season is upon us--starting with Halloween, through New Year's Day, we'll all be celebrating, giving thanks, remembering, honoring, looking back, looking forward, and lighting candles. Whatever traditions or holidays you may be celebrating, may your candles burn brightly.

In ThousandEyes blog news... Big news yesterday with the hijacking of routes to Google properties. Our Technical Marketing Manager, Ameet Naik, gives you the details in his blog post [Internet Vulnerability Takes Down Google](https://blog.thousandeyes.com/internet-vulnerability-takes-down-google/). Ameet got a fast start on the analysis thanks to having Endpoint Agent installed on laptops around the ThousandEyes office. If you want to know who done it, Ameet's post will tell you who the guilty party is. Added bonus: see the outage through the eyes of an Endpoint Agent.

On a happier note, ThousandEyes released its [first annual report](https://www.thousandeyes.com/resources/2018-public-cloud-performance-benchmark-report?utm_source=blog) on the major cloud infrastructure providers \(Google GCP, Microsoft Azure and Amazon AWS\) . We're very grateful for the positive responses the report has received; both critically and in numbers of downloads. Our Sr. Product Marketing Manager, Archana Kesavan, explains the need for the report and the methodology used, in her blog post [What 160M Public Cloud Performance Measurements Mean](https://blog.thousandeyes.com/what-160m-public-cloud-performance-measurements-mean/). If your organization uses any cloud infrastructure provider, you'll want to take a data-driven look at the infrastructures of the infrastructure providers. Not all clouds are created equal.

Going back to the end of October, we celebrated Halloween with two posts: Sr. Product Marketing Manager Angelique Medina strikes fear into our hearts by recapping this year's scary Internet tricks, in [In Outage Space, No One Can Hear You Scream](https://blog.thousandeyes.com/in-outage-space-no-one-can-hear-you-scream/). It reads short and sweet, like most Halloween candy. And our VP of Product Marketing, Alex Henthorn-Iwane, reprises a horror classic in [The Silence of the LANs](https://blog.thousandeyes.com/the-silence-of-the-lans/), a terrifying tale of troubleshooting. A bite-sized treat \(if you like bad puns\).

On a more serious note, Alex gives us a summary of his experiences attending a major Gartner event, in [Three CIO Takeaways from Gartner Symposium 2018](https://blog.thousandeyes.com/three-cio-takeaways-from-gartner-symposium-2018/). The summary of the summary: Security. Cloud monitoring. AI in Ops. Want details? Click that link.

And now for the details of the release...

## Cloud Agents

A big expansion in China, this week! We've added three new Cloud Agents in provider China Mobile:

* Chengdu, China
* Guangzhou, China
* Shanghai, China

你好! Ni hao!

## Reports

A couple improvements to Report Snapshots, to match the PDF-making features available with Reports, and the option to arrange Number cards in a Number widget.

### PDF download of Report Snapshots

In addition to downloading Reports as PDF files, users can now download Report Snapshots as PDF files. When viewing a Report Snapshot, a new **Share** button will be visible \(and the **Share this Snapshot** link will now be a button\):

IMAGE MISSING

### PDF attachments in Report Snapshots

When configuring a Report Snapshot to be emailed automatically, a PDF attachment of the Report can be included in the email.

IMAGE MISSING

On the [Reports page](https://app.thousandeyes.com/reports/), select the **Snapshots** link, then choose either create a new "Scheduled Snapshot" or "Edit Scheduled Snapshots". Click the **Include a PDF attachment of the Report** box to have the PDF attachment included in the emails.

### Arranging Number Cards

The Number Cards in a Number widget of an existing Report can now be arranged via drag and drop. Click the Settings icon of a Report to enter edit mode, then click the Card. The clicked Card will be highlighted, and will be draggable to new locations within the widget.

IMAGE MISSING

## Minor enhancements & bug fixes

Here are the minor enhancements and bug fixes in this week's release:

* API endpoints /agents and /agents/{agentId} now return the hostname field
* Fixed a bug that reverted changes to a duplicated Number card after the Report refresh
* Fixed a bug that could display incorrect coloring of Enterprise Agent status in the Map widget
* Fixed a bug that prevented embedded widgets from refreshing

## Questions and comments

Got feedback for us? Want to suggest a feature that would light your candle? [Send us an email](mailto:support@thousandeyes.com?subject=2018-11-13+Release+Update)!

