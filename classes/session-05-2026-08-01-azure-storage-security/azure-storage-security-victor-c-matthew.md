# My Notes — Victor Chizaram Matthew

---

## Key Concepts I Learned

- Azure Storage security involves multiple layers, including identity, authorization, encryption, network controls, and monitoring. Protecting stored data requires combining these controls rather than depending on a single security mechanism.
- I learned the importance of using **Microsoft Entra ID and Azure RBAC** to control access to storage resources and applying the principle of least privilege when assigning permissions.
- I gained a better understanding of **Shared Access Signatures (SAS)** and how they can provide temporary and limited access to storage resources without exposing the storage account's primary access keys.
- I learned that **storage account access keys and SAS tokens have different security implications**. Access keys can provide broad access to the storage account, while a properly configured SAS can restrict access based on resources, permissions, and duration.
- **Private Endpoints and network restrictions** can be used to reduce exposure of Azure Storage to the public internet and allow storage resources to be accessed through private network connectivity.
- I also learned that security monitoring is an important part of protecting storage accounts, especially for identifying suspicious access, malware, and possible data exfiltration attempts.

---

## Lab / Hands-On Work

### What I did

I followed the session materials and reviewed the process of securing an Azure Storage account.

I explored how storage resources can be protected using Azure RBAC, SAS, secure transfer settings, network restrictions, and private endpoints. I also reviewed the different ways users and applications can authenticate when accessing blobs and other storage services.

In addition, I studied how storage account access keys can be managed and why organizations should avoid unnecessarily relying on broad access credentials.

### What happened / Result

The session helped me understand how to apply different security controls to an Azure Storage environment.

I was able to understand how permissions can be restricted using RBAC and how SAS can provide more controlled, temporary access to specific storage resources.

I also gained a clearer understanding of how network isolation and secure transfer requirements can reduce the attack surface of a storage account.

### Challenges I faced

- Understanding the different authentication and authorization options for Azure Storage required some additional review.
- It was initially difficult to determine when SAS should be used instead of Microsoft Entra ID and RBAC.
- Some network security features, particularly Private Endpoints, are easier to understand when they can be configured and tested in an actual Azure environment.

---

## My Takeaways

One of my biggest takeaways from this session is that **protecting data in Azure Storage goes beyond simply enabling encryption**.

Access needs to be carefully controlled, network exposure should be minimized, and temporary access mechanisms such as SAS should have appropriate permissions and expiration periods.

I also learned that relying on storage account access keys can create unnecessary security risks because they can provide extensive access to storage resources. Using Microsoft Entra ID and RBAC where possible provides a more manageable approach to controlling access.

Another important lesson is that storage security should include monitoring and threat detection. Even when strong preventive controls are in place, organizations still need visibility into how their data is being accessed and whether suspicious activity is occurring.

---

## Questions I Still Have

- What is the best approach for choosing between Microsoft Entra ID, RBAC, SAS, and access keys for different application scenarios?
- How can an organization effectively monitor and investigate suspicious access to Azure Storage?
- What are the recommended practices for securing Azure Storage when applications need to access it from different networks?
- How does Microsoft Defender for Storage respond when malicious content is detected inside a storage account?

---

## Resources I Found Useful

- Microsoft Learn — Implement storage account security: https://learn.microsoft.com/en-us/training/modules/implement-storage-account-security/
- Microsoft Learn — Azure Storage Shared Access Signatures: https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview
- Microsoft Learn — Authorize access to data in Azure Storage: https://learn.microsoft.com/en-us/azure/storage/common/authorize-data-access
- Microsoft Learn — Azure Storage security: https://learn.microsoft.com/en-us/azure/storage/blobs/security-recommendations

---

*Submitted by: Victor Chizaram Matthew · [victor-matthew-folder](https://github.com/victor-matthew-folder)*