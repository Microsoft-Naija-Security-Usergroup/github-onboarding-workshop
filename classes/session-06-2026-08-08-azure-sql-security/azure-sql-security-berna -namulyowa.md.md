# My Notes — \[REPLACE WITH YOUR FULL NAME]

## Key Concepts I Learned

# **SECURITY FOR AZURE DATABASES**

### **Azure SQL Database and SQL Managed Instance Database**

Azure SQL Database is one that is fully managed by the cloud-based database for applications while the SQL Managed Instance is a fully managed SQL server in the cloud.

The strategy deployed in Azure SQL database security is a the defense in depth layered as follows;



* Network security — controls like firewalls that determine who can reach the database.
* Access management — authentication and authorization, RBAC, and the ability to apply least-privilege access at the individual level.
* Threat protection— Microsoft Defender for Cloud detects malicious or anomalous attempts to access the database.
* Information protection — encryption of data at rest and in transit.



**Difference between SQL Authentication and Entra identification**

SQL authentication: username and password are stored in a configuration file/connection string.



Microsoft Entra authentication: no password to manage — MFA is enforced and tokens rotate automatically.



Microsoft Entra ID is the only authentication model that lets Conditional Access, MFA, and Privileged Identity Management (PIM) apply directly to database access.





### **Network Firewall**



Azure SQL has two firewall levels:



\-Server-level firewall rules — apply to every database on the logical server; configurable via the Portal, PowerShell, or T-SQL.

\-Database-level firewall rules— apply to a single database; configurable only via T-SQL (`sp\_set\_database\_firewall\_rule`). Useful when one database needs a tighter IP range than the server.



### Network Isolation



A private endpoint lets sources connect to the database privately instead of through a public endpoint that's open to everyone. All inbound and outbound traffic to the database flows through the private endpoint, and public access can then be disabled entirely.

### 

### **Azure SQL auditing**

Auditing tracks what database activity is captured and where the logs go. There are three possible destinations:



* Log Analytics workspace — for querying audit logs with KQL and correlating with other monitoring/security data.
* Azure Storage account — for low-cost, long-term retention of raw audit logs.
* Event Hub— for streaming audit events to a SIEM or other downstream system in near real time.



Auditing prioritizes database availability, so under extreme load some events may not be recorded. Auditing must be explicitly enabled to monitor database activity.



#### Log Analytics and Microsoft Sentinel



Microsoft Sentinel is a set of security capabilities — analytics, detection, investigation, and automation — layered on top of a Log Analytics workspace.



**What the Log Analytics workspace provides:**



* Centralized storage — a container in Azure Monitor that ingests and stores log/telemetry data from Azure resources, on-prem systems, SaaS apps, and network devices in structured tables.
* The Kusto Query Language (KQL) engine— the same engine Sentinel's analytics rules, hunting queries, workbooks, and notebooks run against to detect threats and surface insights.
* Ingestion pipelines — Data Collection Rules, the Log Analytics/Azure Monitor Agent, and diagnostic settings that feed Sentinel's data connectors.
* Retention and access control— configurable interactive retention plus low-cost long-term retention, and workspace- or table-level RBAC governing who can see which logs.



**Why Log Analytics unlocks Sentinel:**



* No workspace, no Sentinel— enabling Sentinel is an operation performed on top of an existing (or new) Log Analytics workspace; there is no separate Sentinel data store.
* Shared data model — Sentinel reads the same tables Azure Monitor and Microsoft Defender for Cloud write to, so it can correlate security signals with operational and cloud-posture data without duplicating storage.
* Reuse of existing investment— organizations already using Log Analytics for monitoring can turn on Sentinel against that workspace and immediately gain SIEM/SOAR capability over data they're already collecting.
* Unified Security Operations Platform — in the Microsoft Defender portal, Sentinel runs alongside Defender XDR but still depends on the underlying Log Analytics workspace for storage and query.
* Pricing tied to the workspace — Sentinel billing (Analytics Logs, Auxiliary Logs, commitment tiers) is metered on data ingested and retained in the workspace, so workspace design directly drives cost and capability.





### **Implement Transparent Data Encryption (TDE)**



Transparent Data Encryption encrypts data at rest — covering the database files, transaction logs, and backups — with no application changes needed, since encryption/decryption happens transparently at the storage engine.



Default state: On Azure SQL Database, TDE is enabled by default for any database created after May 2017. Older databases and Azure Synapse Analytics dedicated SQL pools need it turned on manually.



Two key management modes:

* Service-managed (default): Microsoft owns and auto-rotates the certificate protecting the Database Encryption Key (DEK), using AES-256. Zero configuration required — good enough for most workloads.
* Customer-managed (BYOK): You supply an asymmetric key stored in Azure Key Vault or Managed HSM as the TDE Protector. You control rotation, backup, and revocation — needed for stricter compliance regimes.



**How to enable it:**

* Portal: go to the database's Data Encryption blade and toggle it on (requires Owner/Contributor/SQL Security Manager role).
* T-SQL: `ALTER DATABASE \[DbName] SET ENCRYPTION ON;` — check status with `sys.dm\_database\_encryption\_keys`.
* PowerShell/CLI: for BYOK, use `Set-AzSqlServerTransparentDataEncryptionProtector` after granting the server access to your Key Vault key.





### Microsoft Defender for Databases



Defender for Databases is a Microsoft Defender for Cloud security plan that adds threat protection and security posture management for database workloads across Azure, hybrid, and multicloud environments.



It has four separate plans:



* Defender for Azure SQL Databases — threat detection and vulnerability assessment for Azure SQL.
* Defender for SQL Servers on Machines — protects SQL Server on VMs, on-prem servers, or Arc-enabled machines (also deployable via Log Analytics).
* Defender for Open-Source Relational Databases — covers Azure Database for PostgreSQL and MySQL, plus Amazon RDS instances for PostgreSQL, MySQL, and MariaDB.
* Defender for Azure Cosmos DB — real-time threat alerts for Cosmos DB.



Each plan is enabled and billed independently, so you can protect only the database types you actually run.



It is enabled using In the Azure portal, go to Defender for Cloud → Environment Settings → select your subscription → Defender plans, then toggle on the specific database plan(s) you need. Coverage can also be scoped per-resource rather than subscription-wide



## Lab / Hands-On Work

**Creating the database**

Create an Azure SQL database under create a resource group, and a database server where it will be hosted.

Choose the location for the server and mine was  (Africa) South Africa North.

For the authentication method we select Use Microsoft Entra-only authentication and you can set the admin or leave the default admin.



After the database and the server where it is hosted are created.

The Microsoft Entra ID admin authentication is also activated.



Create a Microsoft Purview account.( For data classification etc)

Go to Microsoft Purview account, connect the resource group as the database and give the account a name.

Leave all the rest of the options as default.

Register for miscrosoft storage if it requests you to.

Then your Microsoft Purview account will be created.



**Launch the Purview Portal**

&#x20;



Connecting the Purview account to the database

Launch the Purview Portal

Go to data sources and register a data source

Select Azure SQL database, add a an Azure subscription and connect it to the server for the database.

You can scan and see.

Test the connection of the resource to the database. My resource failed to connect to the database.



Create Entra principals in SQL

&#x09;Go to the server and add the managed identity using the Access Control

&#x09;Select Access Control, then add then add a role assignment

&#x09;Choose Reader role -can view all resources but cant make changes.

&#x09;Then Under members you select managed identity and add members.

Connection to the DB still failed because we hadn't assigned a db role to the identity

Go to the database then Query Editor select Microsoft Entra Authentication and Connect

Allow the firewall rule

Create a New Query to create a USER use the command

&#x09;CREATE USER \[nalin]

&#x09;FROM EXTERNAL PROVIDER;

&#x09;GO

Grant the role

&#x09;ALTER ROLE db\_datareader

&#x09;ADD MEMBER \[nalin];

&#x09;GO

Test the connection again, the database connects successfully to the resource.

You can scan and see.



Implement a network isolation

Go to Security under networking you select private access then add private endpoint.

Add a name for the instance then next Resource cross check the server name then next

Add a virtual network.

Enable the Virtual network rule.

Create a private endpoint from private access then Resource continue virtual network (Dynamically allocate IP address) then DNS (Seclect Yes) Tags leave at default then Review + create

Disable the Public access





### What I did

I created an Azure SQL database with only Microsoft Entra Authentication.

I also implemented a network Isolation where I created a private endpoint.



### What happened / Result

The database was created successfully and to access it you need to use Microsoft Entra Authentication.

For the Private endpoint block any IP address that is not registered to access my database.



### Challenges I faced

* The Microsoft Purview account initially failed validation because I hadn't registered for Microsoft Storage; registration took some time to complete, but it succeeded eventually.
* The Purview data source failed to connect to the database on the first attempt — this was resolved only after creating a Microsoft Entra database user for the managed identity and granting it the `db\_datareader` role.





## My Takeaways

* Defense in depth is the core mental model for Azure SQL security — network controls, identity/access, threat detection, and encryption all need to be configured together; no single layer is sufficient on its own.
* Microsoft Entra-only authentication is a meaningfully stronger default than SQL authentication, mainly because it's the only path that lets Conditional Access, MFA, and PIM govern database access.
* Connecting Purview to a database isn't just a network task — it also depends on identity: the managed identity needed both an Azure RBAC role (Reader) and an explicit database role (`db\_datareader`) before the connection would succeed. Access failures aren't always about firewalls.
* Enabling a private endpoint and disabling public access is a simple, high-impact way to shrink the attack surface, but it needs to be sequenced correctly (endpoint and DNS working before public access is switched off) to avoid locking yourself out.
* A lot of "it doesn't work" moments in the lab (Purview validation, the failed data source connection) came down to a missing prerequisite rather than a configuration error — worth checking dependencies methodically before troubleshooting further.



## Questions I Still Have



1. When would a team choose customer-managed (BYOK) TDE over the default service-managed encryption in practice is it purely a compliance requirement, or are there other common triggers?
2. With Entra-only authentication enabled, is there a recommended emergency access process in case Entra ID itself is unavailable?
3. How should audit log destinations be chosen in practice when does it make sense to send to more than one of Log Analytics, Storage, and Event Hub at the same time?
4. Since auditing can drop events under extreme load to protect availability, is there a way to get alerted when that happens, so a gap in the audit trail doesn't go unnoticed?
5. For Microsoft Defender for Databases, do the four plans need to be enabled separately per subscription, or can they be applied centrally across a management group?
6. Once a private endpoint is set up and public access is disabled, what's the recommended way to still allow trusted Microsoft services (e.g., Purview scanning) to reach the database?



## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

* \[Log Analytics workspace overview – Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-workspace-overview)
* \[Multiple workspaces – Microsoft Sentinel in the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/workspaces-defender-portal)
* \[Transparent Data Encryption – Azure SQL Database \& Managed Instance](https://learn.microsoft.com/en-us/azure/azure-sql/database/transparent-data-encryption-tde-overview?view=azuresql\&tabs=azure-portal)
* \[Overview of Microsoft Defender for Databases](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-databases-overview)
* \[IP firewall rules – Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/firewall-configure?view=azuresql)
* \[Auditing – Azure SQL Database and Azure Synapse Analytics](https://learn.microsoft.com/en-us/azure/azure-sql/database/auditing-overview?view=azuresql)
* \[Microsoft Entra authentication – Azure SQL Database \& Managed Instance](https://learn.microsoft.com/en-us/azure/azure-sql/database/authentication-aad-overview?view=azuresql)
* \[Azure Private Link for Azure SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/private-endpoint-overview?view=azuresql)
* \[Discover and govern Azure SQL Database in Microsoft Purview](https://learn.microsoft.com/en-us/purview/register-scan-azure-sql-database)



*Submitted by: Berna Namulyowa·nbernah*

