# My Notes — Michael Chinonso Onwumere

## Key Concepts I Learned

- Learned the basic concept of a **network** as a way of connecting computer systems together across rooms, cities, states, and other locations.
- Learned about the **Microsoft Cloud Security Benchmark (MCSB)**, which provides security best practices and recommendations for protecting cloud environments.
- Learned the three main principles of **Zero Trust**:
  - Always verify or verify explicitly.
  - Use least privilege access.
  - Assume breach.
- Learned about **Microsoft Defender for Cloud** and its role as a cloud-native security platform for managing security posture and protecting cloud workloads across multi-cloud and hybrid environments.
- Learned about **DDoS (Distributed Denial of Service) attacks** and how Azure DDoS Protection and Network Protection can help protect network resources.
- Learned the difference between a **flat network** and a **segmented network**. A flat network allows more free movement between subnets, while a segmented network introduces restrictions and security rules to control traffic.
- Learned how **Network Security Groups (NSGs)** can be used to control network traffic based on security rules.
- Learned about **Application Security Groups (ASGs)** as logical containers that can be used when creating NSG rules and organizing workloads.
- Learned that **NSG rule priority matters** because rules with lower numbers have higher priority.
- Learned that NSGs can be applied to **network interfaces and subnets** to control network traffic.

---

## Lab / Hands-On Work

### What I did

During the hands-on session, I followed the instructor's demonstration on implementing network security controls in Azure.

The lab involved:

1. Creating an **Azure Virtual Network (VNet)**.
2. Creating a **virtual subnet** within the VNet.
3. Creating two Application Security Groups:
   - `ASG-Web-Server`
   - `ASG-Mgt-Service`
4. Creating a **Network Security Group (NSG)**.
5. Understanding that NSGs can be applied to network interfaces and subnets.
6. Creating two virtual machines:
   - A web server VM.
   - A management service VM.
7. Placing the VMs within the same subnet and applying the NSG rules.
8. Adding each VM to its appropriate Application Security Group.
9. Observing how ASGs and NSGs can work together to control and organize network access.

### What happened / Result

- I gained a better understanding of how Azure Virtual Networks provide the foundation for network communication and security.
- I learned how **network segmentation** can be used to introduce restrictions between workloads instead of allowing unrestricted movement across a network.
- I understood how **NSGs and ASGs work together**, with ASGs providing logical grouping of resources and NSGs defining the network security rules.
- I also learned the importance of NSG rule priority when multiple security rules are configured.
- The lab helped me connect the theoretical concepts of network security with practical Azure resources.

### Challenges I faced

- Understanding the relationship between **NSGs, ASGs, subnets, and network interfaces** required careful attention during the demonstration.
- Understanding how traffic restrictions change between a flat network and a segmented network was another area I needed to pay close attention to.
- The different roles of ASGs and NSGs initially required some clarification, but the hands-on demonstration made the relationship easier to understand.
- - I had limited permissions in the Azure subscription provided for the bootcamp, which restricted my ability to fully configure and practice some of the network security controls.
- Despite the restrictions, I followed the instructor's demonstration and gained an understanding of how the controls are implemented.

---

## My Takeaways

My biggest takeaway from this session is that **network security is not just about connecting resources; it is also about controlling how those resources communicate with each other**.

I learned that network segmentation, NSGs, and ASGs can be used to reduce unnecessary network access and support the principle of **least privilege**. I also understood how the Zero Trust principles of verifying explicitly, using least privilege, and assuming breach can be applied to network security.

The session also helped me understand that protecting a cloud environment requires multiple layers of security, including network controls, DDoS protection, segmentation, and continuous security monitoring.

---

## Questions I Still Have

- How can NSGs and ASGs be designed effectively in a large production environment with many applications and virtual machines?
- How does Azure Virtual Network Manager help manage network security and segmentation across multiple VNets?
- What are the best practices for designing a segmented Azure network while still allowing the required application traffic?

---

## Resources I Found Useful

- Microsoft Cloud Security Benchmark (MCSB)
- Microsoft Defender for Cloud
- Azure DDoS Protection
- Azure Virtual Network documentation
- Azure Network Security Groups (NSGs)
- Azure Application Security Groups (ASGs)
- Azure Virtual Network Manager (AVNM)

---

*Submitted by: Michael Chinonso Onwumere · MichaelOnwumere*