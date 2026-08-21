# My Notes — Ejike Etolue

---

## Key Concepts I Learned

- **Secrets vs. Keys vs. Certificates:** Secrets act like plain-text passwords or connection strings used by apps; Keys handle raw cryptographic lifting like encrypting virtual hard disks; Certificates protect web traffic via TLS bindings through providers like DigiCert or GlobalSign.
- **The Control Plane vs. Data Plane Trap:** This is a huge distinction for security teams. The Control Plane is the outer perimeter (building the vault, configuring firewalls), while the Data Plane is the inner lockbox (reading/writing the actual secrets inside). Having 'Contributor' rights on the vault only gives you control plane access, it does not automatically let you see the secrets inside.
- **Azure RBAC Migration over Legacy Policies:** The old Vault Access Policies are officially legacy and will be phased out by Microsoft next year. Shifting to Azure RBAC is mandatory to maintain a proper Zero Trust posture and ensure every single secret access event is fully auditable.
- **Managed Identities (MSI) as Credential Killers:** Using System-Assigned or User-Assigned identities completely eliminates the dangerous developer habit of hardcoding clear-text API tokens or passwords directly inside app configuration files.
- **Soft Delete and Purge Protection Guardrails:** Soft Delete serves as a recycling bin (retaining deleted vaults for 7 to 90 days) and is on by default. Purge Protection completely padlocks the door, once enabled, nobody (not even Microsoft support) can force-delete the vault until the retention timer clears, though it can create major billing surprises on high-end Managed HSMs if misconfigured.

---

## Lab / Hands-On Work

### What I did

- Walked through the lab demonstration where the mentor spun up a Windows App Service web app, enabled its System-Assigned Managed Identity, and used an automated PowerShell script via Kudu console to retrieve a hidden secret string (`foundry-API-key`) from a Key Vault.

### What happened / Result
- The initial script run threw a `403 Forbidden` access error because the Key Vault was still running on the legacy Vault Access Policy model.
- Once the vault authorization model was toggled to Azure RBAC and granted the explicit "Key Vault Secret User" role, the script successfully fetched the bearer token and printed the raw secret value (`cloud security$500`).

### Challenges I faced
- Context-switching between heavy workload at the office, Q3 cram sessions for my AZ-104 networking labs, and catching up on this SC-500 bootcamp requires serious mental gymnastics. Luckily, drawing on my SC-300 foundation made it easy to follow the mentor's live RBAC troubleshooting without getting lost in the syntax.

---

## My Takeaways

Managing infrastructure security means accepting that developers will naturally try to cut corners and embed raw passwords in source code just to make things run fast. Flipped access policies or open network firewalls turn a Key Vault from a secure safety deposit box into an open window. Enforcing Azure RBAC and Managed Identities allows us to secure AI and cloud workloads natively without introducing operational friction, ensuring no single application holds a master key to our backend environment.

---

## Questions I Still Have

- If Purge Protection is absolute and cannot be turned off once enabled, what is the best practice method for halting hourly billing accumulation on an accidentally deployed Managed HSM vault without waiting out the full 90-day retention countdown?
- With my current Q3 schedule stretched thin between heavy work demands and AZ-104 prep, what are the absolute core security baselines in this SC-500 track I should prioritize to ensure I hit my Q4 exam target without burning out?

---

## Resources I Found Useful

- **Class 2 Video Replay:** [Secure Azure Key Vault with defense in depth for the cloud & AI workload - MNSUG YouTube](https://youtu.be/GKqpej4X9B0)
- **Central Workspace:** [GitHub Onboarding Workshop Repository - Main Classes Directory](https://github.com/AGK001/github-onboarding-workshop)

---

*Submitted by: Ejike Etolue · AGK001*