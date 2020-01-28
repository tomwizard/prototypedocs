# Displaying and Alerting for Cloud Unit consumption

ThousandEyes customers who use Cloud Agents have a monthly allotment of units to allocate for tests assigned to those Agents.  The number of Cloud Units per month is specified in the customer's contract.  Customers can be kept up to date on current and projected future usage through the **Usage** tab of the [Account Settings](https://app.thousandeyes.com/settings/account/) page.  Additionally, the ThousandEyes platform will automatically warn the user through the Notifications menu of the app, as well as email the warnings to an organization's billing contact.

Information on units and the formula to calculate the units used by a given configuration of a test can be found in the Knowledge Base article [How Unit consumption works](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmoKAC).

## Current and estimated monthly consumption

The **Usage** tab displays the number of Cloud Units used to date, in your monthly billing cycle.  Additionally, in order to maximize your use of the platform without incurring additional charges or hitting usage limits, ThousandEyes provides a projection of the units which will be used by the end of your billing cycle, based on your unit consumption to date, the rate you are currently using units, and the time remaining in the monthly billing cycle.

In mathematical terms, the projected units, ![](https://lh6.googleusercontent.com/s1SfphKnLr8Ep47W1r0z2FqeLMaM3lA51vVP3wHfJtbxQi6fpoFBNwhaVu603Di0KB83Ufb5Nws2Jgxn261vSWw87mazJW51lga_crPqVRyH-e5LzyWxwZh8mH23oqsgXQ), are calculated by adding the amount of units consumed since the beginning of the cycle,![](https://lh3.googleusercontent.com/ST88XV89S91Cm3ORdLg6-6Vu7ylX0Sls7ZMzghOeCD0K2Cu4HjT3yhipU27LEXIwsga1OJLpZCkVOX9xCX9BHctrI1TAONkO62sfaxPrtMlr8OdRyXFMnvmQquUe5NiPyg), to the units per month cost of the currently configured tests,![](https://lh4.googleusercontent.com/UCXgD9jz903gaOHwbWc4gTN0xZ50IVHownd4EXhmctj-YQivMOMJgOyNk9sAdHjXbMgbQYzzEH8opEOGTUj3daV6nWn2JKbderQI7zFMYjHcieatmAm7FyaQatTPNU7wNw),  multiplied by the fraction of the rounds remaining in the month divided by total rounds in the month:

IMAGE MISSING

Rounds in usage calculation are 15-minute intervals, used as the basic unit of time to handle calculations with fractions of a day. There are 96 rounds in a day \(1 round/15 minutes x 1440 minutes/day\).

Information on the number of Cloud Units consumed is updated every six hours.

### Usage tab panels

The top panel of the **Usage** tab displays the date range of your billing cycle, then provides information on both Cloud Unit usage and Enterprise Agent usage.  Current Cloud Unit usage is displayed both as a percentage of your total monthly units and as the actual units used, out of the monthly allotment.  Below that are the projections of the units used which will be used at the end of the current monthly billing cycle, and the next month's billing cycle, per the above formula. For Enterprise Agents, the number used out of the total allotment is displayed.

IMAGE MISSING

In the above example, as of the current date of December 14th, this organization has used 14% \(626,525 units\) of its total Cloud Unit monthly allotment \(4,320,000 units\) for the period November 29th to December 29th \(a 30-day billing cycle\).  However, at the current rate of Cloud Unit usage, the organization is projected to use 28% by the end of the billing cycle. This indicates the current rate of unit consumption is higher than earlier rate\(s\) of consumption in this billing cycle \(for example, if new tests were just added, then the rate of unit consumption is higher\). The next month's billing cycle is projected to use 31%.  This number is slightly more than the previous month because the projection for Next Month always uses a 31-day billing cycle, irrespective of the actual number of days in the next month's cycle, whereas the projection for This Month always uses the actual number of days in the billing cycle.

 We also see that the organization has installed 12 of its 30 Enterprise Agents.  Additionally, a link to the [Pricing Calculator](https://app.thousandeyes.com/calculator) is provided, in order for customers to calculate the cost of specific tests or of various scenarios.

The second panel of the **Usage** tab contains two tabs: **Cloud Unit Breakdown** and **Enterprise Agents Breakdown**.  The former displays current usage breakdowns by Account Group, Test Type and Test, and optionally breakdowns of the full month's estimated usage.  Check the **Show Estimations** box to display the "Estimated" units used below the currently used units, per the image below.

IMAGE MISSING

 The **Enterprise Agent Breakdown** tab shows usage of Enterprise Agents by Account Group: 

IMAGE MISSING

## Usage alerts

The following levels of projected and actual use by the organization will result in an email sent to the organization's billing contact:

* Estimated usage is greater than 100%
* Actual usage exceeds 90% AND the estimated usage is greater than 100%
* Actual usage exceeds 100%

If your projected or actual use exceeds 100%, you may wish to reduce the number of tests, investigate tests which have lower unit costs that can still meet your testing requirements, or have fewer Cloud Agents running the tests.  Using the metrics on the **Usage** tab, admins can locate the largest sources of unit consumption.

**NOTE:** Only users who have been assigned a role with the _View billing_ permission can view the Billing tab.  Only users who have been assigned a role with the _View organization usage_ permission can view the Usage tab.

**NOTE:** The billing contact Email field can only accomodate a single email address.  To distribute billing contact emails from ThousandEyes to multiple recipients within your organization, we recommend creating a distribution list within your organization and entering the distribution list's email address in the Email field of the billing contact information.  Be sure that senders outside your organization have permission to send email to the distribution list.

