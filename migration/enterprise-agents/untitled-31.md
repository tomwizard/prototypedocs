# Adding or removing Adobe Flash on Enterprise Agents

[BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-the-BrowserBot?), the component of ThousandEyes [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) that runs Page Load and Transaction tests, can include an [Adobe Flash Player](https://www.adobe.com/products/flashplayer.html) component. To add the Flash Player package to an existing agent, or should security or other considerations require removal of the Flash Player, the following content provides information to add or remove the package.

## Flash presence on Enterprise Agents

As of February 16th, 2017, Adobe Flash Player is included by default in the ThousandEyes [Appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) and [Docker installations](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker) of Enterprise Agent along with BrowserBot \(previously, Adobe Flash support was an optional package for these Enterprise Agent installation types\).

Adobe Flash Player in Linux package installations of Enterprise Agent continues to be optional. Normally, installation of Flash Player is done using the `install_thousandeyes.sh` script that is downloaded from ThousandEyes portal when [deploying a new Linux package-based Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method). The install script is run with the `-F` option to install Flash, in addition to the `-b` option to install BrowserBot:

```text
$ ./install_thousandeyes.sh -b -F installation_token
```

Notes:

* To install Adobe Flash Player on an existing Enterprise Agent, BrowserBot must first be installed.
* Installing or removing Flash on a ThousandEyes Appliance first requires [unlocking the Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvrCAC_Unlocking-the-ThousandEyes-Appliance).

## Installation

To install the Adobe Flash Player package, the system must have the necessary package repository configured. The steps below indicate how to check the repository configuration and then run the installation command for the Adobe Flash package\(s\).

### Ubuntu and ThousandEyes Appliances

To install the Adobe Flash Player package `adobe-flashplugin`, the `/etc/apt/sources.list` file must include the Canonical **partner** repository, which is normally added by the `install_thousandeyes.sh` script. If needed, add or uncomment the following line in the file:

```text
deb http://archive.canonical.com/ubuntu CODENAME partner
```

where `CODENAME` is the Ubuntu codename \("xenial", "bionic" etc…\) for the version as shown by the `lsb_release -sc` command.

Install the package with the following commands:

```text
$ sudo apt-get update
$ sudo apt-get install adobe-flashplugin
```

Restarting the te-browserbot service is required:

**Ubuntu 14.04**

```text
$ sudo stop te-browserbot
$ sudo start te-browserbot
```

**Ubuntu 16.04, 18.04 and ThousandEyes Appliances**

```text
$ sudo systemctl restart te-browserbot.service
```

### Red Hat and CentOS

To install the Adobe Flash Player, packages `adobe-release` and `flash-plugin` are required. The `adobe-release` package must be installed first, as it configures the system to use the RPM repository [http://linuxdownload.adobe.com](http://linuxdownload.adobe.com/). The `flash-plugin` package is then downloaded from this repository.

Install the packages with the following commands:

```text
$ sudo yum install adobe-release
$ sudo yum install flash-plugin
```

Restarting the te-browserbot service is required:

**RHEL and CentOS 6.x**

```text
$ sudo stop te-browserbot
$ sudo start te-browserbot
```

**RHEL and CentOS 7.x**

```text
$ sudo systemctl restart te-browserbot.service
```

## Removal

### Ubuntu and ThousandEyes Appliances

Remove the package with the following command:

```text
$ sudo apt-get remove adobe-flashplugin
```

Restarting the te-browserbot service is required:

**Ubuntu 14.04**

```text
$ sudo stop te-browserbot
$ sudo start te-browserbot
```

**Ubuntu 16.04, 18.04 and ThousandEyes Appliances**

```text
$ sudo systemctl restart te-browserbot.service
```

### Red Hat and CentOS

Remove the package with the following command:

```text
$ sudo yum remove adobe-release flash-plugin
```

Restarting the te-browserbot service is required:

**RHEL and CentOS 6.x**

```text
$ sudo stop te-browserbot
$ sudo start te-browserbot
```

**RHEL and CentOS 7.x**

```text
$ sudo systemctl restart te-browserbot.service
```

## Flash end-of-life announcement by Adobe \(2020\)

In July 2017, Adobe published the Flash end-of-life announcement that should happen at the end of the year 2020. According to [the announcement](https://theblog.adobe.com/adobe-flash-update/), at that point, Adobe will "stop updating and distributing the Flash Player". In the same announcement, Adobe is also encouraging content creators to "migrate any existing Flash content to new open formats".

## Related information

 The following Knowledge Base articles provide related information:

* [Enterprise Agent deployment using Linux package method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method) article outlines steps for deploying Enterprise Agents on supported Linux operating systems.
* [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) article lists all operating systems and versions on which Enterprise Agents can be deployed.
* [Unlocking the ThousandEyes Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvrCAC_Unlocking-the-ThousandEyes-Appliance) article provides steps for gaining root access to Enterprise Agent appliances.

