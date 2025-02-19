---
title: "Let's Encrypt Certificates on the Azure Application Gateway"
datePublished: Tue Feb 28 2023 01:00:04 GMT+0000 (Coordinated Universal Time)
cuid: clenjkt0f000309lgbkrtapcg
slug: lets-encrypt-certificates-on-the-azure-application-gateway
tags: azure, letsencrypt

---

## The Security Principles

> 1. The Web’s trustworthiness has become critical to its success
>     
> 2. Furthermore, confidentiality -- while arguably not always strictly necessary -- is often needed
>     
> 3. The Web platform should be designed to **actively prefer secure communication**
>     
> 4. **Barriers to adopting "https://" should be removed** where feasible
>     
> 5. The **end-to-end nature of TLS encryption must not be compromised** on the Web
>     
> 6. Educating and interacting with users regarding security is notoriously difficult. 🙄 (*Emoticon mine*)
>     
> 7. Cryptography will not solve all security problems in the Web platform
>     

[https://www.w3.org/2001/tag/doc/web-https](https://www.w3.org/2001/tag/doc/web-https)

There's a massive push in the industry to make all Websites on the Public Web secure. The latest Chrome version websites as non-secure if served over HTTP, see below:

\[caption id="" align="aligncenter" width="1920"\]

![](https://nkwmiw.bn.files.1drv.com/y4mON0y4MmEWcYTu_SRG3Qd2Iv1NNVeVUCqKnH523xawf6S9TUsGJp2Ya1lvlshrRRjVHqhLsHJ-eTCK1U7Xa1yVBQnmLMQ58Ook9xyd4eGAPmxa0Memet89HRqBNOFvAiDIg3HRe_SX9wS7qVui59TvlWXY3kRp47tjHrN-jTldINn8D0FAR9WpzfH6Wc1z1GAVHUTeCrAU_6ho7Y2LsiL9Q?width=1920&height=1023&cropmode=none align="left")

None other than the UN delivers content over HTTP, it also does HTTP(s). But still\[/caption\]

## Let's encrypt to the Rescue

![](https://upload.wikimedia.org/wikipedia/en/thumb/0/07/Let%27s_Encrypt.svg/375px-Let%27s_Encrypt.svg.png align="left")

The service aims to provide certificates for **FREE** to anyone. It delivers close t0 **600,000 certificates per day**.

\[caption id="" align="aligncenter" width="940"\]

![](https://ohcnrg.bn.files.1drv.com/y4mPKtGuW4OLOqT0CBsGON4tCbH6f9numIdiFy_SVaQiO_7zhZiLAdfGzWrEouZ2m-RbDj8n9y1UDUrDABZLzjOCPr_sL0XBr-li0Qii8JhRUe6IQF9Xe9j1Cb_IdR5Vpbos7RgHAwhvxCTi3-zyWEeRELcNMZplD2vu3eysNuwM4bxnwFuty2BqS23_9Ig3OLI4nrczkPIMt7AQ-BtNnC8Bw?width=940&height=450&cropmode=none align="left")

Lots of certs issued, daily\[/caption\]

Fantastic, my setup is as follows:

* An IaaS scaleset of 2 VMs runing a website on IIS. These boxes are not publicly accesible
    
* A Web Application Firewall tier (WAF) using the Azure Application Gateway
    

**First**

The not so good news: **It's tricky** and it is like this because only domain validated certificates are issued. This means that the host requesting the certificate must be publicly accesible. Only [domain-validated certificates](https://en.wikipedia.org/wiki/Domain-validated_certificate) are being issued, since they can be fully automated. [Organization Validation](https://en.wikipedia.org/wiki/Organization_Validation_Certificate) and [Extended Validation Certificates](https://en.wikipedia.org/wiki/Extended_Validation_Certificate) are not available.

## How-To

**Having Free Certificates in this configuration**

The elements I used for this lab:

* 1 Windows ScaleSet in Azure with 2 VMs
    
    * I installed the public certificates here on the IIS. Do not map the name on the IIS these can cause connection issues.
        
* A public DNS service. Any service does the job
    
* 1 Linux Box
    
    * I ran the Let's Encrypt Bot from this box and the ***DNS A*** record was pointing to it.
        
    * Once the Certificate was issued, I exported the **.cer** and the **.pfx**
        
* 1 Azure Application Gateway
    
    * Firewall Enabled
        
    * Firewall mode set to Prevention
        
    * Configured as WAF
        
    * Listener configured over HTTPs
        
    * Rule Set OWASP 3.0
        
    * The public (***.cer***) for the back-end and private (***.pfx***) for the front-end certs
        

## How does it look

![](https://cncyzq.bn.files.1drv.com/y4mrE-NEuoR4wCKnEF6-J6pO8iv8tclmgtKZTZOVrEjbhFRoMnBw0W8Y3XmBBZ2TgwYd617GYcygXN_S0OF4QTAJ771kaHU1XDwRZwS4o-U0eNiM0vAG-XG9NnbxIkNOkLr4-bdb17nEsjJwuvpk9Kng6MRaIujOTcL2NpOP9AIrXdWcT0tBRYspRJE4c021jT-llC-ichzRnxVHrm87Gyjyg?width=838&height=455&cropmode=none align="left")

## Conclusion

![](https://by7baa.bn.files.1drv.com/y4mDhHpYCHH8auWiEcKRQJLhqUNw3OBYhKC95yEAx39eOOaXVkLbVcu9INbcu_MAu7d-VCf6jqGR9lW9fNg6ECOEc2wd9AU9OBDdwG_ie7Sys1_e4WAK3ETHSChYbagbSpPMrADJrUUub84oE2JcvuT5V_weRp0_jKqGzEwsGSB_9ujLp0tqPo2MeK61yxKxtG8Tx4h3vluGZaXUuVbEYVvcw?width=1911&height=983&cropmode=none align="left")

It is possible and works perfectly.

Doing some googling there seems to be a less complicated way; which I haven't tried:

[***LeSslCertToAzure***](https://github.com/Nexosis/LeSslCertToAzure) a Powershell module to create a TLS cert and apply it to the Azure App Gateway. Will test it, eventually.

Roberto