# Supported Enterprise Agent operating systems

#### Supported Enterprise Agent operating systems

The ThousandEyes Enterprise Agent can be installed as a package on native Linux operating systems, as a ThousandEyes Virtual Appliance in a virtualized environment, as a Physical Appliance, or as a Docker container. The information below describes the supported platforms and operating system versions on which customers can install an Enterprise Agent, as well as the ThousandEyes lifecycle dates for expiration of support, and the policies which determine those dates.

## Linux package installation

For customers wishing to install the Enterprise Agent package on a Linux system, the table below indicates which distributions and versions are supported. Enterprise Agents are supported on the x64 \(64-bit\) architecture.

| Operating System Distribution | Minimum Version | Maximum Version |
| :--- | :--- | :--- |
| Ubuntu Linux | 16.04 LTS | 18.04 LTS |
| Red Hat Enterprise Linux | 7.4 | 7.LATEST |
| CentOS | 7.4 | 7.LATEST |
| Oracle Linux | 7.4 | 7.LATEST |

Access to the latest point release software repositories for each supported OS version is required \(i.e. an Agent installed on RHEL 7.4 needs access to RHEL 7.x repositories\). If access to the required repositories cannot be provided, meeting the package installation dependencies described in [Dependency tree for ThousandEyes Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnSKAS) article must be achieved using other methods, such as a local mirror.

For customers running other distributions or versions of Linux, ThousandEyes recommends installing [Docker](https://www.docker.com/why-docker) on the Linux system, then installing the Docker image of the ThousandEyes Enterprise Agent.

### Operating system support lifecycle

Currently supported versions of each Linux operating system are determined in conjunction with ThousandEyes' [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy). The ThousandEyes support lifecycle includes three phases through which an operating system version transitions before the version becomes unsupported. The tables below provide upcoming dates these phases for each supported operating system distribution.

### Ubuntu Linux

Only Long Term Support \(LTS\) versions of Ubuntu Linux are supported. Ubuntu supports LTS versions for five years from the release date. Once the Enterprise Agent software is released for a specific LTS version, ThousandEyes will provide support for that LTS version until the LTS version reaches End of Life, as defined by Ubuntu.

The Ubuntu Wiki [Releases](https://wiki.ubuntu.com/Releases) page lists the End of Life dates. The corresponding ThousandEyes lifecycle dates are listed below.

| Operating System Version | End of Installation Support | End of Support | End of Life |
| :--- | :--- | :--- | :--- |
| Ubuntu 14.04 LTS \(“Trusty”\) | 1/31/2019 | 4/30/2019 | 6/30/2019 |
| Ubuntu 16.04 LTS \(“Xenial”\) | 1/31/2021 | 4/30/2021 | 6/30/2021 |
| Ubuntu 18.04 LTS \(“Bionic”\) | 1/31/2023 | 4/30/2023 | 6/30/2023 |

###  Red Hat Enterprise Linux / CentOS / Oracle Linux

ThousandEyes bases support for versions of Red Hat Enterprise Linux, CentOS and Oracle Linux on Red Hat's Extended Update Support \(EUS\) schedule. Versions of Red Hat Enterprise Linux for which EUS is currently available are supported by ThousandEyes \(as are the corresponding versions of CentOS and Oracle Linux\).

Extended Update Support is documented in the Red Hat knowledge base article [What is the Red Hat Enterprise Linux Extended Update Support Subscription?](https://access.redhat.com/solutions/22763) In brief, Red Hat Extended Update Support is a paid subscription for software support of certain minor versions of Red Hat Enterprise Linux which are older than the current minor version. Extended Update Support is intended for customers who wish to remain on a particular minor version for an extended period of time \(approximately two years from the release date of the minor version\) while obtaining important software updates, rather than upgrading to the current minor version to obtain updates.

Red Hat does not make available Extended Update Support for all minor versions. Only minor versions which are released during the "Full Support" phase of a major version are eligible for Extended Update Support. Minor versions released in the subsequent "Maintenance Support 1" and "Maintenance Support 2" phases are not eligible for Extended Update Support. Thus, ThousandEyes will **end support for the major version** \(i.e. all minor versions including the most recent minor version\) at the expiration of EUS for the last minor version which was eligible for EUS.

The Red Hat knowledge base article [Red Hat Enterprise Linux Life Cycle](https://access.redhat.com/support/policy/updates/errata) lists the [EUS-eligible minor versions and EUS end dates](https://access.redhat.com/support/policy/updates/errata/#Extended_Update_Support), and the [major version support phases and end dates](https://access.redhat.com/support/policy/updates/errata/#Life_Cycle_Dates). The corresponding ThousandEyes lifecycle dates are listed below.

#### Red Hat 6 \("Santiago"\)

| Operating System Version | End of Installation Support | End of Support | End of Life |
| :--- | :--- | :--- | :--- |
| 6.0 | 8/30/2012 | 11/30/2012 | 1/31/2013 |
| 6.1 | 2/28/2013 | 5/31/2013 | 7/31/2013 |
| 6.2 | 10/7/2013 | 1/7/2014 | 4/7/2014 |
| 6.3 | 3/30/2014 | 6/30//2014 | 8/30/2014 |
| 6.4 | 12/31/2014 | 3/3/2015 | 7/3/2015 |
| 6.5 | 8/30/2015 | 11/3/2015 | 1/30/2016 |
| 6.6 | 7/31/2016 | 10/31/2016 | 12/31/2016 |
| 6.7 | 10/31/2018 | 4/30/2019 | 2/28/2019 |
| **All Other Minor Versions** | **12/31/2018** | **12/31/2018** | **4/30/2019** |

#### Red Hat 7 \("Maipo"\)

| Operating System Version | End of Installation Support | End of Support | End of Life |
| :--- | :--- | :--- | :--- |
| 7.1 | 12/31/2016 | 4/30/2019 | 6/30/2019 |
| 7.2 | 8/31/2017 | 4/30/2019 | 6/30/2019 |
| 7.3 | 8/31/2017 | 4/30/2019 | 6/30/2019 |
| 7.4 | 5/31/2019 | 8/31/2019 | 10/31/2019 |
| 7.5 | 1/31/2020 | 4/30/2020 | 6/30/2020 |
| 7.6 | 7/31/2020 | 10/31/2020 | 12/31/2020 |
| 7.7 | TBD | TBD | TBD |
| **All Other Minor Versions** | **Q4/2021** | **4/30/2022** | **6/30/2022** |

## Virtual Appliance

ThousandEyes Virtual appliances are based on Ubuntu LTS releases.  New versions of the Virtual Appliance are made available when new versions of Ubuntu LTS are certified for the ThousandEyes Enterprise Agent.  ThousandEyes currently provides Virtual Appliances for the following platforms:

* Hypervisors capable of importing an OVA, such as Oracle VirtualBox and VMware ESXi
* Microsoft Hyper-V
* Cisco 1000 ASR series routers
* Cisco 4000 ISR series routers
* Cisco Catalyst 9000 series routers
* Juniper SRX

## Physical Appliance

 ThousandEyes provides an installer image for Intel NUC mini-PCs, based on the same software as the ThousandEyes Virtual Appliance. ThousandEyes will make every effort to ensure that an upgrade path is provided, so that customers can stay on a supported Appliance version. In some cases, customers will need to reinstall the Appliance software in order to stay on a supported Appliance version.  Customers in this scenario will be contacted while the underlying operating system is in an End of Installation Support phase in order to ensure an orderly transition.

## Windows

There is not currently a native version of the ThousandEyes Agent software for Microsoft Windows. Customers running Windows may consider the following virtualization options:

* Windows Server 2008 or higher on x64 architecture: Use Microsoft Hyper-V virtualization software to host a [ThousandEyes Hyper-V Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC#import-hyperv).
* Other Windows versions: Use a virtualization product such as Oracle's VirtualBox platform for virtualization to host a [ThousandEyes Virtual Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC#import-ova). Check out [www.virtualbox.org](https://www.virtualbox.org/) for more details. Other virtualization software such as VMware Workstation can also run Virtual Appliance virtual machines.

 Note: An Ubuntu Linux operating system running in Microsoft's Windows Subsystem for Linux does not support Enterprise Agents.

## Mac OS X

There is not currently a native version of the ThousandEyes Agent software for Mac OS X. Customers running Mac OS X running on an Intel processor may consider the following virtualization options to host a [ThousandEyes Virtual Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC#import-ova):

* Oracle VirtualBox, a freely distributed hypervisor.  Check out [www.virtualbox.org](https://www.virtualbox.org/) for more details.
* Parallels Desktop. Check out [www.parallels.com](https://www.parallels.com/products/desktop/) for more details.
* VMware Fusion. Check out [www.vmware.com](https://www.vmware.com/products/fusion.html) for more details.

