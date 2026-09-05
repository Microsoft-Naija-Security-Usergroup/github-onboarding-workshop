# My Notes — IKECHUKWU EZEONU


---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->


  - **Network Segmentation Gaps**: Evaluated methods to minimize blast radius by partitioning networks into subnetworks, removing default open connectivity, and enforcing Zero Trust perimeter boundaries between environments.
  - **Network Security Groups (NSGs)**: Configured stateful firewall rules at subnet and NIC levels, leveraging priority-based rules, default rules, system tags (e.g., `VirtualNetwork`, `Internet`, `AzureLoadBalancer`), and Service Tags to simplify IP range management.
  - **Application Security Groups (ASGs)**: Grouped virtual machines logically based on application roles (e.g., `Asg-WebServers`, `Asg-AppServers`, `Asg-DbServers`) to write intent-based NSG security rules without managing static individual IP addresses.
  - **Azure Virtual Network Manager (AVNM)**: Scaled network governance across subscriptions and regions by creating network groups, dynamically managing connectivity topologies (Hub-and-Spoke, Mesh), and deploying Admin Rules to enforce mandatory security guardrails over standard NSGs.
  - **Verification via Network Watcher**: Used IP Flow Verify and Next Hop diagnostic tools to validate effective NSG rules, trace packet flow paths, and troubleshoot blocked or misrouted network traffic.


  - **Centralized Inspection Requirements**: Identified scenarios requiring stateful, centralized inspection, including enforcing egress filtering, preventing data exfiltration, threat intelligence-based filtering, and deep packet inspection (IDPS) for east-west and north-south traffic.
  - **Azure Firewall Rules & Policies**: Managed traffic filtering across Network Rules (IP/Port/Protocol), Application Rules (FQDNs and HTTP/S filtering), and NAT Rules (DNAT for incoming traffic). Utilized reusable Azure Firewall Policies to standardize rule sets hierarchy across multiple firewall deployments.
  - **Secured Virtual WAN Hub (Secure Hub)**: Integrated Azure Firewall into Azure Virtual WAN hubs to centrally route, inspect, and enforce security policies across branch offices, remote VPN clients, ExpressRoute connections, and spoke VNets across complex global networks.

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did

1. Created Application Security Groups for web and database tiers, binding them to corresponding VM network interfaces.
2. Configured an NSG with custom inbound and outbound security rules referencing ASGs as sources and destinations rather than explicit IP addresses.


### What happened / Result

- VM-to-VM traffic within subnets was successfully restricted to approved paths defined by ASG-based NSG rules.


### Challenges I faced


---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->

- **Rule Priority Conflicts** Learned that AVNM Admin Rules are evaluated *before* local NSG rules, meaning an explicitly blocked port in an AVNM policy cannot be overridden by a local NSG rule.
- **ASGs** drastically reduce administrative overhead and manual human error by allowing security rules to adapt dynamically as new VMs are added to application pools without editing IP lists.
- Centralized traffic inspection using Azure Firewall in a Hub-and-Spoke or Virtual WAN architecture is crucial for preventing exfiltration and maintaining strict compliance monitoring over outbound traffic.
- Leveraging Azure Virtual Network Manager allows security teams to enforce non-negotiable security guardrails at scale without restricting cloud workload owners from configuring app-specific NSG rules.


---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

-
-

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- **Assess Network Segmentation Gaps - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/segment-isolate-workloads-network-security-controls/2-assess-network-segmentation-gaps/)[cite: 1]
- **Control Traffic with Network Security Groups - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/segment-isolate-workloads-network-security-controls/3-control-traffic-network-security-groups/)[cite: 1]
- **Simplify Rule Management with Application Security Groups - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/segment-isolate-workloads-network-security-controls/4-simplify-rule-management-application-security-groups/)[cite: 1]
- **Azure Virtual Network Manager Overview**(https://learn.microsoft.com/en-us/azure/virtual-network-manager/overview)

---

*Submitted by: Ikechukwu Ezeonu · ikechukwu-ezeonu*
