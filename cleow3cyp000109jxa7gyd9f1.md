---
title: "Azure 500 the TL;DR study guide"
seoTitle: "Azure 500 Study Guide: Quick Essentials"
seoDescription: "Azure AD guide: authentication, identity protection, MFA, and Zero Trust for secure resource management"
datePublished: Tue Feb 28 2023 23:38:11 GMT+0000 (Coordinated Universal Time)
cuid: cleow3cyp000109jxa7gyd9f1
slug: azure-500-the-tldr-study-guide
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/21mJd5NUGZU/upload/9eb019218cd863305054a1f290254c67.jpeg
tags: azure, security, certification, office365, certifications-and-courses, az500, defender-for-endpoint

---

## Following is a set of questions on the Cloud Guru AZ-500 guide

**Which Azure AD External Identities feature lets you invite guest users to collaborate with your organization?**

* Azure AD B2B
    

**What are the Azure AD Connect hybrid identity authentication solutions?**

* Federation
    
* Pass-through authentication
    
* Password hash sync
    

**How can you allow external users to sign up for specific applications themselves?**

* Configure user flows.
    
* Enable guest self-service sign-up via user flows.
    

**Which Azure Active Directory authentication options can enforce on-premises account policies at sign-in?**

* Pass-through authentication
    
* Federation
    

**What can be used to synchronize on-premises Active Directory users to Azure Active Directory?**

* Azure AD Connect
    

**Which Azure AD feature can be used to provide access for consumers using their preferred social, enterprise, or local account identities?**

* Azure AD B2C
    

**Which Azure AD External Identities feature lets you invite guest users to collaborate with your organization?**

* Azure AD B2B
    

### **Contributor vs Owner**

**Contributor cannot modify permissions**

---

**Which of the following are examples of Azure AD permissions?**

* Create a security group
    
* Create an administrative unit
    

**Azure RBAC custom role definitions can include which types of permissions?**

* `notActions` define what actions **cannot** be performed at the management layer in a custom role.'
    
* '`notDataActions` define what actions **cannot** be performed at the data layer in a custom role.'
    
* '`actions` define what actions can be performed at the management layer in a custom role.'
    
* '`dataActions` define what actions can be performed at the data layer in a custom role.'
    

**What is the difference between Owner and Contributor Azure roles?**

* The Contributor role has full access to a resource but cannot modify permissions.
    
* An Owner role has full access to a resource and can modify permissions.
    

**Custom roles are defined in which format?**

* JSON
    

**Which components make up an Azure RBAC assignment?**

* Security principal
    
* Scope
    
* Role definition
    

**What is a valid requirement to create an Azure AD custom role?**

* The Global Administrator role
    
* The Privileged Role Administrator role
    
* An Azure AD Premium P1 or P2 license
    

**Note**: The User Access Administrator role does not permit the creation of Azure AD custom roles. It is an Azure RBAC role, not an Azure AD Role.

**Azure RBAC permission assignments can be scoped to which Azure management scopes?**

* Management groups
    
* Subscriptions
    
* Resource groups
    
* Resources
    

![Scope for a role assignment](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F661fcead-fa5a-4553-8be4-b20b0bc17785_350x275.png align="left")

**What is the principle of least privilege?**

* When a user is given the minimum levels of access required to perform their job functions.
    

**Which of the following are an example of an Azure permission (sometimes referred to as Azure RBAC)?**

* Create a virtual machine
    
* Modify an Azure web app
    

**Azure AD RBAC role assignments can be scoped to \_\_\_\_\_?**

* A tenant
    
* Azure AD resources (e.g., applications)
    
* Administrative units
    

## **There are four fundamental Azure roles:**

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fe3840cc5-5c67-4485-ae10-086330d21ad4_665x471.png align="left")

## **Differences between Azure roles and Azure AD roles**

**Azure roles control permissions to manage Azure resources, while Azure AD roles control permissions to manage Azure Active Directory resources**

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F5598c13f-ce5d-4aca-b322-c105d93c3efb_660x277.png align="left")

18/10/22

FLASH CARDS

The intention is to provide long term knowledge beyond of an exam which one day may expire and may become irrelevant. I'll write about the fundamentals that won't change over the longterm.

Thanks for reading Cloud Fabric! Subscribe for free to receive new posts and support my work.

# **Azure AD identities**

**Application Object**:

**Service principal**: Think of it as a service account in Windows Active Directory

**Difference between Azure AD and On-premise Active Directory**

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F0188de60-aeb7-495c-b1a1-b26d1edc2c4b_767x425.png align="left")

**Azure AD Groups, 2 types**

**Security Groups**: Are used to give group members access to applications, resources and assign licenses. Group **members can be users, devices, service principals, and other groups.**

**Microsoft 365** groups: Used for collaboration, giving members access to a shared mailbox, calendar, files, SharePoint site, and so on. **Group members can only be users.**

**Note no membership**: Assigned or Dynamic - this last one requires at least a P1 license.

## Multi-factor Authentication states

**Disabled→Enabled→Enforced**. Only administrators may move users between states

**Disabled**. User not enrolled for MFA

**Enabled**. User is enrolled in Azure AD Multi-Factor Authentication, but can still use their password for legacy authentication.

**Enforced**. The user is enrolled for MFA. Users who complete registration while in the ***Enabled*** state are automatically moved to the ***Enforced*** state.

## Authentication Alternatives

* Do you need on-premises Active Directory integration? **No?** then you would use Cloud-Only authentication.
    
* If you do need on-premises Active Directory integration, then you would use **Password Hash Sync + Seamless SSO**.
    
* If you do need on-premises Active Directory integration, but you do not need to use cloud authentication, password protection, and your authentication requirements are natively supported by Azure AD, then you would use **Pass-through Authentication Seamless SSO**.
    
* If you do need on-premises Active Directory integration, but you do not need to use cloud authentication, password protection, and your authentication requirements are natively supported by Azure AD, then you would use **Pass-through Authentication Seamless SSO**.
    

## Password Hash Sync

![Users and devices are shown connecting to the on-premises AD, Azure AD, Microsoft 365, and SaaS Apps. Password1 is being used to connect.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F061d1373-8424-4d2e-8d25-cf588fcd223d_465x189.png align="left")

It is important to understand that this is **same sign-in**, not single sign-on. The user still authenticates against two separate directory services, albeit with the same user name and password.

## Pass-through Authentication

* Pass-through authentication (PTA) is a feature of [**Azure AD Connect**](https://oxfordcomputertraining.com/glossary/azure-ad-connect/).
    
* The password need not be present in Azure AD (in any form)
    
* The agent connects outbound to Azure AD and listens for authentication requests, so it only requires outbound ports to be open.
    

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F046c5e1a-8e19-47e9-a587-4cc5f1bc006e_1006x490.jpeg align="left")

## **Federation with Azure AD**

![Diagram showing an internal user going to on-premises AD and Azure. External users are using the web application proxy.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8d8120bd-74b1-4a5a-8e23-85de94251ba7_512x286.png align="left")

This sign-in method ensures that all user authentication occurs on-premise

## Authentication **Decision tree**

![Authentication decision tree described in the text.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F556657f7-403d-420f-adbe-ba6fb0902589_1034x584.png align="left")

## Important authentication considerations:

1. Azure AD can handle sign-in for users without relying on on-premises components to verify passwords.
    
2. Azure AD can hand off user sign-in to a trusted authentication provider such as ADFS.
    
3. Security policies such as account expired, disabled account, password expired, account locked out, and sign-in hours on each user sign-in, Azure AD requires some on-premises components.
    
4. **Sign-in features not natively supported by Azure AD:**
    
    1. Sign-in using smartcards or certificates.
        
    2. Sign-in using on-premises MFA Server.
        
    3. Sign-in using third-party authentication solution
        
    4. Multi-site on-premises authentication solution.
        
    5. Organizations can fail over to Password Hash Sync if their primary sign-in method fails and it was configured before the failure event.
        

## **Azure AD identity protection**

Identity Protection is a tool that allows organizations to accomplish three key tasks:

* Automate the detection and remediation of identity-based risks.
    
* Investigate risks using data in the portal.
    
* Export risk detection data to third-party utilities for further analysis.
    

## **Multifactor authentication in Azure**

The security of MFA two-step verification lies in its layered approach.Authentication methods include:

* Something you know (typically a password)
    
* Something you have (a trusted device that is not easily duplicated, like a phone)
    
* Something you are (biometrics)
    

**Note**:

The Trusted IPs bypass works only from inside of the company intranet.

## **Enable multifactor authentication**

* Remember you can only enable MFA for organizational accounts stored in Active Directory. These are also called work or school accounts.
    
* All users start out Disabled.
    
* When you enroll users in Azure AD Multi-Factor Authentication, their state changes to **Enabled**.
    
* When enabled users sign in and complete the registration process, their state changes to **Enforced**.
    

# **Conditional access conditions**

With access controls, you can either Block Access altogether or Grant Access with more requirements by selecting the desired control:

* Require MFA from Azure AD or an on-premises MFA (combined with AD FS).
    
* Grant access to only trusted devices.
    
* Require a domain-joined device.
    
* Require mobile devices to use Intune app protection policies.
    

![Image showing a Condition to test a user's access. The Condition will allow enforce MFA, or block the user's access.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbf13f2d0-9232-426c-b044-ffafe19d4943_924x389.png align="left")

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbe8f431c-460e-4dac-8318-601048613e19_3000x1444.png align="left")

In this example always require MFA for Teams for a specific user.

Who can reset passwords? See table below:

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F928bd614-0315-4378-8dc8-e349b9c652cc_1428x1498.png align="left")

## Zero Trust

1. Instead of assuming everything behind the corporate firewall is safe, the **Zero Trust model assumes breach and verifies each request as though it originates from an open network**.
    
2. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to **never trust, always verify.**
    
3. Every access request is fully authenticated, authorized, and encrypted before granting access.
    
4. No longer is trust assumed based on the location inside an organization's perimeter.
    

A Zero Trust model requires:

1. **Signals** to inform decisions
    
2. **Policies** to make access decisions
    
3. **Enforcement capabilities** to implement those decisions effectively.
    

**Note**: Identity is the **control plane**. If you can’t determine who the user is, you can’t establish a trust relationship for other transactions.

## **Guiding principles of Zero Trust**

* **Verify explicitly**. Always authenticate and authorize based on all available data points.
    
* **Use least privileged access**. Limit user access with **Just In Time** and **Just Enough Access (JIT/JEA).**
    
* Assume breach.
    
* Verify all sessions are encrypted end to end. Use analytics to get visibility, drive threat detection, and improve defenses
    

The National Institute of Standards and Technology has a Zero Trust Architecture, [NIST 800-207, publication. Click to download, it's a free PDF.](https://doi.org/10.6028/NIST.SP.800-207)

Some key tenets of the Zero Trust Architecture:

* **The entire enterprise private network is not considered an implicit trust zone.**
    
* **No resource is inherently trusted.**
    
* **All communication is secured regardless of network location.**
    
* **Trust in the requester is evaluated before the access is granted.**
    
* **Access should also be granted with the least privileges needed to complete the task**
    

## Tenets of Zero Trust

1. All data sources and computing services are considered resources.
    
2. All communication is secured regardless of network location.
    
3. Access to individual enterprise resources is granted on a per-session basis.
    
4. Access to resources is determined by a dynamic policy.
    
5. The enterprise monitors and measures the integrity and security posture of all owned and associated assets.
    
6. All resource authentication and authorization are dynamic and strictly enforced before access is allowed.
    
7. The enterprise collects as much information as possible about the current state of assets, network infrastructure and communications and uses it to improve its security posture.
    

## Zero Trust view of Networks

1. The enterprise network is not considered an implicit trust zone.
    
2. Devices on the network may not be owned or configurable by the enterprise.
    
3. No resource is inherently trusted.
    
4. Not all enterprise resources are on enterprise-owned infrastructure.
    

## Migrating to a Zero Trust Architecture

It is unlikely that any significant enterprise can migrate to zero trust in a single technology refresh cycle. There may be an indefinite period when ZTA workflows coexist with non-ZTA workflows in an enterprise.

Migration to a ZTA approach to the enterprise may take place one business process at a time. Migrating an existing workflow to a ZTA will likely require (at least) a partial redesign.

## **Key PIM features, Privileged Identity Management**

* Providing **just-in-time** privileged access to Azure AD and Azure resources
    
* PIM allows you to set an end time for the role.
    
* Requiring **approval** to activate privileged roles.
    
* Enforcing **Azure Multi-Factor Authentication** (MFA) to activate any role.Using **justification** to understand why users activate.
    
* Getting **notifications.** Conducting **access reviews.** Downloading an **audit history.**
    

# **Shared responsibility model**

![Diagram that depicts the responsibility zones, which indicate who handles each responsibility scope.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fabd1c6fc-db49-444d-bb2f-10db1de8a1d6_1088x520.png align="left")

Regardless of the deployment type, **you always retain responsibility for the following:**

* Data
    
* Endpoints
    
* Accounts
    
* Access management
    

# **Azure hierarchy of systems**

**Azure Resource Manager** is the deployment and management service for Azure.

![Azure Resource Manager authenticates and handles requests for backend services.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F5b5623e9-325b-4bd9-aeba-031f68e7d0f3_570x300.png align="left")

### **Scope**

Azure provides four levels of scope:

* Management groups
    
* Subscriptions
    
* Resource groups
    
* Resources
    

Lower levels inherit settings from higher levels.

### **Resource Groups**

* All the resources in your group should share the same lifecycle. **You deploy, update, and delete them together.** If one resource, such as a database server, needs to exist on a different deployment cycle it should be in another resource group.
    

# **Azure role-based access control (RBAC)**

## RBAC is:

> **Control the ability for users to create, modify, or delete Azure resources and permissions.**

* RBAC is an authorization system built on Resource Manager that provides fine-grained access management of Azure resources.
    
* You can use RBAC to let one employee manage virtual machines in a subscription while another manages SQL databases within the same subscription.
    
* Each Azure subscription is associated with one Azure AD directory.
    

**RBAC manages who has access to Azure resources, what areas they have access to and what they can do with those resource, examples:**

* Allowing a user, the ability to only manage virtual machines in a subscription and not the ability to manage virtual networks
    
* Allowing a user, the ability to manage all resources, such as virtual machines, websites, and subnets, within a specified resource group
    
* Allowing an app, to access all resources in a resource group
    
* Allowing a DBA group, to manage SQL databases in a subscription
    

# **Defense in depth**

Firewalls, DMZ, VNets, are no longer enough.

## **Network Micro-Segmentation**

A best practice recommendation is to adopt a Zero Trust strategy based on user, device, and application identities. **Zero Trust enforces and validates access control at “access time:**

* **Azure Network Security Groups** can be used for basic layer 3 & 4 access controls between Azure Virtual Networks, their subnets, and the Internet.
    
* **Application Security Groups** enable you to define fine-grained network security policies based on workloads, centralized on applications, instead of explicit IP addresses.
    

## **IP addresses**

* **Private** - A private IP address is dynamically or statically allocated to a VM from the defined scope of IP addresses in the virtual network. VMs use these addresses to communicate with other VMs in the same or connected virtual networks which conforms to RFC 1918.
    
* **Public** - Public IP addresses, which allow Azure resources to communicate with external clients
    

## **Network adapters**

A VM can have more than one network adapter for different network configurations.

# **Distributed Denial of Service (DDoS) Protection**

* If the attack originates from one location, it is called a DoS.
    
* f the attack originates from multiple networks and systems, it is called distributed denial of service (DDoS). A DDoS generally involves many systems sending traffic to targets as part of a botnet.
    
    * botnets are also made up of Internet of Things (IoT) devices
        

## Designing and building for DDoS resiliency:

### **Best practice 1**

* Ensure that **security is a priority throughout the entire lifecycle of an application**
    

### **Best practice 2**

Design your applications to scale horizontally to meet the demands of an amplified load—**specifically**, in the event of a DDoS.

### **Best practice 3**

Implement security-enhanced designs for your applications by using the built-in capabilities of the platform.

## **How Azure denial-of-service protection works**

DDoS Protection blocks attack traffic and forwards the remaining traffic to its intended destination. Within a few minutes of attack detection, you’ll be notified with Azure Monitor metrics.

> **DDoS Protection** `Standard` **can mitigate the following types of attacks:**

* **Volumetric attacks:** The attack's goal is to flood the network layer with a substantial amount of seemingly legitimate traffic.
    
* **Protocol attacks**: Exploiting a weakness in the layer 3 and layer 4 protocol stack. It includes, SYN flood attacks, reflection attacks, and other protocol attacks.
    

## DDOS pricing as of 02/08/2022:

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fa75781de-df29-4248-bb17-c872282131f6_2562x378.png align="left")

**DDoS Protection Standard protects resources in:**

* virtual network including public IP addresses associated with virtual machines,
    
* load balancers
    
* application gateways.
    

## Azure Firewall

* **Built-in high availability** - Because high availability is built in, no additional load balancers are required and there’s nothing you need to configure.
    
* Unrestricted cloud scalability
    
* Network traffic filtering rules
    
* **Outbound Source Network Address Translation (OSNAT) support**
    
* Inbound Destination Network Address Translation (DNAT) support
    
* Azure Monitor logging
    

Azure Firewall has three rule types:

* **NAT rules**
    
* **Network rules, Applied first**
    
* **Application rules**, Applied second
    

## Azure Firewall Pricing as of 03/08/22

## Standard size

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fff47eba2-c2c5-4759-be08-7304be35616b_2570x988.png align="left")

## Premium Size

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F17ec8707-2408-4c39-9ba3-607dbbff74dc_2562x1002.png align="left")

# **Configure VPN forced tunneling**

You configure forced tunneling in Azure via virtual network User Defined Routes (UDR).

# **User Defined Routes and Network Virtual Appliances**

A User Defined Routes (UDR) is a custom route in Azure that overrides Azure's default system routes or adds routes to a subnet's route table.

## **Network Virtual Appliances**

The following figure shows a high-availability architecture that implements an ingress perimeter network behind an internet-facing load balancer. This architecture is designed to provide connectivity to Azure workloads for layer 7 traffic, such as HTTP or HTTPS traffic. **To make an NVA highly available, deploy more than one NVA into an availability set.**

![High availability is provided by two NVAs in an availability set.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F7ca5beda-b15c-406e-8700-15fb46253898_715x495.png align="left")

* The benefit of this architecture is that all NVAs are active, and if one fails, the load balancer directs network traffic to the other NVA.
    
* Both NVAs route traffic to the internal load balancer, so if one NVA is active, traffic will continue to flow.
    
* The NVAs are required to terminate SSL traffic intended for the web tier VMs.
    
* UDRs and NSGs help provide layer 3 and layer 4 (of the OSI model) security. NVAs help provide layer 7, application layer, security.
    

# **Deploy a Network Security Group**

* An individual subnet can have zero, or one, associated NSG.
    
* An individual network interface can also have zero, or one, associated NSG.
    
* You can effectively have dual traffic restriction for a virtual machine by associating an NSG first to a subnet, and then another NSG to the VM's network interface.
    

![Network traffic flow is controlled by NSGs.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F065af9e9-0d76-41ba-b5ac-b7e4ef85e47a_426x307.png align="left")

In this example, **for inbound traffic:**

* The Subnet NSG is evaluated first.
    
* Any traffic allowed through Subnet NSG is then evaluated by VM NSG.
    
* **The reverse is applicable for outbound traffic**
    
* with VM NSG being evaluated first.
    
* Any traffic allowed through VM NSG is then evaluated by Subnet NSG.
    

## How traffic is evaluated

You can associate zero, or one, network security group to each virtual network subnet and network interface in a virtual machine.

### **Inbound traffic**

![NSGs control network traffic to and from the internet .](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbe9cfd08-6ea5-4e0f-890b-832b772525a7_451x338.png align="left")

* **VM1**: To allow port 80 to the virtual machine, both NSG1 and NSG2 must have a rule that allows port 80 from the internet.
    
* **VM4**: Traffic is allowed to VM4, because a network security group isn't associated to Subnet3, or the network interface in the virtual machine. All network traffic is allowed through a subnet and network interface if they don't have a network security group associated to them.
    

Traffic outbound is evaluated in the reverse order, Network Card NSG 1st then Vnet NSG.

**Unless you have a specific reason to, we recommended that you associate a network security group to a subnet, or a network interface, but not both.**

# **Why use a service endpoint?**

* Improved security for your Azure service resources
    
* **Optimal routing for Azure service traffic from your virtual network**
    
* **Endpoints always take service traffic directly from your virtual network to the service on the Microsoft Azure backbone network**.
    
* **Endpoints always take service traffic directly from your virtual network to the service on the Microsoft Azure backbone network**.
    
* With service endpoints, the source IP addresses of the virtual machines in the subnet for service traffic switches from using public IPv4 addresses to using private IPv4 addresses
    

# **Azure application gateway**

Application Gateway can make routing decisions based on additional attributes of an HTTP request, for example URI path or host headers. For example, you can route traffic based on the incoming URL. So if /images is in the incoming URL.

![An application gateway uses rules to access the backend pool.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F832dbde6-e39e-4295-a885-afd5e2ece5a1_599x236.png align="left")

features:

* Secure Sockets Layer (SSL/TLS) termination
    
* Autoscaling
    
* URL-based routing
    
* Multiple-site hosting
    
* Redirection
    
* Session affinity
    
* Custom error pages
    
* Rewrite HTTP headers
    

# **Azure front door**

Front Door works at Layer 7 or HTTP/HTTPS layer and uses **split TCP-based anycast protocol.** Front Door ensures that your end users promptly connect to the nearest Front Door POP (Point of Presence).

![Diagram showing tcp traffic being re-routed using Azure Front Door](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ffa503ede-775a-4cbe-8a15-c2e79db87673_565x351.png align="left")

Features:

* **Accelerate application performance** - Using split TCP-based anycast protocol
    
* Increase application availability with smart health probes
    
* URL-based routing
    
* Multiple-site hosting
    
* Session affinity
    
* TLS termination
    
* Custom domains and certificate management
    
* Application layer security
    
* URL redirection
    
* URL rewrite
    

# **ExpressRoute**

**ExpressRoute** is a direct, private connection from your WAN (not over the public Internet) to Microsoft Services, including Azure.

## **ExpressRoute Encryption**

Azure Virtual WAN uses an Internet Protocol Security (IPsec) Internet Key Exchange (IKE) VPN connection from your on-premises network to Azure over the private peering of an Azure ExpressRoute circuit.

![A network within the on-premises network connected to the Azure hub VPN gateway over ExpressRoute private peering.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F1b49acb2-090e-4edb-a5f4-58e060b61c6d_928x310.png align="left")

# **Endpoint protection**

* **First step:** Install antimalware to help identify and remove viruses, spyware, and other malicious software
    
* Second Step: Monitor the status of the antimalware. Integrate your antimalware solution with Microsoft Defender for Cloud to monitor the status of the antimalware protection.
    

# **Privileged access**

![Process flow diagram that shows that hardware is most secure, when purchased from a trusted OEM that uses Autopilot to provision the device before delivery, then stong security polices are enforced throughout its usage](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fa957c16e-bf63-4e18-a962-21a5b21877bd_1660x744.png align="left")

Zero Trust, means that you don't purchase from generic retailers but only supply hardware from an authorized OEM that support Autopilot.

## **Hardware root-of-trust**

To have a secured workstation you need to make sure the following security technologies are included on the device:

* Trusted Platform Module (TPM) 2.0
    
* BitLocker Drive Encryption
    
* UEFI Secure Boot
    
* Drivers and Firmware Distributed through Windows Update
    
* Virtualization and HVCI Enabled
    
* Drivers and Apps HVCI-Ready
    
* Windows Hello
    
* DMA I/O Protection
    
* System Guard
    
* Modern Standby
    

# **Virtual machine templates**

How you define templates and resource groups is entirely up to you and how you want to manage your solution. For example, you can deploy your three tier application through a single template to a single resource group.

![A single template is used to deploy different resoureces.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Feeb671ae-010c-4243-9fc6-59f9a1f23394_351x214.png align="left")

You don't have to define your entire infrastructure in a single template. Often, it makes sense to divide your deployment requirements into a set of targeted, purpose-specific templates. **When you deploy a template, Resource Manager converts the template into REST API operations**.

![Multiple templates are used to deploy resources.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F26fb824f-ac70-4f2b-9c73-63cf459ba869_324x214.png align="left")

## **Azure Bastion**

* The Azure Bastion service is a fully platform-managed PaaS service that you provision inside your virtual network.
    
* It provides secure and seamless RDP/SSH connectivity to your virtual machines directly in the Azure portal over TLS.
    
* When you connect using Azure Bastion, your virtual machines do not need a public IP address.
    
* Azure Bastion is deployed to a virtual network and supports virtual network peering. Specifically, Azure Bastion manages RDP/SSH connectivity to VMs created in the local or peered virtual networks.
    

![Architecture of a bastion host.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F18523cf4-f323-4c17-93d0-9a233be01a67_673x300.png align="left")

* The Bastion host is deployed in the virtual network.
    
* The user connects to the Azure portal using any HTML5 browser.
    
* The user selects the virtual machine to connect to.
    
* With a single click, the RDP/SSH session opens in the browser.
    
* No public IP is required on the Azure VM.
    

# **Disk encryption**

**Supported operating systems**

* Windows client: Windows 8 and later.
    
* Windows Server: Windows Server 2008 R2 and later.
    
* Windows 10 Enterprise multi-session.
    

Azure Disk Encryption uses the BitLocker external key protector for Windows VMs. **For domain joined VMs, don't push any group policies that enforce TPM protectors.**

## **Features of Containers**

* **Isolation**
    
* \*\*Operating System,\*\*Runs the user mode portion of an operating system.
    
* **Deployment**
    
* **Persistent storage**
    
* **Fault tolerance**
    
* **Networking**
    

## Azure Container Instances

A container builds on top of the kernel, but the kernel doesn't provide all of the APIs and services an app needs to run–most of these are provided by system files (libraries) that run above the kernel in user mode.

Because a container **is isolated from the host's user mode environment, the container needs its own copy of these user mode system files,** which are packaged into something known as a base image.

Because containers require far fewer resources (for example, they don't need a full OS), they're easy to deploy and they start fast. This allows you to have **higher density,** meaning that it allows you to run more services on the same hardware unit, thereby reducing costs.

![Diagram of the Docker architecture](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F100e3db8-df3d-4c43-9a20-be3f444fe0ab_327x367.png align="left")

Containers are built from images that are stored in one or more repositories. These repositories can belong to a **public registry, like Docker Hub, or to a private registry.**

## Azure Container Instances (ACI), is a PaaS service for scenario that can operate in isolated containers:

* Including simple applications, task automation, and build jobs
    
* For full container orchestration, including service discovery across multiple containers, automatic scaling, and coordinated application upgrades, **best to use the Azure Kubernetes Service**
    

### **Features of ACI**

* Deploy containers from DockerHub or Azure Container Registry.
    
* Azure Container Instances enables exposing your container groups directly to the internet with an IP address and a fully qualified domain name (FQDN).
    
* Azure Container Instances guarantees your application is as isolated in a container as it would be in a VM.
    
* Custom sizes
    
* Persistent storage
    
* Flexible billing, Supports per-GB, per-CPU, and per-second billing.
    
* Linux and Windows containers
    

## A container registry

is a service that stores and distributes container images. Docker Hub is a public container registry that supports the open source community and serves as a general catalog of images.

### **Monitor container**

The container monitoring solution in Log Analytics can help you view and manage your Docker and Windows container hosts in a single location:

* View detailed audit information that shows commands used with containers.
    
* Troubleshoot containers by viewing and searching centralized logs without having to remotely view Docker or Windows hosts.
    
* Find containers that may be noisy and consuming excess resources on a host.
    
* View centralized CPU, memory, storage, and network usage and performance information for containers.
    

## **Azure Container Registry authentication**

* **Individual login with Azure AD**
    
* **Service principal**
    
* **Admin account**
    

## Azure Kubernetes Service (AKS)

* Kubernetes is a platform that manages container-based applications and their associated networking and storage components.
    
* The focus is on the application workloads, not the underlying infrastructure components.
    

## **Kubernetes cluster architecture**

A Kubernetes cluster is divided into two components:

* ***Control plane*** nodes provide the core Kubernetes services and orchestration of application workloads.
    
* ***Nodes*** run your application workloads.
    

![kubernetes cluster architecture](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb0b8025a-0ee4-4669-84e9-5db6c05fc792_633x217.png align="left")

# **Azure Kubernetes Service architecture**

Elements:

### **Cluster master**

* kube-apiserver
    
* etcd
    
* kube-scheduler
    
* kube-controller-manager
    

## **Nodes and node pools**

To run your applications and supporting services, you need a **Kubernetes node**. An AKS cluster has one or more nodes, which is an Azure virtual machine (VM) that runs the Kubernetes node components and container runtime:

![A VM kubelet connects to a container through the container runtime. The container access disks and files. The kube-proxy access virtual networking.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F585e9c9a-ef14-4e1c-b2a8-07e1f264ec6d_693x163.png align="left")

### **AKS Terminology**

* **Pools**,Group of nodes with identical configuration
    
* **Node**, Individual VM running containerized applications
    
* **Pods, Single instance of an application. A pod can contain multiple containers**
    
* **Deployment**, One or more identical pods managed by Kubernetes
    
* **Manifest**, YAML file describing a deployment
    

## Azure Kubernetes Service networking

* **Cluster IP** - Creates an internal IP address for use within the AKS cluster.
    
* **NodePort** - Creates a port mapping on the underlying node that allows the application to be accessed directly with the node IP address and port.
    
* **LoadBalancer** - Creates an Azure load balancer resource, configures an external IP address, and connects the requested pods to the load balancer backend pool.
    
* **ExternalName** - Creates a specific DNS entry for easier application access.
    

![Internal traffic uses Cluster IP to access the pod. Incoming direct traffic uses NodePort. Incoming non-direct traffic uses the load balancer.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fce7c5f12-8574-40d3-b144-2d6d685b0d8d_1186x312.png align="left")

## Authentication to Azure Kubernetes Service with Active Directory

The security of AKS clusters can be enhanced with the integration of Azure Active Directory (AD).

![A user is authenticated on first connection. The Cluster Master verifies credentials against Azure AD.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff5f3af6e-865a-4615-962a-46228e24b577_726x257.png align="left")

Azure AD authentication in AKS clusters uses OpenID Connect, an identity layer built on top of the OAuth 2.0 protocol.

# **Azure Monitor**

You can analyze log data that Azure Monitor collects by using queries to quickly retrieve, consolidate, and analyze the collected data.

![Diagram that shows an overview of Azure Monitor.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F2e6a5193-c02c-4e3b-b72a-66ec16966d29_1708x1148.svg align="left")

On the left side of the figure are the sources of monitoring data that populate these data stores.

Processed events that Microsoft Defender for Cloud produces are published to the Azure activity log, one of the log types available through Azure Monitor.

## **Sentinel:**

* **Provides SIEM & SOAR**
    

> **SIEM**: Security information and event management
> 
> **SOAR**: Security orchestration, automation, and response (SOAR)

* **Collect data at cloud scale** across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds.
    
* **Detect previously undetected threats**
    
* **Investigate threats with artificial intelligence**
    
* **Respond to incidents**
    

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F825b317a-cb92-4597-b92a-52c8c2d3b918_533x551.png align="left")

# **Defender for Cloud**

Defender for Cloud is a unified infrastructure security management system, **addresses the three most urgent security challenges:**

* Changing workloads
    
* Increasingly sophisticated attacks
    
* Security skills are in short supply
    

Security Center provides the tools to:

* Strengthen security posture
    
* **Protect against threats**
    
* Get secure faster
    

Security Center (**Note**: called simply Security in Azure) protects non-Azure servers and virtual machines in the cloud or on-premise.

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbda662e6-ffa0-4f4b-94cd-42de91f7e872_2894x1426.png align="left")

## Security Center

Enables you to detect and prevent threats at the Infrastructure as a Service (IaaS) layer, non-Azure servers as well as for Platforms as a Service (PaaS) in Azure. Security Center's supported kill chain intents are based on the MITRE ATT&CK™ framework.

> MITRE ATT&CK®: is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations.
> 
> https://attack.mitre.org/

![Illustration of the Cyber Kill Chain, the 9 steps used to infiltrate and damage an organization.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb5b9c1b8-09d2-4d5e-8184-42ae12fd7dc7_1498x405.png align="left")

# **Security center policies**

Azure Security Benchmark is the foundation for Security Center’s recommendations and has been fully integrated as the default policy initiative.

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb7f0eef2-f0aa-47a7-b59d-1ff4d70231bb_2994x1510.png align="left")

Security Center automatically creates a default security policy for each of your Azure subscriptions.

## Azure policy:

* A **policy** is a rule.
    
* An **initiative** is a collection of policies.
    
* An **assignment** is the application of an initiative or a policy to a specific scope (management group, subscription, or resource group).
    

In practice, it works like this:

1. Azure Security Benchmark is an ***initiative*** that contains requirements.
    
    For example, Azure Storage accounts must restrict network access to reduce their attack surface.
    
2. The initiative includes multiple ***policies***, **ex**: "Storage accounts should restrict network access using virtual network rules".
    
3. Microsoft Defender for Cloud continually assesses your connected subscriptions. If it finds a resource that doesn't satisfy a policy, it displays a ***recommendation*** to fix that situation and harden the security of resources that aren't meeting your security requirements.
    

![Screenshot of Microsoft Defender for Cloud Security Recommendations.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Ff9b5bccb-03a4-45ae-883e-b280b3546053_1284x612.jpeg align="left")

## Microsoft Defender for Cloud has two main goals:

* understand your current security situation
    
* improve your security score
    

Security Center continually assesses your resources, subscriptions, and organization for security issues.

It then aggregates all the findings into a single score so that you can tell, at a glance, your current security situation: the higher the score, the lower the identified risk level

### **Improving your secure score**

To improve your secure score, remediate security recommendations from your recommendations list.

# **Defender for Cloud**

Offered in **two modes**:

* **Without enhanced security features** (Free) - Defender for Cloud is enabled for free on all your Azure subscriptions.
    
* **Defender for Cloud with all enhanced security features**\- not Free
    
    * **Microsoft Defender for Endpoint** - Microsoft Defender for Servers
        
    * **Vulnerability assessment for virtual machines, container registries, and SQL resources**
        
    * **Multi-cloud security**
        
    * **Hybrid security**
        
    * **Threat protection alerts**
        
    * **Track compliance with a range of standards**
        
    * **Access and application controls**
        
    * **Container security features**
        
    * **Breadth threat protection for resources connected to Azure**
        

# **Log Analytics**

Log Analytics helps you monitors cloud and on-premises environments to maintain availability and performance. Log Analytics is the primary tool in the Azure portal for writing log queries and interactively analyzing their results.

![Connected sourses illustration moving data to Azure Monitor](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Faf0e9a07-3c0d-43b2-b300-33b27b99a310_1011x1031.png align="left")

### **Data destinations**

The Log Analytics agent sends data to a Log Analytics workspace in Azure Monitor. The Windows agent can be multihomed to send data to multiple workspaces and System Center Operations Manager management groups. The Linux agent can send to only a single destination.

### **Alerts**

* Alerts in Azure Monitor notify you of critical conditions and potentially attempt to take corrective action.
    
* Alert rules **based on metrics provide near real time alerting based on numeric** values
    
* Rules based on **logs allow for complex logic** across data from multiple sources.
    

![An alert rule has a target and condition.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fe342ec13-1428-4cef-9ccc-e95c601e0a22_303x377.png align="left")

## Azure Monitor makes two types of diagnostic logs available:

* **Tenant logs**. These logs come from tenant-level services that exist outside an Azure subscription, such as Azure Active Directory
    
* **Resource logs**. These logs come from Azure services that deploy resources within an Azure subscription, such as Network Security Groups
    

### **Uses for diagnostic logs**

![Diagnostic logs are exported to Event hubs, storage, and Monitor.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fc089d2a8-101b-4f30-80d7-d2f70123f935_529x564.png align="left")

# **Microsoft identity platform**

Is an evolution of the Azure Active Directory (Azure AD) developer platform, It consists of

* an authentication service
    
* open-source libraries
    
* application registration, and configuration (through a developer portal and application API),
    
* full developer documentation
    
* quickstart samples
    
* code samples,
    
* tutorials,
    
* how-to guides
    

> The Microsoft identity platform supports industry-standard protocols such as OAuth 2.0 and OpenID Connect.

Microsoft Authentication Library (MSAL) is recommended for use against the identity platform endpoints. MSAL supports Azure Active Directory B2C

![Microsoft identity platform for developers](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F4c5d099c-f065-4d0d-8f53-a43ed4990484_782x435.png align="left")

Microsoft identity platform has two endpoints (v1.0 and v2.0), always aim for v2.0. V2.0 endpoint is the unification of Microsoft personal accounts and works accounts into a single authentication system

## Azure AD represents applications following a specific model:

* Identify the app according to the authentication protocols it supports:
    
    * This involves enumerating all the identifiers
        
    * URLs
        
    * Secrets, and related information
        
    * Holds all the data needed to support authentication at run time
        
    * Holds all the data for deciding which resources an app might need to access
        
* Handle user consent during token request time and facilitate the dynamic provisioning of apps across tenants:
    
    * Enables users and administrators to dynamically grant or deny consent for the app to access resources on their behalf.
        
    * Enables administrators to ultimately decide what apps are allowed to do, which users can use specific apps, and how directory resources are accessed.
        

> **An application object describes an application as an abstract entity. Azure AD uses a specific application object as a blueprint to create a service principal. It's the service principal that defines what the app can do in a specific target directory, who can use it, what resources it has access to.**

![Provisioning steps described in the text.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F6dd48ee9-0071-4fe2-bda9-7a2f283bca04_650x673.png align="left")

# **Register an application with App Registration**

* Before an app can get a token from the Microsoft identity platform, it must be registered in the Azure portal.
    
* Registration integrates the app (yours) with the Microsoft identity platform and establishes the information that it uses to get tokens, including:
    
    1. **Application ID**: A unique identifier assigned by the Microsoft identity platform.
        
    2. **Redirect URI/URL**: One or more endpoints at which your app will receive responses from the Microsoft identity platform.
        
    3. **Application Secret**: A password or a public/private key pair that your app uses to authenticate with the Microsoft identity platform. (Not needed for native or mobile apps.)
        

# **Microsoft Graph two types of permissions**

* **Delegated permissions** are used by apps that have a signed-in user present
    
* **Application permissions** are used by apps that run without a signed-in user present; for example, apps that run as background services or daemons. **Application permissions can only be consented by an administrator.**
    

> Your app can never have more privileges than the signed-in user.

For application permissions, the effective permissions of your app will be the full level of privileges implied by the permission. **For example, an app that has the User.ReadWrite.All** application permission can update the profile of every user in the organization.

## **Graph API**

* Graph Security API is an intermediary service (or broker) that provides a single programmatic interface to connect multiple Microsoft Graph Security providers (also called security providers or providers).
    
* Graph Security API federates requests to all providers in the Microsoft Graph Security ecosystem.
    

# **Managed identities**

> Challenge: how to manage the credentials in your code for authenticating to cloud services.

> Solution:
> 
> Managed Identities = **Client ID + Principal ID + Azure Instance Metadata Service (IMDS)**
> 
> Azure Key Vault provides a way to securely store credentials, secrets, and other keys, but your code has to authenticate to Key Vault to retrieve them.

## Two types of managed identities:

* **A system-assigned managed identity** is enabled directly on an Azure service instance.
    
* A user-assigned managed identity
    

# **Data sovereignty**

Data sovereignty is the concept that information, which has been converted and stored in binary digital form, is subject to the laws of the country or region in which it is located.

> `In Azure, customer data might be replicated within a selected geographic area for enhanced data durability during a major data center disaster, and in some cases will not be replicated outside it.`

### **Paired regions**

Each Azure region is paired with another region within the same geography, forming a regional pair.

![A Geography box contains a regional pair box, which in turn contains two region boxes, each with a box in it labeled datacenter.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8b1a9f1d-d6c5-4484-bf3e-eee09ce6db67_779x390.png align="left")

### **Benefits of Azure paired regions**

* Physical isolation
    
* Platform-provided replication
    
* Region recovery order.
    
    * If a broad outage occurs, recovery of one region is prioritized out of every pair.
        
* **Sequential updates**
    
* **Data residency** - To meet data residency requirements for tax and law enforcement jurisdiction purposes, a region resides within the same geography as its pair
    

## **Options for authorizing requests to Azure Storage include:**

* **Azure AD provides superior security and ease of use over other authorization options**
    
    * can use role-based access control (RBAC)
        
    * can grant permissions that are scoped to the level of an individual container or queue.
        
    * Azure AD
        
* **Azure Active Directory Domain Services (Azure AD DS) authorization** for Azure Files
    
* **Shared Key.** encrypted signature string that is passed on via the request in the Authorization header.
    
* **Shared Access Signatures** - A shared access signature (SAS) is a URI that grants restricted access rights to Azure Storage resources.
    
* Anonymous access to containers and blobs
    

> `Azure AD, you avoid having to store your account access key with your code, as you do with Shared Key authorization.`

# **Shared access signatures**

* As a best practice, you shouldn't share storage account keys with external third-party applications.
    
* For untrusted clients, use a **shared access signature** (SAS).
    

# **Azure AD storage authentication**

You can use Azure role-based access control (Azure RBAC) to grant permissions to a security principal, which may be a user, group, or application service principal. The security principal is authenticated by Azure AD to return an OAuth 2.0 token. The token can then be used to authorize a request against the Blob service.

![A Storage Blob Data Contributor and Reader are accessing storage.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F12f14270-26a8-4b0f-a18b-46f465171beb_530x501.png align="left")

With Azure AD, access to a resource is a two-step process. First, the security principal's identity is authenticated and an OAuth 2.0 token is returned. Next, the token is passed as part of a request to the Queue service and used by the service to authorize access to the specified resource.

> You can assign a role to a user, group, service principal, or managed identity. This is also called a *security principal*.
> 
> ![Security principal for a role assignment](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fe74500d0-94bf-4ae8-af24-b12f470dbaa5_325x139.png align="left")

* **Service principal** - A security identity used by applications or services to access specific Azure resources
    
* **Managed identity** - An identity in Azure Active Directory that is automatically managed by Azure
    

## **Storage service encryption**

* All data (including metadata) written to Azure Storage is automatically encrypted using Storage Service Encryption (SSE).
    
* Azure AD integration is supported for blob and queue data operations.
    
* Data can be secured in transit between an application and Azure by using Client-Side Encryption, HTTPS, or SMB 3.0
    
* OS and data disks used by Azure virtual machines can be encrypted using Azure Disk Encryption.
    
* Delegated access to the data objects in Azure Storage can be granted using a shared access signature.
    

> All Azure Storage resources are encrypted, including blobs, disks, files, queues, and tables. All object metadata is also encrypted.

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F54656b2f-0236-4a29-945b-4dc49f78ba45_1027x557.png align="left")

## Azure files authentication

* Azure Files enforces authorization on user access to both the share and the directory/file levels
    
* Share-level permission assignment can be performed on Azure Active Directory (Azure AD) users or groups managed through the role-based access control (RBAC) model
    
* With RBAC, the credentials you use for file access should be available or synced to Azure AD.
    
* You can assign built-in RBAC roles like Storage File Data SMB Share Reader to users or groups in Azure AD to grant read access to an Azure file share.
    
* At the directory/file level, Azure Files supports preserving, inheriting, and enforcing Windows DACLs just like any Windows file servers.
    

## Identity-based authentication for Azure Files offers several benefits over using Shared Key authentication:

* Azure Files supports using both on-premises AD DS or Azure AD DS credentials to access Azure file shares over SMB from either on-premises AD DS or Azure AD DS domain-joined VMs.
    
* Enforce granular access control on Azure file shares.
    
* Back up Windows ACLs (also known as NTFS) along with your data
    

![Diagram of how identity-based authentication works or Azure files.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F015bf94c-5c48-4e3f-8913-296fb69c2304_566x437.png align="left")

> 1. Before you can enable authentication on Azure file shares, you must first set up your domain environment.
>     
> 2. For Azure AD DS authentication, you should enable Azure AD Domain Services and domain join the VMs you plan to access file data from.
>     
> 3. Your domain-joined VM must reside in the same virtual network (VNET) as your Azure AD DS.
>     
> 4. Similarly, for on-premises AD DS authentication, you need to set up your domain controller and domain join your machines or VMs.
>     

* Azure file shares supports Kerberos authentication for integration with either Azure AD DS or on-premises AD DS.
    

Before you can enable authentication on Azure file shares, you must first set up your domain environment

* Azure Files supports preserving directory or file level ACLs when copying data to Azure file shares.
    
* You can copy ACLs on a directory or file to Azure file shares using either Azure File Sync or common file movement toolsets. For example, you can use robocopy
    

`Azure Storage doesn't support HTTPS for custom domain names, this option is not applied when you're using a custom domain name.`

# **SQL database authentication**

![Data authentication flow for AAD and SQL server. An Azure AD database adminstrator and SQL database administrator are shown.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fd29fbeeb-f885-4ec5-ac14-bf3fbe503e90_394x384.png align="left")

> Use Azure Active Directory authentication to centrally manage identities of database users and as an alternative to SQL Server authentication.

Initially, all access to your Azure SQL Database is blocked by the SQL Database firewall. To access a database server, you must specify one or more server-level IP firewall rules that enable access to your Azure SQL Database.

![A diagram has two clouds that both point to database-level firewall rules. After the database-level rules are evaluated the server-level rules are applied.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F9d807453-9274-4498-92fc-4549d52634b9_547x734.png align="left")

# **database auditing**

You can use SQL database auditing to:

* **Retain** an audit trail of selected events. You can define categories of database actions to be audited.
    
* **Report** on database activity. You can use pre-configured reports and a dashboard to get started quickly with activity and event reporting.
    
* **Analyze** reports. You can find suspicious events, unusual activity, and trends.
    

# **Key Vault**

* You can use Key Vault to create multiple secure containers, called vaults.
    
* Vaults help reduce the chances of accidental loss of security information by centralizing application secrets storage.
    
* Key vaults also control and log the access to anything stored in them.
    

Azure Key Vault helps address the following issues:

* **Secrets management**.
    
* Key management
    
* Certificate management
    
* Store secrets backed by hardware security modules (HSMs)
    

> `Azure Key Vault is designed to support application keys and secrets. Key Vault is not intended as storage for user passwords.`

# **Key Vault access**

Access to a key vault is controlled through two interfaces: the **management plane**, and the **data plane:**

* The management plane is where you manage Key Vault itself. Operations in this plane include creating and deleting key vaults, retrieving Key Vault properties, and updating access policies.
    
* The data plane is where you work with the data stored in a key vault. You can add, delete, and modify keys, secrets, and certificates from here.
    

> Authentication establishes the identity of the caller. Authorization determines which operations the caller can execute.

![Users and apps authenticate and then are authorized to the management or data plane.](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb1e68c8c-7360-40a9-b84e-fb83d6d6e588_1148x490.png align="left")

![](https://substackcdn.com/image/fetch/w_2400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F540b7cce-3e99-47d6-aa9d-ea2e2547c726_1031x420.png align="left")

# **key rotation**

![A key is updated using event grid and function apps.](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8d319cf4-2684-4a6d-907a-d2789b770a6f_490x419.png align="left")

1. Thirty days before the expiration date of a secret, Key Vault publishes the "near expiry" event to Event Grid.
    
2. Event Grid checks the event subscriptions and uses HTTP POST to call the function app endpoint subscribed to the event.
    
3. The function app receives the secret information, generates a new random password, and creates a new version for the secret with the new password in Key Vault.
    
4. The function app updates SQL Server with the new password.
    

**Shift Left** is a concept in software development and IT operations that emphasizes **moving tasks, processes, and testing earlier in the software development lifecycle (SDLC)**. The goal is to identify and resolve issues as early as possible, reducing the cost and effort of fixing problems later in the development process.

The term "shift left" comes from the idea of moving tasks **leftward** on a timeline of the SDLC, which is often visualized as a linear process from left (planning) to right (deployment and operations).

---

# **Key Principles of Shift Left**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737333323699/2f34dac1-b56a-42f1-956b-eb118d039703.png align="center")

Devops Security, Controls: DS-6

1. **Early Testing**:
    
    * Perform testing (e.g., unit tests, integration tests, security tests) as early as possible in the development process.
        
    * This helps catch bugs and vulnerabilities before they reach production.
        
2. **Continuous Feedback**:
    
    * Provide developers with immediate feedback on their code changes through automated testing and code reviews.
        
3. **Automation**:
    
    * Automate repetitive tasks like testing, code analysis, and deployment to ensure consistency and efficiency.
        
4. **Collaboration**:
    
    * Encourage collaboration between development, operations, and security teams to address issues early.
        
5. **Proactive Problem-Solving**:
    
    * Identify and resolve potential issues before they become critical.
        

---

### **Why Shift Left?**

1. **Cost Efficiency**:
    
    * Fixing issues early in the development process is significantly cheaper than fixing them in production.
        
2. **Faster Delivery**:
    
    * By catching issues early, you reduce the time spent on rework and debugging, enabling faster delivery of features.
        
3. **Improved Quality**:
    
    * Early testing and feedback lead to higher-quality software with fewer defects.
        
4. **Enhanced Security**:
    
    * Integrating security checks early (e.g., static code analysis, vulnerability scanning) helps prevent security vulnerabilities from reaching production.
        
5. **Better Collaboration**:
    
    * Shifting left encourages collaboration between teams, breaking down silos and improving communication.
        

---

### **How to Implement Shift Left**

1. **Adopt Agile and DevOps Practices**:
    
    * Use Agile methodologies to break work into smaller, manageable chunks.
        
    * Implement DevOps practices to automate and streamline the development pipeline.
        
2. **Automate Testing**:
    
    * Use tools like **JUnit**, **Selenium**, or **Cypress** to automate unit, integration, and end-to-end tests.
        
    * Integrate these tests into your CI/CD pipeline.
        
3. **Integrate Security Early**:
    
    * Use tools like **SonarQube**, **OWASP ZAP**, or **Snyk** to perform static code analysis and vulnerability scanning during development.
        
4. **Continuous Integration (CI)**:
    
    * Set up a CI pipeline to automatically build and test code changes as they are committed.
        
5. **Continuous Delivery (CD)**:
    
    * Automate the deployment process to ensure that code changes can be deployed to production quickly and safely.
        
6. **Code Reviews**:
    
    * Conduct peer code reviews to catch issues early and share knowledge across the team.
        
7. **Monitoring and Feedback**:
    
    * Use monitoring tools to provide real-time feedback on application performance and errors.
        

---

### **Examples of Shift Left in Practice**

1. **Unit Testing**:
    
    * Developers write and run unit tests as they write code, ensuring that individual components work as expected.
        
2. **Static Code Analysis**:
    
    * Tools like **SonarQube** analyze code for quality and security issues during development.
        
3. **Security Testing**:
    
    * Security teams integrate vulnerability scanning into the CI/CD pipeline to identify and fix security issues early.
        
4. **Infrastructure as Code (IaC)**:
    
    * Use tools like **Terraform** or **Ansible** to define and test infrastructure configurations before deployment.
        
5. **Shift Left in CI/CD Pipelines**:
    
    * Automate testing, linting, and security checks in the CI/CD pipeline to catch issues before code is merged or deployed.
        

---

### **Benefits of Shifting Left**

1. **Reduced Risk**:
    
    * Early detection of issues reduces the risk of failures in production.
        
2. **Faster Time-to-Market**:
    
    * By resolving issues early, you can deliver features and updates more quickly.
        
3. **Improved Collaboration**:
    
    * Teams work together more effectively, leading to better outcomes.
        
4. **Cost Savings**:
    
    * Fixing issues early is cheaper than fixing them in production.
        
5. **Higher Customer Satisfaction**:
    
    * Delivering high-quality, secure software leads to happier customers.
        

---

### **Challenges of Shifting Left**

1. **Cultural Resistance**:
    
    * Teams may resist changing their workflows or adopting new tools.
        
2. **Tooling and Automation**:
    
    * Setting up and maintaining automated testing and security tools can be complex.
        
3. **Skill Gaps**:
    
    * Developers may need training to write effective tests or use security tools.
        
4. **Initial Investment**:
    
    * Shifting left requires an upfront investment in tools, training, and process changes.
        

---

### **Shift Left vs. Shift Right**

* **Shift Left**: Focuses on early testing and problem-solving in the development phase.
    
* **Shift Right**: Focuses on monitoring and testing in production to gather real-world feedback and improve the application.
    

Both approaches are complementary and can be used together to ensure high-quality software.

---

Let me know if you need further clarification or examples! 😊

# MCRA Notes (Microsoft Cybersecurity Reference Architectures)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737335321598/c3c8b2ea-4734-4385-8a8b-b6d6f63d8153.png align="center")

**Key Takeaway:** Increasing security resilience requires looking at the full security lifecycle

Security is simple in concept and is similar other risk disciplines that focuses on avoiding, limiting, or managing a negative event well (financial, natural disaster, cybersecurity attacks, etc.)

•**‘Left of bang’** - Before an attack, security must focus proactively on preventing or lessening the impact of an attack with people/process, and technology investments

•**‘Right of bang’** – security must also be prepared to handle the attacks that happen, rapidly and effectively removing attacker access from business assets

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737335480190/c3a9498b-bc43-4419-aea2-3f7f9906c135.png align="center")

**Key Takeaway:** Increasing security resilience requires an end to end security approach

Effective security requires an end to end security strategy and architecture (that follow Zero Trust principles) to connect and guide security people, process, and technology.

# **Common Vulnerability Scoring System (CVSS**

The **Common Vulnerability Scoring System (CVSS)** is a standardized framework for rating the severity of security vulnerabilities. It provides a numerical score (ranging from 0.0 to 10.0) that reflects the severity of a vulnerability, helping organizations prioritize remediation efforts.

In the context of **Microsoft Azure**, CVSS scores are often used to assess the severity of vulnerabilities in Azure services, virtual machines, or other resources. Azure Security Center and other Azure tools may use CVSS scores to highlight critical vulnerabilities and recommend mitigation step

# **Key Components of CVSS**

CVSS scores are calculated based on three metric groups:

1. **Base Metrics**:
    
    * Reflect the intrinsic characteristics of a vulnerability that are constant over time and across user environments.
        
    * Includes:
        
        * **Attack Vector (AV)**: How the vulnerability is exploited (e.g., network, adjacent, local, physical).
            
        * **Attack Complexity (AC)**: The difficulty of exploiting the vulnerability.
            
        * **Privileges Required (PR)**: The level of privileges an attacker needs to exploit the vulnerability.
            
        * **User Interaction (UI)**: Whether user interaction is required to exploit the vulnerability.
            
        * **Scope (S)**: Whether the vulnerability affects resources beyond the vulnerable component.
            
        * **Confidentiality (C)**: The impact on data confidentiality.
            
        * **Integrity (I)**: The impact on data integrity.
            
        * **Availability (A)**: The impact on system availability.
            
2. **Temporal Metrics**:
    
    * Reflect characteristics of a vulnerability that change over time.
        
    * Includes:
        
        * **Exploit Code Maturity (E)**: The likelihood of the vulnerability being exploited.
            
        * **Remediation Level (RL)**: The availability of a fix or workaround.
            
        * **Report Confidence (RC)**: The confidence in the existence of the vulnerability.
            
3. **Environmental Metrics**:
    
    * Reflect the impact of a vulnerability based on the specific environment.
        
    * Includes:
        
        * **Collateral Damage Potential (CDP)**: The potential for collateral damage.
            
        * **Target Distribution (TD)**: The proportion of vulnerable systems in the environment.
            
        * **Security Requirements (CR, IR, AR)**: The importance of confidentiality, integrity, and availability in the environment.
            

### **CVSS Score Ranges**

* **0.0**: No severity.
    
* **0.1–3.9**: Low severity.
    
* **4.0–6.9**: Medium severity.
    
* **7.0–8.9**: High severity.
    
* **9.0–10.0**: Critical severity.
    

## **How Azure Uses CVSS**

1. **Azure Security Center** (rebranded and expanded into **Microsoft Defender for Cloud)**
    
    * Azure Security Center uses CVSS scores to prioritize vulnerabilities in your Azure resources.
        
    * It provides recommendations for mitigating vulnerabilities based on their severity.
        
2. **Azure Defender**:
    
    * Azure Defender integrates with CVSS to identify and alert on critical vulnerabilities in virtual machines, containers, and other resources.
        

# **Compliance design areas**

![Azure landing zone design areas](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/media/alz-design-areas.svg align="left")

Security, governance, and compliance are key topics when designing and building an Azure environment. These topics help you start from strong foundations and ensure that solid ongoing processes and controls are in place.

The tools and processes you implement for managing environments play an important role in detecting and responding to issues. These tools work alongside the controls that help maintain and demonstrate compliance.

As the organization's cloud environment develops, these compliance design areas are the focus for iterative refinement. This refinement might be because of new applications that introduce specific new requirements, or the business requirements changing. For example, in response to a new compliance standard.

**Expand table**

| Design area | Objective |
| --- | --- |
| [Security](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/security) | Implement controls and processes to protect your cloud environments. |
| [Management](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/management) | For stable, ongoing operations in the cloud, a management baseline is required to provide visibility, operations compliance, and protect and recover capabilities. |
| [Governance](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/governance) | Automate auditing and enforcement of governance policies. |
| [Platform automation and DevOps](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-area/platform-automation-devops) | Align the best tools and templates to deploy your landing zones and supporting resources. |

# **The enterprise access model**

### The primary stores of business value that an organization must protect are in the Data/Workload plane:

![Diagram that shows the data/workload plane.](https://learn.microsoft.com/en-au/training/wwl-sci/design-solutions-secure-privileged-access/media/data-workload-plane.png align="left")

![Diagram that shows adding user and application access pathways.](https://learn.microsoft.com/en-au/training/wwl-sci/design-solutions-secure-privileged-access/media/user-app-control-management-data-workload-planes.png align="left")

Each of these planes has control of the data and workloads by virtue of their functions, **creating an attractive pathway for attackers to abuse if they can gain control of either plane.**

![Diagram that shows privileged access pathway to manage and maintain.](https://learn.microsoft.com/en-au/training/wwl-sci/design-solutions-secure-privileged-access/media/privileged-access-over-underlying-planes.png align="left")

These systems must be managed and maintained by IT staff, developers, or others in the organizations, creating **privileged access** pathways

Providing consistent access control in the organization that enables productivity and mitigates risk requires you to:

1. Enforce Zero Trust principles on all access
    
2. Pervasive security and policy enforcement across
    
3. Mitigate unauthorized privilege escalation
    

![Diagram that shows the complete enterprise access model from old tiers.](https://learn.microsoft.com/en-au/training/wwl-sci/design-solutions-secure-privileged-access/media/legacy-tier-model-comparison-new.png align="left")

The enterprise access model incorporates full access management requirements of a modern enterprise that spans on-premises, multiple clouds, internal or external user access, and more.

# **Threat Modeling and the STRIDE Model**

* **Threat Modeling** is a structured approach used to identify, prioritize, and mitigate potential security threats in an application or system.
    
* The **STRIDE model** is a framework used in threat modeling to categorize threats into six categories:
    
    1. **Spoofing**: Impersonating a user or system.
        
    2. **Tampering**: Unauthorized modification of data.
        
    3. **Repudiation**: Denial of actions without proof.
        
    4. **Information Disclosure**: Unauthorized access to sensitive data.
        
    5. **Denial of Service**: Disrupting system availability.
        
    6. **Elevation of Privilege**: Gaining unauthorized access to higher privileges.
        

### **How Threat Modeling Fits into DevSecOps**

* **Integration in CI/CD Pipeline**:
    
    * Threat modeling is performed during the design and development phases of the application lifecycle.
        
    * It ensures that security considerations are embedded early in the development process (shift-left security).
        
* **Automation**:
    
    * Use tools like **Microsoft Threat Modeling Tool** to automate and integrate threat modeling into the CI/CD pipeline.
        
* **Continuous Improvement**:
    
    * Regularly update threat models as the application evolves or new threats emerge.
        

### **Steps to Implement Threat Modeling in DevSecOps**

1. **Identify Assets**:
    
    * Determine the critical components of your application (e.g., databases, APIs, user interfaces).
        
2. **Create Data Flow Diagrams (DFDs)**:
    
    * Visualize how data moves through the application and identify trust boundaries.
        
3. **Apply the STRIDE Model**:
    
    * Analyze the DFDs to identify potential threats in each STRIDE category.
        
4. **Mitigate Threats**:
    
    * Implement security controls to address identified threats (e.g., encryption for information disclosure, input validation for tampering).
        
5. **Validate and Monitor**:
    
    * Use automated security testing tools (e.g., SAST, DAST) to validate mitigations.
        
    * Continuously monitor for new threats and update the threat model.
        

### **Tools for Threat Modeling in Azure**

* **Microsoft Threat Modeling Tool**:
    
    * A free tool that helps developers create and analyze threat models using the STRIDE framework.
        
* **Azure Security Center**:
    
    * Provides recommendations and insights to address security issues identified during threat modeling.
        
* **Azure DevOps**:
    
    * Integrate threat modeling into your CI/CD pipelines using tasks and extensions.
        

### **Why Threat Modeling is Critical in DevSecOps**

* **Proactive Security**:
    
    * Identifies and mitigates security risks before they are exploited.
        
* **Compliance**:
    
    * Helps meet regulatory requirements by demonstrating a structured approach to security.
        
* **Cost-Effective**:
    
    * Fixing security issues early in the development process is less expensive than addressing them post-deployment.
        

# Defender

As of now, there are **14 Microsoft Defender products**, each tailored to secure specific environments, platforms, or workloads. These products can be used individually or integrated into **Microsoft Defender XDR** for a unified security solution.

Microsoft offers a variety of Defender products, each designed to protect different aspects of your digital environment. Here are some of the main ones:

1. **Microsoft Defender for Endpoint**: Protects devices and endpoints.
    
2. **Microsoft Defender for Office 365**: Protects email, prevents phishing attacks, and secures collaboration tools.
    
3. **Microsoft Defender for Identity**: Monitors user behavior and protects against identity-based threats.
    
4. **Microsoft Defender for Cloud Apps**: Secures cloud applications.
    
5. **Microsoft Defender Vulnerability Management**: Manages known vulnerabilities and tracks security posture.
    
6. **Microsoft Defender for IoT**: Protects IoT and OT environments.
    
7. **Microsoft Defender for Servers**: Protects servers.
    
8. **Microsoft Defender for SQL**: Secures SQL databases.
    
9. **Microsoft Defender for Containers**: Protects containerized environments.
    
10. **Microsoft Defender for App Service**: Secures app services.
    
11. **Microsoft Defender for Key Vault**: Protects key vaults.
    
12. **Microsoft Defender for DNS**: Secures DNS infrastructure.
    
13. **Microsoft Defender for Resource Manager**: Protects resource management.
    
14. **Microsoft Defender for open-source relational databases**: Secures open-source databases.
    

There are also other specialized Defender products like **Microsoft Defender Threat Intelligence** and **Microsoft Defender External Attack Surface Management (EASM)**.

# **Fuzz Testing** is a [**Software Testing**](https://www.geeksforgeeks.org/software-testing-basics/)

[technique that](https://www.geeksforgeeks.org/software-testing-basics/) uses invalid, unexpected, or random data as input and then checks for exceptions such as crashes and potential memory leaks.

### Fuzz testing can be done in a variety of ways, including:

* **File fuzzing:** providing random or malformed data as inputs to a file-parsing function to identify issues such as buffer overflows or other memory-corruption issues.
    
* **Network fuzzing:** sending malformed or unexpected data as inputs to a network protocol to identify issues such as [**denial of service (DoS) attacks** or other security vuln](https://www.geeksforgeeks.org/deniel-service-prevention/)erabilities.
    
* **API fuzzing:** s[ending random or unexpected dat](https://www.geeksforgeeks.org/deniel-service-prevention/)a as inputs to an application programming interface (API) to identify issues such as input validation issues or other security vulnerabil[ities.](https://www.geeksforgeeks.org/deniel-service-prevention/)
    

Dangling DNS entries occur when a DNS record points to a resource that no longer exists, such as a decommissioned server, a deleted cloud instance, or an expired domain. This can lead to security vulnerabilities, misconfigurations, or service disruptions. Here's an overview of the issue and how to address it:

---

# **What Are Dangling DNS Entries?**

* A DNS record (e.g., A, CNAME, or ALIAS) points to an IP address or domain that is no longer valid.
    
* Common scenarios:
    
    * A cloud instance is terminated, but the DNS record still points to its IP.
        
    * A domain expires, but subdomains or aliases still reference it.
        
    * A service is decommissioned, but its DNS records are not cleaned up.
        

---

### **Risks of Dangling DNS Entries**

1. **Security Vulnerabilities**:
    
    * Attackers can register the abandoned IP or domain and take control of the DNS entry.
        
    * This can lead to phishing, malware distribution, or impersonation attacks.
        
2. **Service Disruptions**:
    
    * Users may be unable to access the intended service.
        
3. **Reputation Damage**:
    
    * If attackers exploit the dangling entry, it can harm your organization's reputation.
        

---

### **How to Identify Dangling DNS Entries**

1. **Audit DNS Records**:
    
    * Regularly review all DNS records to ensure they point to valid resources.
        
2. **Monitor for Changes**:
    
    * Use tools to detect when resources (e.g., cloud instances) are deleted or modified.
        
3. **Check for Unused Records**:
    
    * Identify records that are no longer in use or point to invalid destinations.
        

---

### **How to Prevent Dangling DNS Entries**

1. **Automate DNS Cleanup**:
    
    * Integrate DNS management with your infrastructure (e.g., cloud platforms) to automatically remove records when resources are deleted.
        
2. **Use Alias Records**:
    
    * In cloud environments, use alias records (e.g., AWS Route 53 Alias) that automatically update or delete when the associated resource is removed.
        
3. **Regular Audits**:
    
    * Schedule periodic reviews of your DNS configuration.
        
4. **Monitor Expiry**:
    
    * Track domain and SSL certificate expirations to avoid unintentional lapses.
        
5. **Implement Security Policies**:
    
    * Enforce policies to ensure DNS records are updated or removed when resources are decommissioned.
        

---

### **Tools to Help Manage DNS Entries**

* **DNS Management Platforms**:
    
    * AWS Route 53, Cloudflare, Google Cloud DNS, etc.
        
* **Monitoring Tools**:
    
    * Tools like Nagios, Datadog, or custom scripts can alert you to changes in DNS or infrastructure.
        
* **Security Scanners**:
    
    * Use tools like DetectDangling or open-source scripts to scan for dangling DNS records.
        

---

### **Steps to Fix Dangling DNS Entries**

1. Identify and remove or update records pointing to invalid resources.
    
2. Verify that all active DNS records point to valid and secure endpoints.
    
3. Implement automated processes to prevent future occurrences.
    

By proactively managing DNS records and integrating DNS management with your infrastructure, you can reduce the risk of dangling DNS entries and their associated vulnerabilities.

# The **Microsoft Cloud Security Benchmark (MCSB)**

is a comprehensive set of security recommendations and best practices designed to help organizations secure their cloud environments, particularly those using Microsoft Azure. It aligns with industry standards like NIST, CIS, and ISO, and provides actionable guidance for improving cloud security posture. Below are the **key items** and focus areas of the MCSB:

---

### **1\. Identity and Access Management (IAM)**

* **Key Focus**:
    
    * Implement strong authentication (e.g., multi-factor authentication (MFA)).
        
    * Use role-based access control (RBAC) to enforce least privilege.
        
    * Monitor and manage privileged accounts.
        
* **Key Recommendations**:
    
    * Enable Azure AD Conditional Access policies.
        
    * Regularly review and revoke unused permissions.
        
    * Use managed identities for Azure resources.
        

---

### **2\. Data Protection**

* **Key Focus**:
    
    * Encrypt data at rest and in transit.
        
    * Classify and label sensitive data.
        
    * Implement data loss prevention (DLP) strategies.
        
* **Key Recommendations**:
    
    * Use Azure Key Vault for managing encryption keys and secrets.
        
    * Enable Azure Storage Service Encryption.
        
    * Implement Azure Information Protection for data classification.
        

---

### **3\. Network Security**

* **Key Focus**:
    
    * Secure network boundaries and segmentation.
        
    * Monitor and control network traffic.
        
    * Protect against DDoS attacks.
        
* **Key Recommendations**:
    
    * Use Azure Firewall or Network Security Groups (NSGs) to restrict traffic.
        
    * Enable Azure DDoS Protection.
        
    * Implement Azure Virtual Network (VNet) peering and private links.
        

---

### **4\. Threat Protection**

* **Key Focus**:
    
    * **Detect, investigate, and respond to threats (DIR)**
        
    * Use advanced threat detection tools.
        
    * Automate threat response.
        
* **Key Recommendations**:
    
    * Enable Microsoft Defender for Cloud (formerly Azure Security Center).
        
    * Use Microsoft Sentinel for SIEM and SOAR capabilities.
        
    * Configure automated responses to security incidents.
        

---

### **5\. Security Operations**

* **Key Focus**:
    
    * **Establish a security operations center (SOC).**
        
    * **Monitor and log all activities.**
        
    * Conduct regular security assessments.
        
* **Key Recommendations**:
    
    * **Use Azure Monitor and Log Analytics for centralized logging.**
        
    * Perform regular vulnerability assessments and penetration testing.
        
    * Implement a continuous monitoring strategy.
        

---

### **6\. Application Security**

* **Key Focus**:
    
    * Secure application development and deployment.
        
    * **Protect against common vulnerabilities (e.g., OWASP Top 10).**
        
    * Use secure coding practices.
        
* **Key Recommendations**:
    
    * Integrate security into DevOps (DevSecOps).
        
    * Use Azure Web Application Firewall (WAF).
        
    * Regularly scan for vulnerabilities in application code.
        

---

### **7\. Endpoint Security**

* **Key Focus**:
    
    * **Secure endpoints (e.g., virtual machines, containers).**
        
    * Protect against malware and unauthorized access.
        
    * Ensure endpoint compliance.
        
* **Key Recommendations**:
    
    * **Use Microsoft Defender for Endpoint.**
        
    * Enable endpoint detection and response (EDR) capabilities.
        
    * Apply security baselines to endpoints.
        

---

### **8\. Governance and Compliance**

* **Key Focus**:
    
    * Establish policies and procedures for cloud governance.
        
    * Ensure compliance with regulatory requirements.
        
    * Conduct regular audits.
        
* **Key Recommendations**:
    
    * Use Azure Policy to enforce organizational rules.
        
    * Leverage Azure Blueprints for consistent deployment.
        
    * Monitor compliance with tools like Microsoft Compliance Manager.
        

---

### **9\. Incident Response**

* **Key Focus**:
    
    * Prepare for and respond to security incidents.
        
    * Conduct post-incident reviews.
        
    * Improve incident response processes.
        
* **Key Recommendations**:
    
    * Develop and test an incident response plan.
        
    * Use Microsoft Sentinel for incident investigation.
        
    * Integrate incident response with threat intelligence.
        

---

### **10\. Backup and Recovery**

* **Key Focus**:
    
    * Ensure data resilience and availability.
        
    * Protect against ransomware and data loss.
        
    * Test recovery processes.
        
* **Key Recommendations**:
    
    * Use Azure Backup for critical data.
        
    * Implement Azure Site Recovery for disaster recovery.
        
    * Regularly test backup and restore procedures.
        

---

### **11\. Secure Configuration**

* **Key Focus**:
    
    * Harden cloud resources and services.
        
    * Follow security baselines and benchmarks.
        
    * Automate configuration management.
        
* **Key Recommendations**:
    
    * Use Azure Security Center to assess and improve configurations.
        
    * Apply CIS or NIST benchmarks to Azure resources.
        
    * Use Infrastructure as Code (IaC) tools like ARM templates or Terraform.
        

---

### **12\. Supply Chain Security**

* **Key Focus**:
    
    * **Secure third-party integrations and dependencies.**
        
    * Monitor for supply chain risks.
        
    * Ensure software integrity.
        
* **Key Recommendations**:
    
    * Use Azure Artifacts for secure package management.
        
    * Monitor third-party dependencies for vulnerabilities.
        
    * Implement code signing and integrity checks.
        

---

### **13\. Monitoring and Logging**

* **Key Focus**:
    
    * Collect and analyze logs for security insights.
        
    * Detect anomalies and suspicious activities.
        
    * Retain logs for compliance and investigation.
        
* **Key Recommendations**:
    
    * Use Azure Monitor and Log Analytics.
        
    * Enable diagnostic logging for all critical resources.
        
    * Set up alerts for suspicious activities.
        

---

### **14\. Encryption and Key Management**

* **Key Focus**:
    
    * Protect sensitive data with encryption.
        
    * Securely manage cryptographic keys.
        
    * Rotate keys regularly.
        
* **Key Recommendations**:
    
    * Use Azure Key Vault for key management.
        
    * Enable encryption for all storage accounts and databases.
        
    * Implement hardware security modules (HSMs) for high-security scenarios.
        

---

### **15\. Zero Trust Architecture**

* **Key Focus**:
    
    * Adopt a Zero Trust security model.
        
    * Verify every request and enforce least privilege.
        
    * Assume breach and minimize attack surface.
        
* **Key Recommendations**:
    
    * Use Azure AD Conditional Access.
        
    * Implement network micro-segmentation.
        
    * Continuously validate trust for all users and devices.
        

---

# Modern security practices assume that the adversary has breached the network perimeter.

This shift in mindset is a cornerstone of **modern security practices**, often referred to as the **"assume breach"** philosophy. Instead of solely focusing on preventing attackers from entering the network, organizations now prioritize **detecting, containing, and mitigating threats** that have already bypassed traditional perimeter defenses. This approach is critical because sophisticated adversaries often find ways to breach even the most secure perimeters.

Here’s how modern security practices address the assumption that the adversary has already breached the network:

---

### **1\. Zero Trust Architecture**

* **Core Principle**: Never trust, always verify.
    
* **Key Practices**:
    
    * Verify every user, device, and application before granting access.
        
    * Enforce least privilege access (only the minimum permissions necessary).
        
    * Use multi-factor authentication (MFA) for all users.
        
    * Continuously monitor and validate trust throughout the session.
        

---

### **2\. Network Segmentation**

* **Core Principle**: *<mark>Limit lateral movement within the network.</mark>*
    
* **Key Practices**:
    
    * Divide the network into smaller, isolated segments (micro-segmentation).
        
    * Use firewalls, VLANs, and software-defined networking (SDN) to enforce boundaries.
        
    * Restrict communication between segments to only what is necessary.
        

---

### **3\. Endpoint Detection and Response (EDR)**

* **Core Principle**: Monitor and respond to threats on endpoints.
    
* **Key Practices**:
    
    * Deploy EDR solutions to detect malicious activity on endpoints (e.g., laptops, servers).
        
    * Use behavioral analysis to identify suspicious activities.
        
    * Automate response actions, such as isolating compromised endpoints.
        

---

### **4\. Continuous Monitoring and Threat Hunting**

* **Core Principle**: Actively search for threats within the network.
    
* **Key Practices**:
    
    * **Use Security Information and Event Management (SIEM) tools to collect and analyze logs.**
        
    * Conduct proactive threat hunting to identify hidden threats.
        
    * Set up alerts for unusual or suspicious activities.
        

---

### **5\. Identity and Access Management (IAM)**

* **Core Principle**: Secure identities as the new perimeter.
    
* **Key Practices**:
    
    * **Implement strong authentication mechanisms (e.g., MFA, passwordless authentication).**
        
    * Regularly review and revoke unnecessary permissions.
        
    * Monitor for compromised credentials and suspicious login attempts.
        

---

### **6\. Encryption and Data Protection**

* **Core Principle**: Protect data even if the network is compromised.
    
* **Key Practices**:
    
    * Encrypt data at rest and in transit.
        
    * Use robust key management practices (e.g., Azure Key Vault, AWS KMS).
        
    * Implement data loss prevention (DLP) solutions to monitor and control data flows.
        

---

### **7\. Incident Response and Recovery**

* **Core Principle**: Be prepared to respond to breaches effectively.
    
* **Key Practices**:
    
    * Develop and regularly test an incident response plan.
        
    * Use automated tools to contain and mitigate threats quickly.
        
    * Conduct post-incident reviews to improve processes.
        

---

### **8\. Assume Breach in Design**

* **Core Principle**: Build systems with the assumption that they will be compromised.
    
* **Key Practices**:
    
    * Design systems to minimize the impact of a breach (e.g., isolation, redundancy).
        
    * Use immutable infrastructure to reduce the attack surface.
        
    * Regularly patch and update systems to address vulnerabilities.
        

---

### **9\. Threat Intelligence Integration**

* **Core Principle**: Leverage external and internal threat intelligence.
    
* **Key Practices**:
    
    * Integrate threat feeds into security tools (e.g., SIEM, firewalls).
        
    * Use indicators of compromise (IOCs) to detect known threats.
        
    * Share threat intelligence with industry peers and partners.
        

---

### **10\. User and Entity Behavior Analytics (UEBA)**

* **Core Principle**: Detect anomalies in user and entity behavior.
    
* **Key Practices**:
    
    * Use machine learning to identify unusual patterns (e.g., logins from unusual locations).
        
    * Investigate and respond to anomalies promptly.
        
    * Correlate behavior with other security events for context.
        

---

### **11\. Backup and Resilience**

* **Core Principle**: Ensure business continuity even after a breach.
    
* **Key Practices**:
    
    * Regularly back up critical data and systems.
        
    * Test backup restoration processes to ensure reliability.
        
    * Implement disaster recovery plans to minimize downtime.
        

---

### **12\. Security Awareness Training**

* **Core Principle**: Empower users to recognize and respond to threats.
    
* **Key Practices**:
    
    * Train employees on phishing, social engineering, and other attack vectors.
        
    * Conduct simulated phishing campaigns to test awareness.
        
    * Encourage reporting of suspicious activities.
        

---

### **13\. Cloud-Specific Security Measures**

* **Core Principle**: Adapt security practices for cloud environments.
    
* **Key Practices**:
    
    * Use cloud-native security tools (e.g., AWS Security Hub, Azure Security Center).
        
    * Implement identity federation and single sign-on (SSO).
        
    * Monitor for misconfigurations and compliance violations.
        

---

### **14\. Deception Technology**

* **Core Principle**: Mislead and detect attackers within the network.
    
* **Key Practices**:
    
    * Deploy decoy systems, files, and credentials to lure attackers.
        
    * Monitor interactions with decoys to identify breaches.
        
    * Use deception to gather intelligence on attacker tactics.
        

---

### **15\. Regular Security Assessments**

* **Core Principle**: Continuously evaluate and improve security posture.
    
* **Key Practices**:
    
    * Conduct penetration testing and red team exercises.
        
    * Perform vulnerability scans and patch management.
        
    * Review and update security policies and procedures.
        

---

# **What's the difference between layer 3 and layer 4 osi model?**

The **OSI (Open Systems Interconnection) model** is a framework for understanding how data moves across a network. **Layer 3** (Network Layer) and **Layer 4** (Transport Layer) serve distinct roles in this process. Here's a breakdown of their differences:

---

### **Layer 3: Network Layer**

* **Primary Role**:  
    Responsible for **logical addressing**, **routing**, and **forwarding data packets** between different networks or devices.
    
* **Key Functions**:
    
    * Assigns **IP addresses** (e.g., IPv4/IPv6) to devices.
        
    * Determines the best path for data to travel (using **routing protocols** like OSPF, BGP).
        
    * Fragments and reassembles packets if necessary.
        
* **Devices**: <mark>Routers, Layer 3 switches.</mark>
    
* **Protocols**:
    
    * **IP (Internet Protocol)**: Handles logical addressing.
        
    * **ICMP (Internet Control Message Protocol)**: Used for diagnostics (e.g., `ping`).
        
* **Example**:  
    When you send data to a device on another network (e.g., accessing a website), Layer 3 ensures the packet reaches the correct network via routers.
    

---

### **Layer 4: Transport Layer**

* **Primary Role**:  
    Manages **end-to-end communication**, **error recovery**, and ensures data arrives reliably (or not) between applications.
    
* **Key Functions**:
    
    * **Segments data** into smaller units (TCP segments or UDP datagrams).
        
    * Manages **flow control** (to avoid overwhelming the receiver).
        
    * Provides **connection-oriented** (TCP) or **connectionless** (UDP) communication.
        
* **Devices**: <mark>Firewalls, load balancers (operating at Layer 4).</mark>
    
* **Protocols**:
    
    * **TCP (Transmission Control Protocol)**: Reliable, connection-oriented (used for web browsing, email).
        
    * **UDP (User Datagram Protocol)**: Unreliable, connectionless (used for streaming, VoIP).
        
* **Example**:  
    When you open a website, Layer 4 ensures the HTTP request (TCP port 80) reaches the correct web server application.
    

---

### **Key Differences**

| **Aspect** | **Layer 3 (Network)** | **Layer 4 (Transport)** |
| --- | --- | --- |
| **Focus** | Routing data across networks. | End-to-end communication between applications. |
| **Addressing** | Uses **IP addresses** (e.g., 192.168.1.1). | Uses **port numbers** (e.g., 80 for HTTP). |
| **Devices** | Routers, Layer 3 switches. | Firewalls, load balancers (Layer 4). |
| **Protocols** | IP, ICMP, ARP. | TCP, UDP. |
| **Reliability** | No built-in reliability mechanisms. | TCP ensures reliability; UDP does not. |

---

### **Real-World Analogy**

* **Layer 3**: Like the postal system routing a letter to a city (IP address = city/street).
    
* **Layer 4**: Like ensuring the letter reaches the correct apartment number (port = specific application/service).
    

---

### **Why It Matters**

* **Layer 3** ensures data gets to the right **network**.
    
* **Layer 4** ensures data gets to the right **application** on that network.
    

Understanding these layers helps troubleshoot network issues (e.g., "Is the problem routing \[Layer 3\] or a blocked port \[Layer 4\]?").

# In azure The flow record allows a network security group to be stateful. what does this mean?

In Azure, when a **Network Security Group (NSG)** is described as **stateful**, it means that the NSG automatically tracks the state of network connections and allows return traffic for established sessions without requiring explicit rules for the return traffic.

---

### **What Does Stateful Mean in Networking?**

A stateful firewall or security group keeps track of the state of active connections (e.g., TCP, UDP, or ICMP sessions). It uses this information to dynamically allow return traffic that is part of an established session.

For example:

1. If an outbound connection is initiated from a virtual machine (VM) to an external server, the NSG will automatically allow the response traffic from the server back to the VM.
    
2. Similarly, if an inbound connection is allowed by an NSG rule, the return traffic for that session is also permitted.
    

### **TL;DR**

* A **stateful NSG** in Azure automatically allows return traffic for established sessions.
    
* This simplifies rule management and improves security.
    
* Flow logs record traffic information, but the stateful behavior ensures that return traffic is handled without requiring additional rules.
    

---

### **How Does This Work in Azure NSGs?**

Azure NSGs are **stateful by default**. This means:

* You only need to define rules for the **initial traffic** (e.g., inbound or outbound).
    
* The NSG automatically handles the **return traffic** for established sessions.
    

---

### **Example**

Suppose you have an NSG rule that allows **inbound HTTP traffic (port 80)** to a VM:

* **Rule**: Allow inbound traffic on port 80 from any source.
    
* When a client sends an HTTP request to the VM, the NSG allows the request because it matches the rule.
    
* The VM processes the request and sends a response back to the client.
    
* The NSG automatically allows the response traffic (even though there is no explicit rule for it) because it is part of an established session.
    

---

### **Key Benefits of Stateful NSGs**

1. **Simplified Rule Management**:
    
    * You don’t need to create separate rules for return traffic.
        
    * This reduces the complexity of managing NSG rules.
        
2. **Improved Security**:
    
    * Only traffic that is part of an established, allowed session is permitted.
        
    * This reduces the risk of unauthorized traffic.
        
3. **Efficient Traffic Handling**:
    
    * Return traffic is automatically allowed, reducing the need for redundant rules.
        

---

### **Limitations**

* **Stateless Protocols**: For stateless protocols like UDP or ICMP, the NSG still treats them as stateful by tracking the flow of packets. However, this is less precise than with stateful protocols like TCP.
    
* **Asymmetric Routing**: If traffic takes a different path for inbound and outbound traffic (e.g., through different network appliances), the NSG may not recognize the return traffic as part of an established session.
    

---

### **Flow Records and Statefulness**

Azure NSGs use **flow logs** to record information about traffic that is allowed or denied by the NSG rules. These logs include:

* Source and destination IP addresses.
    
* Source and destination ports.
    
* Protocol (TCP, UDP, etc.).
    
* Whether the traffic was allowed or denied.
    

The stateful nature of NSGs ensures that flow logs only need to record the initial traffic, as return traffic is automatically handled by the NSG.

---

# [**References**](https://www.geeksforgeeks.org/deniel-service-prevention/)

* [https](https://www.geeksforgeeks.org/deniel-service-prevention/)://docs.microsoft.com/en-us/troubleshoot/azure/active-directory/troubleshoot-dynamic-groups
    
* https://oxfordcomputertraining.com/glossary/pass-through-[authentication/](https://www.geeksforgeeks.org/deniel-service-prevention/)
    
* [https://csrc](https://www.geeksforgeeks.org/deniel-service-prevention/).nist.gov/publications/detail/sp/800-207/final
    
* Microsoft Cloud Security Benchmark v1
    
* [https://learn.microsoft.com/en-au/training/modules/specify-requirements-securing-saas-paas-iaas-services/4-specify-security-requirements-web-workloads](https://learn.microsoft.com/en-au/training/modules/specify-requirements-securing-saas-paas-iaas-services/4-specify-security-requirements-web-workloads)
    
* [https://learn.microsoft.com/en-us/security/adoption/mcra](https://learn.microsoft.com/en-us/security/adoption/mcra)
    
* [https://www.geeksforgeeks.org/software-testing-fuzz-testing/](https://www.geeksforgeeks.org/software-testing-fuzz-testing/)