---
title: "Spoke to Spoke via 2 Azure Firewalls"
datePublished: Thu Jul 18 2024 01:12:07 GMT+0000 (Coordinated Universal Time)
cuid: clyqktc82000408kz8nnaea14
slug: spoke-to-spoke-via-2-azure-firewalls
tags: azure, azuresecurity, azurenetworking

---

Connecting two spokes on two different subscriptions with 2 Azure firewalls on each side. See diagram:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721264879409/90a41ab2-5a6a-42e9-9394-94858d5d18e2.png align="center")

**03/02/25** Planning to write the Terraform modules for this, don't think i'll deploy an azure firewall in the subscription given the cost.

**References**:

* [https://learn.microsoft.com/en-us/azure/firewall/firewall-multi-hub-spoke#routing-on-the-spoke-subnets](https://learn.microsoft.com/en-us/azure/firewall/firewall-multi-hub-spoke#routing-on-the-spoke-subnets)
    
* [https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview#system-routes](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview#system-routes)
    
* [https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections)
    
* [https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections](https://learn.microsoft.com/en-us/azure/load-balancer/load-balancer-outbound-connections)