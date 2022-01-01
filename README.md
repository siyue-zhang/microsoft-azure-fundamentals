# microsoft-azure-fundamentals
Notes for [Exam AZ-900: Microsoft Azure Fundamentals](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3WzVA)

<img src=https://docs.microsoft.com/en-us/media/learn/certification/badges/microsoft-certified-fundamentals-badge.svg width=100>

## Exam Objectives

1. [Describe Cloud Concepts](#cloud-concepts) (20-25%)
2. [Describe Core Azure Services](#azure-core-services) (15-20%)
3. Describe core solutions and management tools on Azure (10-15%)
4. [Describe general security and network security features](#security-privacy-compliance-and-trust) (10-15%)
5. Describe identity, governance, privacy, and compliance features (15-20%)
6. Describe Azure cost management and Service Level Agreements (10-15%)

[Practice Questions](#practice-questions)

## Cloud Concepts

### Cloud Models

**Public cloud**: Azure, physical infrastructure is managed by Microsoft. Lower costs, less maintenance, high availability and reliability.

**Private cloud**: The physical infrastructure is managed by your company. The company wants to own the entire infra. Government agency or a financial institution - own the infra and the data.

**Hybrid Cloud**: Connect Azure to your own-premise infrastructure. Get the best from both sides.

### Types of Services

**IaaS**: The physical infrastructure is managed by Azure. You only manage the virtual server. Access to various computing types, various types of workloads.

**PaaS**: Physical server + virtual machines are managed by Azure (e.g. Azure SQL Database). Automated backups.

**SaaS**: Physical server + virtual machine + software, (e.g. Gmail, online version of Office 365).

### Expenditure

On-premise Web Server + Database Server:
* Buy physical servers
* Buy storage
* Buy OS licences
* Buy database licence
* Networking
* Pay for workforce to maintain the infra
* Cost of electricity

### Shared Responsibility Model

<img src=https://satalyst.com/wp-content/uploads/2021/02/Azure-shared-responsibility-model.png>


## Azure Core Services

### Azure Regions

* Availability zones are physically separate locations within an Azure region
* Each availability zone is made up of one or more datacenters
* Each availability zone is equipped with independent power, cooling and networking

### Azure Free Account

12 months free services, $200 credit, always free 25 services

only for B1S VM

### Resource Groups

Container to hold related resources

### Virtual Network

* Virtual machines are hosted in the virtual network
* VN can consist of multiple subnets
* Each VN needs to be assigned an address space

A public IP address can also be allocated to a VM. It allows for communication to the Internet.

Virtual Network Peering: VM communicate with another VM

### Dedicated Hosts

* This is a service that gives you a physical server as a resource
* Allow you to host one or more VMs on the physical server
* No other customer can host their VM on the physical server
* Hardware isolation at the physical server level
* Has control over the maintenance events that get initiated by Azure platform

### Marketplace

E.g. Wordpress on Windows Server 2016, solution installed OS

### Network Security Groups

* Used to control traffic into your subnet or VM
* Inbound and outbound traffic

<img src=https://docs.microsoft.com/en-us/azure/bastion/media/bastion-nsg/figure-1.png width=700>

1. Deploy a VM
2. Allows RDP traffic via NSG rules (port 3389)
3. Allows HTTP traffic via NSG rules (port 80)

### VM Scale Sets

Scale sets increase/ decrease the amount of VMs when pre-defined critera has been met (e.g. 70% CPU utilization)

* This service allows you to create a set of identical VMs
* Allows you to scale on demand
* Add high availability to infra
* Place the Scale Set behind either a load balancer or an Application Gateway

### Load Balancer

User request -> load balancer -> VMs

Database servers <-> **Internal load balancer** <-> Web servers <-> **Public load balancer** <-> Users

Health Probe - This is used to check whether a backend VM is healthy or not.

Session Persistence - Client IP's can be directed to the same backend VMs

Work at Layer 4 - Network Layer

### Application Gateway

Load balancer that works at Layer 7 - Application Layer

Full managed service: infra, scalability, availability by Azure

URL based routing: user can define mapping between the URL link and the VM

<img src=https://azuretrainings.files.wordpress.com/2019/04/appgw1.jpg>

Web Application Firewall: protect against common attacks such as SQL injection, cross site sripting attacks

### Azure Storage

Different types of services:
* BLOB: object storage solution, store unstructured data, files/ videos/ images/ log files
* File: allow for retrieval of files via Server Message Block protocol
* Table: used for structured NoSQL data, e.g. user data for applications
* Queue: used for storage and retrieval of messages, a single message in the queue max 64 KB

#### BLOB (binary large object)

* Hot storage tier - ideal for objects that are accessed frequently
* Cool tier - optimized for data that is infrequently accessed
* Archive tier - optimized for data that is rarely accessed

### VPN Gateway

Virtual private network gateway, the traffic sent via the Gateway is encrypted.

**Point to Site Connection**: connect workstations to an Azure Virtual Network, you need to install VPN client

**Site to Site Connection**: connect on-premise networks to Azure networks, your on-premise network should have a VPN device with an IP address that is routable over the Internet

### Virtual Network Peering

Connection between VM and VM through Azure backbone network, not public internet (low-latency, security, high-bandwidth)

### ExpressRoute

This sevice allows you to extend a company's on-premise network to the Microsoft cloud using a private connection that is proverd by a connectivity provider

Layer 3 routing

A private link doesn't go via Internet

### Web App Service

Platform as a service on the cloud, service for hosting web applications

.Net, .Net Core, Java, Ruby, Node.js, PHP, Python

Underlying servers can be Windows or Linux

Devops - continuous deployment

Blue Green deployments using staging slots

Authenticate with external providers

### Databricks

Apache Spark-based analytics platform

<img src=https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/data/images/stream-processing-databricks.png>

### HDInsight

Cloud distribution of Hadoop based components

### Azure Resource Manager Templates

ARM templates: JSON template that contains the resources that you want to create in Azure
* Schema: version of template language
* Content version: version of the template
* Resources: main section where you define the resources that need to be deployed as part of the template
* Parameters: customize the deployment of the resources

### Cognitive Services

#### Vision API

E.g. find faces in images, extract text from the images

#### Speech API

Translating speech to text, converting text to speech, speech translation

#### Language API

Text analysis, to understand what a person wants, sentiment

#### Decision API

Detect abnormalities in the data collected

Content Moderator to monitor for offensive language

#### Search API

Bing News Search, Video Search

### Bot Services

Life intercation

.Net

### DepOps Services

Goal is to deliver applications and services at high velocity.

Azure Boards: user stories, backlog items, task, features and bugs

Repos: version control tools

Pipelines: automatically build and test code project

Test Plans: manage manual testing includes user acceptance test, exploratory test and shareholder feedback

Source code can be located in Github.

### Serverless Services

**Azure Functions**: serverless compute service
* Deploy function code onto Azure
* Only pay for the amount of time the code runs

**Serverless Kubernetes**: deploy container based applications

**Azure Logic Apps**: used to design workflows in Azure

**Event Grid**: event-based service
* Work with events generated from Azure services

**API Management**: used to manage backend APIs

**SQL Databases**: serverless version of Azure SQL database
* Only pay for the compute used

**Cosmos DB**

### Azure Functions

* Serverless compute service
* C#, F#, Node.js, Java, PHP
* Pay for only what you use

<img src=./Func.JPG width=600>

Consumption Plan: on-demand run of codes, charged for the number of execution, execution time, Memory used

Max allowable execution time is 5 minutes.

App Service Plan

Purpose: run functions without managing underlining VM

### Event Grid

Event Source -> Event Grid -> Event Handlers

### Logic Apps

* Serverless service
* Build workflows
* Can build workflows via a Visual Designer

E.g. a new file in BLOB -> send an email

### CosmosDB

* Multi-model database: support various APIs for Table, SQL, MongoDB, Cassandra...
* Low latency access to data
* Instant replication of data across regions
* Scales based on demand
* Fully managed and serverless

Throughput: A combined measure of CPU, Memory and IOPS, measured in Request Units

The cost to read 1 KB item is 1 Request Unit. Billing is done on a hourly basis.

### Azure SQL Database

<img src=./sqlDB.JPG width=600>

## Security Privacy Compliance and Trust



## Practice Questions

### VM related storage
1. Data Disk: a managed disk attached to a VM to store application data, max 32TB
2. OS Disk: pre-installed OS, max 2TB
3. Temporary Disk: not a managed disk, short-term storage for applications and processes, may be lost during a maintenance event. During a successful standard reboot of VM, the data on the temporary disk will persist.

### Cosmos DB account cost
Measurement of costing:
* The storage
* The throughput

### Disaster recovery
Can deploy recources across multiple regions

### Load balancer for increase overall availability
With Standard Load Balancer, you can scale your applications and create highly available services.


