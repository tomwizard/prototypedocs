# Sharing Test Data

The ThousandEyes platform provides the **Sharing** menu for users to share test data, either with other users of the ThousandEyes platform or with people who are not users of the platform. You can collaborate with the same graphical view of test results, allowing you to troubleshoot with colleagues, partners or providers, regardless of whether they subscribe to the ThousandEyes platform.

This article explains the two options for sharing test data: Snapshots and Live Shares.  Snapshots let you share test data with anyone, regardless of whether they subscribe to the ThousandEyes platform.  Live Shares permit sharing of test data with other users of the ThousandEyes platform. The article also discusses the Export Data option, which extracts data from our API without requiring the user to create an API query or use additional tools outside the ThousandEyes platform.

## Snapshots

For sharing data with people regardless of whether they are subscribed to the ThousandEyes platform, the Snapshot feature allows you to provide a URL, called a Share Link, to a read-only ThousandEyes test results web page.  This test results page is viewable by anyone who has the Share Link. You can revoke this link at any time.  Snapshots display up to four days of test data in a standard test results page format.

### Snapshot creation and deletion

To create a Snapshot, go to the results page of the test you would like to share.  On the timeline, click on a test round that begins, ends or is in the middle of the data of interest, then select the **Share** button at the upper right corner of the page:

IMAGE MISSING

Clicking on the **Share** button will display the sharing panel, with the Snapshot Sharing tab active:

IMAGE MISSING

1. Select the length of the data window to be shared, up to two days.
2. Select the location in time of the data window you selected in the previous step.  Options are "starting at", "around", and "ending at".
3. Optionally, you may send an email from the ThousandEyes platform with the share link.  Enter the email address of the recipient.
4. If sending an email message from the previous step, you may optionally include a note in the body of the email.  Enter the text of the note in this field.
5. Click the **Link to this snapshot** link to display the Share Link.  Copy the link to your clipboard and paste into a document, a chat or any other application.
6. Click the **Share** button to email your Share Link to the email recipients.  If you do not need to email the Share Link and only wish to copy the Share Link, you can click the **Cancel** button.  Share Link creation does not require clicking the **Share** button.

Recipients of the Share Link will see the timeline set to the same round and View set to the same one as used at the creation of the snapshot.

To remove a Share Link created by a user in your Account Group, navigate to **Sharing &gt; Snapshots**. On the **Shared by users in my account group** tab, locate the row with the name of the test that was shared.  Click the Trash icon to invalidate the link.  You will be prompted to confirm deletion, since the deletion cannot be undone.

IMAGE MISSING

If a test has multiple Snapshots \(such as test "ThousandEyes Customer Success Center", above\), then expand a row and compare the Share Link URL you want to delete to the Share Link listed under in the expanded row, or use the Snapshot Date range column, in order to identify which of the rows is the desired Snapshot to be deleted:

IMAGE MISSING

Once the deletion is confirmed, people who possess the Share Link will no longer be able to view the data.

### Working with Snapshots

As shown in the previous image. the **Sharing &gt; Snapshots** page provides functionality in addition to the delete function.

The **Shared by users In my account group** tab has a table with the following columns:

* **Test Name:** The name of the test from which the Snapshot was taken. 
* **Snapshot Date:** The range in time of the Snapshots data, specified by a date and time, followed by a **+ -** or **±** depending on which setting of 'starting at", 'ending at" or "around' \(respectively\) was used at the time the Snapshot was created \(see \#2 from the "Sharing panel", above\). 
* **Create Date:** The date and time of Snapshot creation.
* **Visits:** The number of times the Share Link has been accessed.

Click on any of the column headings to sort by that column. Click a second time to reverse the order of the sort in the chosen column.

Clicking on a row to expand it will display the following:

* The Snapshot's Share Link \(URL\)
* **Most recent visits**: This section displays the most recent accesses of the Snapshot.  The date of the visit is displayed in hours since the visit.  If the user is a ThousandEyes user and has recently logged in, the user's ThousandEyes name and login ID \(email address\) are displayed, along with the IP address of the visitor's client.
* **Allow only ThousandEyes users to comment:** This box can be checked to prevent Share Link users who do not have ThousandEyes accounts from using the Comments feature. Snapshot recipients can make comments and communicate with the Snapshot creator via the Messenger panel, available on the Snapshot page. Click on the Messaging tool icon in the upper right corner of a Snapshot page to display the Messenger panel: IMAGE MISSING

When Snapshot recipients leave comments, the Snapshot's creator will receive email notification.

The **Shared with me** tab provides a listing of Share Links that other users of the ThousandEyes platform have shared with you.  The columns have the same definitions as above, with the substitution of **Created By** column, which shows the ThousandEyes name of the test creator, as determined by the Name field of the user's [Profile page](https://app.thousandeyes.com/settings/account/?section=profile).

## Live Shares

If the desired recipient of your data is a ThousandEyes customer but not a user in your Account Group \(your current Account Group's name is found by clicking on the User Menu icon in the upper right corner of the ThousandEyes interface\) then you can provide them with a Live Share.  A Live Share is a read-only view of a test's results web page, allowing access to current data, and past data starting from the time of the share's creation. The Live Share's test can be displayed on the recipient's Dashboard, can be the source for new reports, and can in other ways \(though not all ways, e.g. the test can't be deleted\) be treated as a test that belongs to that user's Account Group. As with a Share Link, you can terminate the Live Share at any time.  Live Shares must first be accepted by the desired recipient in order for the shared test to appear in their account.

### Live Share creation and deletion

To create a Live Share for other ThousandEyes users, or to accept a Live Share, go to the [Test Settings](https://app.thousandeyes.com/settings/tests/) page:

IMAGE MISSING

1. Click the "Pending Shares" link at the top of the Test Settings page to display a panel listing all Live Shares other ThousandEyes users have sent to you, awaiting your acceptance. You may accept them or decline them.
2. A listing of Account Groups within your Organization, if your Organization has multiple Account Groups \(the link will not be displayed if your Organization has only one Account Group\).  Check the box next to an Account Group you want to grant access to the Live Share. The link will indicate the number of Account Groups with access to the Live Share, out of the total number of Account Groups in your Organization.
3. For users outside your Organization, click the "Share with other customers" link to display a panel which will allow you to email your desired recipient.  Use the email address which is used by them as their ThousandEyes login.  The link will change to "X other customers" where X is the number of Organizations which have received and accepted the Live Share.  All Account Groups within the Organization will have access to the Live Share. IMAGE MISSING

To delete Live Shares that you provided to another Account Group, click on the "X of  Y account groups" link per step 2 above to display the listing of Account Groups.  Uncheck the box of the Account Group you no longer wish to have access to the Live Share.

To delete Live Shares that you provided to a different Organization, click on the "X other customers" link per step 3 above to display a panel to edit and delete your LIve Share recipients:

IMAGE MISSING

Click the Trash icon to delete a recipient. The Live Share will no longer be available to that Organization.

### Exporting Data

Another method to provide access to your data is to use the ThousandEyes API.  Clicking the **Share** button on a test results page ****displays the sharing panel, which contains the **Snapshot Sharing** tab and the **Export Data** tab.  The latter tab allows you to select a period of data \(up to 1 hour\) to display, making a query to the ThousandEyes API automatically, and opening a new browser window to display the results. The data is rendered in either JSON or XML format You can copy the results to your clipboard and paste into a document, or saved as a file via your browser's Save menu option.

IMAGE MISSING

