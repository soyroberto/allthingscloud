---
title: "Traffic Manager vs Load Balancer in Azure"
datePublished: Tue Feb 28 2023 06:11:47 GMT+0000 (Coordinated Universal Time)
cuid: clenupoib00150aiahi9g1jl0
slug: traffic-manager-vs-load-balancer-in-azure
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/XJXWbfSo2f0/upload/4559905881245e2cfba43e334a8704e1.jpeg
tags: azure

---

Many people get confused with these two services:

1. Traffic Manager
    
2. Load Balancer
    

The Traffic Manager is like the agent you find when you enter a Bank who tell you:

1. Take this QUEUE - you get in, until you reach the end of it.
    
2. You're attended by the next available agent. Not by one in specific but by the next available. It's random. Agent is free, he/she raises its hand and says, you're up :
    
    1. Hello
        
    2. What's up?
        
    3. Here's your request served
        
    4. Goodbye. Get out.
        

You can think about it this way:

The Traffic Manager is an **Individual**; The Load Balancer is a **Group**.

## A Test Scenario:

1. 1 Traffic Manager
    
2. 1 Load Balancer
    
3. 2 Virtual Machines with IIS
    

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Name</strong></p></td><td colspan="1" rowspan="1"><p><strong>Type</strong></p></td><td colspan="1" rowspan="1"><p><strong>Address Or Alias</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>w1</strong></p></td><td colspan="1" rowspan="1"><p><strong>IIS VM</strong></p></td><td colspan="1" rowspan="1"><p><a target="_blank" rel="noopener noreferrer nofollow" href="http://w1.cocodrilo.space" style="pointer-events: none"><strong>w1.cocodrilo.space</strong></a></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>w2</strong></p></td><td colspan="1" rowspan="1"><p><strong>IIS VM</strong></p></td><td colspan="1" rowspan="1"><p><a target="_blank" rel="noopener noreferrer nofollow" href="http://w2.cocodrilo.space" style="pointer-events: none"><strong>w2.cocodrilo.space</strong></a></p></td></tr><tr><td colspan="1" rowspan="1"><p><a target="_blank" rel="noopener noreferrer nofollow" href="http://tfm.cocodrilo.space" style="pointer-events: none"><strong>tfm.cocodrilo.space</strong></a></p></td><td colspan="1" rowspan="1"><p><strong>Traffic Manager</strong></p></td><td colspan="1" rowspan="1"><p><strong>CNAME for </strong><a target="_blank" rel="noopener noreferrer nofollow" href="http://wwwtfm.trafficmanager.net" style="pointer-events: none"><strong>wwwtfm.trafficmanager.net</strong></a></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong>nlb</strong></p></td><td colspan="1" rowspan="1"><p><strong>Load Balancer</strong></p></td><td colspan="1" rowspan="1"><p><a target="_blank" rel="noopener noreferrer nofollow" href="http://nlb.cocodrilo.space" style="pointer-events: none"><strong>nlb.cocodrilo.space</strong></a></p></td></tr></tbody></table>

Like this:

![](https://xaaafw.bn.files.1drv.com/y4mNBfnS3AnMoP_H7034gQS9C__TkhWaKHNKcizfCqluK0bNHZ8RVKu5vFOmXG0nhcxrIxEGuS3MVse19LgOVXtp29qnGczCl_V0wUCsCzfyDC0pQ7tRCrVG4qEI-9DT4Ric0cGqdIyZJofaxZUmxBWpRJpMw-oH6u1qXRA8CKqdSSfW9neFFlSuc2jdozd-9GBgBFhKBF7qmEiKTYLkBcOfw?width=573&height=251&cropmode=none align="left")

The Traffic Manager can direct traffic to different regions and it's the first touchpoint of a request. It's also used in redundancy scenarios to provide continuity, so, in this scenario, basically, the number of components would be duplicated. In separate Data Centers or Azure Regions.

## The How-To

1. I set up a couple of VMs with Windows 2012 R2 and the IIS default website configured. In order to use the load Balancer, **they have to be in the same Availability set**.
    
2. Configured the Load Balancer
    
3. Setup the Traffic Manager
    

## Load Balancer Configuration

![](https://elesgg.bn1304.livefilestore.com/y4mHqxqj89GzgM096XACzq4N1LAO72Hjvprc_tEXRL1eDPTwNnzI5NYVnecJu5kxTx4G-a1nc4zRQ-vqf0QLo-zVrkO6Wxayx7ns54SqeGEiM3O2raOcEkzYIa905o6isNexCtHcmd3_XrQE8Na2_ZVV8i_Pz5K3GxoZ-um6-0JNIEjep2g1t40WdpwyzLrvwLSX6ynuqt2Biahb23VrYD4DA?width=2094&height=788&cropmode=none align="left")

Added the VMs on the Same availability set to the Load Balancer Backend pool. Also, very important you have to allow traffic to port 80 in the Network Security Group otherwise it won't be possible to connect to the endpoint.

![](https://o4fpdw.bn1304.livefilestore.com/y4mogYWvrwsRfNykqPVkvT9Ie7bDyD5wTLNqbSguFR8h3xAmpntqfySfjxtGJ9xmrUkLWxTByTyKrFpmCKZpoiyLi726TslTuw_R7uOxC6xDbW89kKQWoixsLbZs8nmGKrvO3-sCZ4DcdelKdp4kdjr2TTpcaCMZrHiDFyCR-5EgtMEbm8HyDCb749Oal3q_8_GSAz0yceENNwlW7ZYT_Os9A?width=1296&height=1312&cropmode=none align="left")

The Inbound NAT rule is also part of the configuration. In this test, all incoming traffic on Port 80 will go to an Availability set of 2 VMs. This is called [**nlb.cocodrilo.space**](http://nlb.cocodrilo.space)**.** Remember this, the Load Balancer groups resources.

Another view of the configuration with the IP assigned at provisioning time:

\[caption id="" align="aligncenter" width="2352"\]

![](https://z7rfhq.bn1304.livefilestore.com/y4mjSxD_miowAjOhuM_Dxhhjwka1dIqDKVu_ZVgLLLV752ha9b0lz-0Rumg9Dw9FeEyUKCq3DdAPauYejS8TMvj5KG125EXtE6tXmaNZJVWoXXxptG4AmpIZYSJhWA6GcWymOC2AGm7CP4ZDyJfbvlIXlM5mJGz5wk4l4kMPSTmHEntvy3gr_cZdc_DI-gzFI8ptQsqims7y0J-Ahxx-7y39w?width=2352&height=500&cropmode=none align="left")

The IP is mapped to [nlb.cocodrilo.space](http://nlb.cocodrilo.space)\[/caption\]

![](https://z7rghq.bn1304.livefilestore.com/y4mz0rOzg37_C6OLDZbzZ78zfBkcOd8Dg8PCQo9g8lXbXXqI9JxfhiqHRVZCRbjRpHXnGFTXLkWmeaM58PC40Pp3SA-Mj9AwKrj6y1MdUP2wgeuE0AHF97yRzwm_yIXf4p7eAUcutFRUcLZu8kDJ-vF0I8tVaqz_wyLCjgqmd4LUMBGdS2o1kRp6wDGXs8Ycu3h31Fyf3lbRV5h0lXbTiA1fQ?width=1826&height=802&cropmode=none align="left")

Traffic Manager endpoint is to the Load Balancer FQDN &gt; [nlb.cocodrilo.space](http://nlb.cocodrilo.space) and I also created a CNAME for [www.cocodrilo.space](http://www.cocodrilo.space) which points to the Traffic Manager Azure given a name at provisioning time

![](https://p1mamg.bn1304.livefilestore.com/y4mYb3TpdeW4dW3-YDlbzdjGoxaSYDtPdJGQiJeLlEmqcpMFa8-SABFIOTHiLfx260a4CvJ-_xuVzpzFZtR3_kgyTcGvlbl1Taq-m8ZNAXmC6iaz9s3jFISE4A3Sce_YdGfVAcUjoKyoQX5cPtHjyWF-ONMhvLgXSWEqX-XitDvBTV9DK48eax_lJd2mM4XbDNeoceOb6XGAuTiJLqcYzrszg?width=938&height=90&cropmode=none align="left")

This Traffic Manager only has 1 endpoint which is the Load Balancer, and behind it there are 2 VMs:

## And how does it look?

![](https://eleqgg.bn1304.livefilestore.com/y4mtiuegwpz932gHAoRI8ZCkYTeyHsRkHdpnrqWS0pHBJHob1tNeFBG6eDdravMfRJN-gjblPssQoF4ikD_JM-KxN2TtjGHNLb4fePlG3XepRIUy7p5JjWa2xktgdwTJHuQxah2Wvpyl7e52yirNxsvO4Jm68v09lvHPg3NABdQ8H7ricCC9vU6jOdHjfwgP6wfyZycQSnf3zzAEjubJrWClw?width=2234&height=1504&cropmode=none align="left")

2nd time

![](https://3ulp3w.bn1304.livefilestore.com/y4mNOChm6Iwo3ADaDxKzGA5Ks866jZSesrBmDSiLLxdhgM9jNi-TvGbf4dLKIs20TpYW1O5oxSRM6RxaCTstUk-W4vq8dHFDDIBwMC_88hfZnybTNhT2SIyDRxrNEzGGEyPs6ijKR6vYWE4A1jYzJKaVDPYiecttSDMTi1T5bHfLXDXmPmHlrXSyQqzLrsz7pLm6M2Aw3RQHb_TYpHKhGY8aA?width=2200&height=1410&cropmode=none align="left")

Obviously you'd have the same service and the site would look exactly the same. This is to show how the service works/behaves.

## What if one VMs goes off? Or it's rebooted?

## Other Misc Settings

![](https://doxy9w.bn1304.livefilestore.com/y4mWykUPavuxla8o4kcZfXfLmRmiqWqMhBAi_cgdmjqgYThqj_iyf2L-vDBnQf74m9dCOIsF-OArp4eyN9e7dBJug2q6dD-WcXlpgBlAvEHM9iIVWaO9n3cQ8Fkl3cBm0nMOulylU0JUbioTWMTWx86doRBzbnpCtCJgijC9f74aD4lX_CRjEh_jg7DwRFvSda5BLjojAEHrKNM_3gBLliSHw?width=1808&height=1186&cropmode=none align="left")

Another thing I tested in this configuration was persistence and that's why I get almost a 100% round robin every time I hit the address, because the setting was No persistence at all.

![](https://1vujsg.bn1304.livefilestore.com/y4mASGxhTOa-CvxCkGUhWJJOkKtGO89MvK8yg24FUTebj5kyJpEei8LzWOuwhjzSNf_h7z_MaF-qnNbTAJDBudTQZMIRK0ayZI6niaWnm_HzhabZHs78WTqiceL7erDJP6Avnf-j6A0rzeqmAhMQmhIvYPHd4A6jMIIHdfUBzPV2_7jDyqv5OiqF-qCn2L4SNe0Y1mVFI77FbhGC43_s7dllA?width=1802&height=1032&cropmode=none align="left")

[@soyroberto](http://twitter.com/soyroberto)