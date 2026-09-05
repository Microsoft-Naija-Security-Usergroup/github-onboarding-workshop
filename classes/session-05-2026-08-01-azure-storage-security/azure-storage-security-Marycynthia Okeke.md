# My Notes — Okeke Marycynthia

## Key Concepts I Learned

* **Azure Storage Foundation & Endpoints:** An Azure Storage account provides a unique namespace containing all storage data objects. Every object's URL combines the account name with service-specific endpoints:

  * Blob Storage: `.blob.core.windows.net`
  * Azure Files: `.file.core.windows.net`
  * Queue Storage: `.queue.core.windows.net`
  * Table Storage: `.table.core.windows.net`

* Azure Storage is durable, encrypted at rest by default using AES-256, massively scalable to petabytes, and globally accessible over HTTP/HTTPS.

* **Core Storage Services:**

  * **Blob Storage:** Highly scalable object storage for unstructured text/binary data, media, backups, and Data Lake analytics workloads.
  * **Azure Files:** Fully managed SMB and NFS cloud file shares that can be mounted from cloud or on-premises environments. It is ideal for lift-and-shift applications.
  * **Queue Storage:** Provides reliable asynchronous messaging between decoupled application microservices.
  * **Table Storage:** A schemaless NoSQL key-attribute store for structured, non-relational data and IoT telemetry.

* **Blob Storage Types:**

  * **Block Blobs:** Optimized for streaming and storing large amounts of standard data, supporting objects up to approximately 190.7 TiB.
  * **Append Blobs:** Optimized for append operations where new blocks are added to the end. They are ideal for logging and audit trails.
  * **Page Blobs:** Optimized for random read/write operations using 512-byte pages and are used for Azure VM VHD disks.

* **Redundancy & Access Tiers:**

  * **LRS:** Maintains three copies in a single datacenter.
  * **ZRS:** Replicates data across three availability zones.
  * **GRS:** Geo-replicates data to a secondary region.
  * **GZRS:** Combines zone redundancy with geo-replication.
  * **Hot:** Designed for frequently accessed data.
  * **Cool:** Designed for infrequently accessed data with 30+ day retention.
  * **Cold:** Designed for rarely accessed data with 90+ day retention.
  * **Archive:** Designed for offline, long-term storage and requires rehydration before access.

* **Data Plane vs. Management Plane:**

  * **Data Plane (`*.blob.core.windows.net`):** Handles reading, writing, and deleting files through REST/SMB and is directly affected by the storage firewall.
  * **Management Plane (`management.azure.com`):** Handles resource creation, key rotation, and firewall configuration through Azure Resource Manager (ARM).
  * Enabling the storage firewall does not lock administrators out of ARM or the Azure portal.

* **Default Storage Attack Surface & Risks:**

  * Default storage accounts can expose three major security risks:

    * A globally reachable public network endpoint.
    * Default Shared Key authentication using 512-bit access keys without a rotation policy.
    * Potential anonymous blob access.
  * A potential attack chain is:
    **Public/legacy access → Account key/SAS token leaked → Unrestricted privilege reuse → Data exfiltration or ransomware impact**
  * Storage credentials can potentially be leaked through repositories, logs, or memory dumps.

* **Identity-Based Authentication for Azure Files:**

  * Azure Files supports three distinct SMB authentication methods, with only one active per storage account:

    * **On-premises AD DS:** For domain-joined Windows machines using existing AD infrastructure and requiring line-of-sight to Domain Controllers.
    * **Microsoft Entra Domain Services:** A cloud-only managed domain service for cloud-native Windows VMs.
    * **Microsoft Entra Kerberos:** For hybrid/cloud-joined identities accessing file shares over the internet without line-of-sight to Domain Controllers.

---

## Lab / Hands-On Work

### What I did

* Evaluated the security perimeter and attack surface of default Azure Storage Account configurations.
* Analyzed the isolation between Data Plane and Management Plane operations.
* Reviewed how network firewall rules can be configured while maintaining administrative ARM management.
* Compared storage replication architectures:

  * LRS
  * ZRS
  * GRS
  * GZRS
* Reviewed lifecycle management across:

  * Hot
  * Cool
  * Cold
  * Archive
* Reviewed identity-based SMB access models for Azure Files:

  * AD DS
  * Microsoft Entra Domain Services
  * Microsoft Entra Kerberos

### What happened / Result

* Mapped out the attack chain showing how leaked 512-bit storage access keys and public endpoints can lead to data exfiltration and ransomware attacks.
* Established the security-engineered pattern of:

  * Disabling public access by default.
  * Using Entra ID and RBAC instead of Shared Keys.
  * Applying private endpoints/firewalls.
  * Enabling Defender for Storage.

### Challenges I faced

* Understanding the operational constraints of Azure Files identity methods, particularly when line-of-sight to Domain Controllers is required versus using Microsoft Entra Kerberos over the internet.
* Distinguishing between data plane permissions and control plane ARM operations when applying network access restrictions.

---

## My Takeaways

* Shared Keys are an anti-pattern for production environments.
* Enforcing Microsoft Entra ID and RBAC helps eliminate long-lived secret exposure.
* Turning on the storage firewall protects the data plane without locking administrators out of management configurations on the Azure Resource Manager (ARM) layer.

---

## Questions I Still Have

* What is the best strategy for migrating legacy applications dependent on Page Blobs or Shared Keys to modern Azure RBAC and private endpoints?


## Resources I Found Useful

*Submitted by: Marycynthia Okeke · Nechy-Okeke*

