# Password reset on the Virtual Appliance

The ThousandEyes Virtual Appliance can be configured through a web interface which is available at http://&lt;IP address of Virtual Appliance&gt;.  The web interface requires a username and password.  The default username and password are:

**Username**: admin  
**Password**: welcome

The Virtual Appliance installation process will require the password to be changed.

## Resetting password from the app

If the agent is online in the ThousandEyes app, the easiest way to force a password reset is from the [Enterprise Agents tab](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) of the Agent Settings page:  
 

After expanding the Agent's row, a **Reset Appliance Password** link appears. Clicking the link will reset the default username and password on the Appliance.

The final step is to log in to the Virtual Appliance's web management page at http://&lt;IP address of Virtual Appliance&gt; using the default credentials.  In the **Access** tab, you will be required to change the password:

## Resetting password from the hypervisor

If you can't log in to the Virtual Appliance's web management page, the password can be reset using the Virtual Appliance's console.  The console provides a text-driven menu for basic administrative tasks. The console window is a tty device which can be accessed from the hypervisor that is hosting the Virtual Appliance. 

In the console, press the **R** key to reset the password to the default value.

Next, navigate to the Virtual Appliance's web management page at http://&lt;IP address of Virtual Appliance&gt; and log in using the default credentials.  Upon the initial login, you will be required to change the password:

NOTE: If the **Current Password** field has been auto-populated, then your browser's password manager has filled the field with a value that may or may not be correct. If you receive an error that the auto-populated password is incorrect, then delete the contents of the **Current Password** and manually enter "welcome", in order to change the password. We strongly recommend disabling password completing for the Virtual Appliance's URLs.

