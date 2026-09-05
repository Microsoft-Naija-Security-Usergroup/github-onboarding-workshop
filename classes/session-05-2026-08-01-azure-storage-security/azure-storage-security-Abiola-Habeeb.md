# My Notes — Abiola Habeeb

---

## Key Concepts I Learned

This session covered **securing Azure Storage with defense in depth** — how to lock down a storage account for cloud and AI workloads.

- **What a storage account is.** A unique namespace in Azure that holds all your storage objects, exposed through four services: **Blobs** (unstructured data — images, video, backups, logs, ML training data), **Files** (SMB/NFS shares, mountable), **Queues** (messaging/alerts), and **Tables** (schemaless NoSQL for structured data). Each has an endpoint URL of the form `<account>.<service>.core.windows.net`. Data is **encrypted at rest by default with AES-256** (cannot be disabled).
- **Resilience choices.** Redundancy — **LRS** (3 copies, one data center, cheapest), **ZRS** (across 3 availability zones), **GRS** (async copy to a paired region), **GZRS** (both, most expensive/critical). Access tiers — **Hot / Cool / Cold / Archive** (archive is cheapest to store but slow and costly to rehydrate).
- **Why public access is the wrong default.** The main anti-patterns are: public blob/network access left enabled, shared key used for every app, no firewall/VNet rules, and access keys embedded in code or config. Left open, the **attack chain** is: public/legacy access → credential discovered (key or SAS token leaked via repos, logs, dumps) → privilege reuse → data exfiltration / ransomware / lateral movement. The **account key is like a BVN** — it grants full access to the entire storage account, so it belongs in Key Vault, never in code.
- **Data plane vs management plane.** The **management plane** (create/delete/configure the account, firewall rules, RBAC, key rotation) is gated by **Azure RBAC and is not blocked by the firewall**. The **data plane** (read/write/list/delete the actual data) **is** controlled by the firewall and by SAS scoping.
- **Authorization models.** Prefer **Microsoft Entra ID + RBAC** for data access over shared keys. **Shared Access Signatures (SAS)** enforce least privilege by scoping to specific services, permissions, and a time window. An **account SAS** is signed by an account key (rotating the key breaks it), while a **user delegation SAS** is signed by Entra ID credentials and survives key rotation. **Stored access policies** let you centrally define and later revoke/adjust permissions without re-issuing tokens. Best practice is to **disable shared-key authorization** (enforceable via Azure Policy).
- **Network controls.** Restrict access with **firewall rules and virtual-network restrictions**, or disable public network access entirely and use a **private endpoint** (which gives the storage account a network interface on your VNet so only resources on that network can reach it). **Resource instance rules** and **trusted service exceptions** allow specific Azure services through.
- **Microsoft Defender for Storage** detects threats such as malicious access, data exfiltration, and malware upload. It is priced per storage account plus a per-GB malware-scanning charge, and can be enabled/enforced across the environment via Azure Policy.

---

## Lab / Hands-On Work

### What I did


### What happened / Result


### Challenges I faced


---

## My Takeaways

Through this training I now understand that securing storage is really about closing doors and shrinking the blast radius. The account key is the single most dangerous secret — because it grants full, unscoped access to every container, file, queue, and table — so the whole discipline is about replacing it with scoped, revocable access: Entra ID + RBAC, or a tightly-scoped SAS with a short expiry. The demo made the difference concrete: a read-only SAS let me view and download a blob but blocked deletion, and disabling anonymous access meant the raw blob URL returned "public access not permitted." Layering network controls (firewall, VNet restrictions, private endpoints) on top of identity controls, and enforcing it all with Azure Policy, is what defense in depth looks like for storage.

---

## Questions I Still Have

- What's the cleanest way to migrate an environment off shared-key authorization to Entra ID + RBAC without breaking existing applications?
- When should I choose a user delegation SAS over a stored access policy, given both aim to keep access revocable?
- For private endpoints, what DNS configuration is needed so on-prem and cross-VNet clients resolve the storage account privately?

---

## Resources I Found Useful

- Bootcamp — Naija AI and Cloud Security (Microsoft Naija Security Usergroup) GitHub
- [SC-500 study guide — Implementing End-to-End Security Controls for Cloud and AI Workloads](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500)
- [Plan and implement security for storage (training module)](https://learn.microsoft.com/en-us/training/modules/security-storage)
- [Secure storage for Azure Files and Azure Blob Storage (learning path)](https://learn.microsoft.com/en-us/training/paths/implement-storage-azure-files-azure-blob-storage/)
- [Azure Storage documentation](https://learn.microsoft.com/en-us/azure/storage/)
- [Manage Azure Private Endpoints (Azure Private Link)](https://learn.microsoft.com/en-us/azure/private-link/manage-private-endpoint)

---

*Submitted by: Abiola Habeeb · https://github.com/abiolahabeeb*
