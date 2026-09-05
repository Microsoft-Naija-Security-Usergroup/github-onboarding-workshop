# My Notes — Victor Chizaram Matthew

---

## Key Concepts I Learned

- Azure governance provides a structured way to control how cloud resources are created, configured, and managed while ensuring they follow organizational and regulatory requirements.
- I learned that **Azure Policy** can be used to enforce rules across resources, such as restricting allowed locations, requiring specific configurations, or preventing non-compliant deployments.
- I understood the difference between a **policy definition**, a **policy assignment**, and an **initiative**. A policy definition contains the rule, an assignment applies that rule to a particular scope, while an initiative combines multiple related policies into a single governance framework.
- **Resource locks** provide an additional layer of protection for important Azure resources. The two main lock types are **CanNotDelete** and **ReadOnly**, which can help prevent accidental deletion or unwanted changes.
- Microsoft Defender for Cloud can be used to assess security posture, identify compliance gaps, and provide recommendations for improving the security of Azure resources.
- Governance and security controls work best when they are implemented proactively rather than waiting until resources become non-compliant.

---

## Lab / Hands-On Work

### What I did

I reviewed the Azure Policy and resource governance features available through the Azure portal and studied how policies can be assigned to specific scopes.

I also explored how resource locks can be used to protect important resources from accidental deletion or modification. In addition, I reviewed the regulatory compliance and security posture features available through Microsoft Defender for Cloud.

I followed the learning materials to understand how policy definitions, assignments, initiatives, resource locks, and compliance recommendations fit together in an Azure environment.

### What happened / Result

The exercises helped me understand how organizations can establish automated guardrails around their Azure environments.

I was able to see how Azure Policy can be used to enforce organizational requirements and how resource locks provide an additional safeguard for critical resources.

I also gained a better understanding of how Defender for Cloud presents compliance information and security recommendations that can help teams identify areas that require attention.

### Challenges I faced

The main challenge was understanding how the different governance components relate to one another, especially the difference between individual policy definitions and initiatives.

It also took some time to understand how the scope of a policy assignment determines which resources are affected. Reviewing practical examples made the relationship between these components clearer.

---

## My Takeaways

The biggest lesson I took from this session is that cloud security should not depend entirely on people remembering to follow security guidelines.

Azure Policy provides a way to turn organizational requirements into enforceable rules, while resource locks can protect critical resources from accidental changes or deletion.

I also learned that governance is not just about blocking deployments. It is also about continuously monitoring the environment, identifying compliance gaps, and providing a clear path toward remediation.

Using Azure Policy together with Microsoft Defender for Cloud provides a stronger governance approach because organizations can enforce standards while also monitoring their overall security and compliance posture.

---

## Questions I Still Have

- How can Azure Policy remediation tasks be configured to automatically correct existing non-compliant resources?
- What is the best way to structure Azure Policy initiatives for a large organization with multiple subscriptions and management groups?
- How quickly does Defender for Cloud reflect changes in compliance status after a resource has been remediated?
- What is the best balance between enforcing strict policies and allowing developers enough flexibility to deploy resources?

---

## Resources I Found Useful

- Microsoft Learn — Introduction to Azure Policy: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-policy/
- Azure Policy Documentation: https://learn.microsoft.com/en-us/azure/governance/policy/overview
- Azure Resource Locks Documentation: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources
- Microsoft Defender for Cloud Documentation: https://learn.microsoft.com/en-us/azure/defender-for-cloud/

---

*Submitted by: Victor Chizaram Matthew · [victor-matthew-folder](https://github.com/victor-matthew-folder)*