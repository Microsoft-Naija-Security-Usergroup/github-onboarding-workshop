# My Notes — Ejike Etolue

---

## Key Concepts I Learned

- **Scope Hierarchy & Least Privilege in RBAC:** Azure RBAC evaluates permissions top-down from Management Groups $\rightarrow$ Subscriptions $\rightarrow$ Resource Groups $\rightarrow$ Resources. Over-assigning roles at higher scopes creates broad blast radiuses; permissions should be scoped at the Resource Group level wherever possible.
- **Custom RBAC Roles & Limits:** Custom roles define precise permissions using `Actions` (control plane), `NotActions` (subtractions), `DataActions` (data plane operations like reading blob/vault contents), and `AssignableScopes`. Subscriptions enforce a ceiling of 4,000 role assignments.
- **Evaluating Over-Privileged Access:** Remediating stale or excessive permissions is managed through Microsoft Entra Access Reviews and Defender for Cloud CSPM, converting standing assignments into Privileged Identity Management (PIM) eligible roles with time-bound activations.
- **Azure Backup Defense in Depth:** Backup vaults are hardened against ransomware/insider threats via Soft Delete (14 to 180 days), Vault Immutability (WORM lock), Customer-Managed Keys (CMK), and Multi-User Authorization (MUA) using a Resource Guard hosted in an isolated subscription.
- **Infrastructure as Code (IaC) Security:** Scanning Bicep/ARM templates prior to deployment via Microsoft Security DevOps (MSDO) or Checkov in CI/CD pipelines catches misconfigurations early. Parameters holding secrets must use the `@secure()` decorator or pull directly from Key Vault rather than clear-text parameters.

---

## Lab / Hands-On Work

### What I did
- Attended the live Saturday session covering RBAC scope boundaries, custom role JSON structures, Azure Backup security posture tiers, and IaC template scanning with MSDO.
- Evaluated the architectural workflow for configuring Multi-User Authorization (MUA) using Resource Guard to require secondary administrator sign-off for destructive backup operations.
- Analyzed secure Bicep authoring patterns, including secret references to Azure Key Vault and replacing service principal secrets with Managed Identities.

### What happened / Result
- Mastered the configuration logic for scoping least-privilege custom RBAC definitions and securing backup retention policies against unauthorized purge attempts.

### Challenges I faced
- We still haven't been provisioned access to the partner student/test Azure environment. Because of this, I couldn't execute the Bicep template deployments or test custom role creations directly in Azure without incurring personal costs.

---

## My Takeaways

Effective cloud security requires locking down both the identity plane and the deployment pipeline. Using PIM and Access Reviews cleans up standing admin rights, while embedding automated IaC security checks into CI/CD pipelines prevents misconfigured infrastructure from ever reaching production.

---

## Questions I Still Have

- When setting up Multi-User Authorization (MUA) with a Resource Guard, what is the recommended cross-tenant setup if an organization uses separate Entra ID tenants for security oversight versus production workloads?
- How does Microsoft Security DevOps (MSDO) handle custom policy exceptions during CI/CD pipeline builds when a low-risk finding is intentionally waived by the engineering team?

---

## Resources I Found Useful

- **Session Recording:** [Enforce security governance and regulatory compliance - Part 2 (MNSUG YouTube)](https://youtu.be/bj760qx1MSQ)
- **GitHub Workshop Directory:** [MNSUG GitHub Onboarding Workshop Repository](https://github.com/AGK001/github-onboarding-workshop)

---

*Submitted by: Ejike Etolue · AGK001*