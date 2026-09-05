# My Notes — Abiola Habeeb

---

## Key Concepts I Learned

This was Part 1 of implementing network security controls in Azure, focused on the foundations: **virtual networks, subnets, Network Security Groups (NSGs), and Application Security Groups (ASGs)**.

- **Virtual networks and subnets.** A **virtual network (VNet)** is your private, isolated network in Azure, defined by an address space (e.g. `10.0.0.0/16`). It's divided into **subnets** (e.g. `10.0.1.0/24`) that segment workloads — web, application, database, management — so each can be secured independently. Segmentation is the first step of network defense: keep tiers apart so a compromise in one doesn't automatically reach the others.
- **Network Security Groups (NSGs).** An NSG is a stateful set of allow/deny rules that filters traffic to and from a **subnet** or a **network interface (NIC)**. Being **stateful** means that if inbound traffic is allowed, the return traffic is allowed automatically (and vice versa). Each rule specifies direction (inbound/outbound), source and destination, port and protocol, an action (Allow/Deny), and a priority.
- **Rule priority.** Rules are evaluated from **lowest priority number to highest, and the first match wins** — once a rule matches, no later rules are checked. Plan your numbering with gaps (e.g. management in the 200s, apps in the 300s) so you can insert a higher-priority rule later without renumbering.
- **Default rules.** Every NSG includes built-in rules at priority 65000–65500: inbound allows traffic within the VNet and from the Azure load balancer then denies everything else, and outbound allows traffic within the VNet and to the internet then denies the rest. Your custom rules override these because they use lower numbers.
- **Ways to target traffic.** A rule's source or destination can be a specific **IP address**, a **CIDR range**, a **service tag** (a Microsoft-maintained label for a service's IP ranges, e.g. Storage or AzureCloud, so you don't track changing IPs), an **application security group**, or the built-in tags VirtualNetwork / Internet / Any.
- **Application Security Groups (ASGs).** An ASG lets you group NICs by workload role (web, app, database) and then write NSG rules that reference the **group** instead of individual IP addresses. This makes rules readable and lets you scale — adding a new VM to the ASG automatically applies the existing rules, with no rule rewrites.
- **How NSGs and ASGs work together.** You attach VMs to an ASG by role, then write NSG rules like "allow the web ASG to reach the app ASG on port 443." The intent is expressed in terms of roles, which is far more maintainable than a list of IPs and is the recommended pattern for workload rules (with service tags for Microsoft services and specific IPs for on-prem or partners).

---

## Lab / Hands-On Work

### What I did


### What happened / Result


### Challenges I faced


---

## My Takeaways

Through this training I now understand that network security in Azure starts with structure, not just rules. Laying out a VNet and cutting it into purpose-built subnets is what makes everything else possible — you can't isolate a database tier that shares a subnet with the web tier. NSGs then enforce the boundaries, and because they're stateful and evaluated first-match-by-priority, the discipline is in planning the priority numbers and being explicit about what's allowed rather than relying on the defaults. The concept that clicked most for me was the ASG: writing rules against workload roles instead of IP addresses turns a brittle, hard-to-read ruleset into something that scales as VMs come and go. This foundation is what the later Azure Firewall and hub-and-spoke design build on top of.

---

## Questions I Still Have

- When an NSG is applied at both the subnet and the NIC, how are the two rule sets evaluated together, and which effectively wins?
- What's the best practice for naming and numbering NSG rules across many subnets so they stay consistent and auditable?
- How do I use NSG flow logs and Network Watcher to confirm a rule is actually doing what I intended?

---

## Resources I Found Useful

- Bootcamp — Naija AI and Cloud Security (Microsoft Naija Security Usergroup) GitHub
- [Implement network security in Azure (NSGs, service endpoints, Network Watcher) — learning path](https://learn.microsoft.com/en-us/training/paths/implement-network-security/)
- [Protect network infrastructure in Azure — learning path](https://learn.microsoft.com/en-us/training/paths/secure-networking/)
- [Azure Virtual Network documentation](https://learn.microsoft.com/en-us/azure/virtual-network/)
- [SC-500 study guide — Cloud and AI Security Engineer](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500)

---

*Submitted by: Abiola Habeeb · https://github.com/abiolahabeeb*
