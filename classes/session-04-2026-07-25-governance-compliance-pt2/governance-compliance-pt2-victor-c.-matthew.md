# My Notes — Victor Chizaram Matthew

---

## Key Concepts I Learned

- I learned how **security governance can be incorporated into the development lifecycle** by using policy checks and Infrastructure as Code (IaC) security scanning before resources are deployed. This helps identify security issues early rather than waiting until infrastructure is already in production.
- I learned that **Azure Policy** can be used as a preventive control to ensure that resources meet organizational requirements before or during deployment.
- I gained a better understanding of **Azure RBAC** and the importance of assigning only the permissions required for a specific role. I also learned that management-plane permissions and data-plane permissions are handled differently through Actions and DataActions.
- I learned that protecting backups requires more than simply creating backup copies. Features such as **soft delete and immutable vaults** provide additional protection against accidental deletion, unauthorized changes, and ransomware-related attacks.
- I also learned how **Privileged Identity Management (PIM)** and access reviews can help organizations maintain least-privilege access and reduce unnecessary permanent administrative privileges.

---

## Lab / Hands-On Work

### What I did

I explored the different governance and compliance controls covered in the session, including Azure Policy, RBAC role assignments, backup protection, and security controls for Infrastructure as Code.

I reviewed how policies can be used to enforce organizational standards and how role assignments can be evaluated to identify excessive permissions.

I also studied the use of soft delete and immutable vaults for protecting backup data and looked at how IaC templates can be scanned for potential security issues before deployment.

### What happened / Result

The exercises helped me understand how governance can be integrated into both the development and operational stages of cloud infrastructure.

I was able to see how Azure Policy can act as a preventive control, while RBAC, PIM, and access reviews help control who can perform sensitive actions.

I also understood that backup security should be treated as part of the overall security strategy because attackers may target backups after compromising an environment.

### Challenges I faced

- Understanding the difference between management-plane permissions and data-plane permissions initially required some additional review.
- It took some time to understand how multiple governance controls can work together without creating unnecessary restrictions for administrators and developers.
- Understanding the practical implementation of immutable backup protection was easier conceptually than configuring it in a real production environment.

---

## My Takeaways

My major takeaway from this session is that **cloud security should be built into the process from the beginning rather than added after deployment**.

Using Azure Policy and IaC security scanning allows organizations to identify and prevent insecure configurations before they become production problems.

I also learned that having backups does not automatically mean that an organization is protected from data loss. Backup data itself needs security controls such as soft delete and immutability to protect it from malicious or accidental deletion.

Another important lesson was the value of **least privilege and just-in-time administrative access**. Giving users permanent elevated permissions increases risk, so access should be carefully controlled, reviewed, and granted only when necessary.

Overall, the session showed me that effective cloud governance requires a combination of preventive controls, identity management, data protection, continuous monitoring, and accountability.

---

## Questions I Still Have

- How can Azure Policy be designed to enforce strong security requirements without negatively affecting developers who need flexibility during deployments?
- How can organizations determine when a custom RBAC role is more appropriate than an existing built-in role?
- What is the best approach for implementing immutable backups across a large Azure environment?
- How can IaC security scanning be fully integrated into a CI/CD pipeline so that insecure infrastructure cannot reach production?

---

## Resources I Found Useful

- Microsoft Learn — Manage and right-size RBAC role assignments
- Microsoft Learn — Protect backup data with Azure Backup security
- Microsoft Learn — Implement security controls in Infrastructure as Code
- Microsoft Learn — Azure Policy documentation
- Microsoft Learn — Microsoft Entra Privileged Identity Management

---

*Submitted by: Victor Chizaram Matthew · [victor-matthew-folder](https://github.com/victor-matthew-folder)*