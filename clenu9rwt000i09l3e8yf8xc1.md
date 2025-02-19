---
title: "Publishing Dynamics CRM via the Azure AD Application Platform"
datePublished: Tue Feb 28 2023 05:59:25 GMT+0000 (Coordinated Universal Time)
cuid: clenu9rwt000i09l3e8yf8xc1
slug: publishing-dynamics-crm-via-the-azure-ad-application-platform
tags: azure

---

# **What is it?**

**AAD-APAAD Connect**

Pre requisites

1. **An Azure Active Directory Premium Edition.** This is what allows you to Single Sign-on (SSO) to on premise web applications. It’s also available in the Basic Edition; Premium is the one I tested.    ***Source:*** [***https://msdn.microsoft.com/en-us/library/azure/dn532272.aspx***](https://msdn.microsoft.com/en-us/library/azure/dn532272.aspx)
    
2. **Sync enabled and working to your Azure AD Tenant**. In many cases users will first enable the synchronization of user for 365 services such as Mail and/or SharePoint, that’s fine, that Directory lives in Azure and can be used for this.
    
3. **An on premise web application you need to publish to the outside**. It is an absolute ***must*** that the application you’re going to publish and want to provide SSO has Windows Authentication Enabled in IIS otherwise it will not work.
    
4. **Enable the Application Proxy in the Azure Premium Subscription**
    
5. **Install the Application Proxy Connector in a domain joined computer**. I installed the connector in the same server where the application was running.
    
6. **Assign users to the Application**. The users assigned must be the ones synchronized; user locally created in the Azure AD will not be able to connect.
    

### **How does it work?**

![](https://docs.microsoft.com/en-us/azure/active-directory/media/active-directory-application-proxy-sso-using-kcd/authdiagram.png align="left")

**How the Azure App Proxy Works***Source of image:* [*https://msdn.microsoft.com/en-us/library/azure/dn879065.aspx*](https://msdn.microsoft.com/en-us/library/azure/dn879065.aspx)

1. The user enters the external URL assigned when the application was published. In my test scenario the published application was the Microsoft Dynamics 2015.
    
2. Application Proxy redirects the request to Azure AD authentication services to pre-authenticate. This initial authentication happens with the users that DirSync provisioned from the internal Active Directory.
    
3. At this point, Azure AD applies any applicable authentication and authorization policies, such as multifactor authentication. If the user is validated, Azure AD creates a token and sends it to the user. This is the token that will be validated via Kerberos.
    
4. The user passes the token to Application Proxy, this happens in the on premise network
    
5. Application Proxy validates the token and retrieves the **User Principal Name** (***UPN***) from it; and then sends the request, the UPN, and the **Service Principal Name** (***SPN***) to the Connector through a dually authenticated secure channel.These two things are fundamental, **the UPN must match** the user name field in the Azure Active Directory and the **SPN must** be added to the endpoint host, in this scenario where the Azure Application Proxy is installed. **Note**: *Microsoft has declared that it would also provide support in the future for cases where UPN in the cloud doesn’t match UPN* [*on-prem.*It](http://on-prem.It)’s very common that the internal AD domain doesn’t match the outside domain. The internal domain in general is not a routable domain in the Internet while the domain in Office 365 must be. For this reason the routable domain has to be added into the internal forest, using the Domains and Trust console.
    
6. The Connector performs KCD negotiation with the on premise AD, impersonating the user to get a Kerberos token to the application.
    
7. Active Directory sends the Kerberos token for the application to the Connector.
    
8. The Connector sends the original request to the application server, using the Kerberos token it received from AD. The application being the Dynamics CRM front end.
    

### **Step by Step**

1. In case you don’t have the directory enabled you can trial it straight from the Azure interface:
    

![](https://wdpj6w.bn1304.livefilestore.com/y4mXJP-WqYWmhw-oUzRXyf1kkBisJ3YZ3PzhQeQSLM7ELVip49zSBShP3FXHkMb_fE8YYqQvHIaKuiAqtu7NHYxbG6K4HN37tGNa4GbeKSc7ex2yYH_kaIRgNtDHaQ_FIV2CUa1340-mVE0TIu3YY23IZjgps20bB_bWT0D87rIurVQcx7JBt2UKvAScYOspdOmEV9M57t7oc-FS1bg1f7iDg?width=468&height=273&cropmode=none align="left")

The trial lasts 90 days, time enough to give it a go.

1. Enable the Azure Application Proxy. Go to your Azure AD -&gt; **Configure** -&gt; and Scroll down to -&gt; **application proxy** as shown below
    

![](https://wdps6w.bn1304.livefilestore.com/y4mtOnPWLW5X1lixXe6F0oTPJeO4VVh0sdSfQaoby2_rpq1bG_TFdrVAL-uPzoFCu1Rr_qIGoL2IBR8TgCjgtCzi_-kWwRNd_QE-dp7Lafxz0_xYEGAcRw0ShmEfbMYcoklFzqfIZ1oaamgVRX5c4HoMldyafXVLFuwQ87CwCcSryoSpuLcA1_W850yw3qVgcTARcdK5Pv5oSfDdnM39lFt5Q?width=468&height=126&cropmode=none align="left")

1. Publish and configure the application from Azure. Go to your subscription, select the Directory component -&gt; click on applications -&gt; Click on ADD
    

![](https://xnpk6w.bn1304.livefilestore.com/y4mGpURfOvTqJfqrM1nk1dp965-ZLys4dPv9tuO42l8chxBN79nCE-1NxpdAYEj74HfCirOmGJajVqyN09qtrH1prxJHYtmowCjFVTCS8ol_LkUmLylHCPPaAh6h2UcVXf_mOgSiacER1ajfGUdEkyKIV0zmm4QTC1dlnKnMuuvofu5KMnwTIElzdu3xdNl_p6VGk7t6w14vXmv1CRsSeYKaA?width=468&height=294&cropmode=none align="left")

3.1 Select the option marked below, an application to be published from the outside

![](https://vppa1w.bn1304.livefilestore.com/y4mqH_JBGa9yrSycXNMW-Mal1ArV9SedT3in6FbH8XyQaDLeKsL69sL06Cu0YQSFqTYGF9Zo8lZsG9etQTOsb_A9zwRr0zZkZ6nm4I7EXdcDuwlwWJoI0jFviNDzSW1KNHO40etWcvBzZVsrtjg2W_C2815aWJIlbV2oz3l3XDmTJSCXsqCuGDqlS5KcHzUFqNXO5T9BjcETKSmcFaTRfB10w?width=1004&height=522&cropmode=none align="left")

3.2 Give the application a meaningful name and click Next

![](https://wdph6w.bn1304.livefilestore.com/y4mBLVx1a6HlUAvCNxQiNI-V1ymqgxMtayPr-DMUN7h2RoDs3-TBEdCpPqKvXt9sdcpWLT156YDdyY1G9WoXj_6TGLD3qZLE54qzWcb7QPr9ejyg0deJfjUcZjGdqbd7D5SetHbUJO-0fbE32y_gdJSPYSJLGX0MXqQ9LBEVUVFD26ZURZVs092iwx1eJx4BsZOpp3_t396Jka6244BQpNu6g?width=468&height=334&cropmode=none align="left")

3.3 Add the application properties in the next window

![](https://xnpj6w.bn1304.livefilestore.com/y4m1SFjwFaYYpAenXSWtN0slXzUVgOjgmmCR1rcOIcHwMBtESrJoHDYSwIuzkNJohQOowg7Xadhle8n6MoNiQSfx76Unmo7vpPh9iJiKBKZQLb4R9PzwjhmXQpHSWUzHw_wmimglCGHeAb9Uj2cY4lb0ZKU2ax3EczdwhSKtKAsmBXFtnr01aktn3k7J2TCQ58tCM3eRoiWNdiZse4ZL2vB9Q?width=468&height=335&cropmode=none align="left")

* External URL refers to the published address, accessible from the open Internet
    
* The Pre-authentication method will indicate that user has to login with its Azure AD credentials, this to assure the right permissions to access the application. The pass-through method performs no authentication whatsoever on Azure, hence no Single Sign on with this option.
    
* Internal URL is how your users address the on premise application
    

On the configuration of the application itself, make sure you select the following values:

![](https://wdpm6w.bn1304.livefilestore.com/y4mWcAgCxj5FMYPdCKdGn0Sn278ttxcckL6mbdFxg5xUwIwYAlKSzdj2XeMJcOLza0jOMr8Ob_qYUUbGbsUBe2IqBmm8y-E9AUw5Jrobo3pgbZePKxitwpFRue5BR93Zm8l69vfm7phs6POEUJk0XOF5d3LAv7C6O1SNAMtmNqHyMRgtD-gGWUIMGo9D-rLpADECEu7RkI8Z37j8xC5j-pF6g?width=468&height=291&cropmode=none align="left")

Again:

* Name of the application
    
* The external URL will be automatically generated
    
* Pre-authentication set to Azure Active Directory
    
* When the authentication is set to Azure AD the external URL will always be HTTPS
    
* Internal URL can be HTTP or HTTPS. I only tested with HTTPS. I added a certificate to the IIS where the CRM front end is published
    

![](https://wdpl6w.bn1304.livefilestore.com/y4mtRCkb0l2ycWJJSXsH6At_IDFK09WX2kSZ97b6fBvnsLDCsI5AZiVQd7djI3tF_Z3Y68azLlAq1f4CX_7VBwlP7LYtjG25DwHkx7WY1buhQu8D5klg8a88AEa_ORU83tBn02ucLfs5XIlCi6R1ZQBPCy6Q8GFVH-7B-5z8Un32w0FDny3BAAWl3veM1eY90KNThBVXVVtwJ8J8h5kWClSNQ?width=468&height=224&cropmode=none align="left")

This is the continuation of the previous screenshot.

* Select Integrated Windows Authentication
    
* Add the SPN; be aware that the SPN must match the hostname of the external URL, only the hostname not the FQDN (Fully Qualified Domain Name).
    
* Click the Save Button
    

### **Configuration on Premise**

1. Install and Register the Azure Proxy component in the CRM Front end
    
2. Add the Service Principal Name to the CRM front end
    
3. Alternatively add the certificate to the IIS (not included in this document)
    

1. Install the Azure proxy Component
    

![](https://wdpi6w.bn1304.livefilestore.com/y4mZs64hn0Vx-N1o7creNHeLDHX7J5srFK5RFo0oLRSCucXl7NIXvZe8JwbUKOvU4OysBt_22jrgB6Msapa_KSM0rUezC4IqJPeaRi7gRLii3pkzlYHdII9_HO2Jtwoe993sfCRMp0nn3qNU3DIIBJEUdcX9eazAKu3qzb4NBP0szs60G2D-gp91dJfpbtAeZ2TCPF3npXtersZuI3mU46Wow?width=468&height=405&cropmode=none align="left")

Download the connector and from the CRM front end, run the installation as administrator. When you run the installation you’ll be requested to register it as follow:

![](https://wdpk6w.bn1304.livefilestore.com/y4me7Il-bSvNVJ2KMqSm-bKCk8Qu00t7Xn34FvU0V_LW-nWUCoOKu7fDVmUzsZQMVbYUNbAOdRlwCvOdXtxZm5muqeIHUtc4JGrlPXYRUFarjwux-XENMSfDvfrsYEB79YViO5Ql_U3eQ7S26QZwuFuhMBe-Go-2xMHY4yvgMTaorUmM5weCKXP90B44XGeSXI2sjtOKd-k7-J35cJ0klvRhg?width=468&height=303&cropmode=none align="left")

The account I used had two characteristics:

* It was a synchronized account from the on premise AD; I tested with an Azure AD only account with no success.
    
* The account has to be Global admin on the Azure AD only, it can be a regular account in the local AD
    
* Make sure you do not use the same account to register more than 1 connector, I made this mistake and it cost me hours or debugging. One account registers one application only
    

![](https://a2iadw.bn1304.livefilestore.com/y4mVe7y3KKj3ZON-LrX6DWCM4727G0uKFE3ZSyiLknTeqHHBC56OWWh4YfNsjfn7WaEol6850ix8_LyCM4-bR8YU7rWPKdYYO_04f2Pld85z18qt5_2VfZmgIvqG2HHzzpOnWkZrYzxiTEANCBofeN_zs-tOvLTibn_Dug3PdHT-3iXulj73D4oK3504rxMq2UzaJ94kbmmOwGGBd-Np-zlkA?width=670&height=626&cropmode=none align="left")

Remember SPN syntax is: **SERVICE/name**, in this case it’d be:

* HTTP/msdyncrm-allthingscloud
    
* HTTP/msdyncrm-allthingscloud.msappproxy.net
    

![](https://qbrvsq.bn1304.livefilestore.com/y4m5L-axDP9k_KeLvrYl1iDyhw2Z2zbZzJrMDnND_FK0HBjuZvKnYIRMS0dsSFWIlNHKgR_WtxQZP7ZER_nzt3BI7wldWryUKKx78CxB7fcoNWAlnmZ1ynPA35d6VXnlJyoMlexl3SPslk31fDJPSWeDfDVdwtQnVUs3JNkq_iu0j6fMl8JXBGmwFtXkKR1ykH7PAckrPE3cUJD45aSqyTzeQ?width=596&height=636&cropmode=none align="left")

1. Before testing the connection, remember to assign users to the application otherwise, they won’t be able to connect.
    

![](https://ntbbgq.bn1304.livefilestore.com/y4mtbsO8KwXbDIC36WL6fc84es8pUJf6NV-BrmAO2-7AGeVqkNV5XQ_LkPZOpcNCWQhneLy3yGVaunbabWN2K7JhHhGH6cidxRddflf3_XSmCvRX33Af6Ocl-c2zq98sMW-K3AWpqCdnepo_6_LZZA7Mmdj4wR9S-Epy9WeqboymmjvsD-cbhsH-d6ObNlPA3JW-olwrN5yTjb42X4eMlI1eg?width=1018&height=802&cropmode=none align="left")

1. Test
    

Type the external URL you were assigned when you created the Application Proxy. Type the username you gave permissions to in the previous step, type its password

![](https://wtps6w.bn1304.livefilestore.com/y4mTDRBpx3NnXwvU_nexlx4xCz41LEpKIh-HqdKIi3asJss_u4oIjO_CZQ6ELulsyZ_y_WXicTrZolWsBnzCW7q8d8JNDy4kVgetd7dajhyC4hLNq9P30j8j8ORmqn-Nnm5OIVWMOk0cKDHyAeek-JDwiHOXq9gfKeoCAu8H39DDiPyjKvg0tyAZmdYkYa10hs4z3bxgjNFkDy_SHYFAuF8lw?width=467&height=282&cropmode=none align="left")

You should see the application as follows, which is the Dynamics 2015 site:

![](https://wdpr6w.bn1304.livefilestore.com/y4msd9tiUi_3GftOfJ18SWqcV1DBq4Xv2nTWU5WaBXOqnTN1M2g7efabFf_ZWFGqDR3BT2Bs0ienUfT11mx2cEffZp1kRvA9BnfoVfbvNMl5BXRNbTMFJlVMiBMwQaJ5oBs_9l_AdczCsZzgOjAr8yRIRKKlBywCp1oFF1ZX5K227NPgRAiyt-3LS_q0YV_FmE6sKwRldXHQ_QWID8PwWSYPw?width=467&height=283&cropmode=none align="left")

And that covers the configuration of the Dynamics CRM 2015 using the Azure Web Application Proxy.

Roberto