---
title: "Message="The service principal with appId '2565bd9d-da50-47d4-8b85-4c97f669dc36' could not be found in the Azure Active Directory tenant. Please retry"
datePublished: Thu Apr 13 2023 02:22:08 GMT+0000 (Coordinated Universal Time)
cuid: clgehvu4p000009mp3yrle7zm
slug: messagethe-service-principal-with-appid-2565bd9d-da50-47d4-8b85-4c97f669dc36-could-not-be-found-in-the-azure-active-directory-tenant-please-retry
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Vr_yaCXzLP0/upload/e9cff39a9020075936827569416d33e0.jpeg
tags: azure, powershell, azuread

---

When creating a Domain Service instance in Azure with a Terraform template I ran into this issue, I fixed it by running the following commands:

on the Azure command line - powershell in the actual Azure portal, I tried using regular PowerShell with one set of annoying errors:

* <mark>You must call the Connect-AzureAD cmdlet before calling any other cmdlets.&nbsp;</mark> 
    
*  <mark>&nbsp;New-AzureAdServicePrincipal : Error occurred while executing NewServicePrincipal</mark>
    

and the commands lines I was running were:

* **Connect-AzureAD -AccountId &lt;my account&gt;**
    
* **Select-AzSubscription -Subscription 'subname'**
    
* **New-AzureAdServicePrincipal -AppId "2565bd9d-da50-47d4-8b85-4c97f669dc36"** 
    

**The fix:**

1. Connect-AzureAD -accountid &lt;the account id&gt;
    
2. New-AzureAdServicePrincipal **\-AppId "2565bd9d-da50-47d4-8b85-4c97f669dc36"** 
    

![UPN created](https://cdn.hashnode.com/res/hashnode/image/upload/v1681352412199/901f87e2-6a3c-4355-abd1-8810bfa4a40c.png align="center")