# My Notes — Michael Chinonso Onwumere

## Key Concepts I Learned

- Learned that a common issue in cloud networking is a **subnet sitting directly on the Internet**, which exposes resources unnecessarily if not properly secured.
- Reviewed **Network Security Groups (NSGs)**, including their default rules and how custom rule sets can be built to control inbound and outbound traffic.
- Reviewed **Application Security Groups (ASGs)** as logical groupings used alongside NSGs to organize and simplify security rule management.
- Learned about **Azure Firewall** and what it adds beyond NSGs:
  - **FQDN Filtering** — Azure Firewall can filter traffic by domain name (e.g. allow `*.openai.com`, deny everything else), which NSGs cannot do since NSGs only work with five-tuple (source/destination IP, port, protocol) rules.
  - **Threat Intelligence** — Azure Firewall uses a Microsoft-fed threat intelligence feed to block traffic to and from known malicious IPs and domains. The Standard SKU supports Alert and Deny, while the Basic SKU only supports Alert.
  - **Centralized Policy** — Firewall Policy is a separate resource that can be attached to a firewall, allowing organizations to inherit a parent policy, override settings per region, and manage policies at scale through Firewall Manager.
- Learned about **Hub and Spoke topology** as a network design pattern where a central hub (often containing the firewall) manages and secures traffic to and from multiple spoke virtual networks.
- Learned the difference between **Service Endpoints and Private Endpoints** for securely connecting to Azure PaaS services.
- Learned the difference between **Microsoft Entra Private Access and VPN** as methods of secure remote connectivity.
- Learned about **Network Watcher** as a tool for monitoring, diagnosing, and gaining insight into network performance and health in Azure.

---

## Lab / Hands-On Work

### What I did

Due to permission restrictions on the Azure environment i use for the bootcamp, I was not able to fully carry out the hands-on exercise myself. Instead, I closely followed the instructor's live demonstration, which involved:

1. Reviewing a subnet configuration to identify the risk of a subnet being directly exposed to the Internet.
2. Revisiting **NSG default rules** and how custom rules are layered on top of them.
3. Observing how **Application Security Groups (ASGs)** are attached to NSG rules to organize resources.
4. Deploying an **Azure Firewall** instance and attaching a **Firewall Policy** to it.
5. Configuring an **FQDN filtering rule** to demonstrate allowing traffic to a specific domain while denying all other traffic.
6. Reviewing the **threat intelligence** settings on the firewall, comparing Alert-only mode (Basic SKU) against Alert-and-Deny mode (Standard SKU).
7. Walking through a **Hub and Spoke topology** design, with the firewall positioned in the hub VNet to centrally secure traffic from multiple spoke VNets.
8. Comparing **Service Endpoints vs Private Endpoints** for securing access to PaaS resources.
9. Comparing **Microsoft Entra Private Access vs VPN** as remote access options.
10. Briefly introducing **Network Watcher** as a tool for future lab sessions.

### What happened / Result

- I gained a clearer understanding of how Azure Firewall extends the protection provided by NSGs, especially through FQDN filtering and threat intelligence, which operate above the basic IP/port-level rules that NSGs are limited to.
- I understood how **Firewall Policy** allows security rules to be centrally managed and inherited across multiple firewalls/hubs, which is useful in larger environments.
- I saw how the **Hub and Spoke topology** centralizes security enforcement, making it easier to apply consistent policies across multiple virtual networks instead of securing each one individually.
- I was able to compare the trade-offs between Service Endpoints and Private Endpoints, and between Microsoft Entra Private Access and VPN, even though I could not configure them directly.
- Although I could not perform the configuration steps myself, following the demonstration helped me connect the concept of Azure Firewall to the NSG and ASG knowledge from the previous session.

### Challenges I faced

- Limited permissions in my Azure environment, prevented me from deploying and configuring the Azure Firewall and Firewall Policy myself.
- Understanding the distinction between FQDN filtering at the firewall level versus five-tuple filtering at the NSG level required extra attention.
- The differences between Service Endpoints and Private Endpoints, and between Microsoft Entra Private Access and VPN, were introduced quickly, so I need to review these further on my own.
- Despite the restrictions, I followed the instructor's demonstration closely and took detailed notes to reinforce my understanding of the concepts.

---

## My Takeaways

My biggest takeaway from this session is that **NSGs alone are not enough to secure a modern cloud network** — they operate only at the IP/port/protocol level, while Azure Firewall adds a higher layer of control through FQDN filtering, threat intelligence, and centralized policy management.

I also learned that network security design is not just about individual resources but about **topology**. Using a Hub and Spoke model with a centralized firewall makes it possible to enforce consistent security policies across many virtual networks rather than configuring each one separately.

This session builds directly on the previous one: where NSGs and ASGs control traffic at a granular, per-workload level, Azure Firewall and Firewall Policy provide broader, centralized control across the network as a whole.

---

## Questions I Still Have

- In what scenarios would a team choose Service Endpoints over Private Endpoints, given that Private Endpoints appear to offer stronger isolation?
- How does Microsoft Entra Private Access compare to VPN in terms of cost and ease of management for a growing organization?
- How does Network Watcher get used in practice to troubleshoot issues within a Hub and Spoke topology?
- What is the best way to structure Firewall Policies when managing multiple hubs across different regions?

---

## Resources I Found Useful

- Azure Firewall documentation
- Azure Firewall Policy and Firewall Manager
- Microsoft Threat Intelligence feed (Azure Firewall)
- Azure Hub and Spoke network topology
- Azure Service Endpoints vs Private Endpoints documentation
- Microsoft Entra Private Access
- Azure Network Watcher

---

*Submitted by: Michael Chinonso Onwumere · MichaelOnwumere*