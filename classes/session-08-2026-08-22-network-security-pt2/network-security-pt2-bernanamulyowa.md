# My Notes — BERNA NAMULYOWA



## Key Concepts I Learned



**Common issues with Network Security**

* Subnet exposed to any traffic. solution Filter at the subnet with NSGs and ASGs
* No Azure firewall that is no FQDN control. solution Centralize egress through Azure Firewall in a hub VNet.
* Storage account and SQL DB use public endpoints, no private link. Solution Replace PaaS public endpoints with Private endpoint.
* Engineers reach internal admin UI through legacy VPN with full network access. Solution Retire the VPN give users app-only access through Entra Private Access.
* Network watcher disabled in the region-no diagnostic surface. Solution Validate the result with Network Watcher diagnostics



**NSG Structure - anatomy of the rule**

NSG has inbound and outbound. Inbound is traffic in and outbound is traffic going out

The lower the number the higher the priority



#### AZURE FIREWALL

Azure Firewall adds the following compared to NSGs:

FQDN filtering: FQDN works with names and not IPs thus NSGs cannot do FQDN filtering.

Blocks traffic to and from malicious IPs and domains.

**Standard SKU** works with ***Alert and Deny*** and **Basic SKU** works with ***Alert only.***

Helps you create a centralized policy.

***NSGs*** is applied to the ***subnets and network interface*** while ***firewall*** is applied to the ***virtual network***.





#### HUB AND SPOKE TOPOLOGY

***Why Hub and Spoke topology?***

* One firewall inspects all egress and inter-spoke traffic.
* Spokes peer to the hub no spoke-to-spoke peering.
* User-Defined Routes (UDR) push spoke traffic through the firewall.
* Shared services (Bastion, AD, DNS) live in the hub.

The hub virtual network hosts several Azure networking services and these can be used by workloads that are hosted in the spoke virtual network. It is the primary point of egress providing connections to different spokes for cross-virtual network traffic.



Spoke Virtual networks these isolate and manage workloads separately in each spoke. Spokes can represent different environments and exist in different subscriptions and a workload can spread across multiple spokes.







#### SERVICE ENDPOINTS VERSUS PRIVATE ENDPOINTS

Both keep PaaS traffic off the public internet. Only one removes the public endpoint.

||SERVICE END POINT|PRIVATE ENDPOINT|
|-|-|-|
|IP ADDRESS|Keep the Public IP of the PaaS resource and don't assign a private IP|Keep traffic entirely inside your private network interface.|
|TRAFFIC PATH|Route traffic through the Microsoft backbone network while still targeting the public endpoint.|Keep traffic entirely inside your private network interface.|
|DNS CONFIGURATION|Don't require DNS changes.|Require DNS reconfiguration to resolve the service name to the private IP.|
|ON-PREMISES ACCESS|Don't support on-premises traffic via VPN or ExpressRoute.|Seamlessly support hybrid connectivity from on-premises networks.|
|COST|Are free of charge|Incur hourly charges and data processing fees.|
|SECURITY|Retain public endpoint that can be restricted by network rules.|Allows you to completely disable public access for a smaller attack surface.|





&#x20;

#### MICROSOFT ENTRA PRIVATE ACCESS VERSUS VPN

|**Aspect**	|**Entra Private Access**|**Traditional VPN**|
|-|-|-|
|Model|Zero Trust — access per app/resource|Perimeter-based — broad network access once connected|
|Auth|Entra ID + Conditional Access (MFA even on legacy protocols)|AD/RADIUS-based; limited Conditional Access|
|Infrastructure|Cloud-native, lightweight outbound connectors|On-prem gateways, RADIUS/NPS, certs, load balancers|
|Attack Surface|No exposed inbound ports|Public-facing gateway, common attack target|
|Performance|Routed via Microsoft's global edge network|Backhauled through central data center|
|Client|Global Secure Access client; needs Entra-joined device; no pre-logon support|Native VPN client; supports pre-logon/device tunnel|
|Admin Overhead|Low — centrally managed, no gateway patching|Higher — ongoing patching, cert lifecycle, capacity planning|
|Cost|\~$12/user/month (Entra Suite)|Varies by vendor, often bundled with firewall|
|Best For|Cloud-first orgs, Entra-joined devices|Domain-joined fleets needing pre-logon/broad access|





#### NETWORK WATCHER



## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

* https://learn.microsoft.com/en-us/azure/architecture/networking/architecture/hub-spoke

\---

*Submitted by: bernanamulyowa · nbernah*

