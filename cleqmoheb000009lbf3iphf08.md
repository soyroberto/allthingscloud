---
title: "Private Link vs Private Endpoint"
datePublished: Thu Mar 02 2023 04:50:13 GMT+0000 (Coordinated Universal Time)
cuid: cleqmoheb000009lbf3iphf08
slug: private-link-vs-private-endpoint
tags: azure, cloud-computing, azureknowledge

---

**Private Endpoint: It brings the service into your virtual network.** It's a network interface created that uses a private IP address from your virtual network. The service could be almost any available in Azure:

* Azure Storage
    
* Azure Cosmos DB
    
* Azure SQL Database
    

The **private endpoint must be deployed in the same region and subscription as the virtual network.**

**Private Link** – The umbrella Azure service under which you can make your PaaS resources available privately on a virtual network.

![Diagram of Azure private link service.](https://learn.microsoft.com/en-us/azure/private-link/media/private-link-service-overview/private-link-service-workflow.png align="left")