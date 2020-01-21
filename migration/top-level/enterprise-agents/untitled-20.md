# How do I perform an in-place upgrade from the latest RHEL 6 to the latest RHEL 7?

Red Hat Enterprise Linux 7 \(RHEL 7\) is the first major release of RHEL to allow in-place upgrades from the previous major RHEL release \(RHEL 6\). An in-place upgrade offers a way of upgrading a system to a new major release of RHEL by replacing the existing operating system. The following guide will lead you through the process of upgrading [package](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method)-based [Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent)'s underlying RHEL 6 operating system to RHEL version 7.

* [Overview]()
* [Caveats]()
  * [64-bit operating systems only]()
  * [Upgrading not supported on Hyper-V \(possibly others\)]()
* [Upgrade process]()
  * [1. Prepare for the upgrade]()
  * [2. Upgrade]()
  * [3. Post-upgrade tasks]()
* [Troubleshooting upgrade issues]()
* [Further information]()

## Overview <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Overview"></a>

This guide is based on Red Hat's [How do I upgrade from Red Hat Enterprise Linux 6 to Red Hat Enterprise Linux 7?](https://access.redhat.com/solutions/637583) guide. Before proceeding any further, make sure that you have read the aforementioned guide.

ThousandEyes followed the above Red Hat guide and successfully performed the Enterprise Agent upgrade. At the time of the upgrade, a ThousandEyes Enterprise Agent installed on RHEL 6.10 x86\_64 Server Edition Virtual Machine \(VMware\) was upgraded to RHEL 7.6 x86\_64 Server Edition.

Depending on your Enterprise Agent's hardware performance, the whole process could take more or less than an hour; plan your maintenance window accordingly. Your Enterprise Agent won't perform any tests during the upgrade.

Depending on your Enterprise Agent's software custom configurations, additional steps may be required to restore those custom configurations. Carefully analyze the generated preupgrade report.  
The following guide assumes that no custom configurations took place on your Enterprise Agent's Operating System.

## Caveats <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Caveats"></a>

### 64-bit operating systems only <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-64-bitoperatingsystemsonly"></a>

Upgrading from RHEL 6 Server Edition to RHEL 7 Server Edition is supported for x86\_64 architecture \(64 bit\), but not for x86 architecture \(32 bit\). The support is assured by your contract with Redhat, not by ThousandEyes.  
If your Enterprise Agent is running RHEL 6 x86 architecture, you should consider replacing it with a clean installation of RHEL 7 Server Edition x86\_64 architecture.

### Upgrading not supported on Hyper-V \(possibly others\) <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-UpgradingnotsupportedonHyper-V(possiblyothers)"></a>

Red Hat states that only KVM and VMWare virtualization platforms are supported for in-place upgrades. Hyper-V is an example of an unsupported platform.

## Upgrade process <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Upgradeprocess"></a>

All the commands below should be run as root. To reduce the content repetition, all "sudo" command prefixes have been removed and the whole guide assumes that you are running each command in a root shell.

To reach the root shell, use the following command:

```text
$ sudo -s
```

### 1. Prepare for the upgrade <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.Preparefortheupgrade"></a>

#### 1.1 Create a Virtual Machine snapshot

If you have the possibility of creating a backup snapshot of your virtual machine, we encourage you to do so. This will enable you to revert to the known-good state in case the upgrade does not go as smoothly as anticipated.

#### 1.2 Check that your subscription to RHEL repositories is valid and active <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.2CheckthatyoursubscriptionstoRHELrepositoriesisvalidandactive"></a>

```text
# subscription-manager register --username <username> --auto-attach
# subscription-manager repos --enable rhel-6-server-extras-rpms
# subscription-manager repos --enable rhel-6-server-optional-rpms
```

#### 1.3 Update the system to the latest minor version and reboot <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.3Updatethesystemtothelatestminorversionandreboot"></a>

```text
# yum update -y
# reboot
```

#### 1.4 Install the upgrade tool <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.4Installtheupgradetool"></a>

```text
# yum -y install preupgrade-assistant preupgrade-assistant-ui preupgrade-assistant-el6toel7 redhat-upgrade-tool
```

#### 1.5 Run the "preupg" command and read the generated report <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.5Runthe&quot;preupg&quot;commandandreadthegeneratedreport"></a>

```text
# preupg
```

This report will point out possible upgrade contention points. Evaluate whether it is safe to continue with the upgrade process.

#### 1.6 Remove the sandbox selinux module <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-1.6Removethesandboxselinuxmodule"></a>

```text
# semodule -r sandbox
```

### 2. Upgrade <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-2.Upgrade"></a>

#### 2.1 Insert the RHEL 7 installation media <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-2.1InserttheRHEL7installationmedia"></a>

The following step assumes a \(virtual\) CD/DVD Media rhel-server-7.6-x86\_64-dvd.iso is inserted into the VM's virtual CD/DVD drive from hypervisor's VM Settings.

Other installation sources are supported as well - the following command line options are applicable in the next step:

* **"--device \[DEV\]"**- Device or mount point. default: check mounted devices
* **"--iso \[FILE.iso\]"**- Installation image file
* **"--network VERSION"**- Online repos matching VERSION.  Example: **--network 7.6 --instrepo=https://myinternalwebserver.com/rhel7repo/ --cleanup-post**

#### 2.2 Start the upgrade and reboot <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-2.2Starttheupgradeandreboot"></a>

```text
# redhat-upgrade-tool --device /dev/sr0 --cleanup-post
# reboot
```

You may connect to the VM console and observe the output of the upgrade process - wait for its completion.

### 3. Post-upgrade tasks <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.Post-upgradetasks"></a>

A few additional tasks need to be taken care of in order to ensure smooth agent operation.

#### 3.1 Subscribe to additional RHEL 7 repositories <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.1SubscribetoadditionalRHEL7repositories"></a>

```text
# subscription-manager repos --enable rhel-7-server-optional-rpms
```

#### 3.2 Re-install the ThousandEyes agent and BrowserBot <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.2Re-installtheThousandEyesagentandBrowserBot"></a>

If the BrowserBot component was previously not installed or is not needed, don't use the "-b" switch in the following command.

Use the same account group token as found in the /etc/te-agent.cfg file.

```text
# curl -Os https://downloads.thousandeyes.com/agent/install_thousandeyes.sh
# bash install_thousandeyes.sh -b <ACCOUNT_GROUP_TOKEN>
# yum reinstall te-agent -y
# systemctl start te-agent
```

#### 3.3 Enable the BrowserBot service <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.3EnabletheBrowserBotservice"></a>

If the "-b" switch was used to install the BrowserBot component in the step above, enable the te-browserbot service. The upgrade process does not handle this task transparently.

```text
# systemctl enable te-browserbot
```

If you skip this step, the BrowserBot service will not start automatically on the next reboot.

#### 3.4 Enable time synchronization <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.4Enabletimesynchronization"></a>

If you had previously installed the ntpd service, make sure the service is enabled and started. If you didn't have the ntpd service installed before the upgrade, we recommend you install it by running the following command: `yum install ntp`.

```text
# systemctl enable ntpd
# systemctl start ntpd
```

#### 3.5 Upgrade to the latest point release <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.5Upgradetothelatestpointrelease"></a>

The major version upgrade may not have upgraded your operating system to the latest point release. It is recommended to follow Red Hat's point releases.

```text
# yum update -y
# reboot
```

#### 3.6 Resolve any remaining issues reported in step 1.5 \(optional\) <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-3.6Resolveanyremainingissuesreportedinstep1.5(optional)"></a>

If the report generated by the pre-upgrade tool identified any potential issues, now is a good time to resolve them.

## Troubleshooting upgrade issues <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Troubleshootingupgradeissues"></a>

When the upgrade does not seem to be going as planned, the following suggestions outline basic troubleshooting activities. If you cannot figure out what is causing the issue, reach out to [support@thousandeyes.com](mailto:support@thousandeyes.com) and we'll help you out.

#### Problems with te-agent and te-browserbot package installation <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Problemswithte-agentandte-browserbotpackageinstallation"></a>

The first thing to do if the agent software installation fails is the inspection of the installation logs. Use the following command to do so:

```text
# cat /tmp/install_thousandeyes*.log
```

#### The agent does not show up as online in the platform <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Theagentdoesnotshowupasonlineintheplatform"></a>

Inspect the agent logs with the following command:

```text
# tail -f /var/log/te-agent.log
```

#### The agent does not automatically upgrade to the latest version <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Theagentdoesnotautomaticallyupgradetothelatestversion"></a>

Are you subscribed to Red Hat? Is your subscription valid?

Check your subscription with the following command:

```text
# subscription-manager list
```

## Further information <a id="HowdoIperformanin-placeupgradefromthelatestRHEL6tothelatestRHEL7?-Furtherinformation"></a>

The following resources provide related information:

* [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy) Knowledge Base article explains when to expect end-of-support events for each supported operating system.
* [Red Hat KB: How to register and subscribe a system to the Red Hat Customer Portal using Red Hat Subscription-Manager](https://access.redhat.com/solutions/253273)
* [How to create local repository distributed through apache of Red Hat Enterprise Linux 5/6/7 using DVD iso for update or installation?](https://access.redhat.com/solutions/7227)
* [Red Hat KB: How do I upgrade from Red Hat Enterprise Linux 6 to Red Hat Enterprise Linux 7?](https://access.redhat.com/solutions/637583)

