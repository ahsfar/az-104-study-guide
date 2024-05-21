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

- Hands On:
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

- Hands On:
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

- Hands On:

Policy -> Definitions (Under Authoring) + Policy definition (+ Initiative definition is group of policies)
Created on Date tag policy
Assign to your scope -> subscription or resource group
Created policy for tags mandatory
Created policy for fields: tags[Duration] -> notIn: [“LT”,”ST”] & tags[ENV] -> notIn: [“DEV”, “INT” , “UAT”, “PROD”, “LAB”]
Policy e.g.

![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/6318d0de-d6a4-4ed3-b4a8-79e14b8ce276)

[Azure Policy pattern: tags](https://learn.microsoft.com/en-us/azure/governance/policy/samples/pattern-tags)


## 9. Storage account provisioning

•	Requirement #1
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


•	Requirement 2:
- Hands On:

Container/folder under nebula storage account.
Go to nebula storage account -> click container (under data storage):
+ container -> create container named log -> upload a file and create folder named data.

## 10. Storage Account – Data Sharing with External Organization

[Storage account overview](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview)

•	Requirement:
1st – 30th April
IP: 201.34.43.12
2 ways: RBAC (internal or guest user) & Shared Access Signature (if not part of org)
- Hands On:
Nebula storage account: click shared access signature (under security + networking)
Fill up the info and get the connection string to share.

## 11.	File Sharing permission using RBAC

•	Requirement:
User1: Access to read file shares over SMB
User2: Access to read, write, delete and modify NTFS permissions in Azure Storage File Shares over SMB

- Hands On:
2nd way using rbac-> go to nebula storage account: -> IAM -> add role assignment -> Storage file data smb share reader ->next  (+ select member ) -> review and assign.

## 12.	Implement Storage Account Life Cycle mgmt

•	Requirement: Optimize storage cost
Auto change access tier of files in data folder in nebula storage account to Archive if not modified last 75 days.

- Hands On:
Nebula storage account: -> lifecycle mgmt (under data mgmt)-> + add a rule:
Enter info, add conditions, choose folder. And hit add the policy.

## 13.	Azure Storage Redundancy

[Data redundancy - Azure Storage | Microsoft Learn](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy)

- Locally Redundant Storage = LZR
- Zone Redundant Storage = ZRS
- Geo Redundant Storage = GRS
- Geo Zone Redundant Storage =GZRS

## 14.	Virtual Network for Immerse PROD Environment

•	Requirement:

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

- Hands On:
- 
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
![image](https://github.com/ahsfar/az-104-study-guide/assets/91184500/69318a67-2e0b-403a-bc40-dc6eff66b0d6)


