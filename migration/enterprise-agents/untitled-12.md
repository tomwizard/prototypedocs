# Configuring an Enterprise Agent to use a proxy server

Some organizations' security policies require web communication from internal networks to the Internet be sent through a proxy server, in order to inspect and control the communication. Additionally, organizations may deploy proxies for web caching, which can improve web browsing performance and reduce network congestion.

This article provides background information on web proxy servers, and steps to configure proxy server settings on an existing Enterprise Agent. Customers who have not yet installed an Enterprise Agent, and are in an environment which requires a proxy server to access the Internet should first read the ThousandEyes Knowledge Base article [Installing Enterprise Agents in Proxy Environments](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG) to ensure that the installation can be done through a proxy.

Proxies for Voice Layer tests are not configured using the information in this article. Customers needing configuration information for proxies of Voice over IP communication should consult the ThousandEyes Knowledge Base article [SIP Server test settings](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB68CAG).

## Table of contents

1. [Introduction]()
   * [Types of proxy server]()
   * [Configuration methods]()
   * [Additional configuration information]()
   * [Next steps]()
2. [Docker container Enterprise Agents]()
   * [Reconfigure proxy settings for existing Enterprise Agent]()
   * [Static configuration]()
   * [PAC file configuration]()
     * [PAC file stored on Docker Agent]()
   * [Configuring proxy settings for APT package manager]()
3. [Virtual and Physical Appliances]()
   * [Configuring proxy settings for Web Proxy]()
   * [Configuring proxy settings for Apt Proxy]()
4. [Linux package-based Enterprise Agents]()
   * [Configuring proxy settings for Enterprise Agent software]()
   * [Configuring proxy settings for APT package manager on Ubuntu]()
   * [Configuring proxy settings for YUM]() [package manager]() [on RHEL / CentOS / Oracle Linux]()
5. [Installing proxy CA certificates]()
6. [Verification]()

## 1. Introduction

Configuring a proxy on an Enterprise Agent depends on a number of variables.  The type of proxy server will affect the configuration of the Enterprise Agent. Additionally, the type of Agent deployment used \(Appliance, Docker container or Linux package\) will affect the configuration process. Additionally, proxy configuration may need to be performed both for the Enterprise Agent's software, and for the system's package manager which performs software updates. Before attempting to configure the Enterprise Agent, customers should read this Introduction to determine what information will be required. Then proceed to the section\(s\) which contains configuration steps needed for your environment.

#### Types of proxy server

Proxy servers have two principle characteristics which govern the way clients are configured:

* **Explicit or transparent**  
   Proxy servers which require each client to be configured with the proxy's IP address \(or hostname\) and port number, and \(if required\) user credentials, are called explicit proxies. Clients open a TCP/IP-based connection to the proxy. The proxy initiates a second TCP/IP connection to the server.

   Clients connecting to explicit proxies use the same [HTTP methods](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods) \(GET, POST, HEAD, etc...\) for http URLs as with a direct connection to the server. For https URLs, the client issues an HTTP CONNECT method which indicates to the proxy that data in subsequent packets from the client should be transferred directly into the data of packets sent to the server, at a specified domain name or IP address, and TCP port number. In subsequent packets, information including the actual HTTP request method and other request data \(headers and body\) can be sent through the proxy, even when encrypted with SSL/TLS.

   Proxies which do not require clients to be configured with proxy information are called transparent proxies.  Clients make HTTP requests as if the connection were direct to the server.  The transparent proxy, perhaps with the help of other network equipment \(routers using [WCCP](https://en.wikipedia.org/wiki/Web_Cache_Communication_Protocol), policy-based routing, layer 4 switching, or similar infrastructure\) intercepts client packets and performs some amount of inspection and possibly alteration of the packet.

* **SSL decrypting or non-SSL decrypting**  
   For https URLs, a proxy server may decrypt the data in the packet to perform inspection of the contents. Proxy servers which perform SSL/TLS decryption are sometimes called man-in-the-middle \(MITM\) proxies. Each client using the proxy must be configured with the proxy's CA certificate \(also referred to as a signing certificate or root certificate\). The CA certificate is used by the proxy to decrypt and re-encrypt data between the server and the client. To do this, the proxy re-writes the SSL server certificates to appear to have been issued by the proxy's CA certificate, The CA certificate is used by the client to verify SSL server certificates that have passed through the proxy re-write process.

   Non-SSL decrypting proxies do not require clients to be configured with a proxy CA certificate.

Figure 1 below indicates the required configuration information for each of the four combinations of proxy type:

For proxies that are transparent and non-SSL decrypting, no additional configuration in this article is required for the Enterprise Agent.  Configure your Enterprise Agent in the same way that non-proxied Enterprise Agents are configured.

For proxies that are transparent and perform SSL decryption, skip to the last section in this article, entitled [Installing proxy CA certificates]().

The remaining two types of proxy \(explicit SSL decrypting and explicit non-SSL decrypting\) require configuration based on the [configuration method]() and type of deployment \([Appliance](), [Docker container]() or [Linux package]()\).

#### Configuration methods

 When using explicit proxies \(types A and B\) an Enterprise Agent can obtain its proxy information using one of two methods: static configuration or a use a proxy auto-configuration file or "PAC" file.

* **Static**: The Agent is configured with information which is static--the Agent will use the same proxy information--a single proxy IP address \(or hostname\) and port number--for every. request. The configuration information is read at Agent start-up from a local configuration file, and whenever the te-agent process is restarted.
* **PAC file**: The Agent uses a downloaded file of rules to dynamically obtain proxy information. A PAC file contains JavaScript that selects a proxy IP address \(or hostname\) and port \(or selectes no proxy\) for each request, based on variables such as the domain of the web server, the IP address of the client, or a string contained in the path of the URL. For more information on PAC files, consult the ThousandEyes Knowledge Base article [Writing and testing proxy auto-configuration \(PAC\) files](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LBBmCAO). PAC files are downloaded and read by the Enterprise Agent at start-up, and whenever the te-agent process is restarted.

The table below indicates which types of Enterprise Agent deployment support these configuration methods.

|  | STATIC | PAC |
| :--- | :--- | :--- |
| Virtual or Physical Appliance | supported | supported\* |
| Docker container | supported | supported\* |
| Linux Package | supported | supported\* |

**\*** The PAC file method will not configure the Enterprise Agent's package manager, which performs automatic package updates for the operating system and Thousandeyes software. Proxy configuration for the [APT]() package manager \(Appliances, Docker container, and Ubuntu-based Linux package\) or the [YUM]() package manager \(Red Hat Enterprise Linux, CentOS and Oracle Linux installations\) must be done separately with static proxy configuration.

#### Additional configuration information

 In addition to IP address \(or hostname\) and port number, the following configuration information may be required.

* Static configuration

**Bypass list:** A list of domain names, IP addresses or networks to which each request will be compared. A request which matches an entry in the list is sent directly to the web server, rather than sent through the proxy.  Multiple list entries are separated by semi-colons \(no whitespace\). The \* wildcard is permitted with trailing domain name expressions, such as \*.example.com, which would match www.example.com and www.us.example.com. Similarly, \*example.com would match the previous two domain names plus myexample.com, www.myexample.com and www.us.myexample.com.  Networks can be specified by CIDR notation, such as 192.168.1.0/24.

**NOTE:** DNS resolution is **not** performed on the domain name in a request, in order to check the resulting IP address\(es\) against addresses or networks in the bypass list. Only requests specified by IP address can match IP addresses or networks in the bypass list.

* PAC file configuration

**PAC file location:** The URL that the Enterprise Agent will use to download the PAC file when the Agent is booted. PAC files are typically downloaded from a web server, but can also be installed on the Enterprise Agent's local file system and accessed using a file: URL.

* Static and PAC file configurations

1. **Username and password:** If a proxy requires authentication, the Enterprise Agent must be configured with a username and password. Username may be in the form of a simple username, an email address or Windows domain\username. This set of credentials will be sent to a proxy whenever that proxy requires authentication. This includes both test requests and administrative requests \(downloading configuration and uploading data to/from ThousandEyes, software updates from package repositories, etc...\).

    **NOTE:** Authentication to the proxy is performed via the HTTP Basic authentication mechanism, including CONNECT method requests for subsequent HTTPS-based requests. Basic authentication credentials are sent in clear text, encoded in Base64. Organizations which do not allow any credentials to be transmitted on a network in clear text should consider alternatives to credential-based authentication to the proxy, such as configuring the proxy to whitelist Enterprise Agents via their IP addresses.

2. **Package repository proxy**: For accessing an APT or YUM package repository, an organization may use a different proxy than the one used by the Agent's other functions. If so, a second proxy IP address \(or hostname\) and port is required.

#### Next steps

 If needed, consult with your proxy or network administrator to determine which type of proxy you have \(A, B or C\) and what configuration method \(static or PAC file\) is used, and any additional configuration information needed, per the sections above. Then proceed to the configuration instructions for the type of Enterprise Agent \([Appliance](), [Docker container]() or [Linux package]()\) being deployed.

## 2. Docker container Enterprise Agents

 Enterprise Agents deployed as Docker containers should have proxy settings configured [during the container creation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG#deploy-proxy-docker). If a Docker Enterprise Agent which has been deployed requires a change to proxy settings, then reinstall the container image with a new container that is configured with the new proxy settings and with other settings identical to the original container.  

#### Reconfigure proxy settings for existing Enterprise Agent

 If an existing Agent is being reconfigured with new proxy settings, the following is required:

1. The existing Enterprise Agent container must be stopped and removed before creating it again. To stop the Docker-based Enterprise Agent, use the following command:

   ```text
   docker stop my-proxied-agent
   docker rm my-proxied-agent
   ```

2. The newly created docker run command must contain the same hostname \(--hostname\) and host volume directory location \(-v\) configuration parameters. Otherwise, the docker run command will create a new Enterprise Agent.

 See the [Reinstalling the Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker#docker-agent-reinstall) section of the ThousandEyes Knowledge Base article  [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS) for information on reloading Docker images for an existing Docker container Enterprise Agent.

To create the new docker run command with proxy settings, go to the **+ Add New Agent** form of the [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise) page, and select "Docker" for the **Package Type.** Then select "Static" or "PAC" for the **Proxy Type**, and complete the form.

#### Static configuration

 An example of a completed form for static proxy configuration is below:

 For information on the **Name**, **Docker Version** and **Host Vol. Agent Directory** fields, review the ThousandEyes Knowledge Base article [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS).

The **Proxy Host** and **Proxy Port** are required.  **Proxy User**, **Proxy Password** and **Proxy Bypass List** are optional.

Static proxy configuration applies the proxy settings to the Enterprise Agent processes, and to the package manager system updates.

#### PAC file configuration

 An example of the completed form for PAC file configuration is below:

 For information on the **Name**, **Docker Version** and **Host Vol. Agent Directory** fields, review the ThousandEyes Knowledge Base article [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS).

The **PAC File URL** is an http: or https: URL for a PAC file that is loaded from a remote web server, or a file: URL for a PAC file installed on the local file system \(see the [PAC file stored on Docker Agent]() section, below\). The **PAC File URL** is required.  

**Proxy User** and **Proxy Password** are optional.

**NOTE:** The PAC file is loaded from the URL provided when the Enterprise Agent container is started. If the PAC file is updated, container restart is required for the new PAC file to be loaded again.

**PAC file stored on Docker Agent**

 A Docker Enterprise Agent can use a PAC file installed locally on the Docker host, and retrieved via a file: URL rather than downloading the PAC file from a web server. A local PAC file can be configured by placing the PAC file on the Docker host persistent host volume directory, created with the -v flag of the docker run command. For example, if the persistent host volume directory is created with:

```text
-v /storage
```

then the container can be created or recreated with the following command \(only relevant flags are shown\):

```text
docker run \
 ...
 -e TEAGENT_PROXY_TYPE=PAC \
 -e TEAGENT_PROXY_LOCATION='file:///var/lib/te-agent/proxy.pac' \
 ...
 -v '/storage/thousandeyes/<AGENT HOSTNAME>/te-agent':/var/lib/te-agent \
 ...
```

Note the use of triple forward slash in the file: URL above. Then after running the docker run command to create the container, create a PAC file in the following location:

```text
/storage/thousandeyes/<AGENT HOSTNAME>/te-agent/proxy.pac
```

Once the container starts, the PAC file will be read from local storage, without requiring a web server.  The PAC file can be edited from the Docker host.

**NOTE:** The PAC file is loaded from the URL provided when the Enterprise Agent container is started. If the PAC file is updated, container restart is required for the new PAC file to be loaded again.

#### Configuring proxy settings for APT package manager

Additionally, for Docker-based Enterprise Agents the APT package manager's proxy configuration must be configured statically if the APT package downloads must be proxied. Static APT proxy configuration must be added to the docker run command using -e flags, as illustrated in below:

```text
 -e PROXY_APT='1' \
 -e APT_PROXY_LOCATION='<PROXY HOST or IP ADDRESS>:<PROXY PORT>' \
 -e APT_PROXY_USER='<PROXY USER>' \
 -e APT_PROXY_PASS='<PROXY PASSWORD>' \
```

Copy the commands from the completed form and add the above commands to the docker run command, then run the commands on the Docker host.

## 3. Configure proxy settings on Virtual Appliances

Proxy settings on ThousandEyes Enterprise Agent Virtual and Physical Appliance can be configured at any time from the Network tab of the web administrative interface on the Appliance. A proxy for the Enterprise Agent and a proxy for the [APT](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool) package manager can be configured independently. Using a web browser, navigate to `http://<APPLIANCE.IP.ADDRESS.HERE>` and log in, then click on the **Network** menu item \(1\) as shown in the following image:

#### Configuring proxy settings for Web Proxy

Scroll down to the **Web Proxy** section and enable either **Static** or **PAC** option to configure proxy settings for the Enterprise Agent:

#### Configuring proxy settings for APT package manager

A separate proxy configuration for APT \(Ubuntu's package manager\) is available below the **Web Proxy** section. Scroll down to **Apt Proxy** section, and check the **Use Apt Proxy** box. If you wish to use the same proxy settings for the APT proxy as for your web proxy, check the **Same as Web Proxy** box. If a proxy for APT is not configured, the APT package manager will attempt to perform automatic package updates directly to the APT repositories, without using a proxy.

  
Apt proxy configuration section

Click the **Save** button when finished configuring settings.

## 4. Configure proxy settings on Linux package-based Enterprise Agents

Enterprise Agents deployed with the Linux package can be [configured during installation](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG#deploy-proxy-linux) to use a proxy.  The install\_thousandeyes.sh installation script provides command line flags to specify proxy information, and will use that information to configure the /etc/te-agent.cfg file.  Users can later modify this file using an editor and restart the Agent to make configuration changes.

### Configure proxy settings for Enterprise Agent software

The following proxy configuration settings are available in /etc/te-agent.cfg configuration file:

* **proxy-type:**  Possible values are DIRECT, STATIC or PAC
* **proxy-location:** The means for obtaining the proxy hostname \(or IP address\) and port number:
  * When **proxy-type** is set to "STATIC", the **proxy-location** setting should contain &lt;PROXY-HOSTNAME:PROXY-PORT&gt;
  * When **proxy-type** is set to "PAC", the **proxy-location** setting should contain a URL to the location of the proxy PAC file:
    * "file:///absolute/path/to/my/proxy.pac for a PAC file installed on the local file system, or
    * "http://my.domain.com/proxy.pac" for a PAC file that is loaded from a remote web server
* **proxy-bypass-list:** Applies only when **proxy-type** is set to STATIC. An unquoted list of domain names, IP addresses or networks to which each request will be compared. Matching requests are sent directly, rather than sent through a proxy.  Multiple entries are separated by semi-colons \(no whitespace\). The \* wildcard is permitted with trailing domain name expressions.  For example, \*.example.com would match www.example.com and www.us.example.com.  Networks can be specified by CIDR notation, such as 192.168.1.0/24. DNS resolution is not performed in order to check request IP addresses against addresses or networks in the bypass list.
* **proxy-auth-type** - Authentication protocol supported by the proxy server. Can either be empty \(when no proxy authentication is required\), `BASIC`, or `NTLM`.
* **proxy-user** - Username for proxy authentication
* **proxy-pass** - Password for proxy authentication
* **proxy-host** - OBSOLETE. Use **proxy-location** setting.
* **proxy-port** - OBSOLETE. Use **proxy-location** setting.

**NOTE:** When **proxy-type** is set to PAC, the PAC file is loaded from the URL provided when the Enterprise Agent container is started. If the PAC file is updated, container restart is required for the new PAC file to be loaded again.

#### Examples

The following examples show various proxy configurations specified in an /etc/te-agent.cfg file.

Static proxy configuration example:

```text
### Statc proxy configuration
#
# When configuring "STATIC" proxy configuration, configuration
# directive "proxy-location" accepts either an IP address or
# a domain name followed by a colon and a TCP port number.
#
proxy-type=STATIC
proxy-location=10.1.2.32:3128


### Proxy server authentication
#
# If your proxy server requires authentication, the following three
# configuration directives provide the details.
#
# Proxy auth type can be one of:
# - "" (empty, without quotes - when proxy authentication is not required)
# - BASIC
# - NTLM
#
proxy-auth-type=BASIC
proxy-user=jsmith@example.com
proxy-pass=pr0Xyp@ss


### Bypassing proxy for certain test targets
#
# If certain test targets should be excluded from using the proxy,
# "proxy-bypass-list" can be used to match against requests with
# those targets. Unquoted, semicolon-separated list without
# whitespace.
#
proxy-bypass-list=*example.com;localhost;127.0.0.1;192.168.1.0/24
```

PAC-based proxy configuration example:

```text
### PAC file proxy configuration
#
# When configuring "PAC" proxy configuration, configuration
# directive "proxy-location" accepts one of the following:
# "file:///..." for PAC file accessible on the agent's filesystem.
# "http://..." for .pac file which is downloaded from remote HTTP server.
#
# If using "file:///..." option, note the use of triple forward slash.
#
proxy-type=PAC
proxy-location=file:///absolute/path/to/my/proxy.pac
#proxy-location=http://my.domain.com/my/proxy.pac


### Proxy server authentication with PAC file
#
# PAC files do not supply proxy server user credentials.
#
# If your proxy server requires authentication, the following three
# configuration directives provide the details.
#
# Proxy auth type can be one of:
# - "" (empty, without quotes - when proxy authentication is not required)
# - BASIC
# - NTLM
#
proxy-auth-type=BASIC
proxy-user=jsmith@example.com
proxy-pass=pr0Xyp@ss


### Bypassing proxy for certain test targets with PAC file
#
# NOTICE: When "PAC" proxy configuration is used, "proxy-bypass-list"
# configuration directive is ignored.
#
# Proxy bypass exceptions must be defined in the PAC file itself.
#
#proxy-bypass-list=
```

Once done editing /etc/te-agent.cfg, restart the `te-agent` service to pick up the updated configuration:

```text
sudo systemctl restart te-agent
```

### Configuring proxy settings for APT package manager on Ubuntu

Ubuntu's [APT](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool) package manager must be configured separately from the Agent's proxy configuration. The proxy used by the package manager need not be the same proxy used for the main Agent processes. Alternatively, if all needed repositories are mirrored on the internal network, or if communication to standard repositories on the Internet is permitted without a proxy, then this step can be skipped.

**NOTE:** Proxy configuration using a PAC file is not supported by the [APT](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool) package manager. Static APT proxy configuration must be used instead.

To configure a proxy for the APT package manager, create a text configuration file within the /etc/apt/apt.conf.d directory. In this example, we will create the /etc/apt/apt.conf.d/90proxyapt file to store APT proxy configuration. Use an editor to insert the following content into the /etc/apt/apt.conf.d/90proxyapt file:

```text
Acquire::http::proxy  "http://<APT_PROXY_USERNAME:APT_PROXY_PASSWORD@>APT_PROXY_HOSTNAME:APT_PROXY_PORT";
Acquire::https::proxy "http://<APT_PROXY_USERNAME:APT_PROXY_PASSWORD@>APT_PROXY_HOSTNAME:APT_PROXY_PORT";
```

An IP address may be used in place of a hostname/domain name. Username and password are optional. Double quotes are required.

Verification of configured proxy can be done using the following command:

```text
sudo apt-get update
```

If the command completes successfully, the package manager is configured properly.

### Configuring proxy settings for YUM package manager on RHEL / CentOS / Oracle Linux

Red Hat's [YUM](https://en.wikipedia.org/wiki/Yellowdog_Updater,_Modified) package manager must be configured separately from the Agent's proxy configuration. The proxy used by the package manager need not be the same proxy used for the main Agent processes. Alternatively, if all needed repositories are mirrored on the internal network, or if communication to standard repositories on the Internet is permitted without a proxy, then this step can be skipped.

PAC proxy configuration is not supported by [YUM](https://en.wikipedia.org/wiki/Yellowdog_Updater,_Modified) package manager. Static YUM proxy configuration must be used instead.

YUM package manager configuration is stored in /etc/yum.conf file. Edit the file using an editor and insert the following content into the /etc/yum.conf file:

```text
proxy=http://<YUM_PROXY_HOSTNAME>:<YUM_PROXY_PORT>
proxy_username=<YUM_PROXY_USERNAME>
proxy_password=<YUM_PROXY_PASSWORD>
```

Verification of configured proxy settings can be done using the following command:

```text
sudo yum makecache
```

If the command completes successfully, the package manager is configured properly.

## 5. Installing proxy CA certificates

If your proxy server performs SSL/TLS decryption by re-writing and re-signing server SSL certificates for each server contacted, consult the ThousandEyes Knowledge Base article [Installing CA Certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG) and perform the configuration for your Enterprise Agent deployment type \(Appliance, Docker container or Linux package\).

## 6. Verification

To verify that any Enterprise Agent is successfully communicating through the proxy with the ThousandEyes data collector, check the Enterprise Agent's log file using the following command:

```text
tail -f /var/log/te-agent.log
```

Look for entries similar to the following:

```text
[te] {} Resolving proxy hostname <proxy hostname or IP address>
[te] {} Calling check in
[te] {} Done calling check in
```

The presence of `Done calling check in` lines indicates that the Enterprise Agent is successfully communicating with the ThousandEyes collector, and the "Resolving proxy hostname" line indicates the communication is via the proxy.  Use control-c to exit the tail command.

