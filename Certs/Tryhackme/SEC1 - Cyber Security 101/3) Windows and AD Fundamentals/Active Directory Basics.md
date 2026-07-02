
### Windows Domains
- In small companies it is really easy to manage maybe 5-10 computers manually logging into each machine and configuring it however when you are in a big company with say 150 computers 350 users and 4 offices this would not be feasible
- To overcome this we use a windows domain
- A windows domain. The main idea is to manage groups of users and computers to centralise administration in a single repository called **Active Directory** (AD)
- The server that runs the AD is known as the Domain Controller (DC)
- All users can be configured from the AD with minimal effort
- Managing the policies can be done on the AD and applied to the corresponding elements across a network

---

### Active Directory
- The core of a windows domain is the **Active Directory Domain Service** (AD DS) which catalogs all "objects" that exists on a network
- On AD DS we have users, groups, machines, printers, shares, and many others

### Users
- Users are object types in AD known as security principals, meaning they can be authenticated by the domain and can be assigned resources like files printers and other resources on the network
- Users represent 2 entities on a network
	- **People**: represent employees or people that need access to the networks resources such ad printers or computers or shares
	- **Services**: Users are used by services to run and will need their assigned specific privileges to run

### Machines
- Machines are another type of object in AD for every new computer or machine added to the network an object is created
- They are considered security principals and are assigned an account with limited rights
- They still retain their local admin privileges but still requires a password to work.
- They are usually automatically rotated out and comprised of 120 random characters
- They are assigned names in a specific scheme, a device named DC01 will be called `$DC01`

### Security Groups
- We can create groups where we can put users and they will automatically inherit the variable and policies of that group saving time of setting up each object
- Here are examples of Groups made automatically by default
  
  ![](Attachments/Pasted%20image%2020260701230329.png)

### Active Directory Users and Computers
- We can open Active Directory by just locating the app in search
- This opens the Organizational menu of the AD where it shows each of the users, groups, and networks
- They are sorted into Organizational Units (OUs) which are the containers that allow us to separate and define groups of users and machines and their policing requirements. So different offices or different departments in an office have their own OUs
- In the example you can see the OUs on the left and the example OU for THM open with 5 sub/child OUs
  
  ![](Attachments/Pasted%20image%2020260701233807.png)
  
  ![](Attachments/Pasted%20image%2020260701233811.png)
- Some OUs are created automatically such as:
	- **Builtin**: Contains default groups available to any windows host
	- **Computers**: Any machine joining the network gets put here by default
	- **Domain Controllers**: Default OU that contains DCs in the network
	- **Users** Default location for groups and users
	- **Managed Service Accounts**: Accounts used by services in the windows domain

### Security Groups vs OUs
- **OU**: for applying policies to groups of computers and users, a user can only be a member of 1 single OU
- **Security Groups**: These are used to grant permissions over resources such as shared folders or devices on network such as printers.

---

### Managing Users in AD

### Deleting OUs and Users
- To delete an OU or User we need to enable it as by default deleting is disabled for cases such as accidents
- To do this we right click a OU/User and select advanced features
  
  ![](Attachments/Pasted%20image%2020260701234523.png)
- Then in the Advanced features we go to Objects and disable the feature
  
  ![](Attachments/Pasted%20image%2020260701234605.png)

### Delegation
- A feature of AD is that we can delegate control of specific OUs to people like IT support to allow them yo manage passwords or other things on low privilege users and machines.
  
  ![](Attachments/Pasted%20image%2020260701234910.png)
  
  ![](Attachments/Pasted%20image%2020260701234917.png)
- We then use commands to reset or manage passwords from the PowerShell of the person it was delegated too like:
	- `Set-ADAccountPassword sophie -Reset -NewPassword` which will prompt us to enter a new password for Sophie
	- We normally do this first so that if the password is compromised or something like that it is changed for safety, however that means we now know Sophie's password so we need to prompt a new password on login
	- `Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose` She will now be able to enter her new password after using our password we gave to login.

---

### Managing Users in AD
- If we look at the Computers folder in our example it looks like this:
  
  ![](Attachments/Pasted%20image%2020260701235409.png)
- This is where all devices default to, normally this isn't good practice and are divided how the company wants. However, we will go over a example of how they should be setup in 3 sections.
	- **Workstations**: Things like work computers and computers for general use are put we can also set is a default for new devices
	- **Servers**: Devices that provide service to users or other servers
	- **Domain Controllers**: Devices that manage the active directory, these are the most sensitive in a network and are usually only accessible to the higher up staff.

---

### Group Policies (GPO)
- GPO aka Group Policy Objects
- Using Group Policies we can put different configurations and security setting for different OUs
- GPO's are collections of settings that can be applied to OUs
- To configure them we go to Group Policy Management accessible via the start menu
- It shows our complete OU hierarchy where we can create a GPO and drop it into the OU's
  
  ![](Attachments/Pasted%20image%2020260702001739.png)
- GPO's will apply to the OU and their sub OU's. Clicking a GPO in our GPO folder shows its scope and where it is applied
- We can apply Security filtering as well so that specific settings are only applied to specific users/PCs
- We can go to the settings tab to view the contents of the GPO's settings and how they are configured
  
  ![](Attachments/Pasted%20image%2020260702002129.png)
- When we click show we can see the settings
  
  ![](Attachments/Pasted%20image%2020260702002154.png)
- Any change to the GPO would apply to all objects it is linked to
- To change a GPO we right click and edit
  
  ![](Attachments/Pasted%20image%2020260702002256.png)
- In this example we have 10 as our minimum length for passwords
  
  ![](Attachments/Pasted%20image%2020260702002331.png)

### GPO distribution
- GPO's are distributed to the network via a network share stored on the DC called `SYSVOL`
- All users normally have access to this so that they sync their policies
- It can take 2 hours for a GPO to update to a machine after a change
- We can run the command `gpupdate /force` on the desired machine to manually update

### Creating a GPO
- In this example we create a GPO to prohibit access to control panel
- We create a new GPO and edit it. We find under user configurations options for control panel where we toggle the option to enabled:
  
  ![](Attachments/Pasted%20image%2020260702002947.png)
- Then we can simply drag and drop our new GPO into where we want it to apply:
  
  ![](Attachments/Pasted%20image%2020260702003025.png)

---

### Authentication Methods
- All Credentials are stored in the DC
- When a user tries to authenticate to a service using domain credentials, the service will ask DC to verify authenticity. Two protocols can be used:
	- **Kerberos**: Used by recent versions of windows and is the default in any recent domain
	- **NetNTLM**: Legacy auth, it's kept for compatibility and is considered obsolete
	- most networks have both enabled

### Kerberos Authentication
- **Variables**:
	- **KDC**: key distribution centre installed on the **DC** 
	- **User Hash**: an encrypted key derived from the users password
	- **Request TGT**: Sending their username and a timestamp encrypted with the **User Hash**
	- **TGT**: aka Ticket Granting Ticket or krbtgt hash (the hash of the DC's account) which allows the user to request additional tickets to access specific services, which means we no longer have to send the **User Hash**, the **TGT** also has a copy of the **Session Key** so that the **KDC** can just decrypt the **TGT** if it needs it
	- **Session Key**: Given to the user device along with the TGT to authenticate the session for further requests
	- **Request TGS**: Sends username and timestamp wrapped with the **Session Key** and the **TGT** and an **SPN**
	- **SPN**: Service principal name, indicating service and the server name we want to access
	- **TGS**: Encrypted with the Service owners hash which allows us to send requests for services, the **TGS** contains the **Service Session Key** as well as a copy if needed
	- **Service Session Key**: A key to authenticate future requests for the service in that session and is wrapped with the **Session Key**
1) The user sends a **Request TGT** to the **KDC** 
2) The **KDC** sends back a **TGT** and **Session Key**
3) If the user wants to access a service from this point they send a **Request TGS** to receive the **TGS** and **Service Session Key**
4) The user can now send the **TGS** and **Service Session Key** wrapped onto the users Username and Timestamp to validate its connection to the service
   
   ![](Attachments/Pasted%20image%2020260702013027.png)
   
   ![](Attachments/Pasted%20image%2020260702013035.png)
   
   ![](Attachments/Pasted%20image%2020260702013041.png)

### NetNTLM Authentication
- NetNTLM works by using a challenge Response mechanism
  
  ![](Attachments/Pasted%20image%2020260702013115.png)

1) Client sends auth request to the server they want to access
2) The server generates a random number as a challenge and sends it back to the client
3) Client combines their NTLM password hash with the challenge to generate a response and sends it back to verify
4) The response gets forwarded to the DC
5) The DC uses the challenge to recalculate the response and compare it to the original response by the client, the result is send back to the server
6) This gets forwarded to the client and access is granted if conditions are met

---

### Trees, Forests and Trusts
- Sometimes having a single domain is not enough
- In some cases we need to have more than 1 domain
- These are known as Trees, Forests, and trusts

### Trees
- AD has a feature for integrating multiple domains under one namespace to better organize the AD essentially a partition say our domain is thm.local and we want to separate a UK branch and US branch we can divide the domain into subdomains so we can have uk.thm.local and us.thm.local each with its own OU's, users and devices.
- The UK branch will have its own DC and so will the US to configure for themselves
- Each subdomain will not be able to access a DC in another
- A new security group is introduced as the Enterprise Admins which grants access to all subdomains
  
  ![](Attachments/Pasted%20image%2020260702014841.png)

### Forests
- Sometimes we need to combine multiple domains with different namespaces for example THM merged with a company called MHT
- We can connect these 2 together under the same network calling it a Forest
  
  ![](Attachments/Pasted%20image%2020260702014916.png)

### Trust Relationships
- Say for example a user in THM UK needs to access shared files from MHT ASIA servers, for this we need to join together domains in trees and forests by a trust relationship
- Simply it allows different domains to access resources from another
- There are 2 types
	- **One way trust**: If domain A trusts domain B, domain B can be authorised to access resources in domain A. It operates contrary to the access direction
	- **Two way trust**: By default this is how the trust operates where both domains have access to each other when they are under the same tree or forest.