# My Notes — BERNA NAMULYOWA

## Key Concepts I Learned

# **DESIGN AND IMPLEMENT NETWORK SECURITY**

Azure Virtual network is a private network that allows azure resources like virtual machines  to communicate  with each other.

Azure Virtual network helps in filtering network traffic, it helps in coordinating Azure resources, routing of network traffic etc. Using Virtual network peering different virtual networks can communicate with each other and the networks can be in same or different Azure regions.

Subnet is a small network created inside the Virtual network



**Comparison of NSG, Firewall and WAF**



||**USAGE**|**SCOPE**|**MECHANISM**|
|-|-|-|-|
|**NSG**|Controls basic network to and from virtual machines and subnets|operates at individual network interface or subnet level|uses stateful allow or deny based on IP addresses, ports and protocols|
|**FIREWALL**|Secures traffic between different network zones such as the public internet and private cloud|operates at the network perimeter or across entire virtual network|inspects network and transport traffic using domain name FQDN filtering and applies deep packet inspection|
|**WALL**|Protects web applications from specific cyber attacks like SQL injection and cross-site scripting|Focuses strictly on HTTP and HTTPS traffic targeting specific web apps or load balancers|Inspects web application payloads using signature databases, anomaly detection and security rules.|





**What is the Microsoft Cloud Security Benchmark (MCSB)?**

A collection of high-impact security best practices and recommendations that help improve security workloads, data and services on Azure and the multicloud environment.



### **AZURE DDoS PROTECTION**

This is a cloud-native security service which protects Azure resources automatically against distributed denial of Service attacks



**Types Azure DDoS mitigates**

DDoS Attack Strategies

1. **Volumetric attacks**: These attack the network layer with traffic that seems to be legitimate. They include UDP floods, spoofed-packet floods and amplification floods. They are mitigated by absorbing and scrubbing them  with Azure's global network scale automatically.
2. **Protocol attacks**: These exploit the weakness in the layer 3 and 4 protocol stack. They are mitigated by separating between the malicious and legitimate traffic, interacting with the client and blocking malicious traffic.
3. **Resource (Application) layer attacks:** Their target is on the web application packets and disrupt the transmission of data between the hosts. They are mitigated by using A web Application Firewall like the Azure Gateway web Application firewall and DDoS protection.



**There two Protection Tiers**

* DDoS IP Protection:- This is designed for core lightweight protection on small number of public Ip addresses on a apay-per-protected IP model.
* DDoS Network Protection- This is recommended for Enterprises, it is an enhanced  tenant-level protection that provides adaptive tuning, cost protection guarantees and Azure DDoS Rapid Response (DDR) support.



#### Implement and Manage NSGs

There are two types of network topologies

* Flat network- This places all devices in a single address shared space. One without any subnet attached to it. Lateral movement is high in the flat network. It is best for small isolated test labs.
* Segmented network - Here the workloads are split in distinctive subnets. It permits only required traffic between workloads because it uses explicit rules to deny traffic. It is recommended for production environments , multi-tier cloud applications.



**Application Security Group**

It is like a container that helps you create NSG roles.  Security policies can be reused without manually maintaining of the explicit IP addresses.

Any rule assigned and has the lowest number takes the privilege.

## Lab / Hands-On Work



Created a Virtual Network under resource group- Bernanetsec, virtual name: Nalin and default subnet: Nalin-subnet

<img width="2880" height="1800" alt="Screenshot 2026-08-27 120649" src="https://github.com/user-attachments/assets/37880896-dc53-4897-8967-ea29ca053910" />


Created a Application Security Groups one for the webserver (ASG-Nalinwebserver) and the other for the management server (ASG-Nalinmgtserver)
<img width="2880" height="1800" alt="Screenshot 2026-08-27 121536" src="https://github.com/user-attachments/assets/f3883599-3aae-4294-a796-12963d8754e8" />



Created a Network Security Group: NSG-Nalin

<img width="2880" height="1800" alt="Screenshot 2026-08-27 124817" src="https://github.com/user-attachments/assets/4ae46e92-18da-45a6-9e1e-a08d030d720a" />


Apply NSG on a subnet. Select ***subnet*** under the NSG then ***Associate***
<img width="2880" height="1800" alt="Screenshot 2026-08-27 125508" src="https://github.com/user-attachments/assets/6c63e04e-f6f6-4269-8a30-d32626d15536" />




Add an Inbound security rule on the webserver. Select ***Inbound security rules*** click on ***Add*** and fill in the particulars.

<img width="2880" height="1800" alt="Screenshot 2026-08-27 131346" src="https://github.com/user-attachments/assets/92880efc-ccd7-4428-8ea7-c846bda4e4f0" />


Add an Inbound security rule on the mgmtserver. To be able to RDP to the webserver. Select ***Inbound security rules*** click on ***Add*** and fill in the particulars.

<img width="2880" height="1800" alt="Screenshot 2026-08-27 131406" src="https://github.com/user-attachments/assets/be1c76c5-98fc-43bb-bedd-7fb26ba3c652" />




Created a Virtual Machine for the webserver


<img width="2880" height="1800" alt="Screenshot 2026-08-27 133707" src="https://github.com/user-attachments/assets/dfaf223f-0178-4119-91c2-80f4b76d8ec4" />

Created another for the management server
<img width="2880" height="1800" alt="Screenshot 2026-08-27 134537" src="https://github.com/user-attachments/assets/416cde5f-1e87-4c1a-99aa-1b03d3e54dbd" />



Add application security group to both virtual machines

<img width="2880" height="1800" alt="Screenshot 2026-08-27 135052" src="https://github.com/user-attachments/assets/ebf019d0-8250-4e47-bcd5-41c93559d11d" />


Connect the Mgmtserver to the RDP


<img width="2880" height="1800" alt="Screenshot 2026-08-27 141049" src="https://github.com/user-attachments/assets/8788c5c7-5d83-4d88-b368-bc5df0d3062f" />





### What I did

## **Configure DDoS Protection on a virtual network using the Azure portal**

1. **Create a resource group**

Select ***Resource groups***, then ***create*** on the ***basics*** tab, resource group, enter ***mybudnalin***, on region, select ***East US***, then ***review and create***



**2. Create a DDoS Protection plan**

Search ***DDoS*** and select ***DDoS protection plan*** when it appears. Select + Create. On the ***Basics tab***, in the Resource group list, select the ***resource group*** you just created.

On the Instance name box, enter ***DDoSProtectionPlan***, then select Review + create. Select Create.



**3. Enable DDoS Protection on a new virtual network**

Select ***Virtual Network*** then select Create. On the ***Basics tab***, select the resource group you created previously. In the Name box, enter ***NalinVirtualNetwork***, then select the Security tab. On the ***Security tab***, next to DDoS Network Protection, select ***Enable***. On the DDoS protection plan drop-down list, select ***DDosProtectionPlan***. Select Review + create. Select Create.



**4. Configure DDoS telemetry**

Search Public IP, then select ***Public IP address*** when it appears then ***Create***, under ***SKU***, select ***Standard***. On the Name box, enter ***MyPublicIPAddress*** then select ***Static***. On ***DNS name label***, enter ***mypublicdnsng***. Select ***Create***.

To set up ***telemetry***, navigate to the Azure home page, select All resources.

On the list of your resources, select ***DDosProtectionPlan***. Under ***Monitoring***, select ***Metrics***.

Select the ***Scope*** box, then select the checkbox next to ***MyPublicIPAddress***.

Select ***Apply*** then On the ***Metrics*** box, select ***Inbound packets dropped DDoS***. On the ***Aggregation*** box, select ***Max***.

<img width="2880" height="1800" alt="Screenshot 2026-08-29 122602" src="https://github.com/user-attachments/assets/95f5012e-f238-40e4-87bc-6a714fc5372a" />




**5. Configure DDoS diagnostic logs**

Select ***MyPublicIPAddress***. Under ***Monitoring***, select ***Diagnostic settings***. Select A***dd diagnostic setting***.

On the ***Diagnostic setting*** page, in the Diagnostic setting name box, enter ***MyDiagnosticSetting***.

Under ***Category details***, select all 3 ***log*** checkboxes and the ***AllMetrics*** checkbox.

Under ***Destination details***, select the ***Send to Log Analytics workspace*** checkbox.



**6. Configure DDoS alerts**

Select ***virtual machine***, then ***Create***. On the ***Basics tab***, create a new VM using the information in the table below. Select ***Review + create***.

<img width="2880" height="1800" alt="Screenshot 2026-08-29 132604" src="https://github.com/user-attachments/assets/c971eb13-3440-4670-9b92-30cbc7adc9b9" />

On the ***Generate new key pair*** dialog box, select ***Download private key and create resource***.

Save the private key. When deployment is complete, select Go to resource.
<img width="2880" height="1800" alt="Screenshot 2026-08-29 134337" src="https://github.com/user-attachments/assets/1976dbf3-fa74-4840-9e00-5cb08a54247f" />


&#x20; **Assign the Public IP address**

On the ***Overview page*** of the new virtual machine, under ***Settings***, select ***Networking***.

Next to ***Network Interface***, select ***myvirtualmachine-nic***. The name of the nic may differ.

Under ***Settings***, select ***IP configurations.*** Select ***ipconfig1***.

On the ***Public IP*** address list, select ***MyPublicIPAddress***. Select ***Save***.

&#x20; **Configure DDoS alerts**

select ***MyPublicIPAddress***. Under ***Monitoring***, select **Alerts**. Select ***Create alert rule***. On the Create alert rule page, under ***Scope***, select ***Edit resource***.

Select Under DDoS attack or not for the signal name. Under Alert logic find the Operator setting and select Greater than or equal to.

On Threshold value, enter ***1*** (means under attack). Navigate to the details tab and select ***Alert rule name***, enter ***MyDdosAlert***. Select ***Create alert rule.***

<img width="2880" height="1800" alt="Screenshot 2026-08-29 140443" src="https://github.com/user-attachments/assets/cca44a84-8c2a-41b8-a4dc-5f7f1c71af65" />


**7. Test with simulation partners**


### What happened / Result



### Challenges I faced

Too many steps to follow up.



## Resources I Found Useful

<!-- Any links, docs, or Microsoft Learn modules you found helpful -->

* https://learn.microsoft.com/en-us/azure/ddos-protection/types-of-attacks
* https://microsoftlearning.github.io/AZ-700-Designing-and-Implementing-Microsoft-Azure-Networking-Solutions/Instructions/Exercises/M06-Unit%204%20Configure%20DDoS%20Protection%20on%20a%20virtual%20network%20using%20the%20Azure%20portal.html

\---

*Submitted by:Bernanamulyowa · bernah*

