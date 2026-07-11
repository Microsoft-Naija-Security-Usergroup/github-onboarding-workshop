# My Notes — CHINENYE JOAN OKORO


---

## Key Concepts I Learned

ASSIGNMENT 1
- Identity as the Security Perimeter: In the cloud era, traditional network boundaries are no longer sufficient. 
Identity has become the new primary perimeter, making account security vital to preventing tenant-wide compromise.
- Conditional Access Policies: these policies operate on an "if-then" logic 
For example "If a user is signing in from an untrusted location, then require Multi-Factor 
Authentication". They are essential for enforcing access controls based on real-time risks and user context.
- Priviledged Identity Management: A governance tool used to minimize standing administrative privileges by 
enforcing Just-in-Time (JIT) access, where roles are only activated for a limited time and often require 
additional approval workflows.
- Passwordless Authentication: To combat password-based threats, the session highlights advanced 
authentication methods such as Windows Hello for Business, passkeys, and FIDO2 security keys like YubiKeys 
that link access to trusted devices. 
- Authentication methods and strengths in Entra


ASSIGNMENT 2
- API keys are simple strings used to control access to APIs, and in Microsoft 365 Copilot they are stored securely 
in the vault to prevent exposure.
- API keys and OAuth using client ID and secret are API security mechanisms API plugins for Microsoft 365 Copilot 
support.
- Client ID, Client Server, Token Endpoints are the information developers need to providein the Teams Developer 
Portal to integrate with an API secured with OAuth.
- Declarative agents are AI-Powered assistants in Copilot that can securely connect to external APIs and be optimized
for specific scenerios.



---

## Lab / Hands-On Work



### What I did
Step 1: Access the portal using this link https://entra.microsoft.com/
Step 2: Scrolled to Conditional Access on the left panel and clicked on it
Step 3: Configured Named Locations based on IP address and inputted a name, then marked the check box as 
trusted location
Step 4: Navigated to Groups, created a group and named it Finance Dept, then assigned owner.
Step 5: Navigated to Conditional Access, to create new policy
Step 6: Inputted the Name of the policy "conditional_access_policy"
Step 7: Set Conditions 
 Users: selected Users and Groups
 Target Resources: selected all resources
 Network: Configured Yes and selected all trusted networks and locations
 Conditions: selected Device Platforms - cofigured Yes then selected windows and macOS
 Grant: Set to Require multi-factor authentication 
 Session: Selected Sign-in Frequency to 14 hours
Step 8: Enable Policy to Report-only
Step 9: Create

### What happened / Result

<img width="1366" height="768" alt="Picture 24" src="https://github.com/user-attachments/assets/14ead864-b44b-4748-93a4-0479e188c0e5" />
<img width="1366" height="768" alt="Picture 23" src="https://github.com/user-attachments/assets/0dc609ac-1d5a-4083-9054-52a94bdb7147" />
<img width="1366" height="768" alt="Picture 22" src="https://github.com/user-attachments/assets/645ec874-088b-4187-8e12-2ae0e0e0eb95" />
<img width="1366" height="768" alt="Picture 21" src="https://github.com/user-attachments/assets/94667e05-4a3c-41f5-bb2c-1674e445c77b" />
<img width="1366" height="768" alt="Picture 20" src="https://github.com/user-attachments/assets/e90920b9-e0ec-45e8-bdff-79e6fb36a7c2" />
<img width="1366" height="768" alt="Picture 19" src="https://github.com/user-attachments/assets/98cb3185-c004-4476-9a15-54dbad569f13" />
<img width="1366" height="768" alt="Picture 18" src="https://github.com/user-attachments/assets/5d3284b0-aaac-4034-ab72-f96e88228965" />
<img width="1366" height="768" alt="Picture 17" src="https://github.com/user-attachments/assets/f8274ca6-3f0e-45ae-80ec-f465491faf5c" />
<img width="1366" height="768" alt="Picture 16" src="https://github.com/user-attachments/assets/00729723-cafb-48ae-8a43-5fbd9aec237a" />
<img width="1366" height="768" alt="Picture 15" src="https://github.com/user-attachments/assets/e8b1bf66-2cb3-4d9c-a9f4-ca180ab4845a" />
<img width="1366" height="768" alt="Picture 14" src="https://github.com/user-attachments/assets/46902311-3ec7-4b78-9fbb-f38ea571e06b" />
<img width="1366" height="768" alt="Picture 13" src="https://github.com/user-attachments/assets/b0fd780f-a0c5-4f01-bfab-b852512b6416" />
<img width="1366" height="768" alt="Picture 12" src="https://github.com/user-attachments/assets/299b3493-4313-41ba-b35c-75818abaa293" />
<img width="1366" height="768" alt="Picture 11" src="https://github.com/user-attachments/assets/e10b074b-a97c-4f51-9479-6fd32d247ec0" />
<img width="1366" height="768" alt="Picture 10" src="https://github.com/user-attachments/assets/830d6237-b478-4d82-a5f5-4cc7eeb98918" />
<img width="1366" height="768" alt="Picture 9" src="https://github.com/user-attachments/assets/8d241eae-c761-46ed-8608-c540c4d644b1" />
<img width="1366" height="768" alt="Picture 8" src="https://github.com/user-attachments/assets/5d52faf9-b9a4-49ca-af5d-5595fce4e1ae" />
<img width="1366" height="768" alt="Picture 7" src="https://github.com/user-attachments/assets/cbb38382-3d86-4b28-9198-eb05c41b7c1f" />
<img width="1366" height="768" alt="Picture 6" src="https://github.com/user-attachments/assets/bbaf937c-9dd1-439f-b74f-1b1cdfe7df17" />
<img width="1366" height="768" alt="Picture 5" src="https://github.com/user-attachments/assets/e9cc828b-6ea6-45c2-a2b4-bfb489cce655" />
<img width="1366" height="768" alt="Picture 4" src="https://github.com/user-attachments/assets/de304497-a0ee-4805-b5f8-d1c74e82f299" />
<img width="1366" height="768" alt="Picture 3" src="https://github.com/user-attachments/assets/4e0a91b8-e77a-45e1-8d27-2e355ae81df4" />
<img width="1366" height="768" alt="Picture 2" src="https://github.com/user-attachments/assets/bb506c97-f69d-4a23-8653-c80e80af05b7" />
<img width="783" height="446" alt="Picture 1 Lab 1 Question" src="https://github.com/user-attachments/assets/94a7a7cf-05a1-40c3-b179-34657dda17a7" />




### Challenges I faced


---

## My Takeaways

ASSIGNMENT 1
- Adopt Zero Trust Principles: Always verify explicitly. Never assume an identity is safe based 
on location or network; assume breach and verify every access request.
- Implement Just-in-Time Access: Avoid permanent administrative role assignments. Use PIM to grant 
users the least privilege necessary only when they specifically need it, reducing the attack surface.
- Leverage Report-only for Troubleshooting: When configuring Conditional Access, use the "Report-only" 
mode to observe policy impact in your environment without blocking users, then review 
Sign-in logs to diagnose why a policy did or did not apply before enabling "Yes".
- Break glass Accounts: are emergency accounts and they should be excluded during Conditional Access Policy
creation so these accouts will not be logged out.

ASSIGNMENT 2
- Declarative agents in Microsoft 365 Copilot improve efficiency by enabling natural language queries over secured APIs.
- OAuth provides stronger user specific authentication compared to API keys
- Storing credentials in the vault ensures security and easy updates without redeployment.
---

---

## Questions I Still Have

ASSIGNMENT 1
- More knowledge about Break Glass Accounts so I don't log out key identity accounts. What are the types of Break glass accounts?
Can any account be tagged/labelled as Break Glass Account? Just in case a mishap occurs and break Glass accounts were not exclude 
is there any solution?

ASSIGNMENT 2
- I need a basic knowledge of APIs, the documentation was a very challenging read
- No basic knowledge of Visual studio code yet

- I still find it challenging to upload on GitHub. I don't really know the steps , it's usaully trial and error, so if I'm to teach another person the process its somewhat challenging.

---

## Resources I Found Useful

ASSIGNMENT 1

- https://learn.microsoft.com/en-us/training/paths/secure-access-resources-entra/

- https://entra.microsoft.com/

- https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/sc-500

ASSIGNMENT 2

- https://learn.microsoft.com/en-us/training/modules/copilot-declarative-agent-api-plugin-auth/1-introduction


---

*Submitted by: Chinenye Joan Okoro · AriZiv237*
