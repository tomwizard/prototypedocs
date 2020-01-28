# BrowserBot installation fails on Red Hat or CentOS in Amazon EC2

The BrowserBot compontent of an Enterprise Agent perfoms Page Load and Transaction tests.  For customers of Amazon Web Service's Elastic Computing 2 platform, installing a Linux Package-based Enterprise Agent with the BrowserBot component in an AWS Red Hat or CentOS virtual machine may fail due to a missing package on which the te-browserbot package depends.  Most commonly, this is due to disabled repository that contains the dependency package.  To install the BrowserBot component, the repository must first be enabled.

## Identifying the problem

Installation of BrowserBot with a Linux Package-based Enterprise Agent is normally done via the install\_thousandeyes.sh script with the **-b** flag:

```text
sudo ./install_thousandeyes.sh -b <account group installation token>
```

The most common way to detect failure to install BrowserBot is during the execution of the install script in a terminal window.  A typical installation failure for BrowserBot would appear similar to the following \(emphasis added\):  

```text
[ec2-user@ip-10-0-1-48 ~]$ sudo ./install_thousandeyes.sh -b 12345abcde67890fghij12345klmno12

========================== Welcome to ThousandEyes ============================
[ OK ] checking installation privileges
[ OK ] checking architecture (x86_64)
[ OK ] checking operating system (RedHat/CentOS)
[ OK ] checking ThousandEyes (RedHat) installation tools
[ OK ] detecting RedHat flavor (CentOS/6)
[ OK ] checking repository
[ OK ] loading the ThousandEyes public key
[ OK ] installing the ThousandEyes agent
Configuring ThousandEyes
[ OK ] detecting IP address (209.197.221.99)
Selecting log path: The default log path is /var/log. Do you want to change it [y/N]? N
[ OK ] editing configuration file
Installing Add-ons (RedHat)
[ WARNING ] ThousandEyes' BrowserBot (Package required for Page Load and Transaction tests)
(Failed installing ThousandEyes' BrowserBot)
Starting ThousandEyes
[ WARNING ]ThousandEyes' BrowserBot
(Failed starting ThousandEyes' BrowserBot)
Error: Package: te-browserbot-1.10-1.x86_64 (thousandeyes)
Requires: xorg-x11-server-Xvfb
You could try using --skip-broken to work around the problem
You could try running: rpm -Va --nofiles --nodigest
```

In the above example, BrowserBot \(package name "te-browserbot"\) depends on the **xorg-x11-server-Xvfb** package, which was neither present on the system nor could the package be retrieved from a package repository.

Alternatively, you can find a similar error in the installation log file.  The install\_thousandeyes.sh script logs to the /tmp directory in a file  "install\_thousandeyes\_&lt;_random characters_&gt;.log".  The corresponding error in the install log appears as:

```text
yum -y -q install te-browserbot
Error: Package: te-browserbot-1.10-1.x86_64 (thousandeyes)
Requires: xorg-x11-server-Xvfb
```

After running the installation script, your new Enterprise Agent will contact the ThousandEyes collector to register itself. Agent information is displayed on the [Settings &gt; Enterprise Agent](https://app.thousandeyes.com/settings/agents/enterprise/) page.  The General Info section will display the installation status of BrowserBot:

IMAGE MISSING

If logs indicate that a package dependency failed to install, list the system's configured package repositories and their status \(enabled or disabled\) using the `yum repolist all` command:

```text
[ec2-user@ip-10-0-1-48 ~]$ sudo yum repolist all

Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                                                          repo name                                                                                status
rhui-REGION-client-config-server-7/x86_64                                        Red Hat Update Infrastructure 2.0 Client Configuration Server 7                          enabled:      6
rhui-REGION-rhel-server-debug-extras/7Server/x86_64                              Red Hat Enterprise Linux Server 7 Extra Debug (Debug RPMs)                               disabled
rhui-REGION-rhel-server-debug-optional/7Server/x86_64                            Red Hat Enterprise Linux Server 7 Optional Debug (Debug RPMs)                            disabled
rhui-REGION-rhel-server-debug-rh-common/7Server/x86_64                           Red Hat Enterprise Linux Server 7 RH Common Debug (Debug RPMs)                           disabled
rhui-REGION-rhel-server-debug-rhscl/7Server/x86_64                               Red Hat Enterprise Linux Server 7 RHSCL Debug (Debug RPMs)                               disabled
rhui-REGION-rhel-server-debug-supplementary/7Server/x86_64                       Red Hat Enterprise Linux Server 7 Supplementary Debug (Debug RPMs)                       disabled
rhui-REGION-rhel-server-extras/7Server/x86_64                                    Red Hat Enterprise Linux Server 7 Extra(RPMs)                                            disabled
rhui-REGION-rhel-server-optional/7Server/x86_64                                  Red Hat Enterprise Linux Server 7 Optional (RPMs)                                        disabled
rhui-REGION-rhel-server-releases/7Server/x86_64                                  Red Hat Enterprise Linux Server 7 (RPMs)                                                 enabled: 11,067
rhui-REGION-rhel-server-releases-debug/7Server/x86_64                            Red Hat Enterprise Linux Server 7 Debug (Debug RPMs)                                     disabled
rhui-REGION-rhel-server-releases-source/7Server/x86_64                           Red Hat Enterprise Linux Server 7 (SRPMs)                                                disabled
rhui-REGION-rhel-server-rh-common/7Server/x86_64                                 Red Hat Enterprise Linux Server 7 RH Common (RPMs)                                       enabled:    196
rhui-REGION-rhel-server-rhscl/7Server/x86_64                                     Red Hat Enterprise Linux Server 7 RHSCL (RPMs)                                           disabled
rhui-REGION-rhel-server-source-extras/7Server/x86_64                             Red Hat Enterprise Linux Server 7 Extra (SRPMs)                                          disabled
rhui-REGION-rhel-server-source-optional/7Server/x86_64                           Red Hat Enterprise Linux Server 7 Optional (SRPMs)                                       disabled
rhui-REGION-rhel-server-source-rh-common/7Server/x86_64                          Red Hat Enterprise Linux Server 7 RH Common (SRPMs)                                      disabled
rhui-REGION-rhel-server-source-rhscl/7Server/x86_64                              Red Hat Enterprise Linux Server 7 RHSCL (SRPMs)                                          disabled
rhui-REGION-rhel-server-source-supplementary/7Server/x86_64                      Red Hat Enterprise Linux Server 7 Supplementary (SRPMs)                                  disabled
rhui-REGION-rhel-server-supplementary/7Server/x86_64                             Red Hat Enterprise Linux Server 7 Supplementary (RPMs)                                   disabled
thousandeyes                                                                     ThousandEyes                                                                             enabled:    114
repolist: 11,383

```

Per the 'status' column \(user the horizontal scroll bar below the output to scroll right\) many of the repositories have a status of "disabled". If most repositories are disabled, it is likely that the dependency package exists in one of the disabled repositories.  Copy this output or make note of which repositories are enabled and which are disabled, as you may wish to use this information later in this procedure.

## Solution

If you know which repository contains the dependency package, enable it using the `yum-config-manager` command. For example, the xorg-x11-server-Xvfb package is contained in the rhui-REGION-rhel-server-optional repository, so you can enable the repository with the following:

```text
[ec2-user@ip-10-0-1-48 ~]$ sudo yum-config-manager --enable rhui-REGION-rhel-server-optional
```

If the repository is not known, the simplest way solution is first to enable all of your repositories with the `yum-config-manager` command \(but first make note of those repositories that are enabled\):

```text
[ec2-user@ip-10-0-1-48 ~]$ sudo yum-config-manager --enable \*
```

You can verify the the repository or repositories are enabled by repeating the `yum repolist all` .  Or just try to reinstall BrowserBot using the install\_thousandeyes.sh script.  The script's output should indicate successful installation of BrowserBot, or you can check the install log.

## Cleanup

Once you've completed the BrowserBot installation, if you enabled all your repositories but wish to have enabled only the repository which provided the dependency package and not any of the others you enabled, you can then determine which repository provided the package using the  `yum list <`_`packagename`_`>`  command:

```text
[ec2-user@ip-10-0-1-48 ~]$ sudo yum list xorg-x11-server-Xvfb
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Available Packages
xorg-x11-server-Xvfb.x86_64        1.17.2-10.el7                    rhui-REGION-rhel-server-optional
```

The above output shows that the xorg-x11-server-Xvfb package is available in the"rhui-REGION-rhel-server-optional repository.

Next, disable all packages with the following  `yum-config-manager`  command:

```text
sudo yum-config-manager --disable \*
```

 Then, using the information you saved from the first  `yum repolist all`  command, enable the repositories which should be enabled:

```text
sudo yum-config-manager --enable rhui-REGION-client-config-server-7 --enable rhui-REGION-rhel-server-releases --enable rhui-REGION-rhel-server-rh-common --enable thousandeyes --enable rhui-REGION-rhel-server-optional 
```

Then verify the repository statuses are correct by repeating the `yum repolist all` command.

## Further troubleshooting

If enabling all system repositories does not resolve the dependency problem, contact Amazon Web Services technical support to determine what repositories are needed and how to add and/or enable the needed repositories in your /etc/yum.repos.d directory.

