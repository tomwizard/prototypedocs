# Agent deployment with SaltStack module

SaltStack is an operating system configuration management software that uses a controller and receiver model to execute commands and manage configuration on remote nodes. With the ThousandEyes SaltStack module, you can quickly deploy and manage Enterprise Agents on servers inside your configuration management environment. If you already have a working SaltStack environment, then it is relatively easy to add the TE-Agent SaltStack module. For those of you starting with a fresh build, check out the prerequisites section for pointers to get started.

## Table of contents

* [Terminology]()
* [Prerequisites]()
* [Modules]()
* [Downloading the ThousandEyes module]()
* [ThousandEyes module setup]()
* [Configuration options: te-agent.conf.yml]()
* [Applying the module to individual nodes]()
* [Adding the module to]() [highstate]()
* [Multiple Configuration Files]()
* [Agent validation]()
* [Problems and diagnostics]()

## Terminology

Some common terminology used in this Knowledge Base article:

* **salt-minion:** Remote nodes paired to a Salt-master in a configuration management domain
* **salt-master:** A server designated as a SaltStack controller; also a package name that installs the controller software of the same name
* **Enterprise Agent:** Installable component from ThousandEyes containing both the te-agent and te-browserbot services \([description](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent)\)
* **module:** A set of functions grouped based on use case, e.g., the ThousandEyes module contains a function that deploys an Enterprise Agent 
* **state file:** Typically written in YAML format, a checklist of items and their desired state
* **te-agent:** The process responsible for maintaining a connection with the ThousandEyes collector, and performing network tests
* **te-browserbot:** The service responsible for running web-based tests such as Page Load and Transaction tests \([description](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC_What-is-the-BrowserBot)\)

## Prerequisites

A minimal SaltStack environment has:

* a salt-master containing the necessary configuration files, and
* at least one salt-minion to receive and run commands.

Below are the minimum version requirements as well as a few other details to keep in mind. If you find that you're running a version lower than what is specified, your installation experience may differ from the instructions provided. For fresh installs, it is best to use [SaltStack's bootstrap script](https://docs.saltstack.com/en/latest/topics/tutorials/salt_bootstrap.html#salt-bootstrap) to specify the desired version.

* **salt-master:**
  * Minimum version v2017.7.0 \(Nitrogen\)
  * SaltStack is available for most common Linux distributions.
  * \[optional\] install git on the same host to clone "salt-teagent" from GitHub
* **salt-minion:**
  * Minimum version v2017.7.0 \(Nitrogen\)
  * Must be compatible with ThousandEyes Enterprise Agent [Supported Enterprise Agent operating systems](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems)
  * Paired with your salt-master,  check out the walkthrough [SALT IN 10 MINUTES](https://docs.saltstack.com/en/latest/topics/tutorials/walkthrough.html) for more information
* **A registered ThousandEyes account:**
  * To successfully communicate with the ThousandEyes platform a valid Account Token is required

## Modules

A module is a set of functions with a common theme. Functions complete a specific purpose when called on. To call a function, type the module name followed by the function name, separated with a period \(e.g., `test.ping`\).

 Here are some of the modules and functions we will work with in this article:

* **state -** Built-in module used to work with state files:
  * More info at [https://docs.saltstack.com/en/latest/ref/states/writing.html\#state-modules](https://docs.saltstack.com/en/latest/ref/states/writing.html#state-modules)
  * Functions used in this guide:
    * **sls** - Used to apply a state file
    * **highstate** - Running highstate applies the settings in top.sls to the environment
* **thousandeyes** - An state module built by ThousandEyes to help customers manage large-scale Agent deployments:
  * Available at [https://github.com/thousandeyes/salt-teagent](https://github.com/thousandeyes/salt-teagent)
  * Contains three files:
    * **te-agent.conf.jinja** - Default Agent settings, do not modify.
    * **te-agent.conf.yml** - Enterprise Agent Configuration file, modify according to account specifics 
    * **te-agent.sls** - State file to manage Enterprise Agents with the configuration parameters set in te-agent.conf.yml
* **test** - execution module provided with SaltStack to gain basic status information about salt-minions:
  * Detailed function list at [https://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.test.html](https://docs.saltstack.com/en/latest/ref/modules/all/salt.modules.test.html)
  * **ping** - Used later in the article to test the connection between salt-master and salt-minion
* **grains** - runs during each connection to a salt-minion to gather basic system information such as OS and system resources:
  * Detailed info on grains module at [https://docs.saltstack.com/en/latest/topics/grains/](https://docs.saltstack.com/en/latest/topics/grains/)
  * **item** - Function used to call information about a grain item\(system component\)

## Downloading the ThousandEyes module

Available from GitHub at [https://github.com/thousandeyes/salt-teagent](https://github.com/thousandeyes/salt-teagent), cloning the repository directly to your salt-master is the easiest method to obtain the files:

```text
$ git clone https://github.com/thousandeyes/salt-teagent.git
Cloning into 'salt-teagent'...
remote: Counting objects: 20, done.
remote: Total 20 (delta 0), reused 0 (delta 0), pack-reused 20
Unpacking objects: 100% (20/20), done.
```

If Git is not a viable option, download the files from the Github's web-based platform to your local machine. Then use scp to send the files to your salt-master:

```text
$ scp -r salt-teagent username@hostname:~/
```

## ThousandEyes module setup

For SaltStack to run a module, it needs to be in the root directory specified in the salt-master configuration. Run the following commands from the `salt-teagent` folder downloaded from GitHub:

```text
$ sudo mv thousandeyes /srv/salt/
```

The Topfile \(`top.sls`\) contains the hierarchy of nodes in an environment and can allow or limit communication to nodes when running modules. If you don't have a Topfile, you can use the example provided by moving it into the salt folder:

```text
$ sudo mv top.sls /srv/salt/
```

If you already have a `top.sls` file then you can add the statement `thousandeyes.te-agent` to the desired environment. Below is an example to make the module available for any nodes in the base environment:

```text
base:
  '*':
     - thousandeyes.te-agent
```

## Configuration options: te-agent.conf.yml

This YAML file is used to set the state of each package when installing an Enterprise Agent. A sample configuration file is available in the thousandeyes folder provided in the download from GitHub. Copy the sample file into the root SaltStack configuration directory as `/srv/salt/thousandeyes/te-agent.conf.yml`. Modify the configuration file in the root folder to alter any of the default settings. Below is a list of the fuction variables and their possible states.

1. During highstate or when calling a module, SaltStack attempts to match a package's current state to the state listed in the state file:
   1. **installed** - Installed and enabled this is default state for packages 
   2. **removed** - Uninstalled
   3. **purged** - Uninstalled plus any associated configuration files are removed
   4. **managed** - Standard configuration option are set
   5. **absent** - No action is taken
2. Variables: 
   1. **te\_agent** - manages the te-agent service 
   2. **browserbot** - manages the te-browserbot service 
   3. **set\_repo** - Adds the default ThousandEye's repository to the node. This can be set to absent if you plan to use a Custom Repository.
   4. **agent\_utils** - Installs the network tools used by ThousandEye's Agents in network tests [CLI network troubleshooting utilities](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmoAKAS_CLI-network-troubleshooting-utilities)
   5. **international\_langs** - Adds an extension to chromium to assist with international characters
   6. **account\_token** - Used to register the Agent with the associated Account Group.
   7. **log\_path** - Set a filepath for log files, no input defaults to "/var/log"
   8. **proxy\_host** - Configure the proxy hostname or IP address
   9. **proxy\_port** - Input the port number associated with the proxy

Below is an example of a basic configuration, package name on the left, a colon, then package state on the right. After making updates to the configuration file, either call the module directly or run highstate.

```text
account_token       : 'enterAccountTokenHere'
browserbot          : 'installed'
agent_utils         : 'installed'
```

## Applying the module to individual nodes

Before running the module, it is a good idea to check that salt-minion and salt-master have an active connection. The built-in function `test.ping` is the easiest way to check the connection. Unlike a regular ICMP ping, the function `test.ping` attempts to establish a TCP connection and reports either `True` or `False`. In the example below, all salt-minions are targeted. For larger deployments this obviously wouldn't make sense. Replacing the \* with the salt-minion's ID is the easiest way to target a single node.

```text
salt-master-ubuntu$ sudo salt '*' test.ping 
salt-minion-ubuntu:
True
salt-minion-centos:
True
```

Check that the salt-minion is running a [supported Enterprise Agent operating system](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems):

```text
salt-master-ubuntu~/salt-teagent $sudo salt '*' grains.item osfinger

salt-minion-ubuntu:
----------
osfinger:
Ubuntu-16.04
salt-minion-centos:
----------
osfinger:
CentOS Linux-7
```

It is recommended [having at least 1GB of memory available for Enterprise Agents without Browserbot and 2GB with Browserbot running](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements):  
 

```text
salt-master-ubuntu$ sudo salt '*' grains.item mem_total
salt-minion-ubuntu:
----------
mem_total:
992
salt-minion-centos:
----------
mem_total:
992
```

If all three checks above look good, the last step is to apply the ThousandEyes state file. To do this, call the function from the state module. This function takes one argument, which is the name of the state file to use. Use the same name listed in your `top.sls` file which, by default, is `thousandeyes.te-agent`:

```text
$ sudo salt salt-minion-centos state.sls thousandeyes.te-agent

Summary for salt-minion-centos
------------
Succeeded: 8
Failed: 0
------------
Total states run: 8
Total run time: 2.275 s
```

Your output may be different depending on which packages you decided to include in your configuration file. 

## Adding the module to highstate

Highstate refers to a complete list of state files listed in the `top.sls` file. Here is where you can restrict which salt-minions are affected. Some common limitations include matching an operating system or salt-minion ID.

Matching any salt-minions with Ubuntu operating system:

```text
base:
  'os:Ubuntu':
    - match: grain
    - te-agent
```

Matching all salt-minion IDs that start with `te-agent`:

```text
base:
  'te-agent*':
    - te-agent
```

When highstate finishes running, it receives the status from each salt-minion and their final state.

```text
$ sudo salt '*' state.highstate

salt-minion-ubuntu:
----------

...<excluded for brevity>...

----------

Summary for salt-minion-ubuntu
------------
Succeeded: 5
Failed: 0
------------
Total states run: 5
Total run time: 1.504 s
```

## Multiple Configuration Files

In some cases, you may need to deploy Agents requiring a unique configuration, such as production and staging Agents each using a different proxy. To accomplish this, create a state and configuration file specific to each type of deployment. Additional configuration and state files should still reside in the thousandeyes module folder. Modify the first line of the state file to point to the appropriate configuration file. Your production state should now be pointing to your production configuration file.

```text
salt-master-ubuntu:/srv/salt/thousandeyes$ ls 

te-agent.conf.jinja

te-agent-production.conf.yml

te-agent-production.sls

te-agent-staging.conf.yml

te-agent-staging.sls
```

**te-agent-production.sls:**

```text
{% import_yaml "thousandeyes/te-agent-production.conf.yml" as config %}

...<excluded>...
...<excluded>...
...<excluded>...
```

**te-agent-production.conf.yml:**

```text
account_token       : 'enterAccountTokenHere'
browserbot          : 'installed'
agent_utils         : 'installed'
proxy_host          : 'proxy.production.example.com'
proxy_port          : '8080'
```

**te-agent-staging.sls:**

```text
{% import_yaml "thousandeyes/te-agent-staging.conf.yml" as config %}

...<excluded>...
...<excluded>...
...<excluded>...
```

**te-agent-staging.conf.yml:**

```text
account_token       : 'enterAccountTokenHere'
browserbot          : 'installed'
agent_utils         : 'installed'
proxy_host          : 'proxy.staging.example.com'
proxy_port          : '8080'
```

Next, modify the `top.sls` configuration file so that minions are in the desired environments. In the following example, all salt-minions with a name that starts with `production-` will receive the production configuration file `thousandeyes.te-agent-production` \(note the absence of the `.sls` extension\):

```text
base:
  '*':
    - cool_things
    - nifty_widgets
  'production-*':
    - production_stuff
    - thousandeyes.te-agent-production
  'staging-*':
    - staging_stuff
    - thousandeyes.te-agent-staging
```

Now, to apply all changes, run highstate:

```text
$ sudo salt '*' state.highstate

production-salt-minion-ubuntu:
----------

...<exluded>...

----------

Summary for production-salt-minion-ubuntu
------------
Succeeded: 7
Failed: 0
------------
Total states run: 7
Total run time: 35.234 s



staging-salt-minion-centos:

----------

...<exluded>...

----------

Summary for staging-salt-minion-centos
------------
Succeeded: 7 (changed=6)
Failed: 0
------------
Total states run: 7
Total run time: 239.597 s
```

## Agent validation

When complete, any newly created Agents should appear under the Agent management page in your ThousandEyes account:

The fastest way to validate that your new Agents are working as expected is to use them to perform an [Instant Test](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnaUCAS_How-to-use-Instant-Tests).

## Problems and diagnostics

* SaltStack says succeeded but the Agent did not appear in your account:
  * Double check that the account token in your configuration file matches the token shown in your ThousandEyes account. Re-run the module after the configuration file is modified.
* The Agent shows up in your account but is failing network tests:
  * Check if a firewall is restricting traffic necessary for the test type. Consult the [Firewall configuration for Enterprise Agents](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnBtCAK_Firewall-configuration-for-Enterprise-Agents) article for further details.
  * Check if a proxy is restricting traffic necessary for the test type.
* Agent clock is out of sync:
  * NTP or Network Time Protocol is how most Linux servers stay synchronized with the rest of the world. Setting NTP servers with SaltStack is beyond the scope of this article but here are some basic Linux instructions.
  * [What to do when your Enterprise Agent's system clock is out of sync?](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnzKAC_Troubleshooting-time-synchronization-on-Enterprise-Agents)
* When a salt-minion fails `test.ping`:
  * If the salt-minion is online and operational, but failing to return results for `test.ping` command this could be a firewall issue. Check SaltStack firewall documentation below.
  * [https://docs.saltstack.com/en/latest/topics/tutorials/firewall.html](https://docs.saltstack.com/en/latest/topics/tutorials/firewall.html)
* General problems:
  * Run debug command in the foreground: `# salt-master -l debug`
  * Debug modes may help to uncover errors, read more about troubleshooting directly on the SaltStack site.
  * [https://docs.saltstack.com/en/latest/topics/troubleshooting/master.html](https://docs.saltstack.com/en/latest/topics/troubleshooting/master.html)

For any problems not covered here please reach out to [support@thousandeyes.com](mailto:support@thousandeyes.com).

