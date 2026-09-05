# My Notes — Ejike Etolue

---

## Key Concepts I Learned

- **Database Authentication (SQL vs. Entra ID):** Legacy SQL authentication relies on database usernames/passwords embedded in connection strings or config files (high risk of credential exposure). Enforcing Entra ID-only authentication eliminates clear-text credentials, enforces MFA and Conditional Access, centralizes identity governance, and supports Managed Identities and JIT access via PIM.
- **Defense-in-Depth for Databases:** Securing Azure SQL databases requires a multi-layered approach spanning network security (Azure SQL Firewall, Private Endpoints), identity & access management (Entra ID RBAC & contained database users), information protection (Transparent Data Encryption for data at rest, TLS 1.2 for data in transit, Dynamic Data Masking), and threat protection.
- **Firewall Rules vs. Private Isolation:** Azure SQL Server firewalls control IP-level access (server-level via portal/CLI/PowerShell, database-level via T-SQL `sys.database_firewall_rules`). To eliminate internet exposure for sensitive workloads, Private Link/Private Endpoints isolate database traffic strictly to private VNet IP space.
- **Database Auditing & Telemetry Destinations:** SQL Auditing logs database activities, queries (e.g., batch completed groups), and authentication events to Log Analytics Workspaces (integrated with Microsoft Sentinel for threat hunting), Azure Storage Accounts (hardened with immutability/WORM locks), or Event Hubs.
- **Microsoft Defender for SQL & Data Protection:** Defender for Databases provides advanced threat detection against SQL injection, brute-force attempts, and exfiltration. Sensitive fields can be protected using Microsoft Purview classification, Always Encrypted, and Dynamic Data Masking (DDM) to obfuscate PII/financial data.

---

## Lab / Hands-On Work

### What I did
- Observed live Azure portal demonstrations covering Azure SQL Server and database creation with Entra ID-only authentication enabled.
- Evaluated Microsoft Purview integration by registering an Azure SQL Database data source and configuring system-assigned managed identity permissions with contained database user T-SQL scripts (`CREATE USER ... FROM EXTERNAL PROVIDER`, `ALTER ROLE db_datareader ADD MEMBER ...`).
- Analyzed SQL Server Management Studio (SSMS) connection flows using Entra MFA authentication, server-level firewall configuration, and T-SQL query execution.
- Reviewed network isolation workflows via Private Endpoint setup on dedicated VNets/subnets, alongside SQL Auditing configurations directed to Log Analytics and Defender for Databases.

### What happened / Result
- Mastered the configuration sequence for switching from legacy SQL login credentials to Entra ID-only authentication, scoping contained database RBAC roles, and locking down database networks behind Private Endpoints.

### Challenges I faced
- Mentees have not yet been granted access to the official partner student/test Azure environments. Because of this, I was unable to execute the T-SQL user mapping queries, test Private Link connectivity, or run live Purview scans directly within a personal Azure tenant due to cost constraints.

---

## My Takeaways

Relying on SQL authentication and public firewall rules leaves database credentials vulnerable to exposure in code repositories or network interception. Combining Entra ID authentication with Private Endpoints and automated auditing ensures complete visibility and zero-trust data protection for enterprise database workloads.

---

## Questions I Still Have

- How does Microsoft Defender for SQL interact with custom T-SQL stored procedures that execute dynamic SQL strings, does it generate false positives for SQL injection?
- When configuring Microsoft Purview across multi-subscription environments, what is the best practice for managing managed identity cross-subscription RBAC role assignments without over-granting `Reader` rights at the management group level?

---

## Resources I Found Useful

- **Session Recording:** [Implement security for Azure SQL databases (MNSUG YouTube)](https://youtu.be/MLtnRwB4Wyk)
- **GitHub Workshop Directory:** [MNSUG GitHub Onboarding Workshop Repository](https://github.com/AGK001/github-onboarding-workshop)

---

*Submitted by: Ejike Etolue · AGK001*