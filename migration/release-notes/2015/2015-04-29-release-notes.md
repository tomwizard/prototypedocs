# Release Notes: 2015-04-29

### Release update 2015-04-29

While our team has been just as busy as ever creating new components and features for our customers, this week's release contains only a couple of user-visible updates.

## Client-side certificate handling

We've introduced the ability to supply a client-side certificate in the configuration of an HTTP server test. To supply a certificate, open the Advanced tab and copy the certificate \(including both the private key and the certificate\) into the client certificate field of the test configuration.  When adding the certificate, you'll need to provide both the private key and certificate, in order for the certificate to be considered valid.  

Many systems create certificates in PKCS\#12 format.  Since our certificate handling process requires the certificate to be in text format, please note that you can export the certificate using openSSL, using the following command:

```text
$ openssl pkcs12 -in mycert.pfx -out clientcert.pem -nodes -passin pass:<password>
```

Check out our test settings article [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000Cmn7KAC).

## New Cloud Agent locations

We've added cloud agent locations in the following locations over the course of the last release cycle:

* Cordoba, Argentina
* Maidenhead, UK
* Cambridge, UK
* Portsmouth, UK
* Johannesburg, South Africa

These agent locations are available to paying customers; Cloud agents available on trial accounts pull from a different set of locations.

## Legacy report transition

Our team is in the process of transitioning our legacy reports out of production and focusing users on the new version of our Reports module.  Watch for an email from members of our customer success organization offering assistance in converting to the new version of reports, if you're using our legacy version for scheduled reports.

## API v2 and 3

As mentioned in our March 4, 2015 release notes, we are in the process of transitioning out versions 2 and 3 of the ThousandEyes API.  This transition will occur on June 4, 2015, at which point calls to either version 2 or version 3 of our API will cease to return data.  If you've been contacted by members of the ThousandEyes Customer Success organization offering transition assistance, we strongly encourage you to take us up on the offer.

## Bugs squashed

We've also made a few bug fixes in tonight's release.  

### Report snapshot emails

We've corrected an issue which would cause embedded images in report snapshot emails to be grouped at the bottom of the snapshot email in certain clients.  

### Account group creation

Account group creation was failing under certain circumstances where a user account was created and assigned to an account group with no role.

## We still love feedback

As always, if you've got something interesting to say about these release notes, a feature covered here, or just want to say hi, please feel free to [contact us.](mailto:support@thousandeyes.com?subject=Release+Notes+2015-04-29)

