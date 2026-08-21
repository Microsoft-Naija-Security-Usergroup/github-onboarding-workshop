# My Notes — Ejike Etolue

---

## Key Concepts I Learned

- **Azure Policy Definitions vs. Initiatives:** Policy definitions are individual JSON rules evaluating specific resource properties. Initiatives (policy sets) bundle multiple definitions together into standard compliance baselines (such as MCSB, NIST, or ISO 27001) for easier assignment across scopes.
- **Policy Effects (Audit vs. Deny):** `Audit` logs non-compliant resources to the compliance dashboard without interrupting deployment. `Deny` actively blocks non-compliant resource creation or updates at the Azure Resource Manager (ARM) layer.
- **Resource Locks:** Serve as a final safeguard against accidental modification or deletion. `CanNotDelete` permits configuration changes but blocks deletion; `ReadOnly` prevents both configuration updates and deletion.
- **Microsoft Defender for Cloud (MDC) Compliance:** Continuously monitors resource configurations against security benchmarks and regulatory frameworks, generating security scores, misconfiguration alerts, and remediation paths.
- **Global Admin Elevation to Azure Resources:** Entra ID Global Administrators do not have default access to Azure Subscriptions. They must explicitly enable "Access management for Azure resources" in the portal, which grants them root-level `User Access Administrator` rights across subscriptions.

---

## Lab / Hands-On Work

### What I did
- Reviewed the live recording covering Azure Policy enforcement, resource locking, and Defender for Cloud compliance dashboards.
- Evaluated the mentor's demonstration of deploying an Azure Policy at the subscription scope to restrict public network access on Azure Storage Accounts.
- Analyzed the behavioral difference between setting policy parameters to `Audit` (which allowed storage account creation while flagging non-compliance) versus `Deny` (which actively threw a deployment error and blocked creation).

### What happened / Result
- Mastered the logic of policy inheritance across Management Groups, Subscriptions, and Resource Groups, as well as how resource locks override standard contributor permissions to prevent accidental destruction.

### Challenges I faced
- We haven't been granted access to the promised partner student/test environment yet. Because of this, I couldn't safely replicate the policy assignment and storage account deployment demos hands-on without risking unexpected Azure billing.

---

## My Takeaways

Governance doesn't slow down development, it's about putting up automated guardrails so teams don't accidentally deploy insecure infrastructure. Using `Deny` policy effects prevents misconfigurations at the door, making it far more efficient than manually auditing and fixing resource drift after deployment.

---

## Questions I Still Have

- When rolling out a large initiative containing hundreds of definitions, what is the best staged strategy for transitioning policies from `Audit` to `Deny` without risking accidental production outages?
- Will the upcoming partner student environment include Management Group access so we can test policy inheritance hierarchy across multiple subscriptions?

---

## Resources I Found Useful

- **Session Recording:** [Enforce security governance and regulatory compliance - Part 1 (MNSUG YouTube)](https://youtu.be/oN8ZdKTq-p0)
- **GitHub Workshop Directory:** [MNSUG GitHub Onboarding Workshop Repository](https://github.com/AGK001/github-onboarding-workshop)

---

*Submitted by: Ejike Etolue · AGK001*