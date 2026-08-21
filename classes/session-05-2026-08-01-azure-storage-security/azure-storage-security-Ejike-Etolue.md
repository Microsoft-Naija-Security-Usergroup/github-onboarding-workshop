# My Notes — Ejike Etolue

---

## Key Concepts I Learned

- **Data Plane vs. Management Plane Security:** Management plane operations (creating/deleting accounts, updating network rules) are controlled strictly by Azure RBAC at ARM layer. Data plane operations (reading, writing, deleting blobs/files) are authorized via Microsoft Entra ID RBAC, Shared Access Signatures (SAS), or Storage Account Shared Keys.
- **Access Key Risks & Shared Key Authorization:** Storage account access keys (Key 1 & Key 2) grant root-level administrative access across all account services (blobs, files, queues, tables). Best practice requires disabling shared key access globally via Azure Policy and enforcing Entra ID authentication instead.
- **SAS Token Types & Granular Control:** Account SAS spans all services, whereas Service SAS targets specific services/containers, and User Delegation SAS relies on Entra ID credentials without exposing account keys. Using Stored Access Policies on containers allows centralized lifecycle and permission management of SAS tokens.
- **Network Isolation & Private Endpoints:** Storage accounts are exposed publicly via default DNS endpoints. Restricting public network access to selected virtual networks or disabling it completely in favor of Private Endpoints (private NICs inside a VNet) removes public internet attack vectors.
- **Microsoft Defender for Storage:** Provides real-time threat detection, malware scanning on blob uploads (0.15 $/GB), and sensitive data threat detection across storage workloads to prevent data exfiltration and ransomware infiltration.

---

## Lab / Hands-On Work

### What I did
- Observed live Azure portal demonstrations covering storage account creation, blob container provisioning, and file upload workflows.
- Evaluated the behavioral difference between connecting via account-wide Connection Strings versus container-scoped Shared Access Signatures (SAS) within Azure Storage Explorer.
- Analyzed key rotation workflows and verified how rotating Key 1 immediately invalidates active SAS tokens signed by that key.
- Reviewed network access controls, including selected VNet restrictions, Private Endpoint interface provisioning, and Microsoft Defender for Storage configuration.

### What happened / Result
- Mastered the configuration mechanics for scoping least-privilege User Delegation SAS tokens, establishing Stored Access Policies, and enforcing TLS 1.2 / HTTPS-only secure transfer policies.

### Challenges I faced
- Partner test tenant environments have not yet been distributed to mentees. Consequently, I was unable to configure live Private Endpoints, deploy Bicep storage definitions, or test Defender for Storage threat scanning hands-on in a personal tenant due to billing constraints.

---

## My Takeaways

Exposing storage accounts through raw shared access keys creates a massive blast radius. Mandating Entra ID RBAC for data access, locking down network interfaces with Private Endpoints, and disabling anonymous public access turns Azure Storage into a resilient zero-trust baseline.

---

## Questions I Still Have

- How does Microsoft Defender for Storage handle automated quarantine or deletion when a zero-day malicious file payload is uploaded via SFTP or REST API?
- What is the most efficient disaster recovery strategy for rehydrating massive volumes of archived blobs during an emergency cross-region failover?

---

## Resources I Found Useful

- **Session Recording:** [Implement Security for Azure Storage (MNSUG YouTube)](https://youtu.be/HKW1jYi9wKE)
- **GitHub Workshop Directory:** [MNSUG GitHub Onboarding Workshop Repository](https://github.com/AGK001/github-onboarding-workshop)

---

*Submitted by: Ejike Etolue · AGK001*