# ThousandEyes support for SCIM

ThousandEyes is now able to add, update and delete users from identity providers who support the [SCIM 2.0 and 1.1](http://www.simplecloud.info/) standards, dramatically decreasing time to provision users into ThousandEyes and perform ongoing user management.

## Operation

ThousandEyes has made available two SCIM API endpoints to receive user addition, update and deletion requests:

* https://api.thousandeyes.com/scim/v1
  * For SCIM 1.1 based API calls.
* https://api.thousandeyes.com/scim/v2 \(or https://api.thousandeyes.com/scim\)
  * For SCIM 2.0 based API calls.

The operation of SCIM is simple: a Service Provider is able to map attributes from its local user database, and generate SCIM API calls to one of our endpoints in order to generate, update or delete the users on ThousandEyes end:

IMAGE MISSING

The structure of those calls must be compliant to the SCIM 1.1 or 2.0 protocol and schema, and also need to be compliant with our currently supported operations, discussed below.

## Requirements

In order to leverage ThousandEyes SCIM API endpoints, a ThousandEyes user having a role with the following permissions is required:  
 

* View Users
* Edit Users
* API Access

Both SCIM 1.1 and 2.0 Endpoints require the user to authenticate either with HTTP Basic Authentication using your Basic Authentication Token or an OAuth Bearer Token, both which can be created in the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) tab of ThousandEyes' Account Settings page.

By default, users added through SCIM to ThousandEyes will be assigned the "Regular User" role in all Account Groups of the organization where they are created. This default assignment can be changed in the SCIM Settings Section of the [Security & Authentication](https://app.thousandeyes.com/settings/account/?section=security) tab of ThousandEyes Account Settings. Once the users have been created in ThousandEyes, their individual roles can be freely modified in the [Users](https://app.thousandeyes.com/settings/account/?section=users) tab of Account Settings.

IMAGE MISSING

In this particular example, the "SCIM API User Role" under the "Support" Account Group will be granted to all the newly pushed SCIM users. All Roles and Account Groups can be used, as long as the API user making the SCIM API calls has permissions to grant them. Lacking those privileges will cause the SCIM provisioning process to fail.

## Supported features

* [Filtering](https://tools.ietf.org/html/rfc7644#section-3.4.2.2) is supported for both SCIM 1.1 and 2.0 endpoints on the ExternalID and UserName attributes only.
* As of now, there is no support for SCIM Group creation or mapping, meaning that the SCIM /vX/Groups endpoint has no functionality.
* Operations on /Bulk endpoint are not supported.

Below is the list of endpoints and their supported operations:

**SCIM v1** \(https://api.thousandeyes.com/scim/v1\)

* /Users
  * GET - list users
* /Users/{id}
  * GET / PUT \(update\)
  * POST \(create\)
  * DELETE \(delete\)
  * PATCH \(not supported\)
* /Schemas/{type} 
  * accepted "type" values: "users" or "groups"
  * GET - returns schemas for provided type
* /ServiceProviderConfigs
  * GET \(returns supported configurations\)

**SCIM v2** \(https://api.thousandeyes.com/scim/v2\)

* /Users
  * GET - list users
* /Users/{id}
  * GET / PUT \(update\)
  * POST \(create\)
  * DELETE \(delete\)
  * PATCH \(update\)

Configuration

From ThousandEyes perspective, the only needed configuration is creating an API user with the necessary privileges to create the accounts you will be importing. Only two attributes from ThousandEyes will be populated:

1. Name \(not mandatory\)
2. Email \(mandatory and unique\)

From the Service Provider's perspective, the trick is in the mapping of values from the Provider's directory to ThousandEyes' user database. From the provided attributes in the POST data from your provider, we parse for a valid email \(our primary user identifier\) in the following attributes in the provided order:

1. emails - primary:true or first element of the email list.
2. username 

Making sure that a valid and unique email is passed on either of those two attributes to ThousandEyes is key to creation of a new user through SCIM.

Providers that supply a SCIM application usually provide a template where values can be mapped from the local database to what will be sent through SCIM. As an example, here is a basic structure of a SCIM 1.1 call template:

{  
  "schemas": \[  
    "urn:scim:schemas:core:1.0"  
  \],  
  "username": "{$PROVIDER\_DB\_FIELD\_TO\_BE\_MAPPED\_TO\_USERNAME}",  
  "name": {  
    "formatted": "{$PROVIDER\_DB\_FIELD\_TO\_BE\_MAPPED\_TO\_NAME}"  
  },  
  "emails": \[  
    {  
      "value": "{$PROVIDER\_DB\_FIELD\_TO\_BE\_MAPPED\_TO\_EMAIL}",  
      "primary": true  
    }  
  \],  
  "externalId": "{$PROVIDER\_SUPPLIED\_EXTERNAL\_ID",  
  "active": true  
}

For other approaches to push users to ThousandEyes, also check the [Administrative Endpoints on our API](http://developer.thousandeyes.com/v6/admin/) to add, update, and delete users.

Microsoft Azure Active Directory  
Microsoft Azure Active Directory and ThousandEyes can be configured to automatically provision and de-provision user accounts, the procedure is illustrated in [this tutorial](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/thousandeyes-provisioning-tutorial). The **ThousandEyes Tenant** field that is mentioned in the tutorial needs to be filled with the URL [https://api.thousandeyes.com/](https://api.thousandeyes.com/).

