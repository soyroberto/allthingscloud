---
title: "Running cost effective Virtual Machines in the Cloud"
datePublished: Tue Feb 28 2023 00:55:38 GMT+0000 (Coordinated Universal Time)
cuid: clenjf46z000009lggra6e7kn
slug: running-cost-effective-virtual-machines-in-the-cloud
tags: azure

---

![](https://yqz2hw.bn.files.1drv.com/y4mRMHApHilN5fdUUwTRFsrPiDRXu4-de9TMYUSYIBJ_8dDazC2o6ny_GIlKLPgRlT3zHCW5fvfILrih5CpajZmgAlnbvz_wKmspGveEgb5TtEZU_ZeZv3iRgpIbArmdVVpEuJ_zWhKgk1X0O_qgQFwjLK0fmagXKG4d2pzNGOzQTRnBoV_Dhm0UwwdtVLuQAwsEWBNVOTiujdN31id0wdauw?width=225&height=225&cropmode=none align="left")

The logic makes sense, Cloud Providers have excess capacity and instead of having it there idle generating heat and getting depreciated better use it and sell at cheap(er) price.

Customers gain because they pay less and can use them for lower-priority tasks or Hyper performance batch processing, any service that doesn't require continuous running.

Preemptive Virtual Machines are excess Compute Engine capacity and their [availability](https://allthingscloud.info/glossary/availability-2/) varies. A VM of this type can be terminated by the Cloud vendor at any time if it requires access to the underlying resources for other tasks.

## In Google Cloud

* The Compute Engine always terminates instances of this type after they run 24 hours.
    
* They might not always be available for provisioning
    
* These types of instances are not covered by the Google Cloud SLA
    
* These types of instances are not available in the Free-Tier
    

## In Azure

There's a service in the preview for Scalesets using Low-priority VMs:

The amount of available unutilized capacity can vary based on size, region, time of day, and more. **Azure will allocate the VMs if there is capacity available**, but there is no SLA for these VMs. A low-priority scale set is deployed in a single fault domain and offers no high availability guarantee.

## In AWS

Amazon can interrupt your Spot Instance when the Spot price exceeds your maximum price, when the demand for Spot Instances rises, or when the supply of Spot Instances decreases. When Amazon interrupts a Spot Instance, it provides an interruption notice, which gives the instance a two-minute warning before Amazon interrupts it.

Roberto

**Sources**

* [https://docs.microsoft.com/en-us/azure/batch/batch-low-pri-vms](https://docs.microsoft.com/en-us/azure/batch/batch-low-pri-vms)
    
* [https://cloud.google.com/compute/docs/instances/preemptible](https://cloud.google.com/compute/docs/instances/preemptible)
    
* [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-spot-instances-work.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-spot-instances-work.html)