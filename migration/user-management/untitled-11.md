# Adding user indicates email address "is valid but cannot be added at this time"

Occasionally, attempting to add a new user via the Users tab to an organization in the ThousandEyes platform results in an error message indicating that the email address "is valid but cannot be added at this time":

IMAGE MISSING

The error is caused by the email address having previously been used to set up a Trial organization in ThousandEyes. An email address can be used in multiple organizations if all organizations have Standard or Pro plans \(paid subscriptions\), but an email address can only be used once if used in an unpaid organization \(Trial, or the Lite plan that Trial plans become upon trial period expiration\).

## Resolution

 Two options are available to resolve the issue:

1. Use a unique address
2. Delete the Trial or Lite organization

### Using a unique address

 A unique email address can be used in one of two ways:

* Change the email address on the existing Trial or Lite organization
* Use a different email address to add the user to the Standard or Pro organization

 If a different email address is not available, or use of two separate email accounts is not desirable, consider whether your email provider permits address extensions such as "username+extension@domain".  For example, if Joe Smith opened a Trial account with the email address jsmith@thousandeyes.com, then Joe could be given an account in a paid organization by using jsmith+newname@thousandeyes.com.  The thousandeyes.com email domain supports address extensions, and so will deliver email to jsmith+newname@thousandeyes.com to the jsmith email account.

### Deleting the Trial or Lite organization

To delete the Trial or Lite organization, log into ThousandEyes using the email address that generated the error.  Open the [Account Settings](https://app.thousandeyes.com/settings/account/?section=usage) page and navigate to the **Usage** tab.  Click the **Delete** button to delete the account permanently.

IMAGE MISSING

 Once the account has been deleted, you cannot recover the account, nor open a new Trial or Lite account using the same email address.

