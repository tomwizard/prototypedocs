# Enterprise Agent deployment using Docker

Docker container Enterprise Agent is currently supported on 64-bit Linux distributions running Kernel version 3.10 or newer, such as:

* Ubuntu 14.04 LTR or newer
* Debian 7.7 or newer
* Red Hat Enterprise Linux 7
* CentOS 7
* Fedora 24 or newer
* Oracle Linux 7 or newer
* openSUSE 13.2 or newer
* and others \(please refer to official Docker documentation for the [list of supported OSes](https://docs.docker.com/engine/installation/linux/)\)

We do not support Docker for Mac or Docker for Windows for production deployments.

## Installing the Enterprise Agent image

1. Log in to your Docker host as a privileged user
2. Make sure Docker is properly installed. Follow the [official Docker installation documentation](https://docs.docker.com/engine/installation/) to install it on your system. Verify the installation with the **docker run hello-world** command. The output should look similar to:

    **\[..\]**

    **Hello from Docker.  
    This message shows that your installation appears to be working correctly.**

    **\[..\]**

3. Log into ThousandEyes, then navigate to [Settings &gt; Agents &gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/).
4. Click **+ Add New Agent**
5. Select the **Docker** tab
6. Pick a name for your Agent.  The Agent should not contain underscores or spaces in the name.
7. Pick a folder on the Docker host where persistent Agent files will be stored \(e.g. **/opt**\). Folder will be created automatically upon Agent instantiation, and log content will be sent here.
8. _\(optional\)_ Select proxy configuration by clicking Static or PAC, then proxy information.  See the ThousandEyes Knowledge Base article [Configuring an Enterprise Agent to use a proxy server](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG) for more information.
9. Copy the CLI commands generated for your agent, and paste them in the CLI of your Docker host. We recommend saving the commands used, in case reinstallation of the Docker image without changing the Enterprise Agent configuration is needed.

Your Docker-based Enterprise Agent will be installed and start running. The Enterprise Agent will be restarted automatically upon Docker host restart.

**NOTE:** You may receive a **WARNING: Your kernel does not support swap limit capabilities, memory limited without swap** message when issuing the docker run command. You can safely continue as this will not affect your Enterprise Agent installation.

The Enterprise Agent container will be automatically connected to the default docker0 network bridge and assigned a private IP address.  The container uses network address translation \(NAT\) to the Docker host default interface to connect the Enterprise Agent to the network. No additional network configuration is required.

## Stopping, starting and restarting Enterprise Agent

After the installation you can verify that the Enterprise Agent is running by using the **docker ps** command:

```text
docker ps
```

Output should be similar to:

```text
CONTAINER ID IMAGE                         COMMAND         CREATED        STATUS      PORTS NAMES
400b4ad7bb34 thousandeyes/enterprise-agent "/sbin/my_init" 2 minutes ago  Up 2 minutes      <agent-name>
```

You can stop the container by running the following command:

```text
docker stop <agent-name>
```

_Note: If you stop the container using the docker stop command, the container will not automatically restart upon Docker host restart_

To verify that the agent has been stopped, run _docker ps -a_.  This will show status of all containers, including stopped ones.

```text
docker ps -a
```

Output should be similar to:

```text
CONTAINER ID IMAGE                         COMMAND         CREATED        STATUS               NAMES
400b4ad7bb34 thousandeyes/enterprise-agent "/sbin/my_init" 2 minutes ago  Exited (0) 5 sec ago <agent-name>
```

You can start the agent container by using _docker start:_

```text
docker start <agent-name>
```

_Note: The enterprise agent container will automatically restart upon Docker host reboot if started with the docker start command._

## [Removing an Enterprise Agent]()

To remove an enterprise agent container, use the _docker rm_ command.  

```text
docker rm -f <agent-name>
```

If you're permanently removing an enterprise agent, delete the persistent volumes as well.  If you're just updating the container, running docker start will automatically update the container to the latest version.

To remove the persistent volumes on your Docker host:

```text
rm -Rf <host-os-agent-folder>/thousandeyes/<agent-name>
```

## Reinstalling the Enterprise Agent

Enterprise agent containers can be easily removed and reinstalled. You may need to reinstall the enterprise agent in a case of serious enterprise agent failure and/or when suggested to do so by ThousandEyes support. All persistent data for the enterprise agent is stored in the persistent volumes on the host. As long as you keep the &lt;agent-name&gt; consistent, and persistent volumes on the host the same, enterprise agent will keep the data and same identity in the ThousandEyes Application even if you remove the container and replace it with a new one.

You can reinstall the enterprise agent:

1. Ensure you have the latest Enterprise Agent image on your host by running the following command on the Docker host:

    **docker pull thousandeyes/enterprise-agent**

2. Log into ThousandEyes, and navigate to Settings &gt; Agents &gt; [Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/).
3. Click **+ Add New Agent** to open the form
4. Click the "Docker" button for the **Package Type** setting
5. Enter a name for your Enterprise Agent, which must be the same as the name of currently running Enterprise Agent you want to reinstall.
6. Enter a folder on the Docker host where persistent files for the existent Enterprise Agent are already stored \(e.g. **/opt**\).
7. Copy the CLI commands generated for your container by the **+ Add New Agent** form, then paste and run them in the CLI of your Docker host.

**Warning:** Removing data from persistent volumes on the host \(_&lt;host-os-agent-folder&gt;_/thousandeyes/_&lt;agent-name&gt;/\*_\) will result in reinitialization of the Agent. The Agent will register as a new Agent in ThousandEyes.

## [Agent System Time]()

Docker containers use host system kernel clock. Enterprise agent containers cannot alter the clock. If agent's system time is offset, you need to adjust host system time, ideally by configuring valid NTP servers on the host system.

## [Advanced DNS configuration]()

Enterprise Agent containers use the host's DNS settings by default. You can configure a different set of DNS servers for the Enterprise Agent, if needed. When utilizing the **docker run** command upon Enterprise Agent installation, add the **--dns=&lt;dns-server&gt;** parameter before be last line. If you need to add multiple servers, repeat the command:

```text
--dns=8.8.8.8 \
--dns=8.8.4.4 \
thousandeyes/enterprise-agent /sbin/my_init
```

## [Exposing ports for agent to agent tests]()

If you are connecting your Docker-based Enterprise Agent to the world using the NAT network \(which is Docker default\), agent to agent tests targeting your Docker agent will not work out of the box. To enable the agent to agent test traffic to reach your Docker agent hosted behind a NAT network, relevant ports need to be exposed and published. To achieve this, add the following parameters to your `docker run` command:

```text
--expose=49152/udp \
--expose=49153/udp \
--expose=49153/tcp \
--publish=49152:49152/udp \
--publish=49153:49153/udp \
--publish=49153:49153/tcp \
thousandeyes/enterprise-agent /sbin/my_init
```

## [Agent Proxy configuration]()

Customers deploying ThousandEyes Enterprise Agents behind a proxy may need proxy-specific configuration for the Enterprise Agent in order to use certain tests, reporting test data to the ThousandEyes collector and performing software package updates.

You should configure proxy settings upon Enterprise Agent installation. See the [Deploying a Docker Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG_Installing-Enterprise-Agents-in-Proxy-Environments#deploy-proxy-docker) section of the ThousandEyes Knowledge Base article [Installing Enterprise Agents in Proxy Environments](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2pCAG) for instructions on installing Docker

You can verify the proxy settings of a running agent by running the following command on the Docker host:

```text
docker exec <agent-name> cat /etc/te-agent.cfg | grep proxy
```

You cannot change the proxy configuration of a currently running agent. You must reinstall the agent with a new proxy configuration. Follow the [Reinstalling the Enterprise Agent]() section of this article.

##  [Support for Transaction tests ]()

**seccomp**  
Security computing mode is a Linux kernel feature used to restrict container actions. The Docker community has documented how [seccomp is used with containers](https://docs.docker.com/engine/security/seccomp/). ThousandEyes provides a seccomp file which may be used to configure seccomp when deploying containers. .  

**Apparmor configuration**   
AppArmor is a mandatory access control \(MAC\) system used to limit an application's access to resources. AppArmor is currently the default MAC system for the Debian, Ubuntu, Suse, and Arch Linux distributions. 

**SELinux configuration**  
SELinux  is a mandatory access control \(MAC\) system used to limit an application's access to resources.  SELinux is currently the default MAC system for Red Hat Enterprise, CentOS, Fedora, Oracle, and Gentoo Linux distributions. 

**user.max\_user\_namespaces** 

Distributions that share a common code base with Red Hat Enterprise Linux 7 may have a default user.max\_user\_namespaces value of 0 or simply leave this  feature disabled. The Docker community has documented [how this issue affects container deployment along with common resolutions](https://success.docker.com/article/user-namespace-runtime-error). In point release 7.6 and up, the user.max\_user\_namespaces value simply needs to be increased for proper operation. This feature is also required when [running a container as a user other than root](https://www.redhat.com/en/blog/preview-running-containers-without-root-rhel-76). 

**Example deployment \(New Agent\)** 

Step 1: Create a working directory for holding seccomp and apparmor files 

In this example, we will store container volumes within the /var/docker directory and system configuration files within the /var/docker/configs directory 

```text
sudo mkdir /var/docker 
sudo mkdir /var/docker/configs
```

Step 2: Download apparmor and seccomp files to the target directory

```text
cd /var/docker/configs
curl -o te-apparmor.cfg https://attachments.thousandeyes.com/cases/5e66edcf707d/fffa1f366be7
curl -o te-seccomp.json https://attachments.thousandeyes.com/cases/5e66edcf707d/18396a1e3e27
```

Step 3: Ensure that all environment variables are properly configured

**Operating systems using Apparmor**  
The apparmor\_parser may be used to read and apply configuration changes specified within the downloaded te-apparmor.cfg file. e.g.

```text
apparmor_parser -r -W /var/docker/configs/te-apparmor.cfg
```

**Operating systems using SELinux**   
Setting SELinux to "permissive" mode allows applications to run while logging any activity that would violate the system's  current SELinux profile. A review of SELinux logs will reveal if your profile should be updated before returning SELinux to "enforcing" mode. 

Step 4: Modify the installation script 

add the following lines to your "docker run" command

```text
    --security-opt seccomp=/var/docker/configs/te-seccomp.json \
    --security-opt apparmor=docker_sandbox \
```

Step 5: Deploy your container

Begin by pulling the [latest Enterprise Agent container image](https://hub.docker.com/r/thousandeyes/enterprise-agent) from the docker repository

```text
docker pull thousandeyes/enterprise-agent > /dev/null 2>&1
```

Next deploy your Agent using the the modified run command. e.g.

```text
 docker run \
    --hostname='<AGENT NAME>' \
    --memory=2g \
    --memory-swap=2g \
    --detach=true \
    --tty=true \
    --shm-size=512M \
    -e TEAGENT_ACCOUNT_TOKEN=<ACCOUNT TOKEN> \
    -e TEAGENT_INET=4 \
    -v '/var/docker/thousandeyes/<AGENT NAME>/te-agent':/var/lib/te-agent \
    -v '/var/docker/thousandeyes/<AGENT NAME>/te-browserbot':/var/lib/te-browserbot \
    -v '/var/docker/thousandeyes/<AGENT NAME>/log/':/var/log/agent \
    --cap-add=NET_ADMIN \
    --cap-add=SYS_ADMIN \
    --name '<AGENT NAME>' \
    --restart=unless-stopped \
    --security-opt seccomp=/var/docker/configs/te-seccomp.json \
    --security-opt apparmor=docker_sandbox \
    thousandeyes/enterprise-agent /sbin/my_init
```

## Troubleshooting and Log information

If you're directed by ThousandEyes Customer Success team to pull log files for the agent, the logs are found in the persistent volume, under `thousandeyes/<agent-name>/log` folder. The agent log file is called `te-agent.log`, and this file rolls over automatically. You can tail this log from the Docker host using the `tail -f` command. An example is found below, assuming `/opt` was the persistent storage location supplied, and "agent-name" is the name of the agent:

```text
tail -f /opt/thousandeyes/agent-name/log/te-agent.log
```

