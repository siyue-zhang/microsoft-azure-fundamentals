# microsoft-azure-fundamentals
Notes for [Exam AZ-900: Microsoft Azure Fundamentals](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3WzVA)

<img src=https://docs.microsoft.com/en-us/media/learn/certification/badges/microsoft-certified-fundamentals-badge.svg width=100>

## Exam Objectives

1. [Describe Cloud Concepts](#cloud-concepts) (20-25%)
2. [Describe Core Azure Services](#azure-core-services) (15-20%)
3. Describe core solutions and management tools on Azure (10-15%)
4. Describe general security and network security features (10-15%)
5. Describe identity, governance, privacy, and compliance features (15-20%)
6. Describe Azure cost management and Service Level Agreements (10-15%)


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

##  





