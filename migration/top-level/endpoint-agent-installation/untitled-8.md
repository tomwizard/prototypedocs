# Installing Endpoint Agent for Windows via Group Policy

### Installing Endpoint Agent for Windows via Group Policy

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

   ![](https://lh3.googleusercontent.com/pTaSJYdMLt4wyBC_jrEexwBnfDx2AUJq57S5Ovf8Mny0Bu0Is7dEQkq-NRHcy1BybDwygy1Dcg6TJE7e-wvVK7rZKjuN1EuSBbwByjSjmsvTnJdZHOBC68kc88fx6wVfR6wWDJJA)

3. Right-click the newly created GPO and select Edit
4. Expand till you reach:  
    **Computer Configuration\Policies\Software Settings\Software Installation**

   ![](https://lh4.googleusercontent.com/eJyfQWPLUlGIW30LpZGGIDWnVcOc2tqZB54WvqMja36McKAQMuUxQd6uSUFTXuUAxhpeFDkrgN2wW1QBoTO77dcUwPIRHpMaf7ka9Clxxs0e3qjW8trmioyI_2bic4J43ekMCb87)

5. Right click the right-pane and select “**New &gt; Package”**

   ![](https://lh5.googleusercontent.com/31vuOrtURnbCKkvVHzfw0ksHNgfIIUtKSZPxakmGNXnOG8fud3ftK8bvmhPJsTpJiDCoFbyi3VL8WSAojLqKgDDxj4I2KoNxeIGouJ8VcDwhkTf9rIVuaCk8GxG_rgfxkcXIgUGx)

6. Navigate to your network share where the installer is available for all users
7. Double Click the MSI file
8. On the “Deploy Software” window, leave the selection of “Assigned” and click Ok

If you run into the message “There is no software installation data object in the Active Directory” please verify that your file permissions on the network share are setup properly.

##  IE Add-on via GPO

1. Open up Group Policy Management
2. Create a group policy with the appropriate name. In this example, we will use “TE-Endpoint-Agent\_IE”  ![](https://lh5.googleusercontent.com/PwVGd5vraB_ByJQhs9XQ8VEaa1h4q_qETTbzBTzDVKfqW4Rq-cno6q1O4JY9kG1nc9wj93VfZwTybsvNJ7STNsYWClvwuweb8ushnKlZy5av6TjPMif4-zQWiN-kuqkqTp-f0Ped)
3. Right click the newly created GPO and select Edit
4. With the object open, navigate to the following:  Computer Configuration\Policies\Administrative Templates\Windows Components\Internet Explorer\Security Features\Add-on Management
5. Double-click “Add-On List”
6. Click Enable

   ![](https://lh5.googleusercontent.com/ABJdrSaGVo_Z_w3CdkKhWIjbdQStqxwz0IIoGQqxJQopRdWCfEX5TZzgZdFdcdB1Y9bpVbxj7kTq3Eny5pb45uDhU5smnLxHCK55GLQXCCihJ_BBRfWjrD8hgS40rthXO01iAFE0)

7. Click Show

   ![](https://lh4.googleusercontent.com/BsG_7WBCmUYv5KdrRfT_GTuBbMylHqgDOLrSk60bRLONOb0cFDqvsljSQocmhkHE8s8jXtBtPNUNn6dXUO6JZO3MyJm_SLoUKPYQrDwyTYepbCViRP1M6E_N8TQhNQ0U5otON-FV)

8. In the new window, under “Value Name” add the CLSID for the ThousandEyes Endpoint Agent for IE. The current CSLID is: E1F5283B-B591-412E-8E2F-4C65A9C94AF1
9. The Value number is dependant on how you would like users to be able to interact with the Add-On. The current value options are:  
    0 - The add-on is disabled and your employees can’t change it.  
    1 - The add-on is enabled and your employees can’t change it.  
    2 - The add-on is enabled and your employees can change it.

   ![](https://lh3.googleusercontent.com/-OCBqt5OvxpsjMKIjNEAKkTtmw8qORxFdtlVVALEHlY-GmsJFQ0pPk-pt7iu-6-cSgx6nyfqa610bztzBixoxmuJoMBfxL7gvlfZCJTeIU77nSdQhOg2pJ70iq1S6CJVR1_aK8En)

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

   ![](https://lh3.googleusercontent.com/c8V4DRfPTCNEFOR4vX7dEIGr4keWuj--nyOt4VdO91R75rDkGS-IxZ-jggMWCf_iCKI3XBFmtYPC36FMT1XWGyKnd6_7Gr_tjAn0noTwH73CGlhAn-3yNupPldXJEvAvVEiJtEq5)

8. Select Add in the new dialog window

   ![](https://lh6.googleusercontent.com/KchD2BMwxyZnYxZbhttOqQX2Z1_kLiminileiTQd2LnSWwqnGG5drGdnq-H8d1gU7FxkZvCJxwCpMatjxX0VkA01nORqE1Psk5c8xKjws7gPIsA6pfGGMDczjDsqfDJobZjbaTRz)

9. Navigate to a network share where the policy template resides, and select the **chrome.adm** file listed here **policy\_templates/windows/adm/en-US/chrome.adm1**  ![](https://lh5.googleusercontent.com/Bmeid11ef2FG3EXPm4RWvrSZQjriWJxaURTmNMFk9jnFWpQBLEX7-YEh00F5iCIUCJfrvHitw7gvh19lOpxyNxr1dgtAnJtlIUZU7BNMn6vv_4Zkhn9Ay1KV7itFbvIKW9vmYddM)
10. Click Close
11. Expand Classic Administrative Templates \(ADM\), select Google Chrome and subsequently Extensions

    ![](https://lh3.googleusercontent.com/QlspjyO6O3cEpfjjLyrIn6WcF8OWQBATe-PtMGr9faLhXuwYdjaChIRHHEL6k5c3B2TZl8RJJ1Ll3yzlIeMQvMK11QotwKvvBJ1b34cNzGf1cf1BPqpIZuh91HW9SOwPuohad2a-)

12. Open the Configure the list of force-installed extensions policy and select Enabled
13. Click Show
14. Paste the following into value: ddnennmeinlkhkmajmmfaojcnpddnpgb;[http://clients2.google.com/service/update2/crx](http://clients2.google.com/service/update2/crx)

    ![](https://lh3.googleusercontent.com/eCi7V3sCkeMPjqcvEn_anomH9CnZEY1GrJ49cwB1F0xL51TJ8iam5i12SBuogtrYxEx9fTBBN_rNdTkD-QaN8wc4aLitkI0MA8UpTF-wg3wukxFO4hvo3vT6L4roh0D6YH-sHkQZ)

15. Select Ok and close the Group Policy Management Editor
16. Select the organizational unit that you would like to apply the GPO to. Right-click the OU and select Link an Existing GPO

     ![](https://lh4.googleusercontent.com/QerBfJMRtMqCJkUsp_aQxcyNICK2Dp1jwZU0OoCP6TFoduBYMOP-BHlCtwQ3NstlGlzcTwig8KFIP_zRAeeTB3XKgIlIvSy08Upa8kiFjlsYEIpfKZYM3yHhcUc8cDhFp9atsvHQ)  
     ![](https://lh3.googleusercontent.com/kKxQPfyZPohMenfvJGKy8yjRdgAnP-p0RUjvra0OFGHHNMqQGl1oH_231OhlRrUWD882BQMX0qMIjX3zRz27tsHi7J18E1RSRzg86JLeEJggnXAx4MUlQS2CZp2uGCs3mOeuIoxA)

17. Right-click the newly created linked GPO and select Enforced  ![](https://lh5.googleusercontent.com/BoeY_1pTb9yLtnO8e81ZGhjpaQnc_71zMmksN4rxfzLeC1MBrrjaofdoyS3Yxg-_Pt0J8HfJ7XHh7nfVIlwxUCr6676-ELbkNlGGK2MI8cQDPJubd6Epmq9OnSwD9AvZuwOkTZ_n)
18. Wait 15 minutes for the group policy objects to sync across servers, or manually sync the Active Directory Servers through Sites and Services
19. Test end-user machine by running gpupdate.exe

