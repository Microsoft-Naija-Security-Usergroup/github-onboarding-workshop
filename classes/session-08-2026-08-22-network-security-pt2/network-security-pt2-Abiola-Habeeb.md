# My Notes — Abiola Habeeb

---

## Key Concepts I Learned

This session continued Azure network security, focusing on **Azure Firewall, hub-and-spoke topology, service vs private endpoints, Microsoft Entra Private Access, and Network Watcher** (building on the earlier NSG/ASG session).

- **Five common network problems and their fixes.** A subnet exposed to any location (`0.0.0.0/0`) with no NSG → filter at the subnet with **NSG + ASG**; no firewall (uncontrolled outbound) → centralize egress through **Azure Firewall** in a hub subnet; PaaS (storage/SQL) on public endpoints → replace with **private endpoints**; legacy VPN giving full network access → retire it for **Entra Private Access**; and no diagnostics → validate with **Network Watcher**.
- **NSG anatomy.** Rules are inbound/outbound with an Allow or Deny action; **lower priority number wins and first match wins**, so plan number ranges (e.g. 200s for management, leave room to insert a lower-numbered deny later) rather than starting at 100. Targets can be a specific IP, a CIDR range, a **service tag**, an **application security group**, or VirtualNetwork/Internet/Any. Every NSG ships with six default rules at 65000–65500 (including AllowVnetInBound and AllowInternetOutbound) — your rules win because they use lower numbers.
- **Application Security Groups (ASG).** Instead of writing rules against IP addresses, group NICs by workload (web/app/management) and write **role-based** rules against the group. This scales out (add a VM to the ASG) without rewriting subnet or IP rules.
- **Azure Firewall.** Unlike NSGs (which are 5-tuple only), the firewall does **FQDN filtering** (e.g. allow `*.openai.com`, deny the rest), **threat-intelligence** filtering of known-malicious IPs/domains (Standard SKU alerts and denies; Basic SKU alerts only), and **centralized policy** across hubs. Mental model: an NSG is the lock on a room; the firewall is the security desk in the lobby checking name, intent, and reputation. NSG applies to a subnet/NIC; the firewall applies to the VNet.
- **Hub-and-spoke topology.** Spokes peer to a central **hub VNet** that holds the firewall (and shared services like Bastion and DNS); there is no spoke-to-spoke peering, and **user-defined routes (UDR)** push all spoke traffic through the firewall so every ingress, egress, and inter-spoke flow is inspected.
- **Service endpoints vs private endpoints.** Both keep PaaS traffic off the public internet, but only a **private endpoint removes the public endpoint** — it gives the resource a private IP (NIC) in your VNet via Azure Private Link, auto-creates a private DNS zone, lets you disable public access, and is reachable from peered VNets and on-prem over VPN. A **service endpoint** keeps the service's public IP, routes over the Azure backbone, has no private DNS or on-prem reach, and is free.
- **Microsoft Entra Private Access vs legacy VPN.** Legacy VPN authenticates once, hands the user an IP with access to the whole network, checks conditional access only at connect time, and needs a public VPN endpoint (an attack surface, worsened by shared certificates). **Entra Private Access** is app-level and identity-conditional — per-app access, continuous conditional access (MFA per session), outbound-only via a private connector, no public endpoint. VPN trusts the network; Private Access trusts the user, device, and app at every request (zero trust).
- **Network Watcher.** Auto-created per region with any VNet. Tools include **IP Flow Verify** (check whether a port is allowed and which rule hit it), **Effective Security Rules**, **Next Hop**, **NSG Diagnostics**, **Connection Monitor**, **Topology**, and **Traffic Analysis**.

---

## Lab / Hands-On Work

### What I did


### What happened / Result


### Challenges I faced


---

## My Takeaways

Through this training I now understand how the network controls layer together into defense in depth. NSGs and ASGs filter at the subnet/NIC, but they can't reason about domain names or reputation — that's where Azure Firewall comes in, and in a hub-and-spoke design a single firewall in the hub inspects everything because user-defined routes force all spoke traffic through it. The demo made the routing real: after associating a route table with the workload subnet and adding a `0.0.0.0/0` next-hop to the firewall's private IP, the VM's effective routes switched from the default system routes to the firewall, and browsing only worked for FQDNs I explicitly allowed. On the identity side, the biggest shift is retiring legacy VPN (which trusts the network) for Entra Private Access (which grants per-app, continuously-verified access) — the same zero-trust principle we keep returning to. Network Watcher's IP Flow Verify is the tool I'll reach for first when a connection is unexpectedly blocked.

---

## Questions I Still Have

- In a hub-and-spoke design, what's the right way to combine NSGs on each spoke subnet with the central firewall so rules don't conflict or get bypassed?
- For Entra Private Access, how is the private network connector deployed and sized, and what does the rollout look like alongside an existing VPN?
- When should I choose a service endpoint over a private endpoint, given the private endpoint is more secure but costs more and adds DNS complexity?

---

## Resources I Found Useful

- Bootcamp — Naija AI and Cloud Security (Microsoft Naija Security Usergroup) GitHub
- [Protect network infrastructure in Azure — learning path](https://learn.microsoft.com/en-us/training/paths/secure-networking/)
- [Implement network security in Azure (NSGs, service endpoints, Network Watcher)](https://learn.microsoft.com/en-us/training/paths/implement-network-security/)
- [Azure Firewall documentation](https://learn.microsoft.com/en-us/azure/firewall/)
- [Manage Azure Private Endpoints (Azure Private Link)](https://learn.microsoft.com/en-us/azure/private-link/manage-private-endpoint)
- [SC-500 study guide — Cloud and AI Security Engineer](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500)

---

*Submitted by: Abiola Habeeb · https://github.com/abiolahabeeb*
