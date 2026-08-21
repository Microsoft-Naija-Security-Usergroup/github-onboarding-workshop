# My Notes — Promise Ibediogwu Ekele

---

## Key Concepts I Learned


### Azure SQL Database and Azure SQL Managed Instance

* Learned the difference between Azure SQL Database and Azure SQL Managed Instance.
* Azure SQL Database is a fully managed database service designed for modern cloud applications.
* Azure SQL Managed Instance provides greater compatibility with traditional SQL Server workloads and is suitable for organizations migrating existing on-premises databases to Azure.
* Understood that selecting the right database service depends on application requirements, migration needs, and security considerations.

---

### Defense in Depth Security Strategy for Azure SQL

* Learned that securing Azure SQL databases requires multiple security layers rather than relying on a single control.

* The defense-in-depth approach covers:

  * Network security
  * Identity and access management
  * Data protection
  * Threat detection and monitoring

* Understood that a secure database environment combines authentication controls, network isolation, encryption, auditing, and continuous monitoring.

---

### Microsoft Entra ID Authentication

* Learned the importance of using Microsoft Entra ID authentication instead of traditional SQL authentication.

* Understood that Entra authentication reduces password-related risks by using identity-based authentication with tokens instead of stored database credentials.

* Learned that Microsoft Entra ID authentication enables integration with:

  * Multi-Factor Authentication (MFA)
  * Conditional Access policies
  * Managed identities

* Understood why organizations should reduce dependency on SQL authentication because compromised passwords can become an entry point for attackers.

---

### Network Security and Private Endpoints

* Learned how Private Endpoints provide secure connectivity between Azure SQL services and Virtual Networks.

* Understood that Private Endpoints assign a private IP address to the database service, allowing communication through the Microsoft private backbone.

* Learned that private connectivity reduces exposure to the public internet and improves security posture.

* Important operational lesson:

  * Public network access should only be disabled after confirming that private connectivity has been successfully configured to avoid production outages.

---

### Azure SQL Auditing and Monitoring

* Learned how Azure SQL auditing helps organizations track database activities for security monitoring and compliance purposes.

* Understood that audit logs can be sent to:

  * Log Analytics Workspace
  * Azure Storage Accounts

* Learned that monitoring database activities helps organizations detect suspicious activities, investigate incidents, and maintain compliance requirements.

---

### Transparent Data Encryption (TDE)

* Learned how Transparent Data Encryption protects Azure SQL databases by encrypting data at rest.

* Understood that TDE automatically encrypts:

  * Database files
  * Backup files
  * Transaction logs

* Learned that organizations can use:

  * Service-managed keys
  * Customer-managed keys stored in Azure Key Vault

for additional control over encryption.

---

### Dynamic Data Masking

* Learned how Dynamic Data Masking protects sensitive information by hiding data values from unauthorized users.
* Understood that masking does not modify the actual data stored in the database but controls how sensitive information appears in query results.
* Example:

  * Credit card numbers or personal information can be hidden from users who do not require full visibility.

---

### Microsoft Defender for SQL

* Learned how Microsoft Defender for SQL provides advanced threat protection for Azure SQL databases.

* Understood that Defender for SQL helps detect:

  * Suspicious database activities
  * Potential SQL injection attacks
  * Possible data exfiltration attempts

* Learned that database security requires both preventive controls and continuous threat detection.

---

### Microsoft Purview and Data Governance

* Learned that Microsoft Purview is an important data governance solution used to discover, classify, and manage organizational data assets.

* Understood that Purview helps organizations understand their data estate by identifying:

  * Where data exists
  * What type of data is stored
  * Sensitive information within databases and other data sources
  * Data ownership and governance requirements

* Learned that Purview supports compliance and security efforts by helping organizations classify sensitive data and apply appropriate governance policies.

* Understood that in enterprise environments, securing databases is not only about protecting access but also understanding and managing the data itself.

---

## Lab / Hands-On Work


### What I did

* No independent hands-on lab was provided for this session.

* I followed the practical demonstrations performed by the mentor during the session.

* I reviewed the process of configuring Microsoft Entra ID authentication for Azure SQL databases, including:

  * Assigning an Entra administrator
  * Creating database users linked to Entra identities
  * Assigning database permissions

* I followed the demonstration of configuring Private Endpoints for Azure SQL and understood how database connectivity can be restricted through a Virtual Network.

* I reviewed the configuration approach for:

  * Azure SQL auditing
  * Transparent Data Encryption
  * Microsoft Defender for SQL
  * Dynamic Data Masking

* I have also applied related Azure security concepts from this session in my personal Azure projects, including identity-based access control, network security, private connectivity concepts, RBAC, and data protection practices.

---

### What happened / Result

* I gained a better understanding of how enterprise organizations secure database workloads in Azure.
* I understood that database security requires combining identity security, network isolation, encryption, monitoring, and governance.
* The session helped me connect Azure SQL security concepts with the security implementations I have already practiced in my personal Azure projects.

---

### Challenges I faced

* Understanding the difference between SQL authentication and Microsoft Entra authentication required deeper study because it changes the traditional approach of managing database users and passwords, also what if an external resource with is not azure resource want to access the database, how can they do that since we arent using the password but Entra ID authentification.
* Private Endpoint concepts required additional understanding because network configuration must be carefully planned before disabling public access.
* Microsoft Purview is still an area I need to explore further because data governance involves broader concepts beyond database security.

---

## My Takeaways


The major lesson from this session was understanding that securing cloud databases requires a complete security strategy rather than implementing isolated security features.

I learned that identity should be the foundation of database security, and organizations should prioritize Microsoft Entra ID authentication and managed identities instead of relying heavily on passwords.

The discussion around Private Endpoints also improved my understanding of how organizations protect sensitive databases by removing unnecessary public exposure.

Another important takeaway was understanding the role of Microsoft Purview in enterprise security. Before this session, I viewed security mainly from the perspective of access control and infrastructure protection, but Purview introduced me to the importance of knowing what data exists, where it exists, and how sensitive information should be governed.

This session strengthened my understanding that cloud security involves protecting not only infrastructure but also the data lifecycle.

---

## Questions I Still Have


* How do organizations design Microsoft Purview data classification strategies across large Azure environments?
* What are the best practices for migrating from SQL authentication to Microsoft Entra authentication in production environments?
* How should organizations manage customer-managed keys for TDE using Azure Key Vault?
* What are the recommended monitoring queries using KQL for Azure SQL security events?
* How does Microsoft Defender for SQL integrate with Microsoft Sentinel for incident response?

---

## Resources I Found Useful

* Microsoft Learn: Azure SQL Security Overview
  https://learn.microsoft.com/azure/azure-sql/database/security-overview

* Microsoft Learn: Microsoft Entra Authentication for Azure SQL
  https://learn.microsoft.com/azure/azure-sql/database/authentication-aad-overview

* Microsoft Learn: Azure Private Endpoint
  https://learn.microsoft.com/azure/private-link/private-endpoint-overview

* Microsoft Learn: Azure SQL Auditing
  https://learn.microsoft.com/azure/azure-sql/database/auditing-overview

* Microsoft Learn: Transparent Data Encryption
  https://learn.microsoft.com/azure/azure-sql/database/transparent-data-encryption-tde-overview

* Microsoft Learn: Microsoft Purview Overview
  https://learn.microsoft.com/purview/

* Microsoft Defender for SQL
  https://learn.microsoft.com/azure/defender-for-cloud/defender-for-sql-introduction

---

*Submitted by: Promise Ibediogwu Ekele · http://github.com/promibe*
