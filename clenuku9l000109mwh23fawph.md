---
title: "AWS AppStreaming a Quick Test Drive"
datePublished: Tue Feb 28 2023 06:08:01 GMT+0000 (Coordinated Universal Time)
cuid: clenuku9l000109mwh23fawph
slug: aws-appstreaming-a-quick-test-drive
tags: aws

---

It makes complete sense, why do I want to have a Windows Desktop for? Answer: It depends on the role and profile, ex:

* Office Worker, with all the traditional tools: Office, Web Browser, Instant Messaging, etc.
    
* Knowledge Worker
    
* Floor Workers, Assistants, Customer Services, and many others.
    

There are many other scenarios where this makes sense in the practical and the economical perspective, I can use the service anywhere I am: At the Office, while on the road and on a Mobile Device.

What I find surprising is that Microsoft didn't come with this offering, but AWS did. Recently they (Microsoft) cancelled their Remote Desktop Services, which was similar to this, one created the base service, with applications and publish it as a Service, it was very neat and convenient. I wrote some posts about it, [here](http://www.allthingscloud.info/azure-remote-desktop-services-active-directory-enabled/) and [here](http://www.allthingscloud.info/publish-remote-desktop-applications-on-azure/)

What is Microsoft going to do to substitute it? I don't know, they mentioned some alternatives, but they were not really appealing in my opinion, using Citrix, with around 6-7 VMs? Not for me.

## I believe in SaaS first then PaaS and if nothing else fits the requirement then IaaS.

## A Quick Test Drive

![](https://scalpq.bn1304.livefilestore.com/y4m7OzDwwIDZ4H4pAT9OJYXSL2uwNREq-OYIteTMh8wGea8qacKISjviwxQywSALFy9lqzIukttsapDz4it2q3NgsBRIebod7nbWq0rot5d3dhGt-uzuhCOXeUjhKzIbfF9d2A6-0b_cC9gVVGMCXrdDkXEfJBqwkyQgD3xc0ky00_kvK8-rLgKQ2x9kiXQj0J235_8voIs6GEIibjxjM3wMg?width=2164&height=568&cropmode=none align="left")

![](https://5dpn4a.bn1304.livefilestore.com/y4mflTXjnkIE0x9K0kWUyPhFLU9wu3HzGJT242RkNq1xn2_xw4golFJLwzDM0LzAqsMt-yxfUI2TzKITBzpOa6i4oqLNJR3yoFfRXEd5SHYdRU2ZJ8j0aUKqJU_RD6PIddXZ_auClHSDv2Ah4Isf17w7V2LO9p6kzgcqptjVlwnMW8S2h9qW5j8JHf9ukTS5B6Xc4VyugHMsfJKUKaaECjE0Q?width=2540&height=1198&cropmode=none align="left")

![](https://e91wpa.bn1304.livefilestore.com/y4mXBd4EFsIIHs6DFQ5JiSGTsUIhp48_7XcKcpG-xswxQPb2PVLOZ_fj6YHLzLM6r-B6mjj349ueG5SLEGvWls7-EjXnrBIb5pb_6qbW3-jJ4XaOSmQAFBcQIEfyyLKem7DEFlSTsJwD9BleV6GB3DpwexrxN0L7YMyfis3UxMX6ZkBHW7RioytJ8ADbOiaJqLwO8orNW8ZNvdog-NZcA4xHw?width=1908&height=526&cropmode=none align="left")

There were a couple of pre-configured images, when I tested it there was no option to create one's own image.

![](https://rlhpmg.bn1304.livefilestore.com/y4mSb76FuVHUtYT02VcGMt_HU-TyMYP5ip4cn-QJMkV_d0MW0gft2HhBQyw48Aju_jB5zW28MJHTMMF1fM7i7sRJLYWGS18CEKQBvxShw4nYTYpntUqsdzJMFj8yb3k4Tdo_yfQhRl5Q7mGAp71uyUuGetsKrvmGCTLCtjM6GgN7txIyt93EI-c4_SRZw3NzQixX7VS_7aK-bQsvCSZ3166OA?width=2504&height=1138&cropmode=none align="left")

Then the size to use to stream application, in reality, this is a Remote Desktop Services farm provisioned on demand.

![](https://qn9gea.bn1304.livefilestore.com/y4m9H00fczXfw778WB8ju0IOZxiyoiBd8AhIYpw49t3UUr7Jk-lpRzo2i9rp4f3BzNlBLv9gCnFap4847zDrHnQS3mxLhK8ZNs992KriHla52gq3wNKDeT7tM81NValxXAqxeJ7sMfBW3iKNmxTpyByhxVUpRaH7DwnDEyODIrc48VOyYjDg9d_OZhBS-KIWkBe4_SBpKB1fqSRvaNVPclscA?width=2074&height=798&cropmode=none align="left")

Now, this was a little bit confusing, there's the Stack and there's the Fleet. The way I understand it:

* Stack is the set of application(s)
    
* Fleet is the actual instance number to service the requests.
    

Once running, I assigned a user (*roberto*)

\[caption id="" align="aligncenter" width="1642"\]

![](https://hssljq.bn1304.livefilestore.com/y4mcEu7LD14Zf1BIntVw6CLBxJ38KlFktdpV-UzXvE33nLki-s-cpS6gkeYS9_rDTWGdpk2tKWrTNCW40GX1TAW-YDIMoL4pWxITsyP4_7lsecO1WRasSXw040wBsFYRxd7PFH0qo2pVEr1G0OP3uqOb4P3T2BlhoSxwS9FOtrcN8zAU2myNTgZWSJD5ngiEams_4ebSDDbJn_uHzAh17zcTQ?width=1642&height=790&cropmode=none align="left")

With a session expiration of 30 minutes\[/caption\]

![](https://tmaupq.bn1304.livefilestore.com/y4mfBWMIj4w0257gQah61iFuj4SDAPsZCzDtoRM2KG-U9U8Gg8-YAmmyDIFRdv9P_OcWWW1baNSWi0gGpx6wNDQ5hDLcP9swwMkVE2eRNn7jLht41gZmCxvzq36eu0ewWAFvc7YWrgkdgQRjv8SARp7UlMz8-aiA-RnY9jOM2YXT2YcI6tOLXXqOUBU4hv6_gOGip0WKuJvb70EcymYHM2oEg?width=1648&height=484&cropmode=none align="left")

The user created gets a URL to connect into:

![](https://5zpw4a.bn1304.livefilestore.com/y4mLc7puyLmG1SIgtm0TZ-pVx32DfCiLfkjdFBjuR45TVlyn-KL8JXp1g4isHvhqq4rCLoiENpS8hmGlI0MIa7c_wgldJGMbe3csIF8zqxaME0r7W8Nh-R2gQ4uLfOLssaJM_O36ZmqAdfF-HKYflD6dXz_uBdjziOHGuvve1QQF8r9Y1EFCQDrlmfpZqsxQpmftACvguA713FoqLgymrFEzw?width=2556&height=1338&cropmode=none align="left")

Once authenticated this is how it looks. The published applications shown:

\[caption id="" align="aligncenter" width="2546"\]

![](https://hsskjq.bn1304.livefilestore.com/y4m4vU4YbDZYuP1VwhXChzprInXPVcnpssfkyd6baFMYVYRFAfsU4Zf_qG8BnthKjbjaTCZpFzwxvsnMKo_ysJDGQeEXwTNslwKnOpT5XK0ftMHA6v3K-rfwrHwTlKMz6E2ZdEvoaXKVuJvTwhvOcZu-qkfQDK6jA1aYCEcTNMC8CyHq4IXVXGiuGyoJ9Z6xTynVQVE1d_UBnpVnoeqhnIlQA?width=2546&height=666&cropmode=none align="left")

I created a Hello Word file and saved it to the X: session folder\[/caption\]

![](https://tmatpq.bn1304.livefilestore.com/y4mbQhdFLRcG8oWtbNEnSjkWtw_rcJOD3S-9kJPabB-Z9Kco0u8BLVda3hx52wgs5Svz-bHu0CYv70XRYSz67HYHeiWWrqry6JO_4R4QT3mbYQA9hFzl0Nq1EU1y0vWaIPJSfBFaxeaGRXae4xTib3IvcisTvtshKLLzqgeqxuyVvqFVOOZKJQwdBC-Yyu_shMN6Lww8RZmZBuFtW3rpkIgoA?width=2034&height=518&cropmode=none align="left")

The files saved in the Session Folder, are only kept as long as the Fleet is running, I stopped the Fleet and goodbye files.

\[caption id="" align="aligncenter" width="1082"\]

![](https://gqq8gg.bn1304.livefilestore.com/y4mYtl6M1easIyylIPfkYQ2vaAtkA6LgwIgDGv6WWPkCRNxYhc0bGfhEI-X9HB-GTfQNJ3kBdUl8U2kE0Y6oQJkvnPAQJnM4a5d70xSgtDK1WEeqZWDlNvH7Vz_dER4oQMwF6bcuseFgSDDB6_9XkRamTY2DZqgkU02iu42ZJ1BVhuEd3wfE33dWcsf43F9m6HoVyG3nLzfmJAbghqyFMbbhA?width=1082&height=732&cropmode=none align="left")

Ok, I pasted it\[/caption\]

I ran Firefox and and Notepad++ at the same time, there's not full access to the Desktop, but there was access to the file Explorer, and the session is completely lost if the Fleet is stopped, even if the file was saved.

## The Good

* Fast provisioning
    
* Quickly accessible from anywhere
    
* Users are already familiar with this scenario, seamless for them
    

## What could be better or much better

* Active Directory Integration. Why would I need to manage a new set of users? Much better to extend my AD, and assign the users from it.
    
* Provide Persistent Storage for the user sessions, again if an AD was in place, permission would be easy, mapping My Folder to S3, why not.
    
* Documentation is not thaaat bad but could be improved
    

That is it.