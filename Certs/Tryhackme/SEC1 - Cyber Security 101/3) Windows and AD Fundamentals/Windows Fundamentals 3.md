### Windows Updates
- Accessed via the update & security section in settings
- Windows updates can be put off to a later date or not installed at all however you will eventually have to install them for security reasons
  
  ![](Attachments/Pasted%20image%2020260701210954.png)

---

### Windows Security
- Also available from the settings menu "Update and Security"
- There are 4 sections seen here
  
  ![](Attachments/Pasted%20image%2020260701211120.png)
- Warnings are colour coded each meaning a different thing
	- Green: Sufficient protection
	- Yellow: action recommended for review
	- Red: immediate attention required

---

### Virus and Threat Protection
- In virus and threat protection we have scan options and threat history
	- ##### **Scan options**:
	- **Quick scan**: check folders where threats are usually found
	- **Full scan**: check all files and running programs
	- **Custom scan**: choose where and what to check
	- ##### **Threat history**:
	- **Last scan**: shows last scan output
	- **Quarantined threats**: threats isolated until you or the system takes action
	- **Allowed threats**: threats that we have allowed to run.
	  
	  ![](Attachments/Pasted%20image%2020260701211749.png)

### Virus & Threat Protection Settings
- There are a few more settings such as 
	- **Real time protection**: locates and stops malware running or installing on the device
	- **Cloud delivered protection**: options such as one drive to have safer file storage
	- **Automatic sample submission**: send samples of your files so Microsoft can help protect you and others from potential threats. (personally i never enable things like this for privacy and anyone reading this should too)
	- **Controlled folder access**: protect folders files and memory areas from unauthorized changes by unknown applications allowing only approved apps
	- **Exclusions**: Allows you to exclude folders from scans to reduce false positives when you know a folder will flag as a threat
	- **Notifications**: what alerts come up for the user

---

### Firewall & Network Protection
- Traffic coming into our computer is essentialy managed by the firewalls, it controls what traffic is allowed in and out of a computer like a security guard.
  
  ![](Attachments/Pasted%20image%2020260701220213.png)
- There are 3 types in our settings
	- **Domain**: applies to networks where the host can auth as a domain controller
	- **Private**: applies to the user assigned profile used for private and home networks
	- **Public**: applies to public networks such as coffee shops, hotspots, and other locations
- To manage the firewalls we use Windows firewall defender and advanced security accessible via the settings on advanced settings or by search also by run `WF.msc`
  
  ![](Attachments/Pasted%20image%2020260701220554.png)

---

### App and Browser Control
- App and browser control contains settings for:
	- windows defender smartscreen used which scans activity on the web etc to protect against fishing and screens files. We can toggle it to block, warn and off for when it finds something
	  
	  ![](Attachments/Pasted%20image%2020260701220933.png)
	- We also have exploit protection which we don't go too far into
	  
	  ![](Attachments/Pasted%20image%2020260701221008.png)

---

### Device Security
- In device security we have options for hardware related security such as:
	- **Core isolation**: we can toggle memory integrity here which prevents attacks from being inserted into high security processes such as RAM
	- **Security processor (TPM)** : designed to provide hardware based security and security related functions at a hardware level and handles cryptographic operations such as encryption.

---

### BitLocker
- BitLocker is used to encrypt data or drives on the computer when TPM is enabled

---

### Volume Shadow Copy Service
- VSS or Volume Shadow Copy Service
- VSS is used for creating consistent shadow copies aka snapshots of data to be backed up such as:
	- Creating restore points
	- Performing system restore
	- Configure restore settings
	- Delete restore points
- Right clicking our drive in file explorer shows the option for shadow copies
  
  ![](Attachments/Pasted%20image%2020260701222225.png)