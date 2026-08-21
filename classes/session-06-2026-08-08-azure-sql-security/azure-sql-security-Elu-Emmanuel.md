# My Notes — Elu Uchenna Emmanuel

---

## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->

- Securing Azure databases
- SQL Authentication vs. Microsoft Entra ID authentication
- Configuring authentication and managed identity access
- Setting up MS Entra-only authentication

---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did

- Create an SQL database
<img width="1181" height="769" alt="Screenshot 2026-08-12 123742" src="https://github.com/user-attachments/assets/277e13d4-bc7c-4640-8adc-bd7cc3eb0395" />
- Established a firewall rule to allow access to the database server from a selected network.
  <img width="952" height="655" alt="image" src="https://github.com/user-attachments/assets/e5375a9a-37d6-4fb5-9d72-eda847bc98d1" />
- Created a private endpoint and a virtual network. To allow services to the database through a secure endpoint
<img width="767" height="783" alt="image" src="https://github.com/user-attachments/assets/73fc950f-a912-4a4e-b5a3-5a6c076641da" />
- Enabled Azure SQL auditing to track events and write them to a specified storage account or log analytic workspace.
  <img width="994" height="744" alt="image" src="https://github.com/user-attachments/assets/81d05f16-c7c5-4f44-a7ae-37f19c77eaec" />
  
### What happened / Result
- Database deployment was successful with the associated database server created.
  <img width="1594" height="583" alt="image" src="https://github.com/user-attachments/assets/f478b76f-09c1-4e75-b94a-33cbd13794ac" />
- The private endpoint was successfully created
  <img width="1371" height="605" alt="image" src="https://github.com/user-attachments/assets/639e2616-35d1-4957-870e-70c69df777d9" />
- After enabling the Azure SQL auditing and selecting the storage account, an sql audit log folder for the database server was created to log all audit events 
  <img width="1411" height="386" alt="Screenshot 2026-08-13 153611" src="https://github.com/user-attachments/assets/14d0b4bf-e6d5-4469-a775-b718091d2fa8" />
<img width="1191" height="448" alt="image" src="https://github.com/user-attachments/assets/cccb2391-dfe6-4ea1-bd14-2edc38430a42" />

### Challenges I faced
- Yet to understand the essence of running the sql queries
- At first, I was not able to create a private endpoint due to the absence of a virtual network. So I had to create a virtual network in the resource group.
---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->
- Entra ID is the only authentication model that lets the MFA, CA and PIM apply to database access
- Granting a resource access to the database server does not automatically give the resource access to the database itself. You need to directly grant the resource access at the database level.

---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->

- How can I improve in writing sql queries? 

---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->
- https://www.youtube.com/watch?v=MLtnRwB4Wyk
- https://learn.microsoft.com/en-us/training/paths/implement-azure-sql-database-security/

---

*Submitted by: Elu Uchenna Emmanuel · eluemma*
