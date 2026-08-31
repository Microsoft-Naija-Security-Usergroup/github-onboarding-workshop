# My Notes — Elu Uchenna Emmanuel

> **How to use this file:**
> 1. **Download** this file to your computer — click the **Raw** button on GitHub, then right-click and *Save As*, OR click the download icon at the top-right of the file view
> 2. **Rename** the downloaded file — replace `yourname` with your actual first and last name in lowercase, separated by hyphens, e.g. `microsoft-entra-oyimafu-emmanuel.md`
> 3. **Open** the renamed file in any text editor (Notepad, VS Code, TextEdit) and fill in your notes below
> 4. **Upload** your file to GitHub — go into this session folder on your forked repo, click **Add file → Upload files**, drag in your completed file, then click **Commit changes**
> 5. **Open a Pull Request** back to the main repo — the facilitator will review your notes before merging

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- Azure Firewall
- Hub and Spoke topology
- Service endpoint versus private endpoints
- Microsoft Entra private access versus VPN
- Network Watcher

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did
- Create Azure Firewall lab
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
