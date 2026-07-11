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

-
-
-

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
<img width="1366" height="768" alt="Picture 25" src="https://github.com/user-attachments/assets/9fe99e29-58cb-481e-a944-145e93d2ea91" />
<img width="1366" height="768" alt="Picture 24" src="https://github.com/user-attachments/assets/9f629800-627d-4eb5-973d-61ce95ea2f92" />
<img width="1366" height="768" alt="Picture 23" src="https://github.com/user-attachments/assets/5ab06492-24bf-4c9f-99c7-a291f9ed7114" />
<img width="1366" height="768" alt="Picture 22" src="https://github.com/user-attachments/assets/b00f0702-07ed-4838-818d-f95b91186160" />
<img width="1366" height="768" alt="Picture 21" src="https://github.com/user-attachments/assets/35751708-bc1c-4a92-856a-f085af2eea28" />
<img width="1366" height="768" alt="Picture 20" src="https://github.com/user-attachments/assets/7b9cb0a6-09f6-4fa2-b77a-375a0275524e" />
<img width="1366" height="768" alt="Picture 19" src="https://github.com/user-attachments/assets/feeaa345-8f6e-42c8-9140-bcb1d7ee9c7f" />
<img width="1366" height="768" alt="Picture 18" src="https://github.com/user-attachments/assets/10ad02cb-e11b-45aa-946c-04765c71eef6" />
<img width="1366" height="768" alt="Picture 17" src="https://github.com/user-attachments/assets/b8f81de2-dee3-4263-aab8-1c9cf65fe53a" />
<img width="1366" height="768" alt="Picture 16" src="https://github.com/user-attachments/assets/4e540016-5358-47bb-9cd2-78b32ebc8668" />
<img width="1366" height="768" alt="Picture 15" src="https://github.com/user-attachments/assets/5f54d836-a74c-4e69-b6d1-c52255d64f53" />
<img width="1366" height="768" alt="Picture 14" src="https://github.com/user-attachments/assets/b55bbed9-3239-4ac8-9680-c7b5d7a8629c" />
<img width="1366" height="768" alt="Picture 13" src="https://github.com/user-attachments/assets/6900a4f0-3128-43aa-8538-21bdc5cbfb24" />
<img width="1366" height="768" alt="Picture 12" src="https://github.com/user-attachments/assets/7cb9ed74-9b34-44d8-a4a2-6528ba3aa878" />
<img width="1366" height="768" alt="Picture 11" src="https://github.com/user-attachments/assets/147912e4-7eee-4974-8f80-d16b3eca2f56" />
<img width="1366" height="768" alt="Picture 10" src="https://github.com/user-attachments/assets/0f7e9634-cd39-4d94-82e2-5144c335a084" />
<img width="1366" height="768" alt="Picture 9" src="https://github.com/user-attachments/assets/c5fe6070-7270-446b-87eb-706eb763d71c" />
<img width="1366" height="768" alt="Picture 8" src="https://github.com/user-attachments/assets/9a85bcb2-f947-4ea2-befa-0d8877ee19dc" />
<img width="1366" height="768" alt="Picture 7" src="https://github.com/user-attachments/assets/6cccc46c-6194-48f9-90d0-94f8984ad451" />
<img width="1366" height="768" alt="Picture 6" src="https://github.com/user-attachments/assets/dac61802-dc98-4255-bfe5-5ea49d1afb07" />
<img width="1366" height="768" alt="Picture 5" src="https://github.com/user-attachments/assets/1000d5df-7638-481f-a2e3-ed7dec8e753d" />
<img width="1366" height="768" alt="Picture 4" src="https://github.com/user-attachments/assets/3d826d06-a608-49de-8265-55561148cae4" />
<img width="1366" height="768" alt="Picture 3" src="https://github.com/user-attachments/assets/6bd1f562-3fff-481d-a790-19a87bd340bc" />
<img width="1366" height="768" alt="Picture 2" src="https://github.com/user-attachments/assets/57042653-f4ae-42aa-b828-945c99737aa7" />
<img width="783" height="446" alt="Picture 1 Lab 1 Question" src="https://github.com/user-attachments/assets/f056e69d-ba5f-4e55-b81e-0d300e34c00b" />



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
- Visual studio code

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
