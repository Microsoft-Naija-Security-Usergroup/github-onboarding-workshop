# My Notes — Oduola Ifeoluwa

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- Microsoft Defender for Cloud provides advanced threat detection for databases, identifying threats like SQL injection and anomalous access 
-  Azure offers two main managed database services: Azure SQL Database and Azure SQL Managed Instance 
-  Microsoft Entra ID authentication is highly recommended over SQL authentication due to enhanced security features like MFA, conditional access, and no password storage 
- Microsoft Defender for Cloud provides advanced threat detection for databases, identifying threats like SQL injection and anomalous access 

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

Observed the live demo showing how to secure Azure SQL Database.

Followed along as the presenter configured firewall rules and enabled encryption.
### What I did

- Created an Azure SQL Database server and database with Microsoft Entra ID authentication enabled 

- Registered an Azure resource (Microsoft Purview) as a data source for the Azure SQL database 

-  Encountered a connection failure when the Azure resource tried to access the database without proper permissions 
- Assigned a Reader role to the Azure resource's managed identity at the server level 

- Created a database user for the managed identity within the SQL database and granted it the db_datareader role 

- Successfully tested the connection, confirming the resource could now access the database 


### What happened / Result
- The Azure resource successfully connected to the Azure SQL database after the correct database-level role was assigned to its identity.
- A private endpoint was created, enabling secure, private network access to the database.
- Auditing was enabled, allowing for the logging of database activities to a chosen destination.

### Challenges I faced


--- Network connectivity issues impacting the demonstration 

## My Takeaways

<!-- What was most valuable to you personally from this session? -->


---The layered security approach is critical for protecting Azure databases. It's not enough to just enable Entra ID authentication; you must also implement network isolation with private endpoints, enable auditing for activity tracking, and leverage threat detection services like Microsoft Defender for Cloud. Ensuring proper role assignments at both the Azure resource level and the database level is essential for seamless and secure connectivity. The importance of testing connectivity after making changes was highlighted by the initial failure when connecting the Purview resource.

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

- How to effectively set up and manage permissions for multiple Azure resources that need to access various Azure SQL databases in a large organization?
- What are the best practices for configuring retention policies for audit logs stored in Azure Storage or Log Analytics, considering compliance requirements?
-  Can you elaborate on the differences in performance impact between using service-managed keys and customer-managed keys for Transparent Data Encryption?


---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- Microsoft Learn: [https://learn.microsoft.com/en-us/azure/azure-sql/database/secure-overview]

---

*Submitted by: [Oduola Ifeoluwa] · [ife005]*
