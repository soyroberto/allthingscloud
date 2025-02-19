---
title: "Allow external users to Book Office 365 rooms"
datePublished: Tue Feb 28 2023 06:15:27 GMT+0000 (Coordinated Universal Time)
cuid: clenuue9f001c0aia9a31fb6t
slug: allow-external-users-to-book-office-365-rooms
tags: office365, microsoft-office-365

---

## The scenario:

External users, with a different address to the default in your Office 365 want to send a meeting request to a meeting room, and, this is very important, get notified about it, whether the meeting room accepted it or not.

Here's the how:

## Pre-requisites.

* An Office 365 tenant (Of course)
    
* The meeting room(s) have been previously created.
    
* The Powershell module for Office 365. From the 365 tenant go to the Exchange Admin Center, as shown in the picture below:
    
    * \[caption id="" align="aligncenter" width="864"\] In this picture, Chrome is the browser, you MUST use Internet Explorer or the module will not install\[/caption\]
        
        When you use Internet Explorer it will install and it will look like this:
        

![](https://xqwmja.bn1304.livefilestore.com/y4mYeNmb4MOy0D0ixjBX8qVxyxzBYqekmXWtwqaTOzCnIm2GH2BcsuiENjqrHiNms4SmaiF6WZXh9H7Avd1TXQ4g9nq6PBMUQuUKQUdY4xStlraPLPKpgBxqYoaR0Q8bS7I-_tXrSk-I7BfY5zYdg0cP7WC4hGH0wP5s0yW3kuaNT0JFFzyjYIs4GHCxTplUZ1FUtrr35kliNs1ArcJPHz9uA?width=1268&height=556&cropmode=none align="left")

* * Even more, it will open a Powershell Window, in that window type the command:
        

```plaintext
Connect-EXOPSSession -UserPrincipalName <your username, with administrator privileges, here>
```

![](https://5zrkpw.bn1304.livefilestore.com/y4mq2l3WF5136ySsyfZFM5r_CqJRFqkqgXiIYjX-F7VLBmLhzeH72YIfxWSqWXlvWsrfbk7xSF_6WUQIW-kNCNemnq_1VxpcLB0pSnBwvHg8YBY_15SYFzenEhCkabEXylQID3xc58_5VAVRvC_AvlyjvFt0lModsXJNm2syeHqc1BFDOOIVTmokgNkskT2Mh7TmX20r6S-LSNss67zJNzI7g?width=2102&height=928&cropmode=none align="left")

Authenticate as per your security settings and once that is done

Run the PowerShell command:

```plaintext
 Set-CalendarProcessing "<Name of the meeting room here>" -ProcessExternalMeetingMessages $true
```

This allows the resource to accept and process requests from external entities, bear in mind that anyone knowing the email address of the resource will be able to book it, and potentially spam it.

## Test it

![](https://jpeppa.bn1304.livefilestore.com/y4mok4lUmTTK8NCFd3a0Ioz_UutS44Dyol5XsvypsYNQ7vMkDeJ_BKPVkdKxmAcAnGoFHLlhd8bYY7zo6EzkG_qbqvbbv6sKLruLi73JsvSLrGLPPYh6WMK8kPDPdTqUHWVBryEYxzEPtJJPG9HXxU3WBaAFUM5hGW2qWCKBnfwR-dhn_ovowI8mx_Sy44K2ss3n9lTOjk_HM5OcacKWcmTPA?width=1604&height=604&cropmode=none align="left")

And it was accepted:

![](https://vtmzva.bn1304.livefilestore.com/y4m1vrxHDtgQcjo56uJUnl3_bmyOff4o-wNZ2RK0uTk9SVJizfExNzof6F4e4S2_rBuX2Y9KHREEbACTEthrRGTl3oeY8DdEwa02HH_BgKkevr9V6PXPg1bI7h8zilqFJttQ1AvATY-X6Hl0tzzmqNQKS3iTgD4w93h41NJCu4vtcCIZg19vB7Kr0gXXWN8AJcqP8a5qbGrLtSjkskZCuCRsA?width=2132&height=862&cropmode=none align="left")

There's a small caveat in this example, the Free/Busy information for the meeting room is not available if the example was between two Office 365 tenants, that would be possible but the usefulness remains, the meeting room can be freely booked as long as it is available.

And obviously, if the room has been booked, it will reject the invitation:

![](https://8yloaq.bn1304.livefilestore.com/y4mP80B-8PZWNCZ8rhEppF-ZRPzXtVQSQ_30uxyKyIP1VmHx7E1td_yaRqic3FaVDYk_DaHCkvyS25NAWzS-25MZn4EGDkPlYS2a8BNUBi5F81P-7EMOhVZD09rIqJ6UIOPnbYwfyNcUH3I2X2eQxnP7MfDHSNW58_unCaWnWl9j-3nBlmimbboKjCtya3j969Hz6_RNVZ3KopNnnX8V7WrpQ?width=2138&height=1088&cropmode=none align="left")

The verification can also be done via  Powershell:

```plaintext
get-mailbox <Name of the Meeting Room> | Get-CalendarProcessing  | select *external*
```

and it should reply back with:

![](https://w65kxw.bn1304.livefilestore.com/y4m1D8up9GDxJB37pNXI_Jq4eF8pvRVbzp8N5I8reqObuutNhfUa_iegZmaGOuxaiNBk49o20JABjc_vjLy88-9YqqkeAV81bqmT7QlTCXMvkBkYENzNpS0whzQWytuoR0yRiWr_gbek2a-DL1fS-Q16Wjy1HQrLUSprCglim0U_m85ltKys4vuOi1-2yX6Pvbx0VC_dNTeCp6h9AlWcDzHDg?width=2022&height=232&cropmode=none align="left")

Roberto