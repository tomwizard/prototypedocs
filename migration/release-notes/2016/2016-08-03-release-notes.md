# Release Notes: 2016-08-03

Welcome to August! Time for a field day!

IMAGE MISSING

ThousandEyes will be one of ten presenting sponsors at the Tech Field Day conference’s Networking Field on Friday, August 12th.  You can stream the presentation live from 10 AM to 12 PM PDT from the [Networking Field Day page](), with a recording available later via YouTube.  If you're not familiar with Networking Field Day, we encourage you to check it out. Click the link for all the details.

Now, on to this week's product updates...

## FTP Tests

As part of our ongoing effort to add functionalities for our new FTP Test type, we now provide reporting capability for FTP Tests \(API access will be coming in the next release\). Additionally, we now support secure FTP transfer through both the FTPS \(FTP over SSL/TLS\) and SFTP protocols.  An example of an SFTP test being configured:

IMAGE MISSING

Username and password are required.

## Page Load Tests

We’ve added the ability to configure the HTTP Server portion of a Page Load test with the Verify Content feature that exists in the stand-alone HTTP Server test. You can now configure a regular expression-based string to match the content in the target of the Page Load test.

## Alert Rules

When adding an Alert Rule to a test that has Alerts disabled, we now provide a message to the user to indicate that the test is not currently configured to trigger Alerts.  In addition, we’ve clarified the wording on the Alert Conditions for specifying the number of times a condition must be met, either in a row or the number of rounds met out of a larger number of rounds.

## Bugs squashed

* We’ve corrected an issue for FTP Server tests that required re-entry of the password with every configuration change.
* We’ve corrected an issue that caused certain alerts not to trigger, or trigger earlier than their configuration specified.
* Custom Headers defined in test settings are now displayed in the Requests tab, when the Headers link is clicked.

## Questions or comments?

Got a bug? Question? A comment? A shout-out? We would love to hear from you! [Send us](mailto:support@thousandeyes.com) whatever you got!

