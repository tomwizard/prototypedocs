# How to Configure SCIM with Okta

### How to Configure SCIM with Okta

ThousandEyes users can be added, deleted and modified using SCIM 2.0 and 1.1 compatible identity providers, dramatically decreasing time to provision users into ThousandEyes. This document describes the integration between identity provider Okta and ThousandEyes.

This integration has been fully tested by Okta and ThousandEyes but it's currently not available for all Okta organizations. If you wish to try user provisioning on ThousandEyes through Okta, please reach us at support@thousandeyes.com.

## Table of Contents

* [Prerequisites]()
* [Supported Features]()
* [Configuration]()
* [Testing the SCIM integration]()
  * [Adding Users]()
  * [Removing Users]()

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

![](https://lh6.googleusercontent.com/DVe3oU82RNgJUdIXZ5TSmRzq8g6mlh-HPapNpp_x4y5_c6NXfnaBHEgnoB-eeHqhuLzKEsXFxKpNOZwVSaNR4gFiaMXASK81CSUFkMcm5OowvPXqCGPimTyiZYurrKT43TyN3Nb5)

Once in the dashboard, click on the Applications menu, and then on the Applications sub menu:

![](https://lh5.googleusercontent.com/kQix0ZoKMsUTOSxOTIpXTxegdFXXuAEi0Ia2LfrcKnkrpll6gvwBjJB5IQfANQlhOHts2WEadaQ-yGCRP6TBtIVQrqWUX_r8DdCOvl9XJFrIg7rxon2a1NR0ZoTtq4Xj0xCXhOWO)

Click on **Add Application**:

![](https://lh6.googleusercontent.com/a3qpuAJn3ob1ITpv8drlA_Yt2iJ-2KsLoUM7kHmlm9DSnkeHdC49wxh07kAMhySs-DVTyu_L4MRxlB2YTNO2vAkpxaItCFd1RjsUzeu74PBqGzdgcbOdsU0s6093-4bUbtddj9-1)

Type “ThousandEyes” in the search bar, then click on the **Add** button of the listed ThousandEyes App:

![](https://lh3.googleusercontent.com/9aBJvkacOmFROAnU1fU4vdntvhXaw_K38muR7EM9deZEQFFnMHhY4vjA48yup9VHXnq7tN4EluvtbTnLvHttYGq5X-qrEuX7YUbbSmXigbut_B-50LFKhgWR2F5Rid9d-5m4sjwF)

Type in a Name for your Application, then click Next:

![](https://lh3.googleusercontent.com/i2fbjpXVehStXIa0MIbStjpn1r-viZr3Le3R5M72nD48tunPdEcWJ-pI9kDer1IGGX_PKFocNGrGeyacgZdBJCvwdZHQMNnp5aeBKvj6l2ZCQHd1pQruTMpxKqehnoAN5_kPirMh)

Under “Application username format” select in the drop down menu the “Email” option.  
 

If you wish to configure SAML 2.0 SSO click on the “View Setup Instructions” button and follow the steps on the following page to finish SSO configuration in ThousandEyes. Otherwise, you can ignore this part of the configuration and click **Next**. 

![](https://lh6.googleusercontent.com/YujkaWVTGF-5fc7T6j-Lh2TbOSCK97eoDwo33HsNJpMtfkisPxMOJkKHT94yJPBAF-wAuo8H3sTmbvJGnZcQJ8FAPvlEgwRQ7_SVq5REnIQjNf89rVbHGPoFQzcSB7gikdX4NUAV)

In the provisioning settings, check the **Enable provisioning features** box:

![](https://lh6.googleusercontent.com/EeSU0iiVFRkqmW_x1yX4wAxRet5e-7O5PnE-f4O614iST0HRpj5Zdco_IbJUvcpjgjhhfKidSMzEZ9FlhmEVF7Q6Mum0lMJzYYl4Iz2oMCSDeSFWiKjw8I9OzQoyAbb_nbw_erwM)

Now enter the following information in the “API Credentials” form:

* **Username**: ThousandEyes username \(email\) with a role having permissions to create accounts
* **Password**: API token of the selected ThousandEyes user \(found on the Account Settings &gt; Security & Authentication tab\)

![](https://lh3.googleusercontent.com/2rTyhG0bbMAn-8tt_waJC920hzzPeGu9R-H0W5k11PgNfRdz36SpA9mJJrU5g1VlwEUfyxFscy_xpg4fxbnS9xYrqAZxnUBaWWsIrJ_pzeRyNrN9i9exLtgLyLF89FKe0oLx6cdP)

Click on **Test API credentials** to make sure the API token and username were entered correctly. This should return a message similar to this one:

![](https://lh5.googleusercontent.com/3DG8E7uJFPsqdfvYlrhMWLO5ufbyd2UTZRnhleajebmZ-jx2nJJGdTgHBJVXsLok530AB17v1wAPmKNuzlOr3Qwx2ZUpI61hb-nXlEbPZtQuPtz_c4esLGqbDCJNWy2vW7ZSOJ-o)

If an error is present, verify that the selected user has the permissions stated in the Requirements section of this document. If the issues persist, please contact ThousandEyes Customer Success Center \(support@thousandeyes.com\) to assist.

Under “Provisioning Features” select the following options:

* **User Import** - Enabled
* **Schedule Import** - Select a time
* **Okta username format** - Email address

![](https://lh6.googleusercontent.com/lZfu8uKxSuCdEcxRf2xn4KCpVYgnw2gDfi7LTwx6r5ew0kzTICU2iWGbfWCOFIVmhWq2dlqVVbS_v51dRCmTxCqVjUVVjEYWaMTV8HBXNAq-1X96WENMet0uwvWlTlAWXZEwGBvp)

* **Create Users** - Enabled
* **Update User Attributes** - Enabled
* **Deactivate Users** - Enabled

![](https://lh3.googleusercontent.com/dL1t3V_i_iYsSFhCGliIjjchQlHU454y3UN7OsVwtYbJVOxK1EyougvSBa53Au_bd6IVFhIahxIt0GpgW8DINPS767rMiEcUpTAU_MNm3zRP5eIcgTr3wD7B04ejxrpsLRJeIZoQ)

Once this is completed, click on **Next**.  
 

Optional: Add users now so they are integrated to the App. Otherwise just click on “Next”

![](https://lh3.googleusercontent.com/m7kguSba5PgMk17UuPOJ_VSqWDkqa1iRJNe2RFFe70ah-G5ms3x6ou0uGQr5UEfoEbyiYtmTUGaDhNlWGpA45ALKIWLudCNClG0PU7jaSusGtLhNUcXuAeICxXpix_QWd3zpD9yq)

And click on “Done” to finish the configuration:

![](https://lh6.googleusercontent.com/Ae5xFIJf1vy8AwAlUR8aVtNE48tVwnpLtnpBvtxcr-gyHQfOlB0Q0ohffLPQjzCl9Br1SD6qDkpfOWWmGTosCqQxFa1O3Nc05mI8iVQSsSxVPWIkRSa5eAt4HVL2brFzRbrQK6FT)

At this point of time, setup of SCIM with ThousandEyes is complete.

### [Testing the SCIM integration]()

#### [Adding Users]()

To verify that the integration is working, add a user to the Application.

From the home page, go to Applications &gt; Applications

![](https://lh5.googleusercontent.com/Vg9ot6DnKEQfdg3KC1AlbCRI8hHImM29KI9RxztX8svreZOKXo-n5LdW-FW35p0Knz9-kKDeUw6fTYRsbkIgw3us6-zyAzQ9wje6kWELUfXNQ22Kw8QBVHhitrdG-raSUnkAcB0a)

Then click in the newly added app:

![](https://lh6.googleusercontent.com/2BmHRop9_NvXuKuvJdYAi6jdL3A87wh0PWdeekEIAELjwc0wl17yzdVb8v9_pwYPAKxp5XMjhS39cIH_u3Nqu2PHun1v9UnuI4O_XS5ySMKhrhRD7vE1lVk0u8S20dsK3j48KSnd)

Now click on **Assign to People:**

![](https://lh3.googleusercontent.com/s2NzZvyg7i2dcXgXmsDltEfq9nsgPgRZL8rSb90BuHtdBPBGZDp0c3AwKKF7NQF50s2hByUbpZ-ZqyUZppwHHWAQW-reQ-8Q-71kbyvTvi9-l0FxfMaTWJGE_kWP4hCxlJS05vYc)

Select the people you want to be pushed to ThousandEyes as users by clicking on the **Assign** button next to them:

![](https://lh4.googleusercontent.com/X46LHYoRxyDPhDTWhK_ZjvYlf9cOvCIfDjrWM0fGbrCLIQD0OMFUf4ImdTCldFVqQkSN6pW3SXAvoXbTvdUuyhBDHL7Jei6cjHwmzy4bEuB2bg9lcUZzKy9XaFfnJ9wnOeuszpN_)

Then click on **Save and Go Back** after reviewing the user information:

![](https://lh6.googleusercontent.com/FbvBR70-FU_B01dHIU8hYXwaBvpkf50k7Sr9KuLvCRcQuPgtCse-MYE4PWvULcYerg6uhWKgkxz3X0ilUgm1CT7cP_BvQEbVqavIwzyqo9daYrhjp2IXSOKxj0gM4uwahjjdak5t)

Repeat this for all users you want to push to ThousandEyes. When done, click on **Done**:

![](https://lh5.googleusercontent.com/p7nGMRpCMOgsPewtbcDT6RuijD2gKpjEas59StbE8o8QrUgKPhSgynROfRScRsN5Y5vDMRzG4xUxEJjV66i2BYGonh5bjrJA7ojYxTwr5BqgxtJwCGh7fth8Mqwho3XzikcB7Xtt)

If the User ID \(email\) is already registered with ThousandEyes, then the new access, permissions and roles will be configured accordingly on this user, matching what was configured in the “SCIM Settings” section of your organization’s Security and Authentication settings:

![](https://lh5.googleusercontent.com/THCHgU2SOwoyF4ehafgcCm3df_ag45-iVjF9QK6hG8xz3d1YjBdUqlIcf0ekVNDfihBW_1P8vCog9pVZVyNM37fpUI4NAStD_tZdcAqCqLKzk5RkFZktsA1rx3AB1VNUpar_txWQ)

If the user doesn’t exist, it will be created in ThousandEyes and no registration or activation will be required from the newly created user.

Within ThousandEyes, the user should be visible shortly after it was associated with the service from Okta. To validate this, go to the Users section within Account Settings and verify the newly added user is present there:

![](https://lh3.googleusercontent.com/l0DaZ3iakQ2iUOjqxXVjOXd0KYpfDk_L79ogl38nOrhel36gn3_GialgU4oY1J5l6L1Vn-CDGmQDrcxWZInrUe7HBm91FUcDBWR5iMTT2IxFEesGOG8hC2i3z6jmVLn-VLqz8whJ)

#### [Removing Users]()

To delete an user, open the Application from Okta,

From the home page, go to Applications &gt; Applications

![](https://lh5.googleusercontent.com/Vg9ot6DnKEQfdg3KC1AlbCRI8hHImM29KI9RxztX8svreZOKXo-n5LdW-FW35p0Knz9-kKDeUw6fTYRsbkIgw3us6-zyAzQ9wje6kWELUfXNQ22Kw8QBVHhitrdG-raSUnkAcB0a)

Then click in the newly added app:

![](https://lh6.googleusercontent.com/2BmHRop9_NvXuKuvJdYAi6jdL3A87wh0PWdeekEIAELjwc0wl17yzdVb8v9_pwYPAKxp5XMjhS39cIH_u3Nqu2PHun1v9UnuI4O_XS5ySMKhrhRD7vE1lVk0u8S20dsK3j48KSnd)

Now click on the “X” button next to the user you want to delete:

![](https://lh4.googleusercontent.com/ot42yC0zqchNyf5d3AAxlE0QdvSlDHiwxlI7tyP5hVduCiJhdEsMMw2NmquSbwYyhtnxPmLp5wza8kX9xkRW3YmeIaOxoxBQnw165x9vOsfk2s-WnXJtSFHE3I84bZrLb0rSrNDF)

Confirm the prompt to verify that the user will be unassigned from the Application:

![](https://lh5.googleusercontent.com/HA-FFG6G6T5iyzZlP8IaQH1IYGS7HtXp5b6pr3xK97avsj-89o60oMG_3KnNoofT0vdjXLGjTERHw6VJdxWQFcZguKZxcnr9fkOq4WcmcBltFdT1HSOqIqdZqh6Qj46REFoynOha)

The user should be shortly deleted from ThousandEyes. This is also verifiable within the Users section within Account Settings

![](https://lh3.googleusercontent.com/PsxZwFVp-xRxLucDL3-vbap1lgh644VYicrYDqaBO2s1HWdMX1L36zKp4z2jJQ_DrAgBf-KVbpHN1pvzvz5YvKY5ROHj_mSTJk2lb4PMCJFMUD2TJeJRNZtIc8WuKExhkqWYsJwm)

