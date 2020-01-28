# Bash \(ShellShock\) Security notice

On September 24, 2014, a critical vulnerability in the Bash shell \(shipped with many Linux configurations\) was documented in the National Vulnerability Database as CVE-2014-6271.  This notification can be found on the NIST site at[ this link](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-6271).

ThousandEyes Enterprise Agents use Linux-based operating systems to run ThousandEyes Agent software, either by deploying the Ubuntu-based Virtual Appliance \(“VA”, “VAs”\), or installing the Agent package on a supported Linux operating system.  Since both configurations leverage Linux, the Bash shell vulnerabilities collectively known as ShellShock \(CVE-2014-6271, CVE-2014-7169, CVE-2014-7186, CVE-2014-7187\) may be applicable to the platform running your Enterprise Agent:

_NOTE: As of September 24th, 2014, newly downloaded VAs have been patched for this vulnerability.  Please see the section Identification of vulnerable systems for more information._  

##  Identification of vulnerable systems

Virtual Appliances downloaded from the ThousandEyes web site on or after September 24th, 2014 have been patched and are not vulnerable to this issue.  Since ThousandEyes VAs are configured to download and apply security updates automatically, all Internet-connected VAs will have performed the update at this time.

Additional details, including test code for the vulnerability are available here: [https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/](https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/)

To determine whether or not your Enterprise Agent’s platform is vulnerable, access your VA's command line using Secure Shell \(SSH\), and run the test command identified in the article above.  We’ve excerpted the line below for your convenience.  

### ShellShock vulnerability test command:

```text
$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
```

### Expected vulnerable response signature:

```text
$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
vulnerable
this is a test
```

### Expected patched response signature \(Ubuntu/Debian\):

```text
$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
bash: warning: x: ignoring function definition attempt
bash: error importing function definition for 'x'
this is a test
```

### Expected patched response signature \(RedHat/CentOS\):

```text
$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
this is a test
```

Since SSH access is tightly controlled on ThousandEyes VAs, refer to the following Knowledge Base article that is appropriate to your SSH client’s operating system:

* [Windows-based SSH instructions](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnaKAC)
* [Mac OS X and Linux-based SSH instructions](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnrKAC)

For a linux package-based Agent, multiple means of command line access may be available, depending on the configuration of the machine.  If you do not have SSH access with root or sudo privileges, please refer this article to your system administrator.

## Remediation of vulnerable systems

ThousandEyes VAs which have connectivity to the Internet will automatically download and install security patches.  You may confirm the system has been patched using the aforementioned test command, validating against the expected responses.

Linux package-based Enterprise Agents should be patched according to the instructions for the particular Linux distribution.  Consult your distribution’s documentation or support web site to determine the appropriate remediation steps for your distribution of Linux.  We strongly recommend implementing automatic security updates for Linux systems.  Consult your distribution's documentation for implementation instructions of automatic security updates.

Our team has excerpted remediation steps below, which will bring the Bash version up to date below, for Enterprise Agent-supported operating systems.  As always, it is advisable to verify closure of the vulnerability once the update has been made.

### Ubuntu-based remediation:

```text
$ (sudo) apt-get install bash
```

### RedHat Enterprise Linux/CentOS-based remediation:

```text
$ (sudo) yum install bash
```

For more information, please [contact our Customer Success team](mailto:support@thousandeyes.com?subject=CVE-2014-6271).

