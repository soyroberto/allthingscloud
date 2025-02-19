---
title: "Running Windows XP in Azure"
datePublished: Tue Feb 28 2023 01:06:33 GMT+0000 (Coordinated Universal Time)
cuid: clenjt58t000108mchzyih53i
slug: running-windows-xp-in-azure
tags: azure, windows, windows-xp

---

## BUT WHY?

\[caption id="" align="aligncenter" width="1602"\]

![](https://ebegig.bn1304.livefilestore.com/y4mqbxQ7AlPQFbwxhHhmcg6H7QX9xSrBEmYtJb6pTiFxzhmuZp33CqwTatjJcQA6ggKuMbAHfeXZ6hwB4aUP8xcrEMtLuUY8umxksnfnB8Vl7nTmU7DyP1HL9x0GUPvJM2zWsoeeXWeMj8MYIPFRRDDKKsuniBQdyO2Nlos-_U1vo-hooa1mOPvtqkjXbnmmEvgj4YJ4o8CWS8eF9nqLyHrwQ?width=1602&height=1188&cropmode=none align="left")

Doggie's name is Rover\[/caption\]

## The components

* My Azure Subscription
    
* A Windows 2012 R2 SP2 as the base to glue all things together.
    
* A Windows 2003 R2 .VHD
    
* A Windows XP .VHD
    
* The Virtual Box latest version
    

# The How-To

1. On the Windows 2012 R2 install Virtual Box Latest Version
    
2. Get the .VHD Files for XP and [Windows Server 2003](https://www.microsoft.com/en-au/download/details.aspx?id=19727) R2 here and [here](https://www.microsoft.com/en-au/download/details.aspx?id=19727). **Better to Google where to get the VHDs as these links don't live thru time.**
    
3. Create each VM in Virtual Box as Usual
    
4. When installing the Windows 2003 R2 image change the date as it will say the copy has expired. Put a date in 2003 and it will work.
    
5. That's it
    

## The Pictures

![](https://pifyfw.bn1304.livefilestore.com/y4mTp16YAt-TtmzFq9f6qvAWmrAUUCVPPcVt2oF5qKrIUAKmnGeP5Q_7JC7Cp8uslkbob8tFqMDiQgDZ-2rxKw5NjrqKP2U3sBFmnGLqYPalFO1ygSvkvvbeoMOT6EGfah1GpYp93JSymf6PFp1ck70IA7gQ0wghG284mnZ7OTJSXnklaqgBRbO_Fbr2xd1oEYk8UtgHZMclQHnRaZDDbBkyA?width=2560&height=1596&cropmode=none align="left")

\[caption id="" align="aligncenter" width="1630"\]

![](https://1quzug.bn1304.livefilestore.com/y4mZCZZ_bCjsWPgAGEdiuKxWzASPN5yzJ4elf31N2J_aKclREZVYr-0oyDYU0IFampkcjBlC31G_vK3IcCAvmbiis3aTcErXjEt5Ae91Cv8Y4yP0QSipW4kvueZ7NL0cxHwO16rNEdsSxQ0wj5LYHGnXcSa0Fwr3NwtzNF3HeBSGQiWq-XK4RNu3Ob7L3ZXXBqZYfPuFDUTHws5K2f99K58yw?width=1630&height=1430&cropmode=none align="left")

Firefox in Windows 2003 R2\[/caption\]

\[caption id="" align="alignnone" width="2008"\]

![](https://n1mmqg.bn1304.livefilestore.com/y4mRHHB5jBlzO3lt0a1hSyp3iOGY9HOkY8EfOg4qzRMELFp1loVlXZg_SOCZaW3_b_J1YYKi4EOy1HYKWbbtDFyxO7DYKP97UbIAh9ztuq9bgSN_Wno-oKIPF5acBVN8_mzyW3HPGD4DYK9zoDXAI774NxF64TydxqsIF_2DoB_NkG1NiIqsOTgQ37LVmdThkLKgXNxQUz4DkgXvKlrhOwEaQ?width=2008&height=1442&cropmode=none align="left")

Windows XP, 32 bits. Released in October of 2001.\[/caption\]

\[caption id="" align="aligncenter" width="2560"\]

![](https://n1mrqg.bn1304.livefilestore.com/y4mA2NXEkyBzgB1DVn-x6QOlq0SXNp11mP0RxpeZDhrhkKKICF9IK30MggRK_zyn4s_4YmbggCj2byFZxKaeIQ5H3R5AWhTvyDBSRfm_w0bQF4NULuSXwEKYzZv5Bc1djob4tCmoPKUvA3gluLdLvIzdvzAElMqPRlBwsJ1Y-7U0WAxT8zJsPSWaLPZHf87-YodxWRvsWV72EodH7abOGwvYQ?width=2560&height=1584&cropmode=none align="left")

Setup Process for Windows 2003 R2\[/caption\]

\[caption id="" align="aligncenter" width="2546"\]

![](https://axbdzq.bn1304.livefilestore.com/y4mymFwEK7CGeOfpctMCEq3dOYzoD-kNv5b1RDa2-Xfgr0ZCgBRByMwD1UmNZ_QG5jOzPdnT_xbmH6IGp02M78afAJ_Bp4RZoEK0-cbkVmjx84SHJn9V1-dlpZog25HYDGTKcNYmnNFZHUi_ar99-6jACQ2_fxpwjc2mbKrA-K26t3FzyLArWVTEO3x97fJ7DP6HOT3y0YROb4X4agLFgFGJA?width=2546&height=1582&cropmode=none align="left")

I tried to install 2003 R2 from scratch, never got to work. Better use the files\[/caption\]

\[caption id="" align="alignnone" width="2560"\]

![](https://1ulv7w.bn1304.livefilestore.com/y4msUYJrlx0x1W5sYVI3nG6CYZcUJnn928TlKZsMMMxp1lBJe2Fke5jJ_jcxWwM8NRrIB0HZbqgYN-j-nI5Q3jgmdyLuG-CeC3e4MT4letCU7sRnGv7tsFECsNjFCcka83vRZks-bZ2hZ-UhUa-mu27URw933OlkPqIIEhpMMeZYVo_t3e3e8SEHoKw31Ce_1g0lBeGkoPMJhXGKAWz15MPjA?width=2560&height=1600&cropmode=none align="left")

Firefox in 2003 R2\[/caption\]

\[caption id="" align="alignnone" width="2380"\]

![](https://cld8kg.bn1304.livefilestore.com/y4m6qzGWZ2HT-HgsO9DuzxGx7eWfe-vgiyY2kYb2MRpBdDaR8BVKO-mX3fe8H1GcwdJxAnuA7eYsdxGHPH_L7geZDUk_mCzCTqeKUsA8A43FxY6WwY9yTWfds6iklhDdabltK3xyVAsXZMpuxmW5rDkLs_fdcsxE3sxELdSM91iIAr__q1WLdAdBeyiiFOJt1p2EqPSe4_FI-NPya-QjvGGsg?width=2380&height=1492&cropmode=none align="left")

GoodBye\[/caption\]

[@soyroberto](http://twitter.com/soyroberto)