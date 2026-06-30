### Introduction to Defensive Security
- Defensive Security (AKA Blue Teaming)
- The purpose of a blue team is to protect networks and organizations against data breaches and people with malicious intentions.

---

### Responsibilities of Defensive Security
- Key areas of Defensive Security are
	- **Monitoring and detecting** (Observing a network and system for suspicious activity and events. An example, A employee has logged in from Portugal when the company is based in the UK)
	- **Incident Response** (This is when flags are raised from confirmed suspicious activity. The process involves containment and removal of the threat and restoration of the system)
	- **Threat Intelligence** (This involves gathering and using information about the attackers, methods, targets, trends etc.)
	- **Vulnerability Management** (Figuring out where is most vulnerable and likely to be attacked and figuring out the flaws in the system)
	- **Investigation and Analysis** (The collective, Members of defensive security are always monitoring and analyzing whats happening in a organization, separating normal activity from suspicious behavior)

### Example of a defensive security team

![](Attachments/Pasted%20image%2020260629201252.png)

---

### Defensive Security in Practice
- Organizations don't rely on a single method to stay secure there are many layers of defence involved, some examples:
	- **Employee training** (A majority of attacks are often on employees of companies to gain access to the organization, attackers use the complacency of employees to their advantage such as being susceptible to phishing emails etc. This can be prevented by properly training employees)
	- **Intrusion Detection Systems** (**IDS** for short, these include cameras and alert systems)
	- **Firewalls** (Firewalls act as guards on networks, ideally only allowing non malicious traffic through to the network deciding weather or not any traffic should be accepted or rejected)
	- **Security Policies** (Ensures systems are used correctly like blocking access to malicious websites or requiring strong passwords etc.)

### Exploring the Security Operations Centre (SOC)
- Like the name suggests SOC is the organizations centre for security operations, the frontline for protecting the organization, most cases in large companies they operate 365 days a year around the clock.
- They monitor and protect the organizations networks, systems, and data

### SIEMs: The Defensive Security Radar
- SIEM or Security Information and Event Management
- They are a central place for data and information collected from security devices, workstations, servers, and more within an organizations,
- They are critical to sweeping and reviewing what is happening within a organization
- There are mountains of information gathered in even a single day of operations, SIEMs act as a central place to access the information to analyse the organization

---

### Practical: Defend FakeBank
- In this practical we act as a defensive security operator: it is overly simplified as this is a beginner room.

1) We are brought to a panel called Security Analyst Dashboard
   
   ![](Attachments/Pasted%20image%2020260629204029.png)
2) We are instructed to click the unassigned event called Web Discovery attack
   
   ![](Attachments/Pasted%20image%2020260629204240.png)
3) We click copy the IP address and are brought to a panel to take actions
	1) Block the IP address
	   
	   ![](Attachments/Pasted%20image%2020260629204650.png)
	2) Implement Rate limiting
	   
	   ![](Attachments/Pasted%20image%2020260629204533.png)
	3) Update firewall rules
	   
	   ![](Attachments/Pasted%20image%2020260629204548.png)
4) Flag Secured
   
   ![](Attachments/Pasted%20image%2020260629204627.png)
   