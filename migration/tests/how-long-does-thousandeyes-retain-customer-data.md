# How long does ThousandEyes retain customer data?

The ThousandEyes platform retains user data for a finite amount of time. This article covers the data retention periods in different features of the ThousandEyes platform.

## Test views

Test data in the Views is available for up to **31 days**, as seen in a test timeline.

IMAGE MISSING

It is possible to retain a period of data indefinitely using a Saved Event \(created with the **Save** button\). For more information on Saved Events, review the Knowledge Base article [Retaining data beyond the 90-day limit](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn3KAC).

Share Links created with the **Share** button are preserved indefinitely. Share Links created with the [API Snapshot endpoint](https://developer.thousandeyes.com/v6/snapshots/#/create) will expire after 30 days.

## Reports

Data for the Reports feature is available for **93 days**, as shown below. Report Snapshots \(created with the **Snapshots** button\) are preserved indefinitely.

## Alerts

Data for the Alerts feature is available for **90 days**, using the Alert History tab, as shown below.

## Application Programming Interface \(API\)

The [API](http://developer.thousandeyes.com/) retains the test data for **90 days**, with the exception of the following data types which are retained for **30 days**:

* Page Load data
* BGP data
* detailed Web Transaction data \(page-level and step-level detail\)
* detailed Path Visualization data \(per-hop data\)

## Trial accounts

ThousandEyes Trial accounts are limited in duration to 14 days. When the 14-day period ends, all tests stop running and all users, while still being able to log in, are limited to read-only operations. Test data from Trial accounts is available for 14 days, and then expired on a rolling basis. Data for the Reports feature is available for 31 days, and then expired on a rolling basis.

## User audit history

ThousandEyes maintains an audit history \(accessible via the [Activity Log](https://app.thousandeyes.com/settings/account/?section=activityLog)\).  Data is retained for 2 years, and expired on a rolling basis.

## How is retention policy applied to test results data?

Organization's current data retention policy is applied to test results data **when the data is uploaded into the platform**. This means that data that has been uploaded during a trial period \(trial accounts have 14/31-day data retention span, see above\) will not have its retention policy adjusted to 31/93 days when a trial account is converted into a paid account. On the other hand, the data that is uploaded into the platform after the conversion to a paid account has already happened will be retained for the contracted amount of time \(31/91 days, see above\).

