**# Azure Day 1** 
Notes : 
Simple workflow of Resource creation : 
User -> Request through services -> Azure Resource Manager -> Resource

Resource Group :
This is Mandatory in AZURE.
It groups the resources, consider it like AWS CloudFormation stacks. 

Key Points about Resource Groups:
**Lifecycle Management:** 
Resources within a group can be managed collectively, making it easy to handle deployments, updates, and deletions.

**Resource Organization:** 
Grouping resources based on projects, environments, or applications helps keep your Azure environment well-organized.

**Role-Based Access Control (RBAC):** 
Permissions and access control are applied at the resource group level, allowing you to manage who can access and modify resources within a group.


Key Features of Azure Resource Manager (ARM) :
**Template-Based Deployment:** 
ARM uses JSON templates to define the infrastructure and configuration of your Azure resources. This enables repeatable and consistent deployments.

**Dependency Management:** 
ARM automatically handles dependencies between resources, ensuring they are deployed in the correct order.

**Roll-back and Roll-forward:** 
In case of deployment failures, ARM can automatically roll back changes to maintain the desired state, or roll forward to the last known good state.

**Tagging and Categorization:** 
You can use tags to label and categorize resources, making it easier to manage and organize your Azure environment.

==========================END===============================

**Azure Day 2**
Deployment and Azure VM 

**General Purpose VMs**
Example: Standard_D2s_v3

Description: General-purpose VMs are well-balanced machines suitable for a variety of workloads. They offer a good balance of CPU-to-memory ratio and are suitable for development, testing, and small to medium-sized databases.

Use Case: Hosting websites, lightweight applications, or development and testing environments.

**Compute Optimized VMs
**Example: Standard_F2s_v2

Description: Compute optimized VMs are designed for compute-intensive workloads that require high CPU power. They provide a high CPU-to-memory ratio, making them suitable for data analytics and computational tasks.

Use Case: Batch processing, gaming applications, and other CPU-intensive workloads.

**Memory Optimized VMs
**Example: Standard_E16s_v3

Description: Memory optimized VMs are tailored for memory-intensive applications. They provide a high memory-to-CPU ratio, making them suitable for databases, in-memory caching, and analytics.

Use Case: Running large databases, in-memory caching, and analytics applications.

**Storage Optimized VMs
**Example: Standard_L8s_v2

Description: Storage optimized VMs are designed for workloads that require high storage throughput and I/O performance. They provide high local disk throughput, making them suitable for big data and large databases.

Use Case: Big data applications, data warehousing, and large-scale databases.

**GPU VMs**
Example: Standard_NC6s_v3

Description: GPU (Graphics Processing Unit) VMs are equipped with powerful graphics processors, suitable for graphics-intensive applications and parallel processing tasks.

Use Case: Machine learning, graphics rendering, and simulations that require GPU acceleration.

**High-Performance Compute VMs
** Example: Standard_H16r

Description: High-Performance Compute VMs are designed for demanding, parallel processing and high-performance computing (HPC) applications.

Use Case: Simulations, modeling, and scenarios that require massive parallel processing.

**Burstable VMs
**Example: B1s

Description: Burstable VMs provide a baseline level of CPU performance with the ability to burst above the baseline for a certain period. They are cost-effective for workloads with varying CPU usage.

Use Case: Development and testing environments, small websites, and applications with variable workloads.


VM Creation : 

Create a Ubuntu VM : 

Connect using gitbash via ssh : 
ssh -i C:/xxxx/Az_xxxxx_key.pem azureuser@x0.1x9.75.177


Install Jenkins.
Pre-Requisites:

Java (JDK)
Run the below commands to install Java and Jenkins
Install Java

sudo apt update
sudo apt install openjdk-11-jre
Verify Java is Installed

java -version


Now, you can proceed with installing Jenkins

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins


use below to see if the jenkins is up and running : 

ps -ef | grep jenkins

"
Hmmm… can't reach this page <*IP ADDRESS*> refused to connect.
Try:
Search the web for <*IP ADDRESS*>
Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_REFUSED
"
WHY ? the jenkins is running right ? 

Well we forgot one thing. We need to expose the port 8080. just like port 22 is exposed.

once expose try to hit : 
http://20.189.75.177:8080

you should get :
<html><head><meta http-equiv='refresh' content='1;url=/login?from=%2F'/><script id='redirect' data-redirect-url='/login?from=%2F' src='/static/03930419/scripts/redirect.js'></script></head><body style='background-color:white; color:white;'>
Authentication required
<!--
-->
</body></html> 

what is this ? well .... this is jenkins homepage.




**VMSS** - Virtual Machine Scaling Set or Azure AutoScaling
This would auto upscale and downscale the VMs clones based on the incoming traffic. 

==========================END===============================

