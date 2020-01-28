# What is BrowserBot?

ThousandEyes [Virtual Appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) are shipped with both the [Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) and BrowserBot components enabled. When [installing the ThousandEyes Enterprise Agent as a Linux package](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method) on a [supported operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems), you have the option to install BrowserBot, by passing the `-b` flag to the installation script.

## What is BrowserBot?

The BrowserBot is a component of the agent code that manages Page Load and Transaction tests. This is accomplished through running an instance of the [Chromium](https://www.chromium.org/) browser.

On the other hand, HTTP Server tests are using a custom version of [cURL library](https://curl.haxx.se/) under the hood and therefore do not need the BrowserBot installed.

## Can I install BrowserBot onto an existing Enterprise Agent?

Yes. To install the BrowserBot component on an existing Enterprise Agent that does not already have it installed, simply re-run the installation script, including your ThousandEyes Account Group token, and the `-b` flag:

```text
sudo ./install_thousandeyes.sh -b {your account group token}
```

This will install the BrowserBot and all required dependencies. The BrowserBot version information will now appear in the Enterprise Agent's **General Info** panel in the [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) page, as per the image below:

IMAGE MISSING

## Additional hardware resource requirements

When installing the BrowserBot package on an agent, it requires additional memory. Consult the [Enterprise Agent hardware requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements) article for full details.

## Which version of Chromium is BrowserBot using?

There are two methods of determining the Chromium version used:

### Method no.1 - Inspecting HTTP headers in waterfall

Pick any Page Load or Transaction test that has headers collection enabled. Open the results view, select one of the agents, switch to the **Waterfall** tab and click on one of the entries' **Headers** link:

IMAGE MISSING

Once there, open the **Request Headers** tab and search for the `user-agent` \(or `User-Agent` if HTTP protocol version 1.1 was used\) header:

IMAGE MISSING

Notice the browser version specified in the specified request header.

### Method no.2 - Inspecting installed package version

Once you have connected to the agent's SSH console, a simple command suggests the version of Chromium browser used under the hood. For connecting to the SSH console of appliances, we have guides available for [Windows](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnaKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Windows) and [OS X / Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnrKAC_Connecting-to-the-ThousandEyes-Virtual-Appliance-using-SSH-Mac-Linux) workstation operating systems.

For Ubuntu-based operating systems \(including ThousandEyes Virtual Appliances\), use the following command:

```text
$ dpkg -l | grep te-chromium

ii  te-chromium                   68.0.3440.83-1~bionic             amd64        web browser
```

For RHEL/CentOS/Oracle Linux systems, use the following:

```text
$ rpm -qa | grep te-chromium

te-chromium-68.0.3440.83-1~centos7.x86_64
```

The commands above will return the name of the package installed and by naming convention that is the version of the browser installed. In the example above, the browser version is `68.0.3440.83` - the `-1` suffix is not part of the browser version information - it is a package release number.

## Related information

The following resources provide further information about related subjects:

* [What is an Enterprise Agent?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) article describes what a customer-deployable ThousandEyes network vantage point is.
* [Enterprise Agent hardware requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements) article contains all information about computing resource requirements for running Enterprise Agents.
* [How to set up the Virtual Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) provides a step-by-step guide for deploying ThousandEyes agents as virtual appliances.
* [Enterprise Agent deployment using the Linux package method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method) deals with Enterprise Agent installations directly onto a supported operating system.

