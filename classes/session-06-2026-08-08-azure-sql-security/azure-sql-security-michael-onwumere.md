# My Notes — Michael Chinonso Onwumere

## Key Concepts I Learned

- Learned about common **Azure SQL Database security faults**, including weak authentication, excessive network exposure, poor access control, and lack of proper auditing and monitoring.
- Compared **SQL Authentication** with **Microsoft Entra ID Authentication**. SQL Authentication relies on usernames and passwords stored in the database, while Microsoft Entra ID provides identity-based authentication with stronger security features such as MFA, Conditional Access, and Privileged Identity Management (PIM).
- Learned how to migrate an Azure SQL server from SQL Authentication to **Microsoft Entra-only authentication**. The process involves setting a Microsoft Entra administrator, creating Entra principals, testing the new authentication path, and finally disabling SQL Authentication.
- Learned how **Azure SQL Firewall** controls network access to the database by allowing only approved IP addresses or ranges.
- Learned about **Azure Private Link**, which allows private connectivity to Azure SQL through a private endpoint instead of exposing the database over the public internet.
- Explored **Azure SQL Auditing**, which records database activities and helps with security investigations, monitoring, and compliance requirements.
- Learned how **Microsoft Sentinel** can receive and analyze security events and logs from Azure SQL and other Azure services for centralized security monitoring.
- Learned about **Microsoft Defender for Databases**, which provides additional security monitoring, threat detection, and recommendations for protecting database workloads.
- Learned how **Dynamic Data Masking** hides sensitive data from unauthorized users, while **encryption** protects data by converting it into a secure format to prevent unauthorized access.

---

## Lab / Hands-On Work

### What I did

- Followed the instructor's demonstration on securing an Azure SQL Database.
- Reviewed the differences between SQL Authentication and Microsoft Entra ID Authentication.
- Studied the process of moving an Azure SQL server to **Microsoft Entra-only authentication**:
  1. Set a Microsoft Entra administrator.
  2. Create Microsoft Entra users or groups as database principals.
  3. Test the new authentication method using Microsoft Entra authentication and MFA.
  4. Disable SQL Authentication after confirming that the new authentication path works.
- Reviewed how Azure SQL Firewall and Private Link can be used to control and secure network access.
- Learned how SQL Auditing, Microsoft Sentinel, and Defender for Databases contribute to monitoring and threat detection.

### What happened / Result

- I gained a clearer understanding of how Azure SQL can be protected using a combination of **identity, network security, auditing, monitoring, and threat protection**.
- I understood why Microsoft Entra ID authentication provides stronger identity security because it can integrate with MFA, Conditional Access, and PIM.
- I learned that database security should be implemented in layers rather than relying on a single security control.

### Challenges I faced

- Understanding the differences between SQL Authentication and Microsoft Entra ID Authentication initially required some clarification.
- The process of switching to Microsoft Entra-only authentication requires careful testing before SQL Authentication is disabled, because applications using SQL logins may stop working.
- Understanding how Firewall, Private Link, Auditing, Sentinel, and Defender work together as different layers of security required careful attention during the session.
- I was given access to an Azure environment at the subscription level for hands-on practice. However, some of the permissions and resource restrictions limited what I could configure and test.
- I was unable to fully practice some of the concepts covered in the sessions, including creating and managing **Azure Policies, keys, certificates, and secrets**.
- I also encountered restrictions when trying to connect my **Azure database to Microsoft Purview**, which prevented me from completing that part of the hands-on exercise.
- Although these restrictions limited my practical experience, I was able to follow the instructor's demonstrations, understand the concepts, and document the steps involved. I hope to revisit these exercises when I have an environment with the required permissions.
---

## My Takeaways

The biggest lesson I took from this session is that securing a database requires **defense in depth**. Authentication protects who can access the database, Firewall and Private Link control how the database can be reached, while Auditing, Microsoft Sentinel, and Defender help detect and investigate suspicious activities.

I also learned that moving from traditional username-and-password authentication to **Microsoft Entra ID** provides stronger identity controls and allows organizations to apply security features such as MFA, Conditional Access, and PIM to database access.

---

## Questions I Still Have

- What is the best approach for migrating an existing production application that still depends on SQL Authentication to Microsoft Entra-only authentication?
- When should an organization choose Azure Private Link instead of relying mainly on Azure SQL Firewall?
- How can Microsoft Sentinel rules and alerts be configured to quickly detect suspicious Azure SQL activities?

---

## Resources I Found Useful

- [Microsoft Learn — Azure SQL Database Security](https://learn.microsoft.com/azure/azure-sql/database/security-overview)
- [Microsoft Learn — Microsoft Entra Authentication for Azure SQL](https://learn.microsoft.com/azure/azure-sql/database/authentication-aad-configure)
- [Microsoft Learn — Azure SQL Firewall](https://learn.microsoft.com/azure/azure-sql/database/firewall-configure)
- [Microsoft Learn — Azure Private Link for Azure SQL](https://learn.microsoft.com/azure/azure-sql/database/private-endpoint-overview)
- [Microsoft Learn — Azure SQL Auditing](https://learn.microsoft.com/azure/azure-sql/database/auditing-overview)
- [Microsoft Learn — Microsoft Defender for SQL](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-sql-introduction)
- [Microsoft Learn — Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/overview)

---

*Submitted by: Michael Chinonso Onwumere · MichaelOnwumere*