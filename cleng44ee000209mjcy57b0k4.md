---
title: "Cluster an Existing Windows Certificate Authority in Azure"
datePublished: Mon Feb 27 2023 23:23:06 GMT+0000 (Coordinated Universal Time)
cuid: cleng44ee000209mjcy57b0k4
slug: cluster-an-existing-windows-certificate-authority-in-azure
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Hk-C576NPfk/upload/7af255d1a0e54c919e4f64d2d149d5c3.jpeg
tags: windows, ssl-certificate, windows-server

---

# The scenario is as follows:

* An existing issuing Subordinate Enterprise CA running on Windows 2019 in Australia Southeast
    
* Domain joined and Active Directory Integrated, domain name: [***capi.allthingscloud.net***](http://capi.allthingscloud.net) 
    
* Running on Windows 2019, also supported on Windows 2016
    

## TL;DR

* Backup the exisiting issuing CA
    
* Create a storage account in Azure to be used as the cluster witness
    
* Add an additional VM in the same Azure region, add it to the same availability of Node1
    
* Domain join the second VM
    
* Create an SSD disk and attach it to both VMs
    
* Move the Certificate Database to the Shared Disk
    
* Install the Windows Cluster features in Node1 and Node2
    
* Create a Windows cluster from Node1
    
* Install the Certificate Services in Node2
    
* Create a Certificate cluster of two nodes, Node1 & Node2
    
* Assign an IP to the cluster, and reserve it on the DHCP in case necessary
    
* Change the required registry settings
    
* Update DNS with the cluster IP
    

**Notes**:

* Ideally the existing VM belongs to an availability set, if it doesn't the recommendation is to re-create the VM into one, not within the scope of this article.
    
* Clustering is supported only for the Active Directory Certificate Services service. Other Certificate Service role services, such as Web Enrollment, Online Responder, and Network Device Enrollment Service (NDES) are not supported.
    
* The clustered nodes must store the CA database and the CA log file database on shared storage using iSCSI or Shared Bus. The storage must be available to both nodes in the cluster.
    

## The As-Is 🥵

![](https://bn1304files.storage.live.com/y4midBXu2CYV5riJJ6-KoOYHLGxtWqWo7Tar4TfA1N_mM1OP-nZRnCcUsKLdYVZSEhJs2Paut83uEKGmIU6MhkVmRxofuhEW2izMgFR01b64WTm8R_Z8Gb03rqCwlAEgqBRNdGNa6dGky9i-D0rF6o5MS-hxGqnQT-gAxupRXB5sL_QCKQSFKNrZtFoWM5ZXWEO?width=645&height=197&cropmode=none align="left")

## Step by Step 🔢

### Backup the existing Enterprise Certificate Authority

![](https://bn1304files.storage.live.com/y4mOwECfM6NKH9ZyvGkyPMINDdN0BCyPfBJ7DRmmdFmRVCux8Lhy2LCcvqPyVMZyYm5yY04KL1QbIMXfqpC2Iz-cYEGgG2sYR293cfHW2oMKvs6TJnH3LchdUYEwtGxgQBJsIipGTSF9uvLjsPePFcsqI4PETtpr-Xj1CruhDoPP_4Q_OrYy0eaDuaregxgIVm4?width=1520&height=1056&cropmode=none align="left")

\[caption id="" align="aligncenter" width="1014"\]

![](https://bn1304files.storage.live.com/y4mBsBVEZXlNcIkh60gK3xGoP7qFMAMTJw69lXRRzjtfxnaUORKLqiBlzeJdZl1-vfDxs0KoTn9WVsO8tF5HAafAq_QXaS6SvuQGWGBMCl6EClFJs4Q--bkLmvW8Gxi12tOujvDu1VmkG1MFUju0_AksbRYmiD8-PSnU7FrPVvvZvo8oItLgF7m39qb3lacTyrJ?width=1014&height=814&cropmode=none align="left")

Select as shown in the picture, full backup. I will request a password to protect it\[/caption\]

### Create a storage account in Azure to be used as the cluster witness

* Performance/Access Tier: Standard/hot
    
* Replication: LRS
    
* Account kind: Storage V2 (general purpose)
    

\[caption id="" align="aligncenter" width="2852"\]

![](https://bn1304files.storage.live.com/y4m-F-rSIO8VRrKurlF0uOyJPaDkSZ3eOuZlhhSoRjspFyF9H-cstO5HeHplHca9XJXhgcGx-YOZNkcZdnY_PALgCnsacSiXB8KgfZP2BlgxqCvnhp3eEg-pfxP-L8yJx9qQBYJBquFmXnE_OLZFz7yaduq-5oRCu0TxnYEiK92Qlx5ZTuwh3xVq_IEhGi02aQZ?width=2852&height=578&cropmode=none align="left")

Attaching the account will happen further, for now is just creation\[/caption\]

### Add an additional VM:

* In the same Azure region
    
* In the same availability set
    
* In the same Vnet
    

### Domain join the second VM

### Create an SSD disk and attach it to both VMs

\[caption id="" align="aligncenter" width="2812"\]

![](https://bn1304files.storage.live.com/y4m2u7cyj2Xdtup8ATzZ4_OoYFs481819TGkVLBNHkWZkvvXxTg7Uh7FZ2mYt5nRJ9Dmd8UOAIpko_qdaZXK7otHj6bHH66QHFnKvj78-T0jHmMpsba73oOi-X9qhIET334A5uLPf76RmYnOgiDnA_TcSEBowCPlw7yAAafAWsqrN2jR6qo26fgjOUxIEWZu4gS?width=2812&height=750&cropmode=none align="left")

2 Max Shares at the very least\[/caption\]

### Move the Certificate Database to the Shared Disk

I assigned the letter ***E*** to the disk but your standards may vary.

First, **stop the CA**, again, **stop the CA**. Once the CA is not running then go and change the registry keys in the existing CA to point it to the new shared storage

You will need to use the registry editor to do this

The path for the registry key is located at:

* **Computer\\HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\CertSvc\\Configuration**
    

![The registry keys](https://bn1304files.storage.live.com/y4mNWbCypRKqesy_QmHMbrcEgJ_rq0uVhbaEzcc8CwnQAqD4sWAsUAQArpVErxPMDFWVef4MTyF3JXvV5mr7zzw4rRJhVH8wWqty7vzL5kwK8bHpw4hZL3NLwO88m85n-5Coee9Ud0-6rGrbArRiJF2E2c8LwpcNbnMM4oWLAC2RNGD8zowkZQsL3oKrhUBxgSj?width=2584&height=982&cropmode=none align="left")

* Modify values as per the table below:
    

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Registry Key</strong></p></td><td colspan="1" rowspan="1"><p><strong>Old Value</strong></p></td><td colspan="1" rowspan="1"><p><strong>New Value</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>DBDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\Certlog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBLogDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBSystemDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBTempDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr></tbody></table>

**Node1**

Verify the Certificate Authority's database and logs point to the new database on the share disk, as in the image below:

![Right click on the CA properties and select Storage](https://bn1304files.storage.live.com/y4m0i8WP2JR3BGgVO2C0zU2HCVPbAg_e-LstE_q8lG2fC8wWsXpSBqRkEq2bhvBbTsENMiwqwcLD-8NXaIYDp5PNUNqWzIy6CVwu-ODJP6604ou7mOZKLR-FvIUy5uSS4Q9V-x1rh64EbDoDABjq204N7pzOfB_ewMaB24ag4JFuth5yn9posIV5qkiafadE-Bv?width=956&height=1344&cropmode=none align="left")

* Stop the CA
    
* Bring the shared disk offline
    

## Install the Certificate Services in Node2

* Install Cert Services on the second server- only the certificate authority,
    
* Select enterprise subordinate and  restore a backup from Node1 . Do not point the new cert authority to the new storage folder or you will rewrite the CA and you do not want that.
    
* Bring the shared disk online
    
* Stop the newly installed CA
    
* Modify the registry settings and move the CA database toe the newly attached disk, just like in you did in Node 1. They settings are in:
    
    * **Computer\\HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\CertSvc\\Configuration**
        

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Registry Key</strong></p></td><td colspan="1" rowspan="1"><p><strong>Old Value</strong></p></td><td colspan="1" rowspan="1"><p><strong>New Value</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>DBDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\Certlog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBLogDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBSystemDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr><tr><td colspan="1" rowspan="1"><p>DBTempDirectory</p></td><td colspan="1" rowspan="1"><p>C:\Windows\System32\Certlog</p></td><td colspan="1" rowspan="1"><p>E:\CertLog</p></td></tr></tbody></table>

* Start the Certificate Authority in Node2 check that all the certificates are in place, the settings are normal and so on, this will show that mounting from the shared disk was succesful
    
* Stop the Certificate Authority
    
* Unmount the disk and put it offline
    

#  Setup the Cluster 🚀

* Install the Windows Cluster features in the existing CA, **Node1. Features-&gt; Failover Clustering,** make sure to include the command line
    

![](https://bn1304files.storage.live.com/y4mWp-lOU_SA4cGDmbFmQBUdS3GDxeF25GjoqiJ_j8wzGMi8vemv7RoHRw9CB52H2Q872Ip6gcKQBj6NoSEfCsHLt41p-cPSOO0hknlUCmrkzSpgsET6suprJqY6UbwLb-WuvDI5QTyRHZKMb2MZNlGAnlNkJ_mUobaEdZtksFANDzt_sc-4nEzYrLcFbYKEwpf?width=2378&height=1296&cropmode=none align="left")

* I decided to make **Node1** the manager of the cluster and install it here first, simply logic: it's the original node.
    
* Reboot **Node1**
    

## Install the Windows Cluster features in Node2

* Install the Windows Cluster features in **Node2. Features-&gt; Failover Clustering,** make sure to include the command line
    
* Reboot **Node2**
    

## Create the Cluster from Node1

* Mount the shared disk first
    
* Open the Cluster Manager console
    

![](https://bn1304files.storage.live.com/y4mSeE5gMksePVGDG91febGLg31ojcC9s4d_1nBxM3sitU3fSv0rgyzcKennZnxaCxDRH512a8kupUJ_1AZw_5VpearDwV0HVJQiCghlo4gaudnviZJildwRopajtCJSaXqh8vJ_kMBiViJMIusRdUe7Q_cYFLRlOc_2zoX0CQB_Bg0Tvv2BfYxvRvQMtkxIMx5?width=1998&height=832&cropmode=none align="left")

Once in the Cluster Manager select **Create Cluster**

![Create the cluster](https://bn1304files.storage.live.com/y4mCio5KQXobg99eSgU5B5XSdP9PKWXpXxSPgokf7NxKdzo76rvLPh9dk6npePQfmHqDnX4UAF-SOkLpm26FGFs2rvWFFYBvYXIHYzwTrWqrUfhaFfkITZwAp88FMU4pM0TzGiR7-I1JBWQ4l5UHWlfp6U6cxpV8NO30UC2cPlCa0IUW_CXSA9pnqE3JK0rmgtD?width=706&height=556&cropmode=none align="left")

Select the nodes that will make the cluster, **Node1** and **Node2**

\[caption id="" align="aligncenter" width="1366"\]

![](https://bn1304files.storage.live.com/y4maJQ2AcANZMi9qUglxB6QJuY-01FVAn-s6yT-AxTPRFWWO6LeuhD7zM5194kDFiB9DaD8Z_Q1rhgy9fode9tiGc57aEkrqJY367BUJPU1JUmesiANCvw9uvmJQ-9dMU_xXmk616AmS5XlBXneSy6z1wY7G576_SA7VD3Vmcdsz_NhJcyfd7gZ63BJhixH71Pb?width=1366&height=1040&cropmode=none align="left")

This will create the cluster but it's pending to assign a service to the cluster\[/caption\]

## Create the witness for the Cluster

* **Note**: Create the storage account in the same region where the VMs for the cluster are
    

![Take note of the access key and name for the storage account](https://bn1304files.storage.live.com/y4mCpJkntS1WCN8NGEUQ-QkGbvBnVhCJ69X3BokbdzVUbxfwQL3ehPS9SCno54lQANT8AHJni1W-VWOK13Lv73HfDVP1dX1albf20bdAH5gIOnHPwmDK5AkevtNdrgUgNfOHekgySbGX3gW3Yd9zpeQULnCABzvLXTJoFIDcuwYpH4WDknf54llpTEUkLvFJEAN?width=2054&height=878&cropmode=none align="left")

As a local administrator (of **Node 1**) Run the following two commands:

```plaintext
Set-ClusterQuorum -NoWitness
Set-ClusterQuorum -CloudWitness -AccountName <name> -accessKey<key>
```

The cloud witness will be visible in the cluster management console:

![The Cloud Witness](https://bn1304files.storage.live.com/y4mliwUAa4pnbTuLsIF0LD6t-CRNOoje8coE0z7a5c_22Ww0prvT4RYECqOc5FhtHZ3CEJWsG_FslklS8LfWQys77-rE1AyhEOXFCv054_RM2azNfa08GO_CNI01-hA8P6Jg32Vm4ic8br3vCxIt5MAhU-UKd_A9pK9AYb52KYK2lvg209ygeI4Z1LfsPfcpe1R?width=2324&height=980&cropmode=none align="left")

## Add the shared disk to the Cluster

* On Node1, Create a cluster
    
* Mount the shared disk
    
* Enter the cluster name
    
* Select the computers making the cluster, Node1, Node2
    
* Run the cluster testing
    
* Dismiss the 1 NIC only warning
    

## Add the certificate services to the Cluster

**Configure Role-&gt; Select Generic Service-&gt; Click Next**

![Select Generic Service](https://bn1304files.storage.live.com/y4mYhsjKNX2w29q8saYihe2FCC2m1WZchbGZ__wuE06UUbGTjbxvwemiYYQmEWZbf6om2VYxubCrCpz78VeXIAaM-ujbRGdIHB1BEnIEtd5r_mtXf3zsiSdEPkU7fOuA0zTtP9e7joOdveLoyekl2rBvwA-hJaQKFHgpPLBW242JKvx08SqQOnEkV4gZhZVWLu_?width=2120&height=1186&cropmode=none align="left")

**Once there, Select Certificate Services**

![](https://bn1304files.storage.live.com/y4mLMinjVTCIrEUE6tCp6VEXTtJ2qQQzV3rxRYF9VFqBmzW87NP3_X0_pRBpvEfSUAEDWWC_ye82E3wNtLpdX87Nr6kiwPBiP5kLeDO8CkKzEkUWpujhVLh5pvsplmDyaxBwN0zHsZaT4iLnHPhnou3L-5OO08bkQfCCxxM4vnXjMTolRh9BxhTwYNjUqy7jEuT?width=1594&height=1042&cropmode=none align="left")

If the shared disk doesn't appear on the select storage, click Next, it will be added later. Also, make sure the disk can be mounted in at least 2 VMs.

To configure a share registry hive, click Add and type, ***SYSTEM\\CurrentControlSet\\Services\\CertSvc*** and then click OK, Click Next twice

## Review the IP for the cluster

![](https://bn1304files.storage.live.com/y4m7XKzd4LRThcRY3Gq6UWl_eP4IyXlM3uPfOKt4hwu7x4JOWgs7HobfCsa50lGXheiyh3DjBEc50zXi1G7rT5WUB6sar1V28eZFf-oUK7jK0ev-ngeyvbOIihTZ2SZkYS75YKBPyWWQDg3I0ALeEjBLXfc_HgwcT1bANKkyV0r_9Sl0sMqkoLwC55F3NDK_m8T?width=2256&height=1520&cropmode=none align="left")

## Review the Cluster DNS Name

![](https://bn1304files.storage.live.com/y4m4b0iDd4vX1cr3AkXFB1vHInP3nco4uYKYwQo9GC9_MNPZkGb1IUz3gAQeKZ1tPGrdvrf1jUX8rLvQ1qwB-ZTu2erjCdu6lA4hFnyCSEDnH6H7eNir4kQivxoYLcUknhcQDmxFe0xIow15xIedmr8CtLbbuZa1jBjZ4gTvzjzgTcPwMfQfURuLTJwTJl1uuQW?width=2202&height=1384&cropmode=none align="left")

## How the cluster looks like

![](https://bn1304files.storage.live.com/y4muxn88X5qYxXtGj0lIbBFVJ3FMrCJv2hbvVbwRLvqHLFyUt7OQhgF80DkjeNT5DIROY8US6hI0yyRF9QPGxqUARaeWyXor6tyDrpsXHuoTw9331jws3IE56nUg6ZXe_osfSbKvnMUKsAnVOHJF83jCNKuZg7oWD6ruG8QC0uGsistgAI0TjFFW5YwdoJhYYdG?width=2354&height=1324&cropmode=none align="left")

\[caption id="" align="aligncenter" width="1538"\]

![](https://bn1304files.storage.live.com/y4mlZUwbEOAwgk_naxSMKpT9p2DDeEn6ohAAfBdiThBWRiC_nfl0deLahlmChRGTx1NxF47ASfVjHBSSudLhqgnQeVtGbQe5mkmyDgYOYNtLbuWSNaAYc87YJDxCyOLTWYyiRE6f54aQe1_kVziE9nHG-xRgNzU3WziQQGPmycRMPOlRRzcPQa9tg5rOo_k2MK6?width=1538&height=1154&cropmode=none align="left")

I tested running one instance of the cluster and works well\[/caption\]

## Modify the Web enrolment

Because a node in this cluster already had the web enrolment this must be fixed by modifying the ***%systemroot%\\system32\\certsrv\\certdat.inc*** file change the value of sServerConfig to "&lt;Service Name&gt;\\ CA name&gt;"

![sServerConfig be = to the FQDN of the clustername](https://bn1304files.storage.live.com/y4m2C0_4ly0abMe3nAYMIcDU47v2NZXqiXTtSwrXb2BtxngM2aO1N5t8GevhSheuBxkOb9ZOmOFBWQaLfBWJDOZKqH1ev_I2G8Hv5Wd6Thi0LJdQPCBGFmjlBQUU13XGXlOthpRFALFlchYJpcdHshVXhXnbjchgVo_Wmo11TJK-zwS-jzRwLBDGFHByT3yNR9t?width=2542&height=1448&cropmode=none align="left")

**Note**: **dnsHostName** MUST match the **sServerConfig** field in the [***certdat.inc***](http://certdat.inc) file  for the Web Enrolment to work, see image below:

![dnsHostName MUST match the certdat.inc name for the Web enrollment to work](https://bn1304files.storage.live.com/y4mgPcCi425xN8rAzPJaia5zx8J3i-CrJPmM2l-47c6pPuOLIu1YdIKHqof-FrIKFfBRrXIoegIDirMwyTsusvK9914PnN0SEekFzZf_2t1gAK8-HSv_S17cM97HYfZE7rbFThU2r_SmKqTB9Ov12hrra-HNInNlnSQfIWUVvA-9duH3AzBedJdiehN9O386Iju?width=2868&height=1712&cropmode=none align="left")

## After the cluster is setup

**Enable both cluster nodes to update the CA certificate when required**

1. 1. Log on to a domain controller as a member of the Enterprise Admins group, and open the Active Directory Sites and Services snap-in.
        
    2. In the console tree, select the top node. On the View menu, click Show services node.
        
    3. In the console tree, double-click Services, double-click Public Key Services, and then click AIA.
        
    4. In the details pane, select the CA name as it appears in the Certification Authority snap-in.
        
        1. Add the Cert Publishers group, prior verify it contains both cluster members
            

![Enable both cluster nodes to update the CA certificate when required](https://bn1304files.storage.live.com/y4mbnj_fI-IDIDz5C5BEPh-Jdx3kuwlYntlqjsYjjxP52O7wGm5clvuoiuuFbL0eTarMAIeIk-G_Rz_W7qI06h-r1wf2hYHELkmE6-4SKBN4v1IIFqR3n1z2xV9qzIXswszYPNcQQAH9rPM_nuqhXM6DJGxrYlcBLBw6BaefYdU0rUdyyvk8o7eJj7OCdCIEWUg?width=946&height=476&cropmode=none align="left")

**Give both nodes permissions on the Enrolment container**

1. 1. Log on to a domain controller as a member of the Enterprise Admins group, and open the Active Directory Sites and Services snap-in.
        
    2. In the console tree, select the top node. On the View menu, click Show services node.
        
    3. In the console tree, double-click Services, double-click Public Key Services, and then click AIA.
        
    4. In the console tree, click Enrolment Services. In the details pane, select the CA name.
        
    5. On the Action menu, click Properties. Click the Security tab, and then click Add.
        
        1. Add the Cert Publishers group, prior verify it contains both cluster members
            

![Give both nodes permissions on the Enrolment container](https://bn1304files.storage.live.com/y4mz1x8hHXXc6kQWFmk9CndSs3w7LABi8SRAPE0ucJiUw6SY2rc9OjPQZ_QlE7eOxrDMyOiHb3pm6cEIC0BenYxsI_1l2ZvB_ichJEtOjnZQ7WRfXtY-YKmP3yzG4AAkr2SITPcpmDqxV_zOzAUu13qRH-dc8D5O_I49g7Fj7CaFfks_dpu9gDjUqcJFhGNE9H6?width=961&height=613&cropmode=none align="left")

**Give both nodes permissions on the KRA container**

1. 1. Log on to a domain controller as a member of the Enterprise Admins group, and open the Active Directory Sites and Services snap-in.
        
    2. In the console tree, select the top node. On the View menu, click Show services node.
        
    3. In the console tree, double-click Services, double-click Public Key Services, and then click KRA.
        
    4. In the details pane, select the CA name.
        
    5. On the Action menu, click Properties. Click the Security tab, and then click Add.
        
    6. Click Object Types, select Computers, and then click OK.
        
        1. Add the Cert Publishers group, prior verify it contais both cluster members
            

![Give both nodes permissions on the KRA container](https://bn1304files.storage.live.com/y4mNFIgnsGYe48QYa1veEsYXNE5Umd_DwSfrBhpzA0xRc8OtX7RmEJZgqC_Pk1363oBkTYTUGrb6JHOXEDuY_vFXntlIMO0O2TfKkcndWYVMxz-ec29E-tt4gJYheD59ObZkrxPBOeDnxs6eWzxSjtcX9fAbDk7KL0FVZpz70Iazke0TH-0KLySDxE_YleJQswi?width=897&height=618&cropmode=none align="left")

**Adjust the certification authority’s DNS Name in Active Directory Domain Services (ADDS)**

* Log on to a domain controller as a member of the Enterprise Admins group, and open the ADSI Edit snap-in.
    
* In the console tree, click ADSI Edit. On the Action menu, click Connect to.
    
    * In the list of well-known naming contexts, select **Configuration**, and click OK.
        
    * In the console tree, double-click Configuration, Services, and Public Key Services, and then click Enrolment Services.
        
    * In the details pane, select the name of the cluster CA. On the Action menu, click Properties.
        
* Select the attribute **dNSHostName**, and click Edit.
    
    * Enter the service name of the CA as shown in the Failover Cluster Manager under Failover Cluster Management, and click OK twice. Close ADSI Edit.
        

## How does it look

Finally, after a long setup because it does take time between setup and testing, the clustered CA works

![](https://bn1304files.storage.live.com/y4mfFZediyYPewiuVBFyLRTNsk7MrjZvuehRgPcdp8-jKajFj4b5TTqRVK7aUWzpZ-zb1tOwwnMDo2yofDgh87eJtPk-kg0EE8r_oOEFS0uaXFFeCqwJdbGQZG937gbGP0lDLSU72kIkfEo3Xq4F9eIYYBNSAjjeWENa_75Sj6gimOWuFoifqg2D9P_AOvrgqr7?width=2492&height=1510&cropmode=none align="left")

## Proximity Placement Groups

> A proximity placement group is a logical grouping used to make sure that Azure compute resources are physically located close to each other. Proximity placement groups are useful for workloads where low latency is a requirement.

![](https://bn1304files.storage.live.com/y4mmXw9dL_j-9fwheM0B1ZMFgp_9AHuMHKw8Ds-19LyYTeEXC0V6qUHkiKir9GTigm7-U2VT8lsXHJDH4zJ6z_qdt7X8CrRwGxSmQ6x4WBabwCS5Imxyr4s2wWCPTtbG0iu1I3lrRdf2CjSFXRS2JmKvf2DyJY2jH99668rZG5xsOyAdgBBh2gdgfA5gdRdV1Xg?width=2728&height=616&cropmode=none align="left")

![](https://bn1304files.storage.live.com/y4my_XsiSx-Vc8LTI_pQNuEmw-z8DH8cemumMPo6WGOIfkufw2WObMQqc9gHloMeBpm6xvb6lTB7D5tujXVaHFFtp3X8ZnzslvZJAFEO8btkhGhmCn4-Vo0s9IsH1ZSgHcsnfMIH9IyJMjY_kSU9fOMiZfpIu1gdgzw1K5_PLbZs4lgn1cMK2TxxZFA92g9Rxtg?width=2748&height=910&cropmode=none align="left")

I used some references when I was doing research and these post were very useful:

* [https://social.technet.microsoft.com/wiki/contents/articles/15067.step-by-step-guide-clustering-an-existing-certification-authority.aspx#Verify\_and\_Document\_the\_Active\_Directory\_Certificate\_Services\_ADCS\_DNS\_Name](https://social.technet.microsoft.com/wiki/contents/articles/15067.step-by-step-guide-clustering-an-existing-certification-authority.aspx#Verify_and_Document_the_Active_Directory_Certificate_Services_ADCS_DNS_Name)
    
* [https://www.vkernel.ro/blog/clustering-active-directory-certificate-services-ad-cs](https://www.vkernel.ro/blog/clustering-active-directory-certificate-services-ad-cs)