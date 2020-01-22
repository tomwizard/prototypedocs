# Configuring a local mirror of the ThousandEyes package repository

Customers may need to create a local copy of the ThousandEyes Linux package repositories used by ThousandEyes Enterprise Agents for reasons such as change control or security requirements.  This document outlines the requirements and processes to create a local repository mirror containing packages required by the ThousandEyes Enterprise Agents, and to modify ThousandEyes Enterprise Agents to update from the local mirror.

Depending on the type of Linux operating system on which your Enterprise Agents run, you will need to create a Red Hat repository, an Ubuntu repository or both.  Mirroring the ThousandEyes repository requires approximately 10 GB of storage space per repository, along with permissions to install software.

**NOTE**: ThousandEyes Enterprise Agents should run current versions of ThousandEyes packages.  If the Agent cannot update because of failure to reach the mirrored repository or with the repository failing to provide current package versions, then there is risk that certain features of the Enterprise Agent will not work as advertised.  Use this process at your own risk.

## Table of Contents

## Configure a server for the repository

This document provides installation and configuration instructions on a Red Hat Enterprise Linux \(RHEL\) version 7 server operating system and on an Ubuntu 16.04 server operating system.  Other operating systems can be used; consult your operating system documentation to determine what comparable commands are needed for the steps listed below, or contact the ThousandEyes Customer Success Center.

Don’t be confused: a server running any type of operating system can host either Red Hat or Ubuntu repositories or both. In general, however, we recommend using the same Linux distribution for your server’s operating system as the type of repository, if possible.

General system administration tasks for the server, such as application of updates and patches, are out of scope for this document.  Consult your operating system documentation.

### Determine which type\(s\) of repository to create

Customers using any type of ThousandEyes Appliance should create an Ubuntu mirror. This includes Virtual Appliances, Hyper-V Appliances, Cisco IOS XE container-based Enterprise Agents and the Physical Appliance.  

Customers with Enterprise Agents installed via Linux package or Docker container should create mirror types that are the same as the Linux distribution used for the Enterprise Agent.

To determine which type\(s\) of Enterprise Agents are used in your organization, review the listing of your Enterprise Agents from the Enterprise Agents page in the ThousandEyes platform.  Enterprise Agent operating systems are listed in the General Info box:

![](https://lh6.googleusercontent.com/U87pmiiIsck4zIvcBwkmTcjkAgid3qp9ijvHjwbbSMmhpdJiKNI1KdF3LQpRo9g3yAsYECwZ8g8hi6oVh1ytFDUey6dovGrcEjkOFUYGWwj_ZgBGjl50wHIewvFV41XZvXvbxx2w)

  
Be sure to check all your Account Groups, as Enterprise Agents may not be assigned to all Account Groups in an organization.  The Enterprise Agents page has a selector to display Agents in the current Account Group and not in the current Account Group:

![](https://lh6.googleusercontent.com/QSFWdiqIUKeI-PDfCp9sWY_b3kZVXnKPb_PcmPmmQCWfn8fAk6YGMMBI_WNd4pPDcQ5p9uANJOBnoxcyTWF1q0MBxrD225C8OBztzzgwmyh6Z-tWJdoum1Y1ZGz7-mWmAtsW9iCG)

### Install wget and Apache packages

Install wget and Apache’s web server \(httpd\). wget will be used to copy the contents of the ThousandEyes repository to your mirror.

#### For a RHEL operating system:

```text
$sudo yum install wget httpd
```

#### For a Ubuntu operating system:

```text
$sudo apt-get install wget httpd
```

### Configure Apache to start automatically

For systems using Upstart to manage services run the following commands \(Ubuntu 12, 14, Red Hat v6 variants\):

```text
$service httpd start
$chkconfig httpd on
```

For systems using systemd to manage services run the following commands \(Red Hat v7 variants, Ubuntu 16\):

```text
$systemctl start httpd
$systemctl is-enabled httpd
```

### Create a directory for the repository or repositories 

Next we’ll need a directory for the repository’s content.  You’ll need at least 10 GB per repository to host this content.

#### RHEL repository:

```text
$mkdir -p /var/repomirror/yum
```

#### Ubuntu repository:

```text
$mkdir -p /var/repomirror/apt
```

### Set permissions on the directory

Change the directories of each repository to the apache user \(the user is created when installing Apache\):

```text
$chown -R apache:apache /var/repomirror
```

### Mirror the repository

#### RHEL repository:

```text
$cd /var/repomirror/yum
$wget --mirror -e robots=off http://yum.thousandeyes.com/
$find /var/repomirror/ -type f -name '*\?C=*' -delete
$ln -s /var/repomirror/yum/yum.thousandeyes.com /var/www/html/yum
```

#### Ubuntu repository:

```text
$cd /var/repomirror/apt
$wget --mirror -e robots=off http://apt.thousandeyes.com/
$find /var/repomirror/ -type f -name '*\?C=*' -delete
$ln -s /var/repomirror/apt/apt.thousandeyes.com /var/www/html/apt
```

### Configure the web server

Modify the default page for Apache to be the index of the root directory by editing /etc/httpd/conf.d/welcome.conf.  Change the line:

```text
    Options -Indexes
```

to

```text
    Options +Indexes
```

then comment out or delete the lines below the LocationMatch directive block, so that the configuration file has only:

```text
<LocationMatch "^/+$">
    Options +Indexes
    ErrorDocument 403 /error/noindex.html
</LocationMatch>
```

Next, based on whether you’re going to host a Red Hat mirror, an Ubuntu mirror or both, configure Apache’s DocumentRoot \(the directory that is accessed when browsing a URL path of “/”\) to be the newly created repository’s parent directory.  Also, set the option to allow browsing the index of that directory. The configuration file is /etc/httpd/conf/httpd.conf.

This example shows the configuration for a single mirror of the Red Hat type:

```text
DocumentRoot "/var/www/html/yum"

<Directory /var/www/html/yum>
    Options Indexes FollowSymLinks
    AllowOverride None
</Directory>
```

If you are hosting an Ubuntu mirror, change the two instances of “yum” to “apt” in the above configuration.

If hosting both types, the configuration uses the parent directory as the DocumentRoot:

```text
DocumentRoot "/var/www/html"

<Directory /var/www/html/yum>
    Options Indexes FollowSymLinks
    AllowOverride None
</Directory>

<Directory /var/www/html/apt>
    Options Indexes FollowSymLinks
    AllowOverride None
</Directory>
```

Once edits to httpd.conf are complete, restart Apache:

```text
$apachectl restart
```

### Configure SSL/TLS \(optional\)

If your security policies require your local mirror to run SSL/TLS, obtain and install a server certificate on the web server.  This document doesn’t cover creation or installation of server certificates. Consult the Apache Project’s HTTP Server documentation and other publicly available resources.

**NOTE**: self-signed certificates cannot be used to host a repository server, as the certificate verification performed by the yum, apt and other package management utilities will fail.

### Modify iptables or other host-based firewall rules \(if needed\)

If the server is running iptables, then configure a rule \(typically in the INPUT chain\) to allow access to port 80/TCP from any Enterprise Agent \(or port 443 if using SSL/TLS\).  If the server is running another type of host-based firewall, then consult the documentation for the firewall software to allow access to the web server.  

### Test your web server

Verify that you can access the web server in a browser on the local network.  You should be able to use Chrome or another browser to load the web site on port 80/TCP and/or 443/TCP if using SSL/TLS. Ensure that you can get a directory listing of the DocumentRoot directory and the yum and/or apt directories.

## Modify repository files on your Agents

On each Enterprise Agent, you’ll need to modify the repository location in the file that the package manager consults when checking for packages.  The location is based on the choice of installation type: yum, apt or both.

### Linux package and Docker Agents--yum \(RedHat variants\)

**Modify the existing repository file**

Edit /etc/yum.repos.d/thousandeyes.repo and add an enabled=0 line to the file.

####  Create a new repository file

```text
$cp /etc/yum.repos.d/thousandeyes.repo /etc/yum.repos.d/thousandeyes-mirror.repo
```

#### Edit the thousandeyes-mirror.repo file

* Change "\[thousandeyes\]" to "\[thousandeyes-local\]"
* Change "name=Thousandeyes" to "name=Thousandeyes-local"
* Set enabled=1
* Change "basename" to use the destination to the IP address or hostname of the web server
* Change "basename" to use the https protocol if using SSL/TLS

### Linux package and Docker Agents--apt \(Ubuntu variants\)

#### Modify the existing repository file

Edit /etc/apt/sources.list.d/thousandeyes.list and comment out the one line in the top of the file by adding a \# character to the beginning of the line.

#### Create a new repository file

```text
$cp /etc/apt/sources.list.d/thousandeyes.list /etc/apt/sources.list.d/thousandeyes-local.list
```

#### Edit the thousandeyes-mirror.list file

* Change the destination to the IP address or hostname of the web server
* Change the protocol from https to http if not using SSL/TLS

### ThousandEyes Appliance \(physical/virtual\)

Log into the ThousandEyes Virtual Appliance’s web console and select the Advanced Settings tab.  For the Software Repository Location, select the "Custom option", and set the field to the correct URL for your Ubuntu-type repository, including the path to the repository if the repository is not the DocumentRoot \(such as in the case of a server hosting both types of repositories\). For example:

**Software Repository Location** http://apt.mycompany.com/

for a repository that is only hosting an apt/Ubuntu repository mirror, and

**Software Repository Location** http://mirror.mycompany.com/apt

for a repository that is hosting an apt/Ubuntu repository mirror and a yum/Red Hat repository mirror.

The directory you target should contain the thousandeyes-apt-key.pub file.

Save your changes with the **Save** button.

## Synchronization of the mirror

To update the mirror’s contents, run these commands:

```text
$cd /var/repomirror/yum
$wget --mirror -e robots=off http://yum.thousandeyes.com/
$cd /var/repomirror/apt
$wget --mirror -e robots=off http://apt.thousandeyes.com/
$find /var/repomirror/ -type f -name '*\?C=*' -delete
```

This will cause only updated versions of files to be downloaded.  

**NOTE:** ThousandEyes updates Enterprise Agent software frequently.  Scheduled releases occur every two weeks on Tuesdays, typically.  Synchronization should be performed on a regular basis - we recommend weekly.

