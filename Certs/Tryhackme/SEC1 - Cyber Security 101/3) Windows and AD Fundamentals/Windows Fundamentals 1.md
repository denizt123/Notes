### Windows Editions
- Windows history goes back to 1985 and it has been the most dominant OS for home and corporate use.
- Windows XP was a popular version of windows for a long time until Windows Vista was announced, it wasn't received well by windows users and was phased out quickly
- When Windows XP reached its end of life and Windows 7 was released there was panic and a scramble for vendors/hospitals/corporations to get compatible hardware and devices. It wasn't received well.
- Short lived like Vista, Windows 8 came to the market and windows 7 was phased out. Then windows 10 and 11 thereafter.
- Windows 11 comes in 2 flavours, Pro and Home
- Win 10 has also reached its end of support date as of 14/10/25
- Win 11 Pro has an encryption feature called Bitlocker, Windows's own encryption feature.

---

### The Desktop (GUI) - Win 10
- We are going to use the Win 10 desktop for our task for this module
- The desktop has 7 key components:
	- The Desktop
	- Start Menu
	- Search Box (Cortana)
	- Task View
	- Taskbar
	- Toolbars
	- Notification Area
	  
	  ![](Attachments/Pasted%20image%2020260701000849.png)

### The Desktop
- This is where we will have shortcuts to programs, folders, files, etc. 
- The icons can be well organized sorted by date, size, alphabetical or can be scattered to the users liking.
- Right clicking anywhere on the Desktop will give access to a context menu where you can choose options to best suit your organization need or creating new files.
	- There is also an option called Display settings used for making changes to the resolution, orientation and multi screen setup settings.
	  
	  ![](Attachments/Pasted%20image%2020260701001705.png)
	- And we also have the personalisation settings which allows us to change the background of the desktop, fonts, themes, colours etc.
	  
	  ![](Attachments/Pasted%20image%2020260701001841.png)

### Start Menu
- The start menu provides access to all apps/programs/files/utilities etc.
- Clicking on the windows logo will open the start menu.
- It is comprised of 3 sections
	- 1) This section provides shortcuts to actions on your account or login session, lock your screen, signing out, folders belonging to your current user such docs and pictures, and the gear icon which opens settings. And the power icon for shutdown, restart, and disconnect from remote session
	- 2) This shows recently added apps/programs and files. Each letter has its own section. Clicking on the letting header will bring up a letter pad to filter the sections
	- The right side of the start menu has icons known as tiles where you can add applications for quick access, right clicking them will give further options
  
  ![](Attachments/Pasted%20image%2020260701002648.png)

### The Taskbar
- The Taskbar provides quick access to programs, apps, folders, and files you have pinned and displays currently open apps of folders
- Right clicking will open a context menu for taskbar options and other related options
- Hovering open an open app will show a preview of the app

### Notification Area
- Typically at the bottom right of the screen is where the date and time is displayed along with other icons like volume, network, and battery

---

### Remote Desktop (RPD)
- RPD provides a means to connect the GUI of another machines
	- Windows
	  
	  ![](Attachments/Pasted%20image%2020260701011456.png)
	- ![](Attachments/Pasted%20image%2020260701011505.png)

---

### The File System
- The modern file system used on Windows is NTFS (New Technology File System)
- Before that we had FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System) 

### NTFS
- NTFS is known as a journaling file system. In case of failure the file system can repair the files on a disk using info in logfiles automatically
- NTFS fixes limitations of the previous file systems such as
	- Storage of files larger than 4 GB
	- Setting permissions for folders and files
	- File compression
	- Encryption (Encryption File System AKA EFS)
- Right clicking a drive or folder or file allows you to see the properties of the item such as location, permissions etc.
- We can set different permission shown in the graph below
  
  ![](Attachments/Pasted%20image%2020260701012921.png)
- We can select properties and then go onto the security tab to see which users and groups have what permissions
  
  ![](Attachments/Pasted%20image%2020260701013108.png)

### Alternate Data Streams (ADS)
- ADS aka Alternate Data Streams is a attribute specific to NTFS
- Every file has at least one data stream `$DATA`, ADS allows files to contain more than 1 stream of data. Normally windows explorer does not display ADS to the user.
- ADS can be viewed with PowerShell or third party software
- In security malware writers have used ADS to hide data
- It also identifies things like when you download something from the internet it will have that identified
- It contains things like Metadata, Thumbnail icon cache etc.

---

### The Windows\System32 Folders
- The windows folder C:\Windows traditionally contains the windows OS. Normally it resides in C:\ however it doesn't have to
- Environment Variables are stored in `%windir%` containing information on OS system path, number of processors used by the OS and location of temp folders
- Within the windows folder we also have \system32 which contains important files critical to the OS, interacting with this folder should be done with caution as 1 tiny small change could brick the your machine in the worst case.

---

### User Accounts, Profiles, and Permissions
- User accounts are usually either Administrator or Standard User on a normal local system
	- Administrator can make changes to the system like add/remove users, modify groups or other settings on the system kind of like being the root user on Linux
	- Standard Users can only make changes to folders/files belonging to the user and can't do system level changes such as installing new programs. 
- There's a few ways to see what you are currently logged in as
	- Going into system settings and then clicking other users will if you are the admin you can see an option to 'add someone else to this pc'. Clicking on a local user gives the option to change account type or remove the account
- When an Account is made a user profile will be added to c:\Users\"name"
- Each User will have the same folders, however they are unique to the user such as:
	- Desktop
	- Documents
	- Download
	- Music
	- Pictures

### lusrmgr.msc
- In the run menu `Win+R` we can type usrmgr.msc which opens the interface to see assigned permissions to which users and groups are assigned what permissions, if a user is assigned to a group they will inherit the permissions of that group
- A user can be assigned to multiple groups.

---

### User Account Control (UAC)
- A majority of home users are logged in as local admin.
- You don't need elevated privileges to run tasks, surf the internet and using applications as it would make it easier for malware to affect our system
- First introduce with Windows Vista, UAC protects users with privileges
- UAC does not apply to the local Admin account
- When an admin logs in their session does not run with escalated privileges, when an operation which requires higher level privileges the user will be prompted if they permit the operation to run.
- If we right click an application we can see in properties > security which users and groups have what permissions to the file.
  
  ![](Attachments/Pasted%20image%2020260701032417.png)
- A shield icon is marked on applications requiring higher privileges
  
  ![](Attachments/Pasted%20image%2020260701032458.png)
- The admin login prompt
  
  ![](Attachments/Pasted%20image%2020260701032532.png)

---

### Settings and the Control Panel
- Control panel and settings are a central hub for system control, things like network settings, adding devices, managing programs, updates etc.

### Control Panel
- It can be accessed by searching in the start menu or is usually a shortcut in the start menu.
- You can see things like the below options: 
  
  ![](Attachments/Pasted%20image%2020260701162946.png)
- Personally i use network adapter options the most as it allows me to change network settings like dns and the settings presets for my Ethernet connection.

---

### Task Manager
- Task manager allows us to view what applications or services are using what resources such as: RAM, CPU, Disk, and network
  
  ![](Attachments/Pasted%20image%2020260701163333.png)
- We can see things like how hardware is performing or Details on services and apps similarly to Linux with the PID, Description, Which user launched the service etc.
  
  ![](Attachments/Pasted%20image%2020260701163425.png)