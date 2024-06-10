# [Project based approach based on this udemy course](https://www.udemy.com/course/az-104-microsoft-azure-administrator-lab-exam-prep/) 

# Project: Create Azure Infrastructure Company: Immerse Ins.

## 1.	Create account, resource group and Provision Azure subscription.
- [Create an Azure account - .NET | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/azure/create-azure-account)
- [How To Create Azure Free Account | Azure Account Creation](https://www.youtube.com/watch?v=rj1NOtkJ62A)
- [Manage resource groups - Azure portal - Azure Resource Manager | Microsoft Learn](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal)
- [Create a Microsoft Customer Agreement subscription - Azure Cost Management + Billing | Microsoft Learn](https://learn.microsoft.com/en-us/azure/cost-management-billing/manage/create-subscription)


## 2.	Create AAD Tenant for the Immerse Ins. -> immerse.onmicrosoft.com

Assign owner role for the AAD Tenant

- [Quickstart - Access and create new tenant - Microsoft Entra | Microsoft Learn](https://learn.microsoft.com/en-us/entra/fundamentals/create-new-tenant)

## 3.	Purchase a Custom Domain or use existing e.g. immerse.com

## 4.	Map immerse.com -> immerse.onmicrosoft.com

### Hands On:

AAD -> Custom Domain names:
+ add custom domain: immerse.com (click add domain)
Record type: TXT / MX (Research more about it)
![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/175db05a-db9a-4fe0-b0ea-47d6ec9b8795)


Go godaddy -> domain > manage dns -> dns records :
Type: mx 
![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/c613dcb6-4336-4bed-b82e-b9c7f20dceb5)


Name: 
Priority:
Value:
TTL:
Submit above values as they appear on Azure ADD -> Custom Domain -> Immerse.com
After added and verified. Can make it primary.

## 5.	Invite existing users (by email address) – practical approach.

For email most popular approach is office 365 (firstname.lastname@immerse.com)
(GoDaddy also offers email accounts for domain)

• Add Users to AAD in portal.

•	Users (company employees) & Guest Users (could be contractors)

•	Single vs Bult Operation

### Hands On:

How to create or delete users in Microsoft Entra ID - Microsoft Entra | Microsoft Learn
Immerse ADD -> Users -> Bulk Operation -> Create Bulk users:
Download excel file, fill excel in the given format and upload the file. 

## 6. RBAC

[What is Azure role-based access control (Azure RBAC)?](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/89e7c4be-8744-40ff-bfa0-1f16433c5f8f)

Mange user access
Should be able to create any resource for organization
Should be able to create/manage Storage
Should be able to create/manage networks
Should be able to create/manage VM
•	Azure built in Roles (e.g. Contributor, Owner, Reader, User Access Admin, etc)
•	Custom Role

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/225666ff-9442-4519-ae26-1df4a1108c7b)


## 7.	Resource Group

[What is Azure resource manager and resource group?](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview#resource-groups)

- It’s like a folder/container of a project.
- Resource group can contain resources of any region despite of the resource group location.
- Create Resource group for immerse projects according to location.


## 8.	Tags & Tag Policy Creation for Immerse

Resource creation/organization Policy for Organization
Organize by environment (DEV, INT, UAT, PROD, LAB), by expected duration (ST= Short term, LT = Long Term)

•	Tags
Classify Azure Resource -> Key Value Pair e.g. ENV= PROD (specified during resource creation)
One resource can have multiple tags and tags are optional.

•	Azure Policies 
Standard and enforce compliant. 
Common usages: resource governance, regulatory compliance, security & cost mgmt.
Azure policies can be used to ask user to always tag resources.

### Hands On:

Policy -> Definitions (Under Authoring) + Policy definition (+ Initiative definition is group of policies)
Created on Date tag policy
Assign to your scope -> subscription or resource group
Created policy for tags mandatory
Created policy for fields: tags[Duration] -> notIn: [“LT”,”ST”] & tags[ENV] -> notIn: [“DEV”, “INT” , “UAT”, “PROD”, “LAB”]
Policy e.g.

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/6318d0de-d6a4-4ed3-b4a8-79e14b8ce276)

[Azure Policy pattern: tags](https://learn.microsoft.com/en-us/azure/governance/policy/samples/pattern-tags)


## 9. Storage account provisioning

### Requirement 1:
Store backup data rarely accessed for compliance purpose.
Project Name: Nebula
Storage Account: Nebulastorage3672
Access Tier: Cool
Delete Protection (Soft Delete): 15 Days
Should Support: Table, Queue, File Share, Data Lake, Blob
Geographically Redundant
Should be accessible form public internet.
Tags: ENV=PROD, DURATION=LT
Types of Storage Accounts:

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/14e9abdf-0ffd-4a70-bcc5-a0022d7ccd0b)

Access Tier Options:

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/ba14c6bb-5f75-46a4-bb1b-ad7d9786a2dc)

Azure Storage: Overview and Introduction to the Various Solutions

[Azure Storage: Overview and Introduction to the Various Solutions (cloudacademy.com)](https://cloudacademy.com/blog/azure-storage-service-overview/)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/c398336a-b824-43d9-940c-de75ab3272e9)

High-level architecture and data flow of the proposed solution to support incremental back-up. 

[Azure Block Blob Storage Backup | Blog Azure | Microsoft Azure](https://azure.microsoft.com/fr-fr/blog/microsoft-azure-block-blob-storage-backup/)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/ff6f034f-176a-45ed-b8f8-57f653e78a86)


### Requirement 2:
 
### Hands On:

Container/folder under nebula storage account.
Go to nebula storage account -> click container (under data storage):
+ container -> create container named log -> upload a file and create folder named data.

## 10. Storage Account – Data Sharing with External Organization

[Storage account overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview)

### Requirement:
1st – 30th April
IP: 201.34.43.12
2 ways: RBAC (internal or guest user) & Shared Access Signature (if not part of org)

### Hands On:

Nebula storage account: click shared access signature (under security + networking)
Fill up the info and get the connection string to share.

## 11.	File Sharing permission using RBAC

### Requirement:
User1: Access to read file shares over SMB
User2: Access to read, write, delete and modify NTFS permissions in Azure Storage File Shares over SMB

### Hands On:

2nd way using rbac-> go to nebula storage account: -> IAM -> add role assignment -> Storage file data smb share reader ->next  (+ select member ) -> review and assign.

## 12.	Implement Storage Account Life Cycle mgmt

### Requirement: Optimize storage cost
Auto change access tier of files in data folder in nebula storage account to Archive if not modified last 75 days.

### Hands On:

Nebula storage account: -> lifecycle mgmt (under data mgmt)-> + add a rule:
Enter info, add conditions, choose folder. And hit add the policy.

## 13.	Azure Storage Redundancy

[Data redundancy - Azure Storage | Microsoft Learn](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy)

- Locally Redundant Storage = LZR
- Zone Redundant Storage = ZRS
- Geo Redundant Storage = GRS
- Geo Zone Redundant Storage =GZRS

## 14.	Virtual Network for Immerse PROD Environment

### Requirement:

Virtual Network Name: nebula-prod-vnet
Project: Nebula (associated with resource group)
Total No. of servers in VNET: 25
Subnets: DB Servers, Web Servers, App Servers
Location: Australia East

Address space in VNET e.g. 10.0.0.0/22 (1024 IP Addresses) (22 indicates CIDR space)
(10.1.0.0 – 10.1.3.255)
Subnets -> Manage in logical groups. Distribution of address space into multiple groups
Subnet1: 10.1.0.0/24 (around 250 address range)
Subnet2: 10.1.1.0/24
Each subnet will have associated IP address range.
Multiple VNET and VNET Peering. Hybrid Network (Cloud VNET to On-Premises Network).

### Hands On:

Virtual networks: -> + Create
RG-> IP Address: 10.0.0.0/22 -> 
+ Add Subnet 10.0.0.0/26 (app-server) (59 + 5 Azure reserved addresses)
+ Add Subnet 10.0.1.0/26 (db-server)
+ Add Subnet 10.0.2.0/26 (web-server)
Add tags and Review and create.

## 14.	Deploy a VM to the VNET

### Requirement:

#### VM for DB server -> add to VNET (nebula-prod-vnet)
- VM name: nebula-prod-sql
- Project: Nebula
- OS Version: Windows Server 2019
- VNET: nebula-prod-vnet
- Subnet: db-servers
- OS Disk: HDD (125 GB)
- Data Disk: HDD (256 GB)

#### VM for web server -> add to VNET (nebula-prod-vnet)
- VM name: nebula-prod-sql
- Project: Nebula
- OS Version: Windows Server 2019
- VNET: nebula-prod-vnet
- Subnet: web-servers
- OS Disk: HDD (125 GB)
- Data Disk: HDD (256 GB)

### Hands On:
Virtual Machines: -> + Create -> + Create VM -> Give All Info (Basics, Disks, Networking, Management, Advanced, Tags, Review + Create)

## 15. Deploy a VM to the VNET

### Requirement:

#### VM for DB server -> add to VNET (nebula-prod-vnet)
- VM name: nebula-prod-sql
- Project: Nebula
- OS Version: Windows Server 2019
- VNET: nebula-prod-vnet
- Subnet: db-servers
- OS Disk: HDD (125 GB)
- Data Disk: HDD (256 GB)

#### VM for web server -> add to VNET (nebula-prod-vnet)
- VM name: nebula-prod-sql
- Project: Nebula
- OS Version: Windows Server 2019
- VNET: nebula-prod-vnet
- Subnet: web-servers
- OS Disk: HDD (125 GB)
- Data Disk: HDD (256 GB)

### Hands On:
Virtual Machines: -> + Create -> + Create VM -> Give All Info (Basics, Disks, Networking, Management, Advanced, Tags, Review + Create)

## 16. Network Interface (NIC)

VNIC (Can create, delete, move, disassociate and attach new interface – stop VM and do it) can have public or private IP to connect to network.

[Virtual networks and virtual machines in Azure](https://learn.microsoft.com/en-us/azure/virtual-network/network-overview)

## 17.	Network Security Group Rules for Immerse Inc

### NSG Requirements:

No outbound
RDP from 192.34.32.1 (Jump Host)
NSG attached to VNI. Rules have priority (lowest no. highest priority). Deny/allow rules.

### Hands On:
Network Security Group: -> nebula-prod-sql-nsg -> Inbound security rules -> + Add -> Add the info.

## 18.	VNET Peering

### Requirement:

What is Azure Virtual Network? | Microsoft Learn
Nebula-prod-vnet < - > green-field-vnet

### Hands On:
Virtual Network (green-field-vnet): -> Peerings (under setting) -> + Add (enter info and add)


## 19.	Implement RDP using Bastion

Public IP Add on VM for RDP from Internet
Risks: Port Scanning, DDOS Attack, etc…

Solution: Azure Bastion Service -> allow connecting without exposing public IP

### Hands On:
Virtual Machine (select VM): -> connect (Bastion) -> create subnet and Bastion service (Now you should be able to connect)

## 20.	Implement Load Balancer

[Load Balancer | Microsoft Learn](https://learn.microsoft.com/en-us/azure/load-balancer/)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/01521c9c-8d46-41e5-88d4-572de14a4107)

[What is Azure Load Balancer? - Azure Load Balancer | Microsoft Learn](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-overview)

### Hands On:
Create 2 VM: rg -> Nebula -> names: nebula-webserver-prod-1 & nebula-webserver-prod-2
availability set: create new availability set (give name)
webserver subnet
add inbound rule to allow HTTP (80, tcp, any, any,allow)

Go to Windows Server: open server manager-> Add roles and features -> role -> server role (select web server IIS) – hit add features -> role services (select relevant like logging etc.) -> confirm.

Go to Azure Portal: load balancer -> create load balancer -> give info, basic, type: public -> Frontend IP Config -> + add -> give names and add. -> backend pools -> + add pool: give name, VNET, VM , ipv4, + add VMs -> review and create.

Load Balancer: health probes (under settings) -> + Add : name, http, 80, /Deafult.html,5,2 (interval time)

Load Balancer: load balancing rules (under settings) -> + Add : enter info and create.

## 21. Implement Azure Application Gateway

### Requirement:
Each webserver to handle a specific functional domain:
All marketing domain-related web requests (based on URL) -> nebula-webserver-prod-1
All sales domain-related web requests -> nebula-webserver-prod-2

### Solution: 
(Standard load balancer can’t meet these requirements so use azure application gateway.)

Application Gateway: web traffic load balancer. (L7 LB & WAF – protection against DDOS)
Load balancer (layer 4) vs application gateway (later 7)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/493950e9-64ac-4fda-bb5b-5852c7ede2dc)

[What is Azure Application Gateway | Microsoft Learn](https://learn.microsoft.com/en-us/azure/application-gateway/overview)

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/4d3c8ab8-b6b2-4e08-b62e-4ec67d1f7622)

[What is Azure Application Gateway v2? | Microsoft Learn](https://learn.microsoft.com/en-us/azure/application-gateway/overview-v2)

### Hands On:
[Quickstart: Direct web traffic using the portal - Azure Application Gateway | Microsoft Learn](https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-portal)

Nebula-VNET -> + Add subnet -> name: app-gateway-subnet -> 10.0.3.0/29 (10.0.3.0-10.0.3.7 – 3 + 5 Azure reserved addresses)

Load balancing: -> Application Gateway -> + create -> Give Info -> create public IP -> add backend pool: marketing-pool (select VM) & sales-pool (select VM) -> config: frontend (public IP) – routing rules (+ add rule-> listener -> backend targets: add http setting -> add a path) – backend pools -> tags -> review and create.

*Standard LB need VMs in availability set but application gateway we can choose any VM.
