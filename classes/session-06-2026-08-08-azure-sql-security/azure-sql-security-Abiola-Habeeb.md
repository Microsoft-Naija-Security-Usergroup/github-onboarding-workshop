# My Notes — Abiola Habeeb

---

## Key Concepts I Learned

This session covered **implementing security for Azure SQL databases** using a layered, defense-in-depth approach.

- **Two database types.** **Azure SQL Database** is a fully managed cloud database for applications (used in the demo); **Azure SQL Managed Instance** is a fully managed SQL Server in the cloud with near-full compatibility to on-premises SQL Server, making it a good migration target.
- **Four layers of defense.** Network security (firewall — who can reach the database), access management (authentication, authorization, RBAC, least privilege), threat protection (Defender for Cloud detecting attacks), and information protection (encrypting data at rest and in transit).
- **SQL authentication vs Microsoft Entra ID authentication.** SQL auth requires a username/password that ends up stored in a config file or connection string (often in a repo) — high risk if leaked, and it offers no MFA, no conditional access, and its logins are auditable only inside SQL, not in Entra sign-in logs. **Entra ID authentication is the best practice**: no passwords, MFA enforced, conditional access by device/location, sign-in risk evaluation, and PIM for just-in-time time-bound access. Migration path: set the Entra admin → create Entra principals in SQL → test → disable SQL authentication.
- **Server vs database access.** A logical **SQL server** hosts multiple databases; server-level config affects all of them, but each database also has its own config. Access to the *server* is not access to the *data* — you must create a **contained database user** for an identity (`CREATE USER [name] FROM EXTERNAL PROVIDER`) and grant it a database role (e.g. `db_datareader`, `db_datawriter`, `db_owner`). Connecting an Azure resource therefore takes three things: an RBAC role, a database user, and a firewall rule allowing the client IP.
- **Azure SQL firewall.** Two levels: **server-level rules** (apply to every database; set via portal, PowerShell, CLI, or T-SQL) and **database-level rules** (per database; set **only via T-SQL**). "Allow Azure services and resources to access this server" is what lets other Azure services (e.g. Purview) connect.
- **Network isolation with private endpoints.** A public endpoint on the internet is a risk. Use a **private endpoint** so the server is reachable only from peered VNets, ExpressRoute, or site-to-site VPN, keeping traffic on Microsoft's private backbone. Critical order: **create and test the private endpoint first, then disable public access** — otherwise you lock yourself out.
- **Auditing.** Tracks sign-ins and queries run against the database for compliance. Log destinations: **Log Analytics Workspace** (query with KQL, built-in Sentinel analytics for brute force / anomalous login / impossible travel), **Azure Storage** (set immutability so logs can be read but not overwritten; stored as `.xel`), or **Event Hub** (stream to a third-party SIEM).
- **Information protection.** Data at rest is protected by **Transparent Data Encryption (TDE)** (on by default; service-managed or customer-managed keys in Key Vault). Data in transit is protected by **TLS 1.2+**. Additional controls include **dynamic data masking** (hide sensitive fields like card numbers from unauthorized users) and **Always Encrypted** (data stays encrypted even from the database engine).
- **Microsoft Defender for Databases** detects SQL injection, anomalous access, brute force, and data exfiltration across all databases in the subscription (including open-source databases). It differs from auditing: auditing records activity, Defender detects and blocks attacks.

---

## Lab / Hands-On Work

### What I did


### What happened / Result


### Challenges I faced


---

## My Takeaways

Through this training I now understand that securing a database is a stack of independent controls, not a single switch. The single biggest shift is moving from SQL authentication to Entra ID–only authentication: it removes the stored username/password that is the most common cause of database compromise, and it layers on MFA, conditional access, and PIM. What made it concrete in the demo was seeing that even after assigning an RBAC role, a resource still couldn't reach the database until a contained database user and a database role were created and the client IP was allowed through the firewall — access to the server is genuinely separate from access to the data. On top of identity, private endpoints remove the public attack surface (create and test before disabling public access), auditing gives a compliance trail, TDE and TLS protect data at rest and in transit, and Defender for Databases watches for active attacks.

---

## Questions I Still Have

- In a hybrid environment with synced on-prem AD, what's the cleanest way to grant database access to a synced identity versus a cloud-only one?
- When auditing many databases, when is per-database auditing worth the extra effort over server-level auditing given the "events may be dropped under load" caveat?
- For Always Encrypted vs dynamic data masking, when should each be used, and can they be combined on the same column?

---

## Resources I Found Useful

- Bootcamp — Naija AI and Cloud Security (Microsoft Naija Security Usergroup) GitHub
- [Implement security for Azure SQL databases — learning path](https://learn.microsoft.com/en-us/training/paths/implement-azure-sql-database-security/)
- [Configure platform-level security for Azure SQL (training module)](https://learn.microsoft.com/en-us/training/modules/configure-azure-sql-platform-security/)
- [SC-500 study guide — Cloud and AI Security Engineer](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500)
- [Azure SQL documentation](https://learn.microsoft.com/en-us/azure/azure-sql/?view=azuresql)

---

*Submitted by: Abiola Habeeb · https://github.com/abiolahabeeb*
