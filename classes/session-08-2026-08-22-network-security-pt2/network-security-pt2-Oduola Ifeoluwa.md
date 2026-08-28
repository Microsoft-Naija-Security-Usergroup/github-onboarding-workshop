# My Notes — ODUOLA Ifeoluwa


## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- Azure Firewall's capabilities for FQDN filtering, threat intelligence, and centralized policy management were explained and demonstrated.
- The importance of using private endpoints over public endpoints for services like storage accounts and SQL databases was emphasized.
- Network Watcher was showcased as a tool for network monitoring and troubleshooting, with features like IP flow verify and topology analysis.

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did
- Created a virtual network named "test-FW-VN" with subnets for workload, jump server, and Azure Firewall management.
- Deployed two virtual machines: "SRV-JUMP" (jump box with a public IP) and "SRV-WORK" (workload server with only a private IP).
- Deployed Azure Firewall and configured its associated subnet and public IP.
- Created a route table named "firewall-routes" and associated it with the workload subnet.

### What happened / Result
- The Azure Firewall successfully controlled traffic, allowing access to "www.bing.com" and DNS, while blocking access to "www.microsoft.com" due to the absence of a specific allow rule.
- The hub-and-spoke network setup with traffic routing through the firewall was effectively demonstrated.
- The lab successfully illustrated how to isolate servers using subnets and control their internet access via firewall rules.

### Challenges I faced
Encountered an issue where the Azure Firewall creation failed initially due to the missing "Azure firewall management subnet," which required adding the subnet and re-initiating the firewall deployment.

- Network connectivity seemed slow at times, impacting the speed of resource deployment and testing.

---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->


---It was incredibly valuable for understanding the practical application of Azure Firewall in a hub-and-spoke architecture. Seeing how to configure the firewall rules (application and network) to control specific FQDN access and port traffic provided clear, actionable knowledge. The demonstration of routing traffic through the firewall using user-defined routes was particularly insightful for securing network communications. It also highlighted the importance of proper planning, including subnet design and resource naming conventions, for efficient and secure cloud deployments.

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

- What are the key differences and advantages of using Azure Firewall Manager compared to the classic firewall configuration shown in the demo?

- Could you provide more details on the specific use cases and benefits of enabling the "firewall management nick" and the "NAT gateway"?


---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

-

---

*Submitted by: ODUOLA Ifeoluwa · ife005*
