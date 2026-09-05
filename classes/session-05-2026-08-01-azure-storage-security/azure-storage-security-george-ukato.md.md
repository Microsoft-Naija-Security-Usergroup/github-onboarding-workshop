# My Notes — \[George Ukato]



## Key Concepts I Learned

<!-- Write the main ideas covered in today's session -->



* Identity-Based Authentication for Azure files: \[i] On-premises AD DS \[ii] Microsoft Domain Services \[iii] Microsoft Entra Kerberos.
* File Movement \& Migration Option: AZ Copy, Storage Explorer, Azure file Sync, Azure Data Box, Azure Migrate.
* Service Endpoints and their URL: Blobs, Files, Queues, Tables.

\---

## Lab / Hands-On Work

<!-- Describe what you did in the lab. Include steps, commands, or screenshots descriptions -->

### What I did



* Created a storage account edited the network and security configurations.
* Created a container and uploaded some files to the container.
* Configured classic share files and was able to map the folder to my computer after running the power shell command.
* During the lab, I successfully accessed the Azure Storage Account using both the access key and the connection string, which granted full access to the storage account and its resources.
* I was able to streamline access to a specific Azure Storage service by using Shared Key authorization, which allowed me to define the services that could be accessed and the permissions granted to each.
* During the lab, I explored how Shared Access Signatures (SAS) can be used to grant secure, limited access to specific files or resources at the container level. I also learned the difference between generating SAS tokens using an Account Key and a User Delegation Key.



### What happened / Result



* The result were as expected. However, I didn't understand the full concept of user delegation key and I have a question on it.







### Challenges I faced



* I had a limited window to carry out the practical lab because I was using a borrowed Azure environment. I look forward to receiving access to our test Azure environment, which will give me more time to practice and explore the concepts covered during the sessions.



\---

## My Takeaways

<!-- What was most valuable to you personally from this session? -->



* Once key rotation is performed, any existing connections or applications using the old storage account key will no longer be able to authenticate until they are updated with the new key.
* In a production environment, it is recommended to disable public access and configure a private endpoint connection to provide secure, private access to the storage account.
* Disabling anonymous access prevents users from accessing files through their direct URL. A Shared Access Signature (SAS) must be generated to provide authorized access.

\---

## Questions I Still Have

<!-- Anything you want to follow up on or ask the mentor -->



* Could you please explain why the User Delegation Key did not grant access to the files? From my understanding of your explanation, using a User Delegation Key should allow access without relying on the storage account key, and key rotation should not affect the connection. I may have misunderstood part of the explanation, so I would appreciate it if you could clarify how it works.

\---

## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->



* The PIM role assignment provided by Emmanuel Itoje enabled me to access the required Azure resources and complete the hands-on lab exercises.
* 

\---

*Submitted by: \[George Ukato] · \[gukato]*

