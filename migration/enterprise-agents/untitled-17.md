# Upgrading Docker Enterprise Agents - ThousandEyes Customer Success Center

The original ThousandEyes Enterprise Agent Docker image was created using the Ubuntu 14.04 LTS base image.  [Canonical](https://www.canonical.com/), the developer of Ubuntu, has indicated in their [support lifetime policy](https://wiki.ubuntu.com/Releases) that the 14.04 LTS version is no longer supported as of April 2019. ThousandEyes has therefore upgraded the Enterprise Agent Docker image to the Ubuntu 18.04 LTS operating system.

Customers that do not have an automated Docker container redeployment solution in place \(such as [Kubernetes](https://kubernetes.io/) or the simpler [Docker Compose](https://docs.docker.com/compose/)\) must manually redeploy existing Docker-based Enterprise Agent containers.

This article provides detailed instructions on how to redeploy the Enterprise Agent Docker container to implicitly upgrade the agent's underlying operating system.

### Table of contents

* [Identifying Docker-based Enterprise Agents that should be upgraded]()
* [Redeploying a Docker container - overview]()
* [Upgrade/redeployment guide]()
  * [Recreating the "docker run ..." command]()
    * [Using the runlike tool]()
    * [Recreating the "docker run ..." command manually]()
  * [Redeploying a Docker-based Enterprise Agent]()
  * [Post-redeployment tasks]()
  * [Upgrade verification]()
* [Getting support]()
* [Related information]()   

## [Identifying Docker-based Enterprise Agents that should be upgraded]()

Within the ThousandEyes web application, select  [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) within the left-hand navigation pane \(pointers \#1 and \#2 in the following figure\):

  
Identifying end-of-life Docker-based Enterprise Agents

Once in the view, pay attention to the following elements:

* **The filtering feature \(3\)** can be used to narrow down the agent list - use the **Installation Type** filter with the `Docker Container` option selected.
* **Red triangle icon \(4\)** will point out agents requiring your attention.

 In the expanded agent view, the following sections provide further information:

* **Operating System section \(5\)** provides information about the agent's underlying operating system version. `Ubuntu 14.04.x LTS`, the operating system that was used as a base for the previous Docker image, is currently reaching the end-of-life stage.
* **Installation Type section \(6\)** provides confirmation that you are looking at a Docker-based Enterprise Agent. 

Once you've identified which agents are Docker-based and require upgrading, proceed to the following sections to find out how. 

## [Redeploying a Docker container - overview]()

The principles underlining Docker's implementation of Linux containers guarantee that Docker containers will operate consistently between re-deployments.  This consistent operation requires that the container input parameters, and the way that containers use these parameters, do not change across container versions. 

To put the above in a more tangible form - the container functionality does not change when the following conditions are met:

1. An identical `docker run ...` command is used to create a new container
2. The container state files have not been tampered with
3. The container was shut down gracefully \(optional, depends on the container implementation, but helps to ensure consistency of the container's state files\)
4. The container image provider has created the updated container image in a manner that ensures identical input processing

Therefore, the challenge of upgrading a Docker container image for an existing container is narrowed down to either having the original `docker run ...` command, or being able to recreate it.

## [Upgrade/redeployment guide]()

As identified in the previous section, successfully upgrading a Docker container by recreating it from an updated image requires having the original `docker run ...` command. If you already have the original `docker run ...` command, skip the following section that deals with ways to regenerate the lost `docker run ...` command and head directly to the [section describing redeployment steps]().

### [Recreating the "docker run ..." command]()

If you happen to find yourself in a situation where you are not in possession of the original `docker run ...` command that was used to create the agent container, you will need to recreate it. The solutions presented below are not the universal silver bullet to address this issue with 100% accuracy, yet they will provide sufficient tools and methods that you can use to achieve your goal and come up with a `docker run ...` command that is sufficiently similar to the one that was used initially.

#### [Using the runlike utility]()

The Docker user community has created a tool that inspects a running container's configuration and outputs the container's original `docker run ...` command, or the best approximation it can come up with. This tool is called `runlike`.

 On Ubuntu-based docker host you can install the `runlike` utility with the following commands:

```text
sudo apt-get install python-pip
sudo pip install runlike
```

Then, run the `runlike` command by providing it a name of the container it should inspect and recreate the `docker run ...` command for:

```text
runlike my-docker-agent
```

The generated output will be similar to the following \(here, for the sake of readability, newlines were inserted into the generated output before quoting it\):

```text
docker run \
  --name=my-docker-agent \
  --hostname=my-docker-agent \
  --env=TEAGENT_ACCOUNT_TOKEN=12345678123456781234567812345678 \
  --env=TEAGENT_INET=4 \
  --env=PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
  --env=CODENAME=trusty \
  --env=FLAVOR=ubuntu \
  --env=DEBIAN_PUBLIC_KEY_FILE=thousandeyes-apt-key.pub \
  --env=DEBIAN_FRONTEND=noninteractive \
  --env=TEAGENT_CONF=/etc/te-agent.cfg \
  --env=TEAGENT_LOG_PATH=/var/log/agent \
  --env=TEAGENT_LOG_FILE_SIZE=10 \
  --env=TEAGENT_PROXY_TYPE=DIRECT \
  --env=TEAGENT_PROXY_LOCATION= \
  --env=TEAGENT_PROXY_USER= \
  --env=TEAGENT_PROXY_PASS= \
  --env=TEAGENT_PROXY_BYPASS_LIST= \
  --env=PROXY_APT= \
  --env=APT_PROXY_USER= \
  --env=APT_PROXY_PASS= \
  --env=APT_PROXY_LOCATION= \
  --env=SHM_SIZE= \
  --volume=/var/lib/docker/volumes/thousandeyes/my-docker-agent/te-agent:/var/lib/te-agent \
  --volume=/var/lib/docker/volumes/thousandeyes/my-docker-agent/te-browserbot:/var/lib/te-browserbot \
  --volume=/var/lib/docker/volumes/thousandeyes/my-docker-agent/log/:/var/log/agent \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_ADMIN \
  --dns=10.6.0.11 \
  --dns=10.6.0.12 \
  --network=macvlan-dmz-pub-502 \
  --restart=unless-stopped \
  --detach=true \
  -t thousandeyes/enterprise-agent /sbin/my_init
```

The generated command above is fairly accurate - the only thing that was missing in this particular case was the `--ip=10.5.2.226` part, which is probably due to manual IP assignment being a fairly uncommon thing in the Docker world.

The `runlike` tool generates the relevant output by inspecting the output of the `docker inspect` command. You are encouraged to:

* **Inspect the output** of `docker inspect` yourself, to make sure something important has not been missed out, and
* **Store** the `docker inspect` output of the running container for the post-upgrade verification.

To store the `docker inspect` output, run the following command:

```text
docker inspect my-container-name > my-container-name.inspect.ORIG
```

This command will store the `docker inspect` output in the file called `my-container-name.inspect.ORIG`, located in the current directory.

#### [Recreating the "docker run ..." command manually]()

The manual process of recreating the `docker run ...` command consists of the following steps:

* Inspecting the existing container's configuration to create initial `docker run ...` command version
* Repeating the container deletion and redeployment process until all significant differences between the old and new container configuration are gone.

To inspect the running container's configuration, use the following command:

```text
docker inspect my-container-name
```

To store the running container's configuration in a file for later comparison, use the following command:

```text
docker inspect my-container-name > my-container-name.inspect.ORIG
```

Once you have the above, head to [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) section of the web portal, click the **Add New Enterprise Agent** button and open the **Docker** tab. In there, a basic `docker run ...` command for deploying Docker-based Enterprise Agent is waiting for you:

  
The incomplete "docker run ..." command

You will have to fill in the main details:

* **Container name \(1\)** is the name of the container on the Docker host. You should use the same name here as your existing container has.
* **Container storage directory path \(2\)** determines where the container's data storage location is.  **IMPORTANT:** You need to get this value right - if you don't, the new container will be deployed as a new agent. Examine the `docker inspect` output file you created earlier to determine this value.

Filling in the two items outlined above will generate the basic `docker run ...` command \(3\) for you. From here on, the effort to recreate an identically configured container is a matter of trial an error:

1. Redeploy the agent as outlined in the [next section]() of this manual
2. Generate a new `docker inspect` file using the `docker inspect my-agent-name > my-agent-name.inspect.NEW` command
3. Use the `diff` tool to compare the original and new `docker inspect` outputs
4. Adjust the `docker run ...` command and go back to step \#1
5. Repeat until all relevant container configuration differences are ironed out

### [Redeploying a Docker-based Enterprise Agent]()

If you've skipped the [Recreating the "docker run ..." command]() section above because you already have the original `docker run ...` command at hand, you are still encouraged to store the current running container's `docker inspect` output for later inspection and comparison with the inspect output from the newly created container. You can store the running container's docker inspect output with the following command:

```text
docker inspect my-container-name > my-container-name.inspect.ORIG
```

Then, upgrading a Docker-based Enterprise Agent by redeploying the container is a fairly straightforward process. It consists of the following four commands:

```text
# Update the ThousandEyes Enterprise Agent Docker image
docker pull thousandeyes/enterprise-agent

# Stop the existing container
docker stop '<AGENT-CONTAINER-NAME>'

# Delete the existing container
# (This action leaves container's state files intact.)
docker rm '<AGENT-CONTAINER-NAME>'

# Re-create the container with the updated image
docker run ...<the rest of the docker run command that you have stored somewhere>
```

This is it. The agent has been redeployed from the latest `thousandeyes/enterprise-agent` base image. Proceed to the [post-redeployment tasks section]() below for the final touches.

### [Post-redeployment tasks]()

#### Installing internal CA certificates

The `docker run ...` command generally takes care of all aspects of container configuration. The only remaining task that is currently not handled during the container creation is the installation of your internal CA certificates on your new agents. Head over to the [Docker-related section of the CA certificate installation guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG_Installing-CA-Certificates-on-Enterprise-Agents#installing-on-docker) for further information.

#### Removing unused Docker images

You can clean up obsolete \(dangling in Docker-speak\) container images by running the following command:

```text
docker image prune
```

Alternatively, you can remove all unused container images \(all images that are not associated with at least one running or stopped container\) using the following command:

```text
docker image prune -a
```

This should free up some disk space on your Docker host.

### [Upgrade verification]()

Once the upgrade process has completed successfully, the agent information panel in the web UI will present the following information:

  
Docker Enterprise Agent upgrade verification

The important details to pay attention to are:

1. **Agent continuously checking in:** Once the upgrade is complete, the agent should be checking in with the platform roughly once every minute.
2. **Operating system version updated:** The Ubuntu 18.04.x LTS text should be displayed.
3. **Agent and BrowserBot versions up to date:** The upgrade process installs the latest available software versions. This section should not be showing any red text indicating obsolete software versions.

## [Getting support]()

If you have any questions or you encounter a setback when redeploying your Docker-based Enterprise Agents, [reach out to ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) for assistance.

## [Related information]()

The following articles provide further related information:

* [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy) article explains how ThousandEyes handles Enterprise Agent operating system end-of-life events.
* [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) article lists all currently supported operating systems and related information.
* [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker) guide describes steps to run a new Docker-based Enterprise Agent.

