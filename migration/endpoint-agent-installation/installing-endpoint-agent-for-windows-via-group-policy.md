# Installing Endpoint Agent for Windows via Group Policy

## **Requirements:**

* A shared network drive
* Endpoint agent accessible via installed network drive
* Ability to create Group Policy Objects in Active Directory   

## **Process:**

### Recommendations

It is recommended to not create a single GPO to join multiple configurations, mainly for user flexibility. You can easily upgrade a GPO geared towards IE without editing Google Chrome GPO, or vice--versa.

This documentation was done under Windows Server 2012

## MSI Installer via GPO

1. Open up Group Policy Management
2. Create a group policy with the appropriate name. In this example, we will use “TE-Endpoint-Agent\_MSI\_Installer”

   IMAGE MISSING

3. Right-click the newly created GPO and select Edit
4. Expand till you reach:  
    **Computer Configuration\Policies\Software Settings\Software Installation**

   IMAGE MISSING

5. Right click the right-pane and select “**New &gt; Package”**

   IMAGE MISSING

6. Navigate to your network share where the installer is available for all users
7. Double Click the MSI file
8. On the “Deploy Software” window, leave the selection of “Assigned” and click Ok

If you run into the message “There is no software installation data object in the Active Directory” please verify that your file permissions on the network share are setup properly.

##  IE Add-on via GPO

1. Open up Group Policy Management
2. Create a group policy with the appropriate name. In this example, we will use “TE-Endpoint-Agent\_IE”  IMAGE MISSING
3. Right click the newly created GPO and select Edit
4. With the object open, navigate to the following:  Computer Configuration\Policies\Administrative Templates\Windows Components\Internet Explorer\Security Features\Add-on Management
5. Double-click “Add-On List”
6. Click Enable

   IMAGE MISSING

7. Click Show

   IMAGE MISSING

8. In the new window, under “Value Name” add the CLSID for the ThousandEyes Endpoint Agent for IE. The current CSLID is: E1F5283B-B591-412E-8E2F-4C65A9C94AF1
9. The Value number is dependant on how you would like users to be able to interact with the Add-On. The current value options are:  
    0 - The add-on is disabled and your employees can’t change it.  
    1 - The add-on is enabled and your employees can’t change it.  
    2 - The add-on is enabled and your employees can change it.

   IMAGE MISSING

10. Click Ok to close the Add-On List window
11. Click Ok again to close the Configuration for Add-On List window
12. Assign the GP to a specific OU
13. Right click the GP under the OU you have assigned it - Click Enabled
14. Right click the GP again, and click enforced.

## Google Chrome via GPO

1. Download the ADM/ADMX templates from Google using this link: [https://dl.google.com/dl/edgedl/chrome/policy/policy\_templates.zip](https://dl.google.com/dl/edgedl/chrome/policy/policy_templates.zip)
2. Open Group Policy Management
3. Expand Group Policy Objects
4. Right-click Group Policy Objects and select New
5. Provide a name for your new Group Policy Object \(GPO\)
6. Right-click your newly created GPO and select Edit
7. Expand Computer Configuration, expand Policies, right-click Administrative Templates and click Add/Remove Templates

   IMAGE MISSING

8. Select Add in the new dialog window

   IMAGE MISSING

9. Navigate to a network share where the policy template resides, and select the **chrome.adm** file listed here **policy\_templates/windows/adm/en-US/chrome.adm1**  IMAGE MISSING
10. Click Close
11. Expand Classic Administrative Templates \(ADM\), select Google Chrome and subsequently Extensions

    IMAGE MISSING

12. Open the Configure the list of force-installed extensions policy and select Enabled
13. Click Show
14. Paste the following into value: ddnennmeinlkhkmajmmfaojcnpddnpgb;[http://clients2.google.com/service/update2/crx](http://clients2.google.com/service/update2/crx)

    IMAGE MISSING

15. Select Ok and close the Group Policy Management Editor
16. Select the organizational unit that you would like to apply the GPO to. Right-click the OU and select Link an Existing GPO

    IMAGE MISSING  
     IMAGE MISSING

17. Right-click the newly created linked GPO and select Enforced  IMAGE MISSING
18. Wait 15 minutes for the group policy objects to sync across servers, or manually sync the Active Directory Servers through Sites and Services
19. Test end-user machine by running gpupdate.exe

