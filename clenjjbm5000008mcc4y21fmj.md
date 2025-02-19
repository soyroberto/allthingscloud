---
title: "Understanding Azure Reserved Instances"
datePublished: Tue Feb 28 2023 00:58:54 GMT+0000 (Coordinated Universal Time)
cuid: clenjjbm5000008mcc4y21fmj
slug: understanding-azure-reserved-instances
tags: azure, azure-vm-instances

---

![](https://irwiag.bn.files.1drv.com/y4mZMbbrZnIHxvrGzfj-g729wCVZYktkaUvdV5wLrp1B50q9W-A3XCa2j308-XRjxIqqEG0aMVtrDr4L6R2IhlWxcmkUzX-uwd4AwY-ohjnSUCNpexDoVzekMaLC-nMeKYSNL8VQaep0tS8AG4d_atID23DfkyBMXG27hgLtOixorobhf3xXcgEzNqoEZ6TvQdE4qtRv-ZyjdUyGtWduxRjlg?width=1024&height=670&cropmode=none align="left")

If you are consuming cloud resources you're probably facing some challenges such as cost management, optimization and confidence on how spending is happening. Have you ever faced any surprising cost at the end of the month?

Perhaps someone forgot to delete a 24 Core, 56 GB of RAM high performance VM?

Azure has made available **Reserved Instances**, its fundamental principle is to save money over a period of time by paying upfront.  You **can pay 1 or 3 years in advance**. The savings go from 40% to 70% depending on the size of the VM selected.

There are two types of subscription to make use of Reserved Instances:

* The production type available as part of the Enterprise Agreement
    
* The Pay as you Go
    

* Make One Single up-front payment
    
*  Select 1 or 3 year terms
    
* Reserve Virtual Machines in advance
    
* Save around 70% over on-demand pricing
    
* If the VM(s) run Windows Server you can save around 80% with hybrid use benefit
    
* Have flexibility to modify
    
* Have a simple purchase experience
    
* Assign at the Enrolment level or subscription level
    

## A practical Example

Let's say you need a horsepower VM: 4 CPUs plus 28 GB of RAM running 24x7 on Windows, let's see how much it costs:

\[caption id="" align="aligncenter" width="566"\]

![](https://vskwdq.bn.files.1drv.com/y4m9HtVXw-3puptDK3yEHaNrZY2T5X4Q4lgy5QDt2xZEO7X5PC2n5mNn6-TR2Ncva-ZY2ALquscQZiKPl4tdbXVbcdt4U8yYkofgDBAE3HbkXSvKHuWD_uNIaEB25MvsCvJ8IgdHYqCbAtLdFLSYgfGWz46yW0cCrURyo8RdZMqtB9WD9KKNJhyhiHaxbBqxh-YG2kD9u2U57pS3jz6C89IUA?width=566&height=132&cropmode=none align="left")

A D12 V2 VM running Windows Server 2016\*. This prices will vary according to your licensing.\[/caption\]

![](https://lc5oig.bn.files.1drv.com/y4mdOtCMf6Ozv5d2uO28EwDvCSuq9YacIlU-LWv0pJ68x-2f4zDdJmFB-wU4Hqg5GKkMuNA0LbbYX5v0z7_4aekMvNBEKpgvKGJCuEzwnS6dg_WfH6OwNok7WrMRgXzWg4MgsCD54SUiopFjgKrVj3ktwMjWgPXTqWCsyrGuyBQ0oD8WxgVBRPkxp0JvfFihl2hFhgrxnnYZDtVsFFA8hEV9Q?width=1422&height=474&cropmode=none align="left")

## How to Purchase

**Pay-as-you-Go**

![](https://memnxq.bn.files.1drv.com/y4mQiNKMo6qfW_rHMMEr5M8_aZLmIDYODNTnPBIEJv0gJTx3xrny_INgZjP6W9WUshd1LYxSX-evmqqHJJK0abgdHvC5C853uu126R12XxZ_CLnSE0zUDr_8hAxhPAT89_tiPr-QGfKsw1sDgd6SpcK7WgAtJwn2azpR4JMKVUzIoQ6ZJw1_70dhP3b8VWh3h2vGkehx3VpTGNo2D8UI0ZEbw?width=1880&height=1205&cropmode=none align="left")

In the Azure portal do: **Create a Resource** - Type **Reserved Instances** and Select **Create**

Then let's just fill the blanks. This first example is for 1 Year

![](https://yz7vpw.bn.files.1drv.com/y4mfYFd0HYNjSi4LyPBOMrN9_xD-4SV1yCyuKY5CKGMvHNybRx0Sr4YN3iukg1TX4vlvSerKsmGg3DM_4C3_PdhOpgwW9SlKvjuO941wdREpr3odNz5Vsu330A_I1hetn4lVmso-TEWAbAR1-JPM9I4-hXkfVFOIf9rBWUWQuoWIp7yevOJStvrLdXtmmPWhI7XIvqtLQq6xanZPbNxu8e-nQ?width=1740&height=990&cropmode=none align="left")

## 1 Year

![](https://h0dgxw.bn.files.1drv.com/y4mBqQ4ipdizURgM-OuGmZY35S-C9-jcdLrtNIXHSjfjs-h40o7uFNRHnkegWb9_W3z2iu-hHlcM4lnvF3tKBpeYkSjg8JBWIChWuhjoWVUTN2Hmv3fqw-3Qy_0ZIOMxqHnNPGBITF1FPQI3suhjJNjqzjNxpihbVluKhSaWKi7TpAw44ACzqkD2IFncP-VrJh59rd77ZWbgLPgNy_FxJVvCw?width=1174&height=718&cropmode=none align="left")

**$3,124 Australian Dollars (AUD)$2,207.75 USD**

## 3 Years

![](https://7ms4jq.bn.files.1drv.com/y4meA8DHXa1izrkT0YOQUuUSglATDDBkvtyvWRqdewipzhqecMtBbMjfDYg-ksKLd-H7pHHSfAbtjcej-AAIPP9hFMbwnLjLts6SkjCGRicwGek8FsXgksuiccb2e74VIGgMzwZwEYJJvz9JAo5DAuYIUOVj5izkwBfH4tN6YffWa2H_RZI9iGRY-XdtnaD8J667i_3IUS2JaUWOS0qQmh0TA?width=1178&height=701&cropmode=none align="left")

**$6,173 Australian Dollars (AUD) equivalent to $4,361.35 USD**

Things to understand:

* **Name**: VM Name
    
* **Subscription**: Where will this instances be assigned
    
* **Scope**: Will this instance be shared among multiple subscriptions? In an Enterprise Agreement (EA) it's quite common to have multiple subscriptions
    
* **Region**: In which of the Azure datacenters this instance will exist
    
* **Optimize For**:
    
    * Instance size flexibility will apply the reservation discount to other VMs in the same VM size group
        
    * Capacity priority reserves data center capacity for your deployments, offering additional confidence in your ability to launch the VM instances when you need them
        

You will have a view of the cost of the reservation before executing it. Then all you have to do is select Purchase and that's it.

**The reservation term will begin as soon as payment is processed.**

Once you've done it your next option is ***View this Reservation*** to see the status of your purchase.

* If later on you decide to cancel or exchange at any time, you have the option to do it in the overview section of your reservation.
    
* If you need to cancel **there may be a 12% early termination fee**, the refund you'd receive is the remaining pro-rated balance minus the early termination fee.
    
* If you need to do an exchange you can do it to change to another region, VM size group or term. It has to be something equal or greater value, then the new 1 or 3 year term starts from when you create the new reservation.
    

## **How it is applied?**

Once you've bought it, the reservation discount will automatically apply to VMs that match the size and quantity.

* You don’t have to change anything in your deployment
    
* You don’t have to pick the OS either, just purchase the amount of instances you require.
    

The VM usage is separate from the RI (Reserved Instances) inventory, on the backend the Microsoft systems are doing the match-making to ensure the usage is matched automatically to the right reservation.

For VMs that may not run the full hour, the reservation will be filled from other VMs not using a reservation, including concurrently running VMs

The diagram below clarifies how the Reserved VM Instance is applied

\[caption id="" align="aligncenter" width="1014"\]

![Screenshot of one applied reservation and two matching VM instances](https://docs.microsoft.com/en-us/azure/billing/media/billing-reserved-vm-instance-application/billing-reserved-vm-instance-application.png align="left")

**Source**: [https://docs.microsoft.com/en-us/azure/billing/billing-understand-vm-reservation-charges\[/caption\]](https://docs.microsoft.com/en-us/azure/billing/billing-understand-vm-reservation-charges[/caption])

To understand restrictions and clarify more you can visit the [Azure Reserved VM Instances offering](https://azure.microsoft.com/en-us/pricing/reserved-vm-instances/) page, the FAQ at the end clarifies about restrictions in VM sizes. 

If you want to see an example of how the usage is presented across different means like the CSV file in your billing and EA Portal you can check this documents:

[Understand Azure reservation usage for your Pay-As-You-Go subscription](https://docs.microsoft.com/en-us/azure/billing/billing-understand-reserved-instance-usage)

[Understand Azure reservation usage for your Enterprise enrolment](https://docs.microsoft.com/en-us/azure/billing/billing-understand-reserved-instance-usage-ea#usage-summary-page-in-enterprise-portal)

And this tutorial explains with detail how you can manage your Reserved Instances through [Azure Cost Management](https://azure.microsoft.com/en-us/services/cost-management/)

[Tutorial: Optimize reserved instances](https://docs.microsoft.com/en-us/azure/cost-management/tutorial-optimize-reserved-instances)

Now, go and save some money!

Enjoy!

[gaby@allthingscloud.info](mailto:gaby@allthingscloud.info)