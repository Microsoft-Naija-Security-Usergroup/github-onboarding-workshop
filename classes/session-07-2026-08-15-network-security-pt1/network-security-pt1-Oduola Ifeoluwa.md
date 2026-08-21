# My Notes — ODUOLA Ifeoluwa

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

-  The role of Network Security Groups (NSGs) and Application Security Groups (ASGs) in controlling network traffic and segmenting workloads 

- Understanding the difference between flat and segmented networks and the security implications of each

- The concept of Microsoft Cloud Security Benchmark and its role in establishing security best practices 

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did
- Created a resource group named "class security" 
-  Created a virtual network named "the class" with a subnet named "blessed subnet"
- Created two Application Security Groups (ASGs): "ASG web server" and "ASG management server" 
-  Created a Network Security Group (NSG) named "NSG class review and create" and associated it with the "blessed subnet"

### What happened / Result


### Challenges I faced
- The presenter faced challenges with screen sharing at one point and also noted that their own system might be blocking external access to the web server's page, preventing a full demonstration of internet connectivity from the web server

---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->

The most valuable takeaway for me was understanding how Network Security Groups (NSGs) and 
Application Security Groups (ASGs) work together to create granular security policies. 
Seeing the practical demonstration of how specific rules could allow or deny traffic based on application groups and protocols was very insightful. 
The distinction between flat and segmented networks and the importance of segmentation for security was also a key learning point.
---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

- How can I effectively troubleshoot NSG rules if traffic is unexpectedly blocked or allowed? 
- What are the best practices for naming and organizing NSGs and ASGs in a large enterprise environment?
- How do Azure Firewall and NSGs complement each other, and when should one be prioritized over the other?

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- https://microsoftlearning.github.io/AZ500-AzureSecurityTechnologies/Instructions/Labs/LAB_02_NSGs.html

---

*Submitted by: Oduola Ifeoluwa · ife005 *
