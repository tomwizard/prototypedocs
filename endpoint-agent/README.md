# Endpoint Agent

{% hint style="info" %}
**For Mac OS Catalina Users**: Starting with Mac OS Catalina, Mac Gatekeeper no longer allows applications that are not notarized by Apple to be installed via graphical installers. The following error will be displayed in this scenario:

**“Endpoint Agent for exampleorg-x64-1.23.0.pkg” can’t be opened because Apple cannot check it for malicious software.**

To workaround this issue, either approve opening the installer from the local machine’s **System Preferences -> Security & Privacy -> General** configuration page, or use the command line instructions below:

1. On the local machine, open a terminal window.
2. Run the following command, replacing the example filename/path:

```bash
sudo installer -pkg "~/Downloads/Endpoint\ Agent\ for\ exampleorg-x64-1.3.0.pkg " -target /
```

After running the command and confirming sudo permissions, the agent will install. If you are using the browser extension, you can now review the Install the Browser Extension instructions.
{% endhint %}
