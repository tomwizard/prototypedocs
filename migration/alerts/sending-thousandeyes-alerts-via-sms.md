# Sending ThousandEyes Alerts via SMS

An often-asked question is how to send ThousandEyes Alerts to a Small Message Service \(SMS, commonly referred to as "texting"\) enabled device such as a smartphone.  ThousandEyes does not provide an SMS service or SMS integration, but customers can send ThousandEyes Alerts via SMS using their mobile provider's SMTP-to-SMS \(email-to-txt\) gateway. 

With an email-to-txt gateway, email can be sent to a special address which will convert the email to a text, and send the text to the phone number associated with that email address.  Most commonly \(in the USA\), the email address is the 10-digit phone number, followed by the '@' sign, then the email domain the provider uses for email-to-txt messaging.  For example, the fictitious provider "MegaISP" might use an email address of _4155556789@txt.megaisp.com_ for the customer whose phone number is \(415\) 555-6789.

A number of publicly accessible web sites list mobile providers and the email address formats used to send email to their mobile customers.  A list of those web sites can be found [here](https://www.google.com/?gws_rd=ssl#q=list+email+to+text).

Once the correct email address is known, the **Send emails to** field of an Alert Rule can be configured with the needed email addresses, which will send the Alerts to SMS-enabled devices.  The **Send emails to** field is located under the **Notifications** tab of your Alert Rule configuration.

IMAGE MISSING

Click the **Edit emails** link to add the email address to the list of available email addresses, if this is the first time assigning the email address to an Alert Rule.  Once the new email is added to the list of emails in your Account Group, a notification will be sent to the new email address, which will verify the email-to-text process is working.

