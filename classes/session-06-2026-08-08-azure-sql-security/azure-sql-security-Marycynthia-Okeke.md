# My Notes — Marycynthia Okeke

## Key Concepts I Learned

- **Network Isolation & Firewalls**
  - **Azure SQL Firewalls:** Operate at two levels:
    - **Server-level firewall rules:** Stored in the `master` database and support up to 256 rules.
    - **Database-level firewall rules:** Configured through T-SQL using `sp_set_database_firewall_rule`.
  - **"Allow Azure Services" Toggle:** Enabling this option allows Azure resources from any tenant to access the server through its public IP. It should therefore remain **OFF** and be replaced with more specific controls such as named VNet rules, IP rules, or Private Endpoints.
  - **Private Endpoints (Azure Private Link):** Assign a network interface with a private IP address from the Virtual Network to the Azure SQL logical server. This allows traffic to be routed through Microsoft's private backbone and removes exposure through the public internet.

- **Data Protection & Encryption**
  - **Transparent Data Encryption (TDE):** Provides real-time, page-level encryption for databases, backups, and transaction logs at rest.
  - Azure SQL Database has TDE enabled by default using **Service-Managed Keys**, with the option to use **Customer-Managed Keys through Azure Key Vault**.

- **Auditing & Threat Detection**
  - **Azure SQL Auditing:** Records database events such as logins, failed logins, and executed queries or batches. Audit logs can be sent to **Log Analytics, Azure Storage, or Event Hubs**.
  - **Microsoft Defender for Databases:** Monitors Azure SQL Database, SQL Managed Instance, Cosmos DB, and Open-Source Azure databases for potential threats such as SQL injection, brute-force login attempts, anomalous access locations, and data exfiltration through large result-set dumps.
  - **Microsoft Sentinel Integration:** Sending SQL logs to a Log Analytics workspace enables Microsoft Sentinel analytics rules for automated alert correlation and threat hunting across Entra ID sign-ins, Defender alerts, and SQL logs.

---

## Lab / Hands-On Work

### What I Did

- Created an **Azure SQL Database** instance.
- <img width="736" height="373" alt="SQL DB CREATED" src="https://github.com/user-attachments/assets/6c85f906-8fcf-4d4a-9eb1-3ac2a05f4a59" />

- Configured identity access control by assigning a **Reader** role for control-plane access.
- <img width="955" height="423" alt="Added role" src="https://github.com/user-attachments/assets/4f25f4df-3ccb-4563-9ea4-e1f32a227e40" />

- Installed **SQL Server Management Studio (SSMS)** on the local environment to manage queries and test database access.

- Attempted to provision a **Microsoft Purview** account for automated data governance and classification.

### What Happened / Result

- Successfully established access to run queries using **SQL Server Management Studio (SSMS)**.
- - <img width="680" height="540" alt="studio sql server" src="https://github.com/user-attachments/assets/ce556f7e-c008-44c8-817d-d1e4ff810261" />
- Encountered a permission boundary error while provisioning Microsoft Purview because the assigned subscription role did not have sufficient administrative scope to register the required resource provider and create the Purview account.

### Challenges I Faced

- Navigating **RBAC limitations** when attempting to deploy governance tools such as Microsoft Purview alongside the database environment.
- Verifying that client-side tools such as SSMS can authenticate successfully through Azure SQL firewall rules without unnecessarily exposing the database server endpoint.

---

## My Takeaways

- **Least-privilege RBAC** controls, such as granting a basic Reader role, limit what users can modify in Azure. However, administrative actions such as setting up Microsoft Purview require higher privileges or the necessary resource provider permissions.
- Disabling public endpoints through **Private Link** and routing SQL Audit logs to a **Log Analytics workspace** provides a foundation for securing enterprise databases and enabling Microsoft Sentinel detection rules.

---

## Questions I Still Have

- How do **database-level firewall rules** interact with or take precedence over **server-level firewall rules** when a client connects through SSMS?

---

## Resources I Found Useful

- **Microsoft Learn:** Microsoft Entra service principals with Azure SQL

---

*Submitted by: Marycynthia Okeke* 
