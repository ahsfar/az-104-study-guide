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

## 3.	Purchase a Custom Domain or use existing e.g. immerse.com.

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

It’s like a folder/container of a project. 
Resource group can contain resources of any region despite of the resource group location.
Create Resource group for immerse projects according to location.


