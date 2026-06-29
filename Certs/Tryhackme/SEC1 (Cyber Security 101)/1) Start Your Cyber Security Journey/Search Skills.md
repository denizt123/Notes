### Intro
- This room goes over popular websites  to gather information for various purposes
- Knowing where to search is just as important as knowing what to search for.

---

### Shodan
- Shodan is basically a search engine for all public network connections, searching for networking equipment, industrial control systems, traffic cameras - basically anything with a public network connection what it is running and where
- For example we can search for `apache 2.4.1` and it will show us a list of every single public server it has in its database with information from their HTTP headers such as `Country`, `Port`, `Org`, `Hostname`
- This information is extremely useful for pentesting as sometimes there are known CVE affecting that version

### Practical
- We are taken to a mock website of Shodan for the purpose of demonstration where we are to search the term **apache**, review the first entry and find the domain associated with the IP `185.243.115.47` 
  ![](Attachments/Pasted%20image%2020260629220138.png)
  
- We can clearly see the domain as `tryhackme.thm` which is our flag for this task

---

### VirusTotal
- VirusTotal puts together results from over 70 antivirus engines and website scanners.
- You can submit a file, URL, domain or a file hash and VirusTotal will flag the input if the engines flag it as malicious
- It is not foolproof, even for the URL https://tryhackme.com/paths it was flagged by at least 1 engine.

### Practical
- Once again we use a mock website called TryDetectMe, our task is to review information on a file called invoice_payment.exe
- We are asked the question of how many vendors identified the files as dangerous. In this case 52 did.
  
  ![](Attachments/Pasted%20image%2020260629221112.png)

---

### Vulnerability Databases (CVE)
- CVE aka Common Vulnerabilities and Exposures
- The closest thing to a universal dictionary of Known Vulnerabilities
- Each vuln is assigned a unique identifier `CVE-YEAR-NUMBER`
- Sometimes they can receive monikers if they are impactful such as Heartbleed, React2Shell and Log4Shell
- These vulns have a CVSS score based on Impact, Complexity and Availability. This is done to prioritise risk
- [ExploitDB](https://www.exploit-db.com/) is a Database of known and developed exploits along with Proof of concepts - [CVE](https://www.cve.org/) Lists all known vulns even if they are patched and no exploits exist

### Practical
- Once again we are in a mock vuln database where we must search the vuln `CVE-2026-1337` and retrieve the CVSS score.
  
  ![](Attachments/Pasted%20image%2020260629232135.png)
- The Score is 10 meaning this is a high risk vuln

---

### Technical Documentation (MAN)
- This part of the room is quite simple, it teaches us how to use the man command in Linux CLI - short for manual

### Practical
- It asks us to open a link to see their example page however, this can be done in Linux quiet easily
- It asks us how we could use netcat (nc) to open a connection for host.example.com on port 42
- fairly simple the answer is nc host.example.com 42
  
  ![](Attachments/Pasted%20image%2020260629232828.png)

---

### GitHub
- Fairly simple here as well just a overview of what GitHub is
- GitHub is used by devs, coders, researches pretty much anyone who works on the technical side of computers is familiar with GitHub.
- People can upload files on pretty much anything, exploits and poof of concept, code, applications
- For example if we wanted a proof of concept on a vuln or a scanner script or analysis of a vuln we can find it by searching GitHub in most cases.

### Practical
- Same thing again - mock website - search for `CVE-2026-1337` - read the README - answer the question - What is the name of the script in the repository that will demonstrate the vulnerability?
  
  ![](Attachments/Pasted%20image%2020260629233411.png)