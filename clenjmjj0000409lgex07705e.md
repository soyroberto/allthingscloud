---
title: "Converting an Office 365 Domain from Federated to Managed"
datePublished: Tue Feb 28 2023 01:01:25 GMT+0000 (Coordinated Universal Time)
cuid: clenjmjj0000409lgex07705e
slug: converting-an-office-365-domain-from-federated-to-managed
tags: office365

---

## Background

![](https://0xkx1g.bn.files.1drv.com/y4my7M4Y9geoTaHPs0o8XxBSrKfuYSOmS2FLziaVpleDq6zSl6Msgo_cIewyiDDY6aKRJB6yZXxjqUGGIaLxYYvQtknuSYSUE7_kob2CMyaVDptmTJx4RS0zCm4Y44xNf7axgwnx0-30JMWbGE2lyoce2zq4E0GyAMqvLUeEBjIvIHPNQqUA-NmIy4FDlU9TToYu0_4Q0SbGqqaM04fdrDKsg?width=1920&height=1080&cropmode=none align="left")

[***allthingscloud.info***](http://allthingscloud.info)

One day I needed to implement identity synchronization and federation. So, I installed  dirsync, plus ADFS. All worked fine and as expected.

I deleted all those instances, the Domain Contoller, the Exchange Mailbox Role and the ADFS.

What I never did was convert back the [***allthingscloud.info***](http://allthingscloud.info) domain from Federated to Managed in 365.

I thought it was going to be much more complex considering the ADFS doesn't exist anymore, but no.

## Super straightforward

1. Install the required Modules
    
    1. ```plaintext
        Install-Module -Name AzureAD
        ```
        
    2. ```plaintext
        Connect-AzureAD
        ```
        
2. Install the [Microsoft Online Services Sign-In](https://www.microsoft.com/en-us/download/details.aspx?id=41950) Assistant
    
3. Install the MSonline Module
    
    1. ```plaintext
        Install-Module MSOnline
        ```
        
4. Login to 365 and the following command:
    
    1. ```plaintext
        Set-MsolDomainAuthentication -DomainName allthingscloud.info -Authentication managed
        ```
        

\[caption id="" align="aligncenter" width="2272"\]

![](https://cy7xca.bn.files.1drv.com/y4m9qtyVvnuhIWLskBfJQ4RzTBIZW27ZiZUmzzkAb5p7wvI5__q2FRMcJ8cmRV30P-AeBiGL1DBwxUm-ic9pTnfI2NWe2A2p2YfxBBS9Wq82UyBmv4fb1tZgykZ_fOri6o0aWCAUmSlNfi-GzryH03bdtz33vzSgK8wRbArfuQqj-RG0t-_CtxrmW2YNbaYQIr3sGIbODO05LQWWohtS4XATw?width=2272&height=566&cropmode=none align="left")

Converted to Managed\[/caption\]

Roberto