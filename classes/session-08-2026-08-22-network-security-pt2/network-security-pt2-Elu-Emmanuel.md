# My Notes — Elu Uchenna Emmanuel

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- Azure Firewall
- Hub and Spoke topology
- Service endpoint versus private endpoints
- Microsoft Entra private access versus VPN
- Network Watcher tools (IP Flow verify, Topology etc.)

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did
- Created Azure Firewall lab
  
  <img width="654" height="307" alt="image" src="https://github.com/user-attachments/assets/ec3e0dae-86f9-443d-97ab-4bcf840412c8" />

- Created vnet with 2 subnets (workload subnet and jump host subnet)
- Created a custom route that ensures all outbound workload traffic from the workload subnet must use the firewall
- Firewall Application rules that only allow outbound traffic to www.bing.com
- Firewall Network rules that allow external DNS server lookups

### What happened / Result


### Challenges I faced


---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->
- Securing Azure networks requires more than controlling access. It requires proper segmentation, centralized traffic inspection, intelligent routing, and continuous visibility into network connectivity.

---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

-
-

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- https://www.youtube.com/watch?v=UTo-odhI2PQ&list=PLa-LpBaTz1E9aeXW-vgAzwZDOq3viw3CC
- https://learn.microsoft.com/en-us/training/paths/implement-network-security-controls-azure/

---

*Submitted by: Elu Uchenna Emmanuel · eluemma*
