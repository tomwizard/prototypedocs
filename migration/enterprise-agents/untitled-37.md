# IaaS Enterprise Agent deployment - Amazon AWS

ThousandEyes Enterprise Agents can be deployed in some infrastructure-as-a-service providers natively. The ThousandEyes IaaS-based Enterprise Agent deployment method allows customers to deploy Enterprise Agents in their Amazon AWS environments, with only a few clicks.

## Requirements

 Deploying an Enterprise Agent in the AWS environment using the IaaS deployment method requires an Amazon AWS account with the following:

1. An SSH key pair previously created
2. A VPC network \(present by default in a new AWS account\)
3. An IP subnet in the VPC network \(present by default in a new AWS account\)
4. Privileges to deploy a new [CloudFormation](https://aws.amazon.com/cloudformation/) stack with an [EC2](https://aws.amazon.com/ec2/) instance

##  Deployment

 To start the IaaS Enterprise Agent deployment, head to the [Settings -&gt; Agents -&gt; Enterprise Agents](https://app.thousandeyes.com/settings/agents/enterprise/?section=agents) section of the web portal and expand the **"+ Add New Agent"** dialog. Click on the **"IaaS Marketplaces"** button \(1\) and the following content should appear:

IMAGE MISSING

In the dialog above, click on the **"Launch In AWS"** button \(2\). This will open a new tab in your browser and lead you to the [AWS CloudFormation management console](https://console.aws.amazon.com/cloudformation/). Note the location of the indicator with number "6" - this is where you will get your account group token needed in one of the steps below.

Once AWS CloudFormation console loads in a new browser tab, you will see the **"Create stack"** screen as outlined here:

IMAGE MISSING

The URL-based template location is already pre-selected \(3\). The [Amazon S3 URL](https://s3-us-west-1.amazonaws.com/oneclick-ea.aws.thousandeyes/aws-ea-oneclick.yaml) where the template will be retrieved from is also pre-populated.   
Click the **"Next"** button \(4\) to continue with the creation process.

**Note: We currently do not support IaaS Marketplaces deployment for AWS China.**

The following Enterprise Agent configuration details page will appear:

IMAGE MISSING

The following options should be configured on this page:

* **Stack name** \(5\) \[REQUIRED\]: The name of the CloudFormation stack. It is suggested to use the same identifier for Stack name and agent hostname.
* **AccountToken** \(6\) \[REQUIRED\]: The account group token that is used to associate your new agent with your ThousandEyes account. Consult the pointer no.6 in the deployment screenshot no.1 above for the location of your account group token.
* **BrowserBot** \[OPTIONAL\]: Whether to enable the [BrowserBot](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnsKAC) compontent or not. Defaults to "true". Required for the execution of Page Load and Transaction tests.
* **Hostname** \(7\) \[REQUIRED\]: Hostname of your new Enterprise Agent. Using the same value for Hostname and for Stack name is suggested.
* **KeyName** \(8\) \[REQUIRED\]: The name of the SSH public key that should be installed on the EC2 instance hosting the new Enterprise Agent.
* **SubnetId** \(9\) \[REQUIRED\]: Select the subnet that you want to connect your new agent to.
* **VpcId** \(10\) \[REQUIRED\]: Select the VPC in which the subnet \(9\) resides.

 Once the details of your new CloudFormation stack are configured, click on the **"Next"** button \(11\).

The following stack **"Options"** page will open:

IMAGE MISSING

No configuration change is required on this page. Once you're satisfied with your stack options configuration, click the **"Next"** button \(12\).

You will be led to the following "Review" page:

IMAGE MISSING

You are encouraged to closely review your stack configuration. If anything is not configured properly, use the **"Previous"** button that will lead you back to the step where you can perform the correction. Once you're entirely satisfied with the configuration, use the **"Create stack"** button \(13\) to initiate the stack creation process.

The following screen should appear in front of you \(you may need to click the "Reload" icon on the right side\):

IMAGE MISSING

Stack creation can take several minutes. While the stack is being created, the "CREATE\_IN\_PROGRESS" label is displayed in the table. Eventually, the stack creation will be complete and the "CREATE\_COMPLETE" label \(15\) will replace the in-progress one:

IMAGE MISSING

Back in your ThousandEyes account, the notification about new agent should appear shortly:

IMAGE MISSING

Congratulations!  
You have just deployed a new Enterprise Agent in your Amazon AWS account using our IaaS deployment method.

## Instance maintenance

 Generally, no manual maintenance of the provided image is required. The [Ubuntu OS](https://www.ubuntu.com/) contained within the image is configured to automatically apply security updates as they are released by the OS vendor [Canonical](https://www.canonical.com/).

There are two scenarios where manual instance maintenance can be expected:

* Automatic security updates will install new Linux kernels that include critical security updates. To fully apply these updates, instance reboot will be required.
* The underlying operating system has reached its end-of-life stage. Agent replacement procedure will need to be performed.

 ThousandEyes will communicate these manual maintenance requirements to customers using the [Announcements](https://success.thousandeyes.com/Articles?category=Announcements) section of our support portal. You are encouraged to subscribe to this section in order to receive email notifications when new announcements are posted.

## Connecting to SSH

 EC2 instances created by IaaS-based Enterprise Agent deployments provide SSH service for management purposes. To connect to the isntance using SSH, you will first need to obtain instance IP address\(es\). One way to find agent IP address\(es\) is by looking at agent's General Info panel of the expanded Enterprise Agent entry in Settings -&gt; Agent -&gt; Enterprise Agents section of the ThousandEyes web portal.  
Alternatively, you can leverage [EC2 management console](https://console.aws.amazon.com/ec2) to find your instance IP addresses. Once you open the EC2 console, you are presented with the following view:

IMAGE MISSING

Use EC2 instance filtering facilities \(1\) to locate your instance. When you've located the instance, click on it \(2\) to select it. Then consult the "Description" tab \(3\) of the instance information panel. Look for the public \(4\) and private \(5\) IP address information.

To connect to the appliance, use the **"ubuntu"** username and the SSH key that was used while creating the agent.

## Removing the CloudFormation-based Enterprise Agent deployment

 To remove the Enterprise Agent created using our IaaS-based deployment method, we suggest removing the whole CloudFormation stack related to your agent. To start the removal process, log in to your [CloudFormation management console](https://console.aws.amazon.com/cloudformation) and find the stack related to the agent you want to remove:

IMAGE MISSING

Leverage the stacks searching facilities \(1\) provided by AWS to find the relevant stack. Once you have located the stack related to Enterprise Agent in question, right-click on the stack name \(2\) will open the context menu. Choose the **"Delete Stack"** \(3\) action.

The following confirmation window will be presented to you:

IMAGE MISSING

Make sure you are deleting the correct stack \(4\). Once ready, click the **"Yes, Delete"** button \(5\) to initiate the removal process.  
You will be lead back to the stack list page.

There, the "DELETE\_IN\_PROGRESS" label \(6\) will be displayed in the "Status" column:

IMAGE MISSING

The last thing that remains to be performed is to delete the Enterprise Agent itself. Head to the Settings -&gt; Agents -&gt; Enterprise Agents section of the ThousandEyes web portal and find your agent. You can use the agent filtering facilities \(7\) to locate your agent:

IMAGE MISSING

Once you've located your agent, click on options icon \(8\) to reveal menu. Select the **"Delete"** option \(9\) to remove the Agent. Confirm the action by clicking **Delete** in the side pane prompt.

## Frequently Asked Questions

### Which EC2 instance type is used by ThousandEyes IaaS-based AWS deployment method?

 Instance type used: **t2.medium**

### Are networks with required proxy usage supported by IaaS-based Agent deployments?

 Yes. However, the configuration of proxy settings must be performed as if the Agent was deployed using our package-based deployment method:

* Connect to the agent using [SSH]()
* Perform the proxy configuration as described in the [proxy configuration KB article](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000LB2kCAG) \(consult the section that deals with configuring proxy settings on Linux package-based Enterprise Agents\).

