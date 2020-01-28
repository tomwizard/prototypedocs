# What is an Enterprise Agent?

Our ThousandEyes platform uses _Agents_ to run tests against targets configured for measurement.  An _Agent_ is a Linux server running custom ThousandEyes software, which checks in with an agent collector to obtain instructions from the ThousandEyes platform.  Generally speaking, these are lightweight machines, which are tasked solely with acting as ThousandEyes Agents.  Within the Agent ecosystem, we have two main types of agent: _Cloud Agents_ and _Enterprise Agents_.

## Cloud Agents

Cloud Agents are servers deployed globally in tier 2 or tier 3 data centers, managed and maintained by the ThousandEyes operations team.  These servers are available for the use of our customers on a unit consumption basis, and are shared by all customers.  These servers are capable of running all test types available in the ThousandEyes platform.

## Enterprise Agents

An Enterprise Agent is an endpoint that is used to test targets from inside your network, or from infrastructure within your control. Enterprise Agents can be easily installed on your own network, in data centers and branch offices, using a lightweight virtualized system called a Virtual Appliance, or using a Linux package installed on a supported Linux distribution.  Enterprise Agents collect data for the exclusive use of your account, and are not shared with other organizations.

### Virtual Appliance

The Virtual Appliance is a lightweight all-in-one package, intended for customers to rapidly deploy into a hypervisor platform.  The Virtual Appliance contains a web-based management console, which allows customers to configure network, proxy and other settings specific to this Virtual Appliance.  One of the biggest benefits of the Virtual Appliance is that it is manageable by someone with little-to-no Linux expertise.

IMAGE MISSING

Installation of a Virtual Appliance requires that a hypervisor be available.  Check out [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnmKAC) for suggestions on enabling an appropriate hypervisor.

The Virtual Appliance runs Ubuntu Linux server 16.04, and keeps itself up to date by downloading and applying security updates automatically.  It is available in two different distribution options; an industry standard .ova template format, and a Microsoft Hyper-V .zip file.  Both versions can be downloaded from our Add &gt; New Agent page.  In addition, customers can preconfigure virtual appliances for their exclusive use.  This binds the customer's account token to the agent, such that it cannot be modified - and requires less configuration during enterprise agent deployment.

### Linux package

The Linux package installation will run with any compatible version of Linux.  Check the ThousandEyes Knowledge Base article entitled "[Supported agent operating systems](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnoKAC)" for the current list of Linux distributions which support the Enterprise Agent Linux package.  This package is available to be installed on the host, and runs as a service, once configured.  When installing via the Linux package approach, the only software which is kept up to date is the software required by the agent code.

Installation instructions for installing the Agent using the Linux package method can be found [here](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnZKAS).

### Clusters

Enterprise Agents can be grouped into Agent clusters.  Clusters allow you to add capacity as needed to a single logical Agent.  When a test is assigned to the cluster, the cluster software assigns the test to the Enterprise Agent in the cluster that has the least load for the type of test being assigned.  Note that clustering does not provide a fail-over mechanism.  If one member of the cluster goes offline or experiences similar issues, the tests of that cluster member are not reallocated to the other members of the cluster.

Cluster members can be either Virtual Appliances or Linux package Enterprise Agents.  
 

## Hardware requirements

Consult a dedicated [Enterprise Agent hardware requirements](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2uCAG_Enterprise-Agent-Hardware-Requirements) article for details.

## Additional resources

* For firewall rule recommendations for Enterprise Agents, see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA044000000CnBtCAK)
* If you are interested in the type of data collected by ThousandEyes agents, see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnpKAC)

