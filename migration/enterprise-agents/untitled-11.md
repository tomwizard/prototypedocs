# Migrating ThousandEyes appliance or package-based Enterprise Agent to Docker

There are various reasons why one would want to migrate the deployment method of their [Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent-1472236187506). Generally, one of the most frequent nudges towards migration is Enterprise Agent's underlying operating system reaching the [end-of-support stage](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy). Our [physical](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnOKAS_Setting-up-a-physical-appliance) and [virtual](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnwKAC_How-to-set-up-the-Virtual-Appliance) appliances and [package-based](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnZKAS_Enterprise-Agent-deployment-using-Linux-Package-method) Enterprise Agent deployments are subject to such end-of-support events and require either an in-place upgrade or a migration to a newer and still supported version. Upgrading efforts for appliances and/or package-based agents tend to take a certain amount of effort, but upgrading Docker-based agents is nearly effortless, which makes it an attractive deployment method. Consult the [Why Docker?]() section below for details.

This article is a special version of the article that guides you through the [agent replacement by the migration of the agent identity files](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ASAS_Replacing-an-Enterprise-Agent-using-Agent-Identity-Files). This guide starts by taking the same approach for collecting agent identity files from an existing agent, then continues to explain how to prepare your new Docker-based Enterprise Agent's storage to pick up the identity of your existing agent instead of creating a new one.

In case you have not seen it yet, you are encouraged to review our [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades) article - it provides an overview of all possible upgrade paths.

#### Table of contents

* [Why Docker?]()
* [Is there a simpler migration path?]()
* [Migration guide:]()
  * [Step 1a: Collect identity files from an appliance]()
  * [Step 1b: Collect identity files from a package-based agent]()
  * [Step 2: Determine the new Docker agent's data storage location]()
  * [Step 3: Place the \*.sqlite identity files]()
  * [Step 4: Generate and run the "docker run ..." command]()
  * [Step 5 \(optional\): Install your CA certificates]()
  * [Step 6 \(optional\): Migrate SSH keys]()
  * [Step 7: Wipe the original agent]()
* [Questions?]()
* [Related information]()

## [Why Docker?]()

Using Docker detaches you from what ThousandEyes [supports as an underlying operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) for deploying Enterprise Agents. If Docker can run on your x64-based operating system of choice, your Docker-based Enterprise Agent will run on it as well.

Secondly, Docker-based Enterprise Agent deployment is an attractive option because it [cuts down future upgrading efforts significantly](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52KSAS_Upgrading-Docker-Enterprise-Agents) - once you have your `docker run ...` command for each agent, the entire upgrade consists of running a few Docker commands - pull the latest image, stop and delete the existing agent container and recreate it with a freshly-download image. Such an upgrade is usually completed in a matter of seconds.

Caveats?

There is only one significant and quite visible disadvantage - virtual and physical ThusandEyes appliances provide an administrative web interface for basic appliance configuration tasks. Such administrative web interface is not provided by the Docker-based agents - Docker-based agents utilize Docker-provided configuration facilities, mainly command line arguments.

## [Is there a simpler migration path?]()

 Maybe. As outlined in greater detail in the Replacement overview section of the [Replacing an Enterprise Agent using Agent Identity Files](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ASAS_Replacing-an-Enterprise-Agent-using-Agent-Identity-Files#overview) article, you can potentially leverage a simpler method to replace your agents - the [agent clustering method](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnYJCA0_Replacing-an-Agent).

**WARNING: Customers using the metered billing model are not advised to use the agent clustering method.** The agent clustering method creates a new agent ID, and units consumed by the original agent \(the one you are intending to replace\) will not be transferred to the new agent. Instead, the new agent's unit consumption will start from zero.

## [Migration guide]()

The migration consists of five relatively simple steps:

1. Collecting the original agent identity files
2. Determining the new Docker agent's data storage location
3. Placing the collected `*.sqlite` files into the new agent's data storage location
4. Generating and running the `docker run ...` command
5. Wiping the original agent

Read on - the following sections will explain each step with a sufficient amount of details and references to other Knowledge Base articles where more related information is provided.

### [Step \#1a: Collect identity files from an appliance]()

The process of collecting identity files from an appliance starts with unlocking the appliance. [Unlocking the ThousandEyes Appliance](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnvrCAC_Unlocking-the-Thousandeyes-Appliance) article has all the details, but we can summarize the process into two essential steps:

1. Connect to appliance's SSH console
2. Run the `sudo apt-get install te-va-unlock` command

Once the steps above have been completed, the appliance is unlocked. At this point, such appliance can be treated as a Linux package-based Enterprise Agent deployment. Therefore, continue to the [Step 1b: Collect identity files from a package-based agent]() section below.

### [Step \#1b: Collect identity files from a package-based agent]()

The procedure of collecting identity files from a Linux package-based is described in detail in the Obtaining identity files from the original Agent section of the [Replacing an Enterprise Agent using Agent Identity Files](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ASAS_Replacing-an-Enterprise-Agent-using-Agent-Identity-Files#obtaining-identity-files) article. Here is a short summary of the process:

1. Stop the te-agent service - use `sudo systemctl stop te-agent` on modern systems, `sudo stop te-agent` on older systems such as Ubuntu 14.04 and RHEL 6.x
2. Disable the te-agent service - use `sudo systemctl disable te-agent` on modern systems, `sudo update-rc.d -f te-agent remove` on Ubuntu 14.04, `sudo chkconfig te-agent off` on RHEL 6.x
3. Move the agent identity files `/etc/te-agent.cfg` and `/var/lib/te-agent/*.sqlite` files to a temporary location, like your SSH user's home directory

At this point, the original agent will stop collecting data and checking in with the ThousandEyes platform.

### [Step \#2: Determine the new Docker agent's data storage location]()

ThousandEyes' dialog for creating new Docker-based Enterprise Agents provides two input fields that determine the default data storage location for the upcoming Docker agent:

* **Host Vol. Agent Directory** configures the general path prefix under which the container data is stored.
* **Name** value is primarily used to configure the container's name and hostname, but it is also used in the generated storage paths, to make sure each container has its files stored separately.

The two settings listed above are pointed out by \#1 and \#2 markers in the following figure:

  
Docker Enterprise Agent configuration dialog

The generated `docker run ...` command above contains three paths that retain container's data and are bind-mounted into the container when it is running:

* `/var/lib/te-agent` is the agent state directory, pointed out with \#3 above, **the one that we're interested in**
* `/var/lib/te-browserbot` contains [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-the-BrowserBot-1472236191200) data and logs
* `/var/log/agent` contains agent logs

The default `/var/lib/te-agent` path within the container has the following storage path on the host:

```text
<HOST_VOL_AGENT_DIR>/thousandeyes/<NAME>/te-agent
```

As an example, let's use the value of `/docker-data` as a Host Vol. Agent Directory and the name `my-new-docker-agent` as the name of the new Docker agent. This would give us the following default agent state storage path:

```text
/docker-data/thousandeyes/my-new-docker-agent/te-agent
```

The example path above is the location where the `*.sqlite` identity files collected in [step \#1b above]() should end up in.

### [Step \#3: Place the \*.sqlite identity files]()

This step is a relatively simple one:

* Pre-create the Docker agent's `te-agent` storage directory
* Place the `*.sqlite` identity files into the created directory
* Make sure `*.sqlite` files are owned by `root` user and `root` group

Let's reuse the example path from the previous step. To create the target `te-agent` directory, use the `mkdir -p` command:

```text
$ sudo mkdir -p /docker-data/thousandeyes/my-new-docker-agent/te-agent
```

Now place the `*.sqlite` identity files into the target directory. If you are converting an existing package-based agent into a Docker-based one on the same host, you can simply use the `mv` tool to move the files. If you are migrating the agent from another host, copy the files to the target host first \(i.e. with the `scp` tool\), then move them to the final location:

```text
$ sudo mv *.sqlite /docker-data/thousandeyes/my-new-docker-agent/te-agent
```

Ensure the proper permissions of the `*.sqlite` files - they need to be owned by the `root` user and `root` group:

```text
$ sudo chown root.root /docker-data/thousandeyes/my-new-docker-agent/te-agent/*.sqlite
```

This concludes the transfer of relevant agent state files. Let's continue and transfer the agent configuration settings.

### [Step \#4: Generate and run the "docker run ..." command]()

In [step \#1b]() above, the `/etc/te-agent.cfg` file has been collected. Let's inspect its content:

```text
$ sudo cat /etc/te-agent.cfg
account-token=<YOUR-ACCOUNT-GROUP-TOKEN-HERE>
crash-reports=1
log-level=DEBUG
log-file-size=10
log-path=/var/log
num-log-files=10
proxy-type=DIRECT
proxy-location=
proxy-user=
proxy-pass=
proxy-bypass-list=
```

The `account-token` setting is generally handled implicitly by the `docker run ...` command generator below. However, pay attention to the `proxy-*` settings - you may need to refer back to their values below.

Now head over to the [Cloud & Enterprise Agents &gt; Agent Settings](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents&add-agent) section of the ThousandEyes web portal, click the **Add New Enterprise Agent** button and switch to the **Docker** tab. The familiar Docker agent creation dialog should appear:

  
Docker Enterprise Agent configuration dialog - a filled-out example

You should fill in all the necessary details - **Nam**e \(1\), a designated and absolute **Host Vol. Agent Directory** \(2\) path. If your original agent's `proxy-*` settings were configured, manipulate the proxy-related section of the dialog \(3\) to reach the identical proxy configuration.

On the right-hand side, the full `docker run ...` command will be generated \(4\). Pay particular attention to the `/var/lib/te-agent` directory's storage path on the host \(5\) - the path should be identical to the one pre-created in the [step \#3]() of this guide.

For additional information about deploying Docker Enterprise Agents, consult the [Docker-based Enterprise Agent deployment guide](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker).

Once you're satisfied with the generated `docker run ...` command, run it on your new host. Continuing with the existing example, the following commands should be run to create and start the new Docker agent:

```text
$ docker pull thousandeyes/enterprise-agent > /dev/null 2>&1
$ docker stop 'my-new-docker-agent' > /dev/null 2>&1
$ docker rm 'my-new-docker-agent' > /dev/null 2>&1
$ docker run \
  --hostname='my-new-docker-agent' \
  --memory=2g \
  --memory-swap=2g \
  --detach=true \
  --tty=true \
  --shm-size=512M \
  -e TEAGENT_ACCOUNT_TOKEN=<REDACTED> \
  -e TEAGENT_INET=4 \
  -v '/docker-data/thousandeyes/my-new-docker-agent/te-agent':/var/lib/te-agent \
  -v '/docker-data/thousandeyes/my-new-docker-agent/te-browserbot':/var/lib/te-browserbot \
  -v '/docker-data/thousandeyes/my-new-docker-agent/log/':/var/log/agent \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_ADMIN \
  --name 'my-new-docker-agent' \
  --restart=unless-stopped \
  thousandeyes/enterprise-agent /sbin/my_init
```

 Once the command above returns, you should see your new agent container running. You can inspect the Docker containers' state with the `docker ps` command.

In the ThousandEyes web portal, you should see your original agent checking in again, and data collection for tests assigned to this agent will be restarted. If you expand the agent, you'll notice the agent's reported **Installation Type** changed to `Docker`.

### [Step 5 \(optional\): Install CA certificates]()

If custom CA certificates were installed on your original agent, install them on your new Docker-based agent as well. On appliances, you can find installed CA certificates in the **Network &gt; CA Certificate** section of the administrative web interface. Consult the [guide for installing CA certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG_Installing-CA-Certificates-on-Enterprise-Agents) for more information.

### [Step 6 \(optional\): Migrate SSH keys]()

Virtual and physical appliances may have multiple SSH keys installed on them that you may want to migrate over to your new Docker host. Head over to the **Appliance Access** section of the appliance's administrative web interface and review the list of installed SSH keys.

### [Step 7: Wipe the original agent]()

As an extra precautionary measure, all ThousandEyes software, configuration and state information should be removed from the original agent.

**WARNING: This action is irreversible.** After the following command is executed, if something unexpected happens to your replacement agent and unless you have other means of restoring the agent state files \(out-of-band backup\), you will not be able to recover agent state files. However, if your replacement agent is already running and communicating with the platform, you most likely have nothing to worry about.

On Ubuntu systems and ThousandEyes appliances, the following command wipes all ThousandEyes agent-related software, configuration and state files:

```text
$ sudo apt-get purge te-agent te-browserbot
```

On RHEL-based systems use the following command to achieve the same effect:

```text
$ sudo yum remove te-agent te-browserbot
```

That's it. Great success! You've successfully migrated your non-Docker agent to a Docker-based one.

## [Questions?]()

If you have any questions regarding the migration procedure, or if you get stuck at some point in the migration process, don't hesitate to [reach out to the ThousandEyes Customer Success team](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000UGTFCA4_Getting-support-from-ThousandEyes) and we'll help you out.

## [Related information]()

The following resources provide further reading into related topics:

* [Enterprise Agent support lifecycle policy](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000fyhbCAA_Enterprise-Agent-support-lifecycle-policy) documents when to expect end-of-support events for your Enterprise Agents.
* [How to plan for Enterprise Agent upgrades](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52FSAS_How-to-plan-for-Enterprise-Agent-Upgrades) will guide you through available upgrading options.
* [Replacing Enterprise Agent using agent identity files](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA02R000000Q52ASAS_Replacing-an-Enterprise-Agent-using-Agent-Identity-Files) outlines where Enterprise Agent stores internal state information and how migrating this state information can be leveraged to perform an agent upgrade/replacement.
* [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems) lists all operating systems on which a native package-based Enterprise Agent can be deployed.
* [Enterprise Agent deployment using Docker](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnXKAS_Enterprise-Agent-deployment-using-Docker) guides you through the Docker-based agent deployment steps.
* [Installing CA certificates on Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2fCAG_Installing-CA-Certificates-on-Enterprise-Agents) guide will help you install your custom CA certificates.

