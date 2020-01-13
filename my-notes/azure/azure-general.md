
#### Azure commands


`az login`


#### Resource group

An Azure resource group is a logical group in which Azure resources are deployed and managed. When you create a resource group, you are asked to specify a location. This location is where resource group metadata is stored, it is also where your resources run in Azure.


`az group create --name myResourceGroup --location eastus`


####  Azure Active Directory (Azure AD) 

(Azure AD)  is Microsoft’s cloud-based identity and access management service, which helps your employees sign in and access resources in:

    External resources, such as Microsoft Office 365, the Azure portal, and thousands of other SaaS applications.

    Internal resources, such as apps on your corporate network and intranet, along with any cloud apps developed by your own organization.

####  Azure subscription

An Azure subscription has a trust relationship with Azure Active Directory (Azure AD). 
A subscription trusts Azure AD to authenticate users, services, and devices.
Multiple subscriptions can trust the same Azure AD directory. Each subscription can only trust a single directory.



#### Create a create service principals

An Azure service principal is an identity created for applications, hosted services, and automated tools to access Azure resources. 
This access is restricted by the roles assigned to the service principal, giving you control over which resources can be accessed and 
at which level. 

```
az ad sp create-for-rbac --skip-assignment
```

response: with appId and password
```json

{
  "appId": "559513bd-0c19-4c1a-87cd-851a26afd5fc",
  "displayName": "azure-cli-2018-09-25-21-10-19",
  "name": "http://azure-cli-2018-09-25-21-10-19",
  "password": "e763725a-5eee-40e8-a466-dc88d980f415",
  "tenant": "72f988bf-86f1-41af-91ab-2d7cd011db48"
}

```

#### Example of a service principals for us:

pass: D67OyqNwxQwQZl/WtWy9Zdk0PqvpgES7dnh0kpAy/2A=
Application ID: 8b373a77-1aae-49f4-80bc-f77b9b1ad871

This application id has Contributor privileges on the “Tesco Sandpit Early Access” subscription.
It can be used by multiple teams / team members for pipelines in this subscription as and where required.


#### Azure Key Vault (AKV)

Azure Key Vault (AKV) in the cloud. It offers the benefits of HSM. 
Azure Key Vault is a cloud-hosted management service that allows users to encrypt keys and small secrets by using keys that are protected by hardware security modules (HSMs). 

create a key vault 2) create a secreat 3)  Register an Azure Application and create Keys 4) get client id 
 

For Keys: Create, Import, Get, List, Backup, Restore, Delete, Update, Sign, Verify, Wrap, Unwrap, Encrypt & Decrypt

For Secrets: Create, Update, Get, List, Delete

For Certificates: Create, Update Policy, Contacts, Import, Renewal, Update

