---
title: "Schedule the Start of a VM in Azure"
datePublished: Tue Feb 28 2023 00:57:04 GMT+0000 (Coordinated Universal Time)
cuid: clenjgyaz000109lgahb1e9ip
slug: schedule-the-start-of-a-vm-in-azure
tags: azure, automation

---

## Background:

![](https://tq4bdw.bn.files.1drv.com/y4mmVLa-TiYPpzg2ML2gYQF5Ltuy2XPRR2JWuoNFggkIJiQIs3VkRY0eFODN1dz3k2-CzLHtBGDNpfkRK0aUtWG_a5fSUrogth0mEp3XplW5wccIp_TndmGgm6Uum8RxGaa0VXOKbeLrbmH5N0R-vRXAZzdrXuwY2MD_rMSLzg_0HExti02VjEzNQuGLRsH4wnGPPKWBxAv-vmDTGK-G6o2Sg?width=1024&height=669&cropmode=none align="left")

I used to carry my own personal laptop all around the place, customers, conferences, libraries, etc. In order to have my tool of choice for work. As things have become mobile, the need for a physical device most of the time seems to be unnecessary.

And with the availability of almost "unlimited" resources in the Cloud, I can easily have my own workstation and connect to it wherever I am, whenever I need to.

Having a remote resource hosted in the Cloud has some implications:

* **Cost**: I really don't need that much of power, just the standard tools - Office, Visio, Visual Studio, Powershell and the occasional Wireshark, Fiddler, etc. But still has a cost implication
    
* **Patches** and **updates**: Just as any other physical workstation it does require management
    
* Turning **ON** and **OFF**: In order to keep costs under control, I need to run this resource as needed, there's no point to have it ON during the weekends or after midnight
    
* A **local computer** to perform a **Remote Desktop Connection** to the VM in the Cloud. Again, as I have an almost zero policy for carrying computers and tablets, I have a **Surface RT** at the Office.
    

![](https://szl01a.bn.files.1drv.com/y4mHAkxUL9q7jeckNIGNsnu1dVBar8qVuSNZkaHM_NzJuB2CdBUl2PdoF6dSmoMa45WBn5D4LBoXHp6wXzc8IC7HCtCGSKonVGnRbza6rOplPKV6xeTt9VeQBrD12YkNC4ByhxObeUSkF5iGxaxokiDmwR-pt8Mq5CDI_s6UP0GZJmUrOjEPAOT_3g5Waf8SjUkRQLeNQMJP7StxU0arCBAJQ?width=459&height=255&cropmode=none align="left")

Based on these considerations I decided to run a **Windows 10 Pro** on Azure, a 2 Core, 16 GB RAM with 125 GB of Disk, not SSD as it's more expensive and Word doesn't run faster on it. It's a **Standard D11** in the VM Definition Size

## Turn it ON and OFF

My logic:

* I'd rather automate it and forget about it.
    
* I arrive at the office and it's already available to work.
    
* Not having to log in to the portal or open the app on my iPhone.
    
* I like the convenience
    

## Steps

* Create an automation Account
    
* Import the runbook from the marketplace
    
* Publish the runbook
    
* Create a schedule
    
* Tie the Runbook to the schedule
    

![](https://jwwsvw.bn.files.1drv.com/y4mZ1PFv6dARA7kyrpN2etP6XY70RATTEazofcnWacslDDY6hyul32pS_ZsYoMFBFgQUM8ss8DSbb9sRVpOnYyyYzRF2DxW2kaBcQQ2An9JLMpGKPka1pH9UF5mO8MQp9VGW6WzEj-lI0IskNl8wXJsAWBYVth483B8usTkOnv5W9WVjESe3wFRXrK0K2ikVLV-y2xdkxImQKf5lmu6EE7q0g?width=658&height=920&cropmode=none align="left")

Import the Runbook

![](https://xfvgna.bn.files.1drv.com/y4mEVwWzX8YhLaHtSXNA1C6FoAVSGjlAtEPS72P2FMohnfdaIMWZou3x1KC15Sues3uFOUhZF8n37dNNj3QB0PWeHEMTU4mLXu860eUnu8dBAQXJKgpPYS60xGFvZUX-SL0JdgJ260jWWDczQodAqDcztCwSL8H_eALxtI9jkxS4swEGU-8YEOBh-B37ie0NCsIdk0KXbVFXqNdLyYfSKgqEg?width=864&height=707&cropmode=none align="left")

Give it a name

![](https://fgngwq.bn.files.1drv.com/y4mKD_dWMyVDVbsSkugT9zaVICn0BU3qUdTJn9JAlOooHqyAlRuXvF1vD7TGP9pYNdfeIfn1MsM11feiK2tPr9v5p0d4FJfVY9FoP1ypMCjuUf257gEIrnJO7vdhfaGoGyoZJsob1IC8cfgkblDi9iILf37muk1KMeqWv9T1KBlKEv8jxhQxD77NfHcwjvJYjkJAbQg3eXzGYWEbaujtQ-SDQ?width=1024&height=614&cropmode=none align="left")

Go to the newly created runbook and click Edit as shown below:

![](https://vq4abw.bn.files.1drv.com/y4mV-AvBP722JFAWJZupD5hQbu9PkVSB42gUaDRiFfZpDkj6XOwModh9kW_MXLwKf2ZV_jM5UXQWzlCClccEAvnesX14sxddLabdPmhJ9Xxv8_3wujwWpH4I4u-c7DlIjZPwsfMyqdFSPYJXGJg-20m1rgWBKJY35O17wDVEfEBuwoxruimBn03mOEd-Jikmon6YscaGA4mpUvolaHL55O-QQ?width=1843&height=648&cropmode=none align="left")

Publish the Runbook

![](https://uzlzza.bn.files.1drv.com/y4mxQkXGzZurzFyDVobm-iKepFcjiMH9Fceu8PykBZ6x7kz0SORu8ihVWRYBssolXnhlC8SNSC6fMktTKQJ5i24l7ITpDYlwRRupSq6sYMvRF-BCMWPndR11aMJDJVjBfEp7U64WDFSAXAXZF4piAb-O7bXb_pdi-jRprlRLFGWij665f1JSUdYXxvmBAMRoBGEug_jxAYyZmtxFZsGODb12w?width=1491&height=386&cropmode=none align="left")

Create a Schedule

\[caption id="" align="aligncenter" width="1023"\]

![](https://45q4tw.bn.files.1drv.com/y4m8Jhz-e99wnw1WBzFaPtfYP5u3Yl2vEbixlRzjn6RBXoBMoAzDQLTk3gigPAZUopq_3uBHzUVCHrzLEPwFammB6IKooF_nrObaYcMw8FT8nP-mY-GplisXAqBlx2Ybv3idIOWcIBzZeC9wWqFbkSFRUeqe6ALkyz0YNmONJZHheUu6mHwWeLKcc_KeNAsq6komRK7Deqd_cXFYIgQHqctRg?width=1024&height=487&cropmode=none align="left")

I set up a Monday-Friday recurrence starting at 9 am\[/caption\]

Tie the Runbook to a schedule. You can create almost any combination of days/dates

![](https://jjdpta.bn.files.1drv.com/y4mTSsx98e7NMHtKTH87dJ16m5UwdC3bmSHU-R6X9BGPeN9PYeMbiNXNQ8OLriaCm0tFrljtDu60CAivnPx8fMXuSJnunTvNNtOGdO0E_pBT8zI-m16uq-Mo1QdrsoL18QvdQXSgU_ydBVLi-Q-ZskwxpXlIsISvKj3d3cFhk0E6WOC4nhEcUNKIuI7U0XejB5TFLKOxFd7jQeTl_QQUBZW8w?width=863&height=179&cropmode=none align="left")

Specify the VM parameters

\[caption id="" align="alignnone" width="789"\]

![](https://8slceq.bn.files.1drv.com/y4mXNPSQ-LUfQnTuCN3hxXDibGQqp_IJwU4inEVpHYKTMu42i56cnHIIvkP0vhxW9aMpG6TiPameNQisa9K9jX-lDztc5keTKMrCFUOLDHvbqf00FH1qiMBKj2eAto4XhtOkj_kKy2_k5sO6zMIW8-5yVhaBIhjvMUXJs4ddxyw66P6CqLgB_tC0WLHb-N0rY2avjWUXsVRKdbO-Isv_Ayujw?width=789&height=776&cropmode=none align="left")

Specify the Resource group and the VM name. If not VM name is specified, all the VMs in the RG will be started\[/caption\]

## Verify

\[caption id="" align="aligncenter" width="1860"\]

![](https://woc4pq.bn.files.1drv.com/y4mJN8tsyZ_xA3GgXMAs7zrKeZ5omPWZZEWe2UBNRpYA5xUbxe2-cpftDHmSCQqSZInL4pp7XamA4VHdy_6lSegbF029Qrmdma91i205h7CBgw72the82__esJzClBhg7P1uNnCMDe3-e9fiLg9tKvB2LcwhaKapMAZqzRD3fJJz5RDGnent6b-E0_yW8vjnTCwkegOoa6yJI1qxYHeKXL37Q?width=1860&height=408&cropmode=none align="left")

Startup completed as scheduled\[/caption\]

## What about the shutdown?

![](https://jwwrvw.bn.files.1drv.com/y4mQFx1TyLQkCjp-mP5PZzB0e0XVxes6ZcXZa0V58EjagWpC7WfBUhZaNQ7iRdueTuWh2ZHE2xWHbSr1LbPOIba1QqvNqs6TzaiXJ--8tYmgVku6tz2lHlGUHyU0vMQYpDoB9Zo1bQI1r7fPE5OKL2xMuTAbbmBWQZbd2a9qVuz5KDrXkCg7YYcOyjUQkgHFW5KxuN0WbDEUNmud_YI1-xkaA?width=1238&height=408&cropmode=none align="left")

Roberto