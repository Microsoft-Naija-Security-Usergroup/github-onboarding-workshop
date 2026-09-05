# My Notes — Elu Uchenna Emmanuel
---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- How Azure virtual network and Subnets works
- Flat network and Segmented network
- NSG and Azure Firewall Comparism and where it can be scoped
- VNET, Subnet, NSG and ASG creation
- DDOS protection and Plans
---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did
- Secure Vnet using NSG and ASG. 
-- I will be creating a resource group and ensure all resources created are inside the RG, to ensure resources are easily removed once I delete the RG in order not to incur unexpected cost.
- Create a virtual network with one subnet 
- Create two application security groups 
- Create a network security group and associate it with the virtual network subnet
- Create inbound NSG rules to allow all web traffic to web servers and RDP to the management servers
- Create a virtual machine to use as a web server
- Create a virtual machine to use as a management server
- Associate each virtual machines network interface to it’s ASG
- Test the network traffic filtering

### What happened / Result
- Vnet was successfully created and associated subnet
  <img width="933" height="275" alt="image" src="https://github.com/user-attachments/assets/6596a187-b87f-4845-8fa2-5be1338f8c93" />
  <img width="431" height="493" alt="image" src="https://github.com/user-attachments/assets/c165118e-6a8a-4ab4-b7fc-fd0213ba63cc" />
- NSG and ASG created successfully
  <img width="414" height="474" alt="image" src="https://github.com/user-attachments/assets/1881ffab-31fc-4cf8-b93a-2540edb67fc6" />
  <img width="889" height="425" alt="image" src="https://github.com/user-attachments/assets/28e1b50e-351f-437f-8906-bd0f89dc4926" />

- Create inbound NSG rules to allow all web traffic to web servers and RDP to the management servers
  <img width="429" height="794" alt="image" src="https://github.com/user-attachments/assets/86145818-f3cf-4dfe-a9b1-e3e78459349c" />
  <img width="452" height="805" alt="image" src="https://github.com/user-attachments/assets/136d2993-0466-4db4-b563-f18c85e9a6c4" />
  <img width="940" height="308" alt="image" src="https://github.com/user-attachments/assets/8f8484e8-4a53-4830-9af3-4b04c821ae91" />

- Create a virtual machine to use as a web server and management server
  <img width="936" height="467" alt="image" src="https://github.com/user-attachments/assets/131249b6-9294-486a-88b1-c1818ccf06e9" />
  <img width="940" height="442" alt="image" src="https://github.com/user-attachments/assets/a8bb444d-4192-4cff-a275-8e3edd1f9cba" />

- Associate each virtual machines network interface to it’s ASG
  <img width="422" height="441" alt="image" src="https://github.com/user-attachments/assets/5e0b8084-466d-4296-9900-19cdb18083fe" />
  <img width="423" height="450" alt="image" src="https://github.com/user-attachments/assets/1f347cd7-b639-4d20-b42b-d5c739b73327" />

- Successful RDP access to mgmt. server
  <img width="940" height="682" alt="image" src="https://github.com/user-attachments/assets/2c89da01-7637-48fb-88cc-32ab16c35fc5" />
- Failed RDP access to the webserver
  <img width="936" height="435" alt="image" src="https://github.com/user-attachments/assets/a577d41f-7983-428e-be0a-665da1c2cd48" />
- Successful RDP access to web server
  <img width="486" height="1080" alt="WhatsApp Image 2026-08-20 at 15 37 12" src="https://github.com/user-attachments/assets/2ad23bc2-5e77-4cb0-8b3e-464bf94638f0" />
- Failed RDP access to the management server
  <img width="486" height="1080" alt="WhatsApp Image 2026-08-20 at 15 37 11" src="https://github.com/user-attachments/assets/7cbb210c-9cc4-4232-bc46-83e2592ee726" />

### Challenges I faced
- None. Deployment was seamless

---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->
- Effective Azure network security begins with proper segmentation and enforcing least-privilege network access through the right controls.
- Ensure your ASG is in the same region and resource group as your VM and Vnet
---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

-
-

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

- https://www.youtube.com/watch?v=UCaGi_nARpk&t=3392s
- https://learn.microsoft.com/en-us/training/paths/implement-network-security-controls-azure/

---

*Submitted by: Elu Uchenna Emmanuel · eluemma*
