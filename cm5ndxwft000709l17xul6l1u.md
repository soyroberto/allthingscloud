---
title: "How to Save Terraform State in an Azure Storage Account"
seoTitle: "Saving Terraform State in Azure Storage"
seoDescription: "Learn how to save Terraform state in an Azure Storage Account to facilitate team collaboration and version control"
datePublished: Wed Jan 08 2025 04:14:20 GMT+0000 (Coordinated Universal Time)
cuid: cm5ndxwft000709l17xul6l1u
slug: how-to-save-terraform-state-in-an-azure-storage-account
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/1C37UztDU8s/upload/45a9588536d2fe0673a7307810ff7aa7.jpeg
tags: azure, terraform

---

I personally prefer not to do this but some teams do and it's a good way to collaborate and a cheap(est) alternative to using the Terraform Cloud with the intention of allowing a team to build cloud services.

I've only used one storage account per resource group assigned to a Terraform project, I haven't tested storing more than one Terraform project state on the same storage account but different container. I'd presume it's doable.

## Terraform Backend

It starts with the terraform block:

`terraform {`

`}`

This blocks allows the configuration of Terraform's backend among many others not covered here:

**backend**. Specifically refers to the Terraform State. The state is the persistent data keeping track the resources Terraform manages. **Note**: **The default backend is always local.**

## Some of the Cloud supported backends:

* **AWS S3**
    
* **Azure Storage Account (blob storage)**
    
* **Google Cloud Storage**
    

I didn't change anything on the **main.tf** where the logic for the password generator is. I added the ***backend.tf*** file:

```bash
terraform {
  backend "azurerm" {
    resource_group_name  = "RGTFSTAUPWD"       # Resource group of the storage account
    storage_account_name = "saauetfpwd"      # Name of the storage account
    container_name       = "terraform-state"       # Name of the container
    key                  = "terraform.tfstate"     # Name of the state file
  }
}
```

As a good practice enable versioning on the the blob as this will allow to roll back in case required or review the previews states (passwords):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736308806969/a15b3e66-2644-4a1c-9292-0426ff5b5bd8.png align="center")

# Running the password generator:

On the command line:

| `terraform apply -auto-approve -var length=10; terraform output espassword` | **Will generate a 10 character password:** $CZ0QFn3bc |
| --- | --- |
| `terraform apply -auto-approve -var length=255; terraform output espassword` | **Will generate a 255 character password (why not)**: 7MM2Z1m#jlfzw{Oj1lq1VQJjE&XkXD?F6wUH-O)&YXyZTHTq&lt;=l{ZkRT?-W}Zpea9Sq({b#9\_U=k62{*aUfeBfd*XR-V&r9N)g+3-dvoLG&B3\*AE+U(V8Xt1Jj)cw-MS=!KMB\_c?#\]ME!(zGZt8xo0j{A&lt;usUYrHHvNZ0vSJOW!&gt;k=csrtseWoXng&gt;IV%\_MrAZBv\[#}ag-LG:tBpB)6pZ\[%BV\_5+(zofSmCr&gt;MutoV4XEKB\[2OL\[b(rXm9bH\]gC |

## Looking at the versions on the Azure portal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736309407713/a69c794d-6785-457b-833e-b472d0c0c475.png align="center")

## The 10 character password:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736309423136/a3da9b9c-df0b-4be6-9b44-94e9eaca180d.png align="center")

## The 255 password:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736309481212/b6185441-96f8-46b4-8ec5-656e4a88aade.png align="center")

## Pre-requisites:

* As a very minimum you'd require an Azure account (obviously)
    
* Being logged into the Azure subscription when running this code