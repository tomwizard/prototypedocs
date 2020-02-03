# Installing Enterprise Agents in Proxy Environments

Some organizations' security policies require web communication \(HTTP, HTTPS and FTP\) from internal networks to the Internet be sent through a proxy server, in order to inspect and control the communication. Installation of an Enterprise Agent requires varying degrees of internet access, depending on the type of Enterprise Agent being installed. Additional or different installation steps may be required to install an Enterprise Agent when a proxy server is required for internet access.

## Types of proxy server

 Proxy servers have two principle characteristics which govern the way clients are configured:

* **Explicit or transparent**  Proxy servers which require each client to be configured with the proxy's IP address \(or hostname\) and port number, and \(optionally\) user credentials, are called explicit proxies. Proxies which do not require clients to be configured with proxy information are called transparent proxies.
* **SSL decrypting or non-SSL decrypting**  Proxy servers which perform SSL/TLS decryption require each client to be configured with the proxy's CA certificate \(sometimes called a signing certificate or root certificate\). Non-SSL decrypting proxies do not require clients to be configured with a CA certificate.

Figure 1 below indicates the required configuration information for each of the four combinations of proxy type:

For proxies that are transparent and non-SSL decrypting, no additional configuration is required to perform the Enterprise Agent installation. Follow the installation instructions for your type of Enterprise Agent installation without a proxy.

The remaining three configurations of proxy are referred to in the remainder of this document with the following letters :

* **A:** Explicit, SSL decrypting proxy configuration
* **B:** Explicit, non-SSL decrypting proxy configuration
* **C:** Transparent, SSL decrypting proxy configuration

Consult with your proxy or network administrator to determine which type of proxy you have, and obtain all required information before proceeding.

## Types of Agent deployment

 Click the link below that corresponds to the type of Enterprise Agent installation being performed, to be taken to instructions for that installation type.

* [Deploying a Linux package Agent]()
* [Deploying a Docker Agent]()
* [Deploying an Appliance]()

## Deploying a Linux package Agent

 Deploying a Linux package Agent is performed by downloading and running the install\_thousandeyes.sh shell script.  The instructions for downloading and running the script are found by going to the **+ Add New Agent** form of the [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise) page, and selecting "Linux Package" for the **Package Type**, then clicking the **Show Advanced Options** link. The instructions are reproduced below:

```text
curl -Os https://downloads.thousandeyes.com/agent/install_thousandeyes.sh
chmod +x install_thousandeyes.sh
sudo ./install_thousandeyes.sh -b <ACCOUNT-TOKEN>
```

 In the first line, the curl command is used to download the install\_thousandeyes.sh file.  The curl command may require additional flags to use the proxy.

In the third line, the install\_thousandeyes.sh script is executed.  The script runs the Linux system's package management tool \(if Ubuntu, the APT package manager; if Red Hat/CentOS/Oracle Linux, the YUM package manager\) to download and install the Enterprise Agent software packages. To download and install the Agent through the proxy, the APT or YUM configuration file must be edited to include proxy information.  Then the script configures the installed Agent. The script may require additional command line flags to use the proxy.

The following configuration steps may be required:

1. [Install the proxy server's CA certificate]()
2. [Configure the system package manager to use the proxy server]()
3. [Run the curl command with modified flags]()
4. [Run the install\_thousandeyes.sh script with modified flags]()

 For proxy configuration A, B or C use the following table of steps:

| Proxy Configuration | Perform the following configuration steps |
| :--- | :--- |
| A | 1, 2, 3, 4 |
| B | 2, 3, 4 |
| C | 1, then [standard Linux package installation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS) |

####  1. Install the proxy server's CA certificate

 Depending on a customer's process for installing new systems, the proxy's CA certificate may not be installed by default. If the certificate is not pre-installed, the procedure to add a CA certificate to a Linux system with an Enterprise Agent is provided in the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-linux).  Select either the [Ubuntu](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-linux-ubuntu) or the [Red Hat Enterprise Linux / CentOS / Oracle Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-linux-rhel-centos) section.

**IMPORTANT:** Only install the CA certificate into the system CA certificate store. Do not perform the BrowserBot CA certificate installation, as the BrowserBot package is not yet installed.

#### 2. Configure the package manager to use the proxy server

 The install\_thousandeyes.sh script runs the system's package manager \(APT or YUM\) to download and install Agent packages. Additionally, the package manager will be used to automatically update the Agent packages and perform essential operating system updates. The procedure to configure the system package manager to use the proxy server is provided in the ThousandEyes Knowledge Base article [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG). Select either the [Ubuntu](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#config-proxy-linux-apt) or [RHEL / CentOS / Oracle Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#config-proxy-linux-apt) section.

The proxy used by the package manager need not be the same proxy used for the main Agent processes. Alternatively, if all needed repositories are mirrored on the internal network, or if communication to standard repositories on the Internet is permitted without a proxy, then this step can be skipped.

#### 3. Run the curl command with modified flags

 Modify the curl command to use flags for the proxy name or IP address and port number, and optionally a username and password:

```text
curl \
  -x <PROXY IP ADDRESS or HOSTNAME>:<PROXY PORT> \
  -U <USERNAME>:<PASSWORD> \
  -Os https://downloads.thousandeyes.com/agent/install_thousandeyes.sh
```

 Depending on the characters used in the username and password, the &lt;USERNAME&gt;:&lt;PASSWORD&gt; string may need to be enclosed in double-quotes to avoid being interpreted by the shell.

#### 4. Run the install\_thousandeyes.sh script with modified flags

 Run the chmod command to make the script executable.  Then, with the proxy name or IP address and port number, and optionally a username and password, modify the script command's flags:

```text
chmod +x install_thousandeyes.sh
sudo ./install_thousandeyes.sh \
  -b \
  -t STATIC \
  -P <PROXY IP ADDRESS or HOSTNAME>:<PROXY PORT> \
  -U <USERNAME> \
  -u <PASSWORD> \
  <ACCOUNT TOKEN>
```

 The script will install the Enterprise Agent and the optional BrowserBot component. Omit the -b flag if BrowserBot is not required. The script will also configure the /etc/te-agent.cfg file with the proxy information provided by the command's flags.

Alternatively, if the Enterprise Agent will use a PAC file to select its proxy, then modify the script command for the PAC file:

```text
chmod +x install_thousandeyes.sh
sudo ./install_thousandeyes.sh \
  -b \
  -t PAC \
  -P <PAC FILE URL> \
  -U <USERNAME> \
  -u <PASSWORD> \
  <ACCOUNT TOKEN>
```

To see all the supported command line flags of the script, use the --help flag:

```text
./install_thousandeyes.sh --help
```

**NOTE:** Authentication to the proxy is performed via the HTTP Basic authentication mechanism, including CONNECT method requests for subsequent HTTPS-based requests. Basic authentication credentials are sent in clear text, encoded in Base64. Organizations which do not allow any credentials to be transmitted on a network in clear text should consider alternatives to credential-based authentication to the proxy, such as configuring the proxy to whitelist Enterprise Agents via their IP addresses. 

## Deploying a Docker Agent

 Deploying a Docker Enterprise Agent is performed by running a series of docker commands on the Docker host.  The commands are created by going to the **+ Add New Agent** form of the [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise) page, and selecting "Docker" for the **Package Type**, then filling out the form.

The following configuration steps may be required:

1. [Install proxy server's CA certificate on the Docker host]()
2. [Configure Docker to use the proxy server]()
   * [Ubuntu 16.04 / RHEL 7 / CentOS 7]() or
   * [Ubuntu 14.04]()
3. [Create Enterprise Agent Docker container with proxy configuration]() 
4. [Install proxy server's CA certificate into the Enterprise Agent container]()
5. [Configure the container package manager to use the proxy server]()

  For proxy configuration A, B or C use the following table of steps:

| Proxy Configuration | Perform the following configuration steps |
| :--- | :--- |
| A | 1, 2, 3, 4 |
| B | 2, 3, 4 |
| C | 1, then [standard Docker installation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS), 4 |

### 1. Install proxy server's CA certificate on the Docker host

Depending on a customer's process for installing new systems, a Docker host may not have the proxy's CA certificate installed by default. If the required certificate is not pre-installed, the procedure to add a CA certificate to a Linux system acting as the Docker host is provided in the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2f#installing-on-linux).  Select either the [Ubuntu](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-linux-ubuntu) or the [Red Hat Enterprise Linux / CentOS / Oracle Linux](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2f#installing-on-linux-rhel-centos) section.

For other Linux distributions or non-Linux Docker hosts, consult your operating system documentation for more information on adding CA certificates to your system's certificate store, or contact the ThousandEyes Customer Success team.

**IMPORTANT:** Only install the CA certificate into the system CA certificate store. Do not perform the BrowserBot CA certificate installation.

### 2. Configure Docker to use the proxy server

 This procedure configures the Docker commands to use the proxy server when communicating to servers on the internet.

**2.1 Ubuntu 16.04 / Red Hat Enterprise Linux 7 / CentOS 7 / Oracle Linux**

 Create the /etc/systemd/system/docker.service.d directory:

```text
sudo mkdir -p /etc/systemd/system/docker.service.d
```

 Edit the file in which then Docker proxy configuration will be stored:

```text
sudo nano /etc/systemd/system/docker.service.d/proxy.conf
```

 Enter the following environment variable configuration, replacing the sample values shown below with your proxy configuration information:

```text
[Service]
Environment="HTTP_PROXY=http://user:pass@10.1.2.32:3128/"
Environment="HTTPS_PROXY=http://user:pass@10.1.2.32:3128/"
```

 Reload the systemd configuration:

```text
sudo systemctl daemon-reload
```

 Restart the Docker service \(warning, this command restarts all running Docker containers\):

```text
sudo systemctl restart docker
```

 Verify whether the newly configured environment variables HTTP\_PROXY and HTTPS\_PROXY have the correct values:

```text
sudo systemctl show --property=Environment docker
```

 Download the Docker image using the docker pull command:

```text
docker pull thousandeyes/enterprise-agent
```

**2.2 Ubuntu 14.04**

 Edit the file in which the Docker proxy configuration will be stored:

```text
sudo nano /etc/default/docker
```

 Append the following content, replacing the sample values shown below with your proxy configuration information:

```text
export  "http_proxy=http://user:pass@10.1.2.32:3128/"
export "https_proxy=http://user:pass@10.1.2.32:3128/"
```

 Restart the Docker service \(NOTE: this command restarts all running Docker containers\):

```text
sudo restart docker
```

 Download the Docker image using the docker pull command:

```text
docker pull thousandeyes/enterprise-agent
```

### 3. Create Enterprise Agent Docker container with proxy configuration

 Log in to the ThousandEyes web application and open the [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise) page.  The commands to create the Enterprise Agent Docker container are produced by opening **+ Add New Agent** form and selecting "Docker" for the **Package Type**, then by completing the form.  An example of the completed form is below:

Note that Docker container Agents do not support use of PAC files for automatic updates.  APT, the package management tool which performs the updates, does not have the ability to parse PAC files.  For customers who select PAC as the **Proxy Type**, a single proxy must be chosen and configured manually for automatic updates of the ThousandEyes and operating system packages. For more information, refer to the [Configuring proxy settings for system updates - APT on Ubuntu](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#config-proxy-linux-apt) section of the ThousandEyes Knowledge Base article [Installing Enterprise Agents in Proxy Environments](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG).

Copy and run the provided commands on the Docker host to create the Enterprise Agent Docker container.

### 4. Install proxy server's CA certificate into the Enterprise Agent container

 The procedure to add your proxy server's CA certificate into the new Enterprise Agent Docker container is found in the [Installing on Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-docker) section of the ThousandEyes Knowledge Base article [Installing CA certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2f#installing-on-docker).

## 5. Configure the container package manager to use the proxy server

For Docker-based Enterprise Agents the APT package manager's proxy configuration must be configured statically if the APT package downloads must be proxied. The procedure to configure the APT package manager's proxy configuration is found in the Configuring proxy settings for APT package manager section of the ThousandEyes Knowledge Base article [Installing Enterprise Agents in Proxy Environments](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG).

##  Deploying an Appliance

 Deploying a Virtual Appliance requires downloading the OVA format file or Hyper-V format file from the Enterprise Agents page of the ThousandEyes platform, and importing the file into a hypervisor. Physical Appliances require downloading an ISO image. If a customer's browser can reach [https://app.thousandeyes.com](https://app.thousandeyes.com/) then downloading the required file is possible from the **+ Add New Agent** form of the [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise) page. If needed, customers should contact their network administrator for steps to configure a browser to use their proxy server.

The following configuration steps may be required:

1. [Configure Agent to use the proxy server]()
2. [Configure the Appliance's package manager to use the proxy server]()
3. [Install proxy server's CA certificate on the Appliance]()

 Once the Virtual Appliance is imported into your virtualization platform and started, or the Physical Appliance installed from the ISO image, then for proxy configuration A, B or C use the following table of steps:

| Proxy Configuration | Perform the following configuration steps |
| :--- | :--- |
| A | 1, 2, 3 |
| B | 1, 2 |
| C | 3 |

#### 1. Configure Agent to use the proxy server

 The procedure to configure the Appliance's Agent to use the proxy server is provided in the [Configuring proxy settings for Web Proxy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#config-proxy-appliance-web) section of the ThousandEyes Knowledge Base article [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG).

#### 2. Configure the Appliance's package manager to use the proxy server

 The Appliance used the APT package manager. The package manager will be used to automatically update the Agent packages and perform essential operating system updates. The procedure to configure the APT package manager to use the proxy server is provided in the [Configuring proxy settings for APT Proxy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG#config-proxy-appliance-apt) section of the ThousandEyes Knowledge Base article [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG).

The proxy used by the package manager need not be the same proxy used for the main Agent processes. Alternatively, if all needed repositories are mirrored on the internal network, or if communication to standard repositories on the Internet is permitted without a proxy, then this step can be skipped.

#### 3. Install proxy server's CA certificate on the Appliance

 The procedure to configure the Appliance to use a CA certificate are found in the [Installing on Appliances](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG#installing-on-va) section of the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG).  
 

