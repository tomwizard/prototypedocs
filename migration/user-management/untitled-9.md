# How to Configure SCIM with Okta

### How to Configure SCIM with Okta

ThousandEyes users can be added, deleted and modified using SCIM 2.0 and 1.1 compatible identity providers, dramatically decreasing time to provision users into ThousandEyes. This document describes the integration between identity provider Okta and ThousandEyes.

This integration has been fully tested by Okta and ThousandEyes but it's currently not available for all Okta organizations. If you wish to try user provisioning on ThousandEyes through Okta, please reach us at support@thousandeyes.com.

### [Prerequisites]()

 To perform configuration in ThousandEyes,  a user having a role with the following permissions is required:

* View Users
* Edit Users
* API Access

### [Supported Features]()

* User provisioning \(creation\)
* User deletion
* User modification
  * Display name

 Group information or other user attributes cannot be translated into Account Groups, Roles or any other ThousandEyes structure.

### [Configuration]()

 To begin, open Okta and click on the **Admin** button on the top right:

IMAGE MISSING

Once in the dashboard, click on the Applications menu, and then on the Applications sub menu:

IMAGE MISSING

Click on **Add Application**:

IMAGE MISSING

Type “ThousandEyes” in the search bar, then click on the **Add** button of the listed ThousandEyes App:

IMAGE MISSING

Type in a Name for your Application, then click Next:

IMAGE MISSING

Under “Application username format” select in the drop down menu the “Email” option.

If you wish to configure SAML 2.0 SSO click on the “View Setup Instructions” button and follow the steps on the following page to finish SSO configuration in ThousandEyes. Otherwise, you can ignore this part of the configuration and click **Next**. 

IMAGE MISSING

In the provisioning settings, check the **Enable provisioning features** box:

IMAGE MISSING

Now enter the following information in the “API Credentials” form:

* **Username**: ThousandEyes username \(email\) with a role having permissions to create accounts
* **Password**: API token of the selected ThousandEyes user \(found on the Account Settings &gt; Security & Authentication tab\) IMAGE MISSING

Click on **Test API credentials** to make sure the API token and username were entered correctly. This should return a message similar to this one:

IMAGE MISSING

If an error is present, verify that the selected user has the permissions stated in the Requirements section of this document. If the issues persist, please contact ThousandEyes Customer Success Center \(support@thousandeyes.com\) to assist.

Under “Provisioning Features” select the following options:

* **User Import** - Enabled
* **Schedule Import** - Select a time
* **Okta username format** - Email address IMAGE MISSING
* **Create Users** - Enabled
* **Update User Attributes** - Enabled
* **Deactivate Users** - Enabled IMAGE MISSING

Once this is completed, click on **Next**.  
 

Optional: Add users now so they are integrated to the App. Otherwise just click on “Next”

IMAGE MISSING

And click on “Done” to finish the configuration:

IMAGE MISSING

At this point of time, setup of SCIM with ThousandEyes is complete.

### [Testing the SCIM integration]()

#### [Adding Users]()

To verify that the integration is working, add a user to the Application.

From the home page, go to Applications &gt; Applications

IMAGE MISSING

Then click in the newly added app:

IMAGE MISSING

Now click on **Assign to People:**

IMAGE MISSING

Select the people you want to be pushed to ThousandEyes as users by clicking on the **Assign** button next to them:

IMAGE MISSING

Then click on **Save and Go Back** after reviewing the user information:

IMAGE MISSING

Repeat this for all users you want to push to ThousandEyes. When done, click on **Done**:

IMAGE MISSING

If the User ID \(email\) is already registered with ThousandEyes, then the new access, permissions and roles will be configured accordingly on this user, matching what was configured in the “SCIM Settings” section of your organization’s Security and Authentication settings:

IMAGE MISSING

If the user doesn’t exist, it will be created in ThousandEyes and no registration or activation will be required from the newly created user.

Within ThousandEyes, the user should be visible shortly after it was associated with the service from Okta. To validate this, go to the Users section within Account Settings and verify the newly added user is present there:

IMAGE MISSING

#### [Removing Users]()

To delete an user, open the Application from Okta,

From the home page, go to Applications &gt; Applications

IMAGE MISSING

Then click in the newly added app:

IMAGE MISSING

Now click on the “X” button next to the user you want to delete:

IMAGE MISSING

Confirm the prompt to verify that the user will be unassigned from the Application:

IMAGE MISSING

The user should be shortly deleted from ThousandEyes. This is also verifiable within the Users section within Account Settings

IMAGE MISSING

