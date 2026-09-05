# My Notes — Promise Ibediogwu

---

## Key Concepts I Learned

- How to move from flat, open networks to a centralized hub-and-spoke model where all traffic gets inspected by an Azure Firewall before it reaches its destination.
- The difference between Network Security Groups (NSGs) and Azure Firewall: NSGs only do basic 5-tuple filtering (source/destination IP, port, protocol), while Azure Firewall can filter by FQDN (e.g. `*.openai.com`) and uses threat intelligence feeds — something NSGs simply can't do.
- How User-Defined Routes (UDRs) work: instead of relying on Azure's default system routes, you can create a route table that forces traffic (e.g. `0.0.0.0/0`) through the firewall's private IP as the "next hop," so nothing leaves the network unchecked.
- Why Application Security Groups (ASGs) are better practice than writing rules against static IPs — rules are written against a workload's role/tag (e.g. "WebServers"), so they don't break every time a server is redeployed with a new IP.
- The role of Azure Network Watcher in troubleshooting — specifically IP Flow Verify (checks if a packet is allowed/denied based on NSG rules), Effective Routes (confirms UDRs actually overrode the system routes), and Next Hop (confirms the path traffic is taking).
- The importance of subnet isolation (e.g. separating a Jumpbox subnet from a Workload subnet) to reduce the "blast radius" if one part of the environment is compromised.
- The distinction between Service Endpoints (still expose the service's public IP but travel over the Azure backbone) and Private Endpoints (assign the service a private IP inside the VNet, removing public exposure entirely, but requiring Private DNS zone setup).

---

## Lab / Hands-On Work


### What I did
I didn't carry out a personal hands-on lab for this session — I followed along and studied the process as the mentor (Oyimafu Emmanuel) demonstrated it live. The walkthrough covered:

1. Deploying a VNet (`10.0.0.0/16`) with three subnets: the reserved `AzureFirewallSubnet`, a `JumpSubnet`, and a `WorkloadSubnet`.
2. Deploying a Standard SKU Azure Firewall (deliberately avoiding Premium SKU to keep lab costs down), which also required a dedicated `AzureFirewallManagementSubnet` and its own separate public IP.
3. Configuring the firewall with Network Rules (e.g. allowing DNS over UDP 53) and Application Rules (allowing specific FQDNs).
4. Creating a Route Table, associating it with the Workload subnet, and adding a route sending `0.0.0.0/0` traffic to the firewall's private IP as the next hop — force-tunneling all outbound traffic through the firewall for inspection.
5. Updating the Jumpbox/Workload VM DNS settings so name resolution would also pass through the firewall correctly.

### What happened / Result
Following the mentor's steps, the workload subnet's traffic was successfully forced through the Azure Firewall rather than going straight out to the internet. Traffic could then be selectively allowed or blocked based on FQDN rules, demonstrating the difference between this and a basic NSG setup.

### Challenges I faced
Since I observed rather than executed the lab myself, my main challenge was mentally tracking the sequence of dependencies — for example, understanding why the firewall management subnet is mandatory and non-optional, and why DNS settings needed updating after the route change for resolution to keep working through the firewall.

---

## My Takeaways


The most valuable part for me was seeing why "default" is never secure by default — a flat network with system routes and no firewall in the path is inherently open. The session made it clear that real security is something you actively architect (via UDRs, hub-and-spoke, FQDN filtering), not something you get for free from Azure's defaults. I also found it useful that the mentor emphasized doing things manually first, before automation — it reinforces that understanding the underlying architecture matters more than memorizing a Terraform/Bicep script. The point about following an SOP not being a sign of ignorance, but a mark of consistency and security discipline, also stuck with me.

---

## Questions I Still Have


- When scaling this hub-and-spoke setup to multiple spokes/regions, how does peering interact with the firewall routing — does each spoke need its own route table pointing to the same central firewall?
- Beyond IP Flow Verify, Effective Routes, and Next Hop, are there other Network Watcher tools (e.g. Packet Capture, Connection Troubleshoot) worth learning for deeper diagnostics before moving to IaC?

---

## Resources I Found Useful


- Session recording/summary notes on Implementing Network Security Controls in Azure (Part 2) — Cloud & AI Security Boot Camp 2026
- [What is Azure Firewall?](https://learn.microsoft.com/en-us/azure/firewall/overview) — overview of Azure Firewall, FQDN filtering, and threat intelligence
- [Tutorial: Deploy and configure Azure Firewall and policy using the Azure portal](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal-policy) — hands-on walkthrough matching this session's lab (firewall subnet, route table, application/network rules)
- [Virtual network traffic routing](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview) — how system routes work and how User-Defined Routes override them
- [Hub-and-spoke network topology](https://learn.microsoft.com/en-us/azure/networking/design-guide/hub-spoke) — design principles for centralizing security enforcement at the hub
- [Network security groups and application security groups](https://learn.microsoft.com/en-us/azure/networking/design-guide/network-application-security-groups) — how ASGs group resources by role instead of static IP
- [Azure Network Watcher documentation](https://learn.microsoft.com/en-us/azure/network-watcher/) — hub page linking IP Flow Verify, Next Hop, and Effective Routes/Security Rules
- [Next hop overview](https://learn.microsoft.com/en-us/azure/network-watcher/next-hop-overview) — details on the Next Hop diagnostic tool used in this session

---

*Submitted by: Promise Ibediogwu · https://github.com/promibe*