# Instructions for mitigating Meltdown and Spectre on Enterprise Agents

As of February 22, 2018, updates for ThousandEyes Enterprise Agents have been made available and tested for the Meltdown and Spectre Version 1 and 2 vulnerabilities. This document outlines recommendations for mitigating vulnerabilities in Enterprise Agents deployed in customer environments. Follow the instructions below for each Enterprise Agent deployment type to apply security updates to your Enterprise Agents.

Please see the ThousandEyes Knowledge Base article [Security Advisory: Meltdown and Spectre](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009SQkCAM_Security-Advisory:-Meltdown-and-Spectre) describing ThousandEyes' general response to the Meltdown and Spectre vulnerabilities.

## Instructions by Agent deployment and environment

### Linux Package Enterprise Agents deployed in virtual environments

Customers who run their own hypervisor software must patch the hypervisor and the host operating system on which the hypervisor runs, in addition to the guest operating system running the Enterprise Agent. Check the information below for your host operating system and hypervisor, or consult your vendor's support resources for updates.

Customers who use cloud-based service providers to run virtual environments will typically be responsible for updating the operating systems of the guest virtual machines.

#### VMware

* [https://www.vmware.com/us/security/advisories/VMSA-2018-0002.html?src=vmw\_so\_vex\_amaur\_427](https://www.vmware.com/us/security/advisories/VMSA-2018-0002.html?src=vmw_so_vex_amaur_427)
* Download and install patch 
* Addresses side-channel analysis due to speculative execution
  * CVE-2017-5753
  * CVE-2017-5715 
* Applies to VMware products 
  * ESXI
  * Workstation / Workstation Pro
  * Fusion / Fusion Pro
* [https://www.vmware.com/us/security/advisories/VMSA-2018-0004.html?src=vmw\_so\_vex\_amaur\_427](https://www.vmware.com/us/security/advisories/VMSA-2018-0004.html?src=vmw_so_vex_amaur_427)
* Download and install patch
* Addresses Hypervisor-Assisted Guest Remediation for speculative execution issue
  * CVE-2017-5715 
* Applies to VMware products 
  * vSphere
  * ESXI
  * Workstation / Workstation Pro
  * Fusion / Fusion Pro

#### Windows

* [https://support.microsoft.com/en-us/help/4072698/windows-server-guidance-to-protect-against-the-speculative-execution](https://support.microsoft.com/en-us/help/4072698/windows-server-guidance-to-protect-against-the-speculative-execution)
* For Agents deployed in Hyper-V environments Windows Server will need to be updated first. Once the Server has been updated Hyper-V's registries will need to be modified to stop VM to VM and VM to host attacks. Refer to instructions linked above.

| Version | KB Article Showing updates and patches |
| :--- | :--- |
| Windows Server, version 1709 \(Server Core Installation\)  | [4056892](https://support.microsoft.com/en-us/help/4056892) |
| Windows Server 2016 | [4056890](https://support.microsoft.com/en-us/help/4056890) |
| Windows Server 2012 R2 | [4056898](https://support.microsoft.com/en-us/help/4056898) |
| Windows Server 2012  | Not available |
| Windows Server 2008 R2 | [4056897](https://support.microsoft.com/en-us/help/4056897) |
| Windows Server 2008 | Not available |

#### Amazon Web Services \(AWS\) 

* See this link: [https://aws.amazon.com/security/security-bulletins/AWS-2018-013/](https://aws.amazon.com/security/security-bulletins/AWS-2018-013/)
* Underlying virtualization infrastructure should be patched for Meltdown and Spectre 
* Customers are still responsible to update OS kernels for their hosts 

#### Google Cloud 

* See this link: [https://www.blog.google/topics/google-cloud/answering-your-questions-about-meltdown-and-spectre/](https://www.blog.google/topics/google-cloud/answering-your-questions-about-meltdown-and-spectre/)
* Underlying virtualization infrastructure should be patched for Meltdown and Spectre 
* Customers are still responsible to update OS kernels for their hosts 

#### Microsoft Azure

* See this link:[https://azure.microsoft.com/en-us/blog/securing-azure-customers-from-cpu-vulnerability/](https://azure.microsoft.com/en-us/blog/securing-azure-customers-from-cpu-vulnerability/) 
* Underlying virtualization infrastructure should be patched for Meltdown and Spectre 
* Customers are still responsible to update OS kernels for their hosts 

For virtualized operating systems, follow instructions found under _Linux Package Enterprise Agents deployed in physical environments._

### Linux Package Enterprise Agents deployed in physical environments

#### Ubuntu

For Ubuntu based systems to upgrade to the latest kernel run the following commands, or follow instructions found at  [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades)

Here's the quick & easy version:

```text
$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ uname -rs 
Linux 4.4.0-98-generic 
$ sudo reboot 
<boot process> 
<boot process> 
<boot process> 
$ uname -rs 
Linux 4.4.0-112-generic
```

| Version | Kernel Base | Patch |
| :--- | :--- | :--- |
| Ubuntu 14.04 LTS | [4.4 HWE](https://usn.ubuntu.com/3522-2/) | [https://usn.ubuntu.com/usn/usn-3540-2/](https://usn.ubuntu.com/usn/usn-3540-2/) |
| Ubuntu 14.04 LTS | 3.13 | [https://usn.ubuntu.com/usn/usn-3542-1/](https://usn.ubuntu.com/usn/usn-3542-1/) |
| Ubuntu 16.04 LTS | 4.13 HWE | [https://usn.ubuntu.com/usn/usn-3541-2/](https://usn.ubuntu.com/usn/usn-3541-2/) |
| Ubuntu 16.04 LTS | 4.4 | [https://usn.ubuntu.com/usn/usn-3540-1/](https://usn.ubuntu.com/usn/usn-3540-1/) |

\*refer to patch notes to check if your kernel version has been patched. 

#### Red Hat Enterprise Linux and CentOS

* All patched Kernels 
  * https://access.redhat.com/security/vulnerabilities/speculativeexecution
* RHEL 6.x and CentOS 6.x
  * Patched Kernel
  * https://access.redhat.com/errata/RHSA-2018:0008
  * kernel-2.6.32-696.18.7.el6
* RHEL 7.x and CentOS 7.x
  * Patched Kernel
  * https://access.redhat.com/errata/RHSA-2018:0007
  * kernel-3.10.0-693.11.6.el7

You can check your current kernel version with "uname -rs"

```text
[root@centos68 ~]# uname -rs
Linux 2.6.32-696.3.1.el6.x86_64
```

If your kernel is not currently patched you can retrieve the latest updates with "yum update". Once run, check that a patched kernel has been loaded with "rpm -qa \| grep kernel" - then reboot to apply the update.

```text
[root@centos68 ~]# rpm -qa | grep kernel
kernel-firmware-2.6.32-696.18.7.el6.noarch
kernel-2.6.32-642.11.1.el6.x86_64
dracut-kernel-004-409.el6_8.2.noarch
kernel-2.6.32-696.3.1.el6.x86_64
kernel-headers-2.6.32-696.18.7.el6.x86_64
kernel-2.6.32-696.18.7.el6.x86_64
kernel-2.6.32-642.15.1.el6.x86_64
kernel-2.6.32-642.el6.x86_64
```

After the reboot, run "uname -rs" once again to verify the new kernel has been loaded.

```text
[root@centos68 ~]# uname -rs
Linux 2.6.32-696.18.7.el6.x86_64
```

### ThousandEyes Virtual and Physical Appliances

The latest security updates from Ubuntu should have been applied to your Appliances automatically. Since this change affects the kernel, customers will be required to reboot the Agent. Review the ThousandEyes Knowledge Base article [Rebooting ThousandEyes Appliances for Spectre and Meltdown mitigation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009Sa6CAE) for more information on the proper way to verify that the kernel has been updated and actions required.

### ThousandEyes Enterprise Agents deployed as Docker containers

Due to Docker's design, which shares the kernel of the container with the host, there are no upgrades needed within deployed Docker containers. Please refer to appropriate operating system documentation in order to update the host's underlying operating system.

## Additional information

### Performance impact

 We do not expect a significant performance impact based on testing done in our lab environment.  See [this link](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0440000009STUCA2) for information showing details on the nominal performance impact.

### Further updates

 This article will be updated as more updates are made available.

