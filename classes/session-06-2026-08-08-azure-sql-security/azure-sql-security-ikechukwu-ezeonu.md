# My Notes — IKECHUKWU EZEONU

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- **Authentication & Managed Identity**: Configured Microsoft Entra ID authentication to eliminate credentials in code, leveraging System-Assigned and User-Assigned Managed Identities for seamless service-to-service authentication.
- **Network Isolation**: Secured database access using Azure Private Link (Private Endpoints) to isolate traffic from the public internet, configuring firewall rules, and setting up Virtual Network (VNet) Service Endpoints.
- **Data Encryption**: Learner Transparent Data Encryption (TDE) with Service-Managed Keys or Customer-Managed Keys (BYOK via Azure Key Vault) for data at rest, along with Always Encrypted to safeguard sensitive data both in transit and at rest.
- **Data Protection & Access Control**: Implemented Dynamic Data Masking (DDM) to obfuscate sensitive fields (e.g., credit card numbers, email addresses) for non-privileged users without altering underlying data.


- **Azure SQL Auditing**: Configured auditing at both the server level and database level to log database events (e.g., successful/failed logins, schema changes, executed queries).
- **Audit Storage**: Routed logs to three primary destinations based on compliance requirements: Azure Blob Storage (for long-term cost-effective retention), Log Analytics Workspaces (for active querying via KQL), and Event Hubs (for real-time integration with external SIEMs like Microsoft Sentinel).
- **SQL Managed Instance Auditing**: Understood auditing configurations specific to Azure SQL Managed Instance, including server audits using T-SQL, Extended Events, and routing to Blob Storage or Event Hubs.
- **Compliance Strategies**: Designed audit policies structured around regulatory frameworks (e.g., GDPR, HIPAA, PCI-DSS) using retention policies, immutable storage, and role-based access control (RBAC) to ensure audit log integrity.


- **Microsoft Defender for Databases**: Explored how Microsoft Defender for Cloud provides Advanced Threat Protection (ATP) against anomalous activities like SQL injection, brute-force attacks, and privilege abuse across managed databases.
- **Defender Coverage**: Configured Defender across Azure SQL Databases, Azure SQL Managed Instance, and open-source relational databases (e.g., Azure Database for PostgreSQL, MySQL, MariaDB).
- **Vulnerability Assessment (VA)**: Configured automated scanning and vulnerability assessment baselines to detect security risks, misconfigurations, and compliance drift.
 - **Alert Routing & Coverage Validation**: Set up email alerts and action groups to route security alerts directly to SOC teams, and verified security posture through simulated threat activities and Defender status reports.



---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did

- Configured Microsoft Entra ID authentication for Azure SQL Database, created an Entra admin, and granted access using Managed Identities.
- Restricted public network access to the Azure SQL logical server, creating a Private Endpoint connected to a custom Virtual Network.
- Enabled Transparent Data Encryption (TDE) with Key Vault customer-managed keys (BYOK).


### What happened / Result

- Public access to the database was successfully blocked, and connectivity was successfully limited to resources within the designated VNet.

### Challenges I faced

- **Private Link Resolution**: DNS resolution for connecting to the database via Private Endpoint is still not very clear to me.

---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->

- Defense-in-Depth is essential for database security: relying solely on network isolation or database credentials is not enough. Implementing  a layered Managed Identities, Private Links, Encryption, Auditing, and Defender threat detection provides true security.
- Managed Identities are a huge improvement over traditional connection strings and password-based authentication, drastically reducing the risk of secret leaks.
- Defender for Databases combined with Log Analytics and Azure Sentinel provides complete visibility, making real-time threat detection and incident response much faster and manageable.

---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

-
-

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- **Configure Azure SQL Platform Security - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/configure-azure-sql-platform-security/)
- **Configure Azure SQL Auditing - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/configure-azure-sql-auditing/)
- **mplement Defender for Databases - Microsoft Learn**(https://learn.microsoft.com/en-us/training/modules/implement-defender-databases/)
- **Microsoft Entra Managed Identities Overview**(https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
- **Azure SQL Database Security Guidelines & Best Practices**(https://learn.microsoft.com/en-us/azure/azure-sql/database/security-overview)


---

*Submitted by: Ikechukwu Ezeonu · ikechukwu-ezeonu*
