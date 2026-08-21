# My Notes — Iniobong Johnson

---

## Key Concepts I Learned

### Role Based Access Control, RBAC

RBAC, which means Role Based Access Control, is used to manage access to resources and enforce the principle of least privilege by ensuring users are only given the permissions required for their roles.

### Azure RBAC Scope Levels

There are four main scope levels within Azure RBAC:

- Management Group,
- Subscription,
- Resource Group,
- Resource.

These scopes help determine where a particular role assignment will apply.

### Managed Identities

Managed Identity helps eliminate the need to store credentials when workloads need to authenticate to Azure resources. The roles assigned to a managed identity determine which resources an application or automation can access.

There are two types of managed identities, System Assigned and User Assigned.

A System Assigned Managed Identity is tied directly to the lifecycle of the Azure resource. If the resource is deleted, the identity is also deleted.

A User Assigned Managed Identity is created separately and can be shared across multiple Azure resources.

I also learned that both System Assigned and User Assigned Managed Identities can coexist depending on the requirements of the environment.

### Built In Roles and Custom Roles

Azure provides a large number of built in roles for different access requirements. Before creating a custom role, it is important to review the available built in roles to confirm whether a role already exists that meets the required permissions.

This can help reduce unnecessary custom configurations and make role management easier.

### Azure RBAC Custom Roles and Microsoft Entra Custom Roles

Azure RBAC Custom Roles and Microsoft Entra Custom Roles operate differently.

An Azure RBAC Custom Role controls access to Azure resources, while a Microsoft Entra Custom Role controls permissions related to Microsoft Entra resources.

This means that an Azure RBAC Custom Role does not affect a Microsoft Entra Custom Role, and vice versa.

### Azure Backup RBAC Roles

I also learned about the different built in RBAC roles available for Azure Backup.

- Backup Contributor is responsible for backup vault setup, management, and security related configurations.

- Backup Operator is mainly responsible for day to day backup and recovery operations.

- Backup Reader provides read only access and can be useful for auditing, monitoring, and helpdesk related activities.

If a user does not need to configure the vault or manage security settings, assigning the Backup Operator role may be more appropriate than giving broader permissions.

---

## My Takeaways

My key takeaway from this lesson was the importance of checking the available built in roles before creating a custom role.

Before creating a new role, it is important to confirm whether Azure already provides a built in role that meets the required permissions. This supports the principle of least privilege, reduces unnecessary custom configurations, and makes access management easier.

---

*Submitted by: Iniobong Johnson · Inib12*
