# My Notes — CHINENYE JOAN OKORO

---

## Key Concepts I Learned

1.	Azure Key Vault is a fully managed cloud service for storing and managing sensitive information such as API keys, passwords, connection strings, encryption keys, and certificates.
The three most important things in Azure Key Vault are secrets, keys, and certificates, they are the three pillars of protecting sensitive data and workloads in the cloud. Together, they form the foundation of defense in depth for both traditional and AI-driven applications.
Secrets Management - Key Vault securely stores sensitive values like passwords, API keys, and connection strings.
Key Management - Provides cryptographic keys for encryption, decryption, and signing operations.
Certificate Management - Centralized handling of TLS/SSL certificates for applications and services. Two Authorized Trusted Partners for certificates in Key Vaults are The Global Sign and DigiCert.
2.	RBAC (Role-Based Access Control) and Managed Identities shows how Azure controls who can access the Key Vault and how applications authenticate securely without exposing credentials respectively.
RBAC (Role-Based Access Control): 
Role Assignments - You assign roles like Reader, Contributor, or Owner to users, groups, or service principals. Each role has specific capabilities.
Principle of Least Privilege - Over-permission increases risk, especially in multi-tenant or AI workloads. Grant only the permissions necessary for a task.
Managed Identities:
Two Types
•	System-Assigned: Created automatically for a resource (like a VM or Function App) and deleted when the resource is removed. One identity to one resource.
•	User-Assigned: Created independently and can be shared across multiple resources. One identity to many resources.



3.	Azure Key Vault has two access models (planes):
 Control Plane
•	Controls who can manage the Key Vault itself.
•	Examples: creating or deleting the vault, setting access policies, configuring RBAC roles.
•	Permissions here are about administration and configuration, not about accessing actual secrets.
•	Managed through Azure Resource Manager (ARM) and governed by Azure RBAC.
Data Plane
•	Controls who can access the contents inside the vault (secrets, keys, certificates).
•	Examples: reading a secret, writing a new key, deleting a certificate.
•	Permissions here are about using the vault’s data.
•	Governed by either Access Policies (older model) or Azure RBAC roles (modern model).

4.	Access Control of Key Vault: Azure RBAC and Vault Access Policies 
Azure RBAC
•	Scope-based: Permissions can be applied at subscription, resource group, or resource level.
•	Integration: Works with Microsoft Entra ID (Azure AD), conditional access, and identity governance.
•	Roles: Uses built-in roles like Key Vault Secrets User, Key Vault Administrator, or custom roles.
•	Strengths: Centralized, scalable, easier to enforce least privilege across multiple vaults.
•	Best Practice: Recommended for modern deployments.

Vault Access Policies
•	Vault-specific: Permissions are configured directly inside each Key Vault.
•	Granular operations: You can grant specific actions (Get, List, Set, Delete) for secrets, keys, and certificates.
•	Legacy model: Original method before RBAC integration.
•	Limitations: Harder to manage at scale, doesn’t integrate smoothly with Entra ID.
•	Use Case: Still supported, mainly for backward compatibility.

5.	Data Protection features in Azure Key Vault: they’re pointing to the built in safeguards that ensure sensitive information is always secure.
Firewall and Network Access
•	You can restrict which networks or IP ranges can reach your Key Vault.
•	By default, Key Vault is accessible over the public internet, but you can lock it down to:
o	Trusted IP ranges
o	Virtual Networks (VNets) with service endpoints or private endpoints
•	This ensures only approved networks can talk to your vault, reducing exposure to external threats.

Soft Delete and Purge Protection
•	Soft Delete: When a secret, key, or certificate is deleted, it isn’t gone immediately—it’s retained for a recovery period (default 90 days).
•	Purge Protection: Prevents permanent deletion until the retention period expires. Even administrators cannot bypass this safeguard.
•	Together, these features protect against accidental or malicious deletion of critical encryption material.
Operational Guardrails
•	Built-in safety checks and policies that prevent risky operations.
•	Examples:
o	Preventing deletion of a vault without purge protection enabled.
o	Enforcing role-based access and logging every access attempt.
o	Alerts and monitoring through Azure Monitor to detect unusual activity.
•	These guardrails ensure that operational mistakes or misconfigurations don’t compromise security.

6.	Token: you can generate a token but can’t store a token in a key vault.
Types of Token are Access Token and Refresh Token.
Access Token - when you authenticate an environment, you generate a token and has  a lifetime of 1 hour.
Refresh Token - lets you renew access without re signing in and has a lifetime of 14 days.

-
-
-

---


## My Takeaways

- If you are not using a Key Vault, Azure Policy will flag you because you are not being compliant.
- Some developers have secrets embedded in their scripts which is not good for the system because once a bad actor has access to the application configuration (s)he can extract the secret and use it. Instead of embedding secrets in code, applications retrieve them securely at runtime.
- Role-Based Access Control (RBAC) and Managed Identities eliminate the need for storing credentials, reduce attack surfaces, and enforce consistent access governance. In AI workloads, this means models and services can securely retrieve secrets (like API keys or database credentials) without exposing them in code or configuration files.
- RBAC (Role-Based Access Control) is about who can do what, at what scope, with the least privilege possible. It’s the backbone of access governance in Azure, especially for sensitive services like Key Vault.
- Rotate Secrets centrally every 3 months or 6 months depending on company policy
- Monitor Anomalous Access with Defender – In case of in coming attack you are to enable Defender for Cloud on your Key Vault to monitor the network, the secret itself.
- Separating the control plane from the data plane ensures that someone who can configure the vault doesn’t automatically get access to the sensitive secrets inside it. This enforces least privilege and strengthens defense in depth.
- Recently, based on feedback and security checks, Microsoft has discouraged customers from using Vault Access Policies and enforced they migrate to Azure RBAC so that they can track every event for visibility on the activity log.
- Azure RBAC is best for any environment adopting a unified Zero Trust Model.
- Data protection in Key Vault isn’t just about encryption—it’s about network isolation, recoverability, and operational safety nets. These features make sure your secrets and keys remain secure even in the face of accidents or attacks
- For best practice, Sign in securely using Azure AD/Managed Identity and always sign out of the application to ensure tokens are invalidated and sessions are closed. This prevents unauthorized reuse of your session or token, especially important in shared environments or when using elevated privileges.


---

## Questions I Still Have

- Credential Rotation
-
-

---

## Resources I Found Useful

(https://learn.microsoft.com/en-us/training/paths/configure-key-vault-security/)

-

---

*Submitted by: Chinenye Joan Okoro · AriZiv237*
