### System Configuration
- Here we talk about System Configuration AKA `MSconfig` 
- We can run it by searching it in the start menu or in `win+R` start menu simply with `msconfig` 
- There are 5 sections here:
	- General: There are options here to select what devices and services windows loads on boot.
	  
	  ![](Attachments/Pasted%20image%2020260701173217.png)
	- **Boot**: Here we can define various boot options for the OS
	  
	  ![](Attachments/Pasted%20image%2020260701173259.png)
	- **Services**: Lists all services configured for the system regardless of if they are running or stopped. These run in the background
	  
	  ![](Attachments/Pasted%20image%2020260701173429.png)
	- **Startup**: Configure startup items, this is best to do in task manager and it even redirects us. In the TryHackMe VM there is no startup settings in task manager for this kind of system so we can run `shell:startup` to access these settings in the run menu. I'm not using the VM for my purposes so mine looks like a the second image.
	  
	  ![](Attachments/Pasted%20image%2020260701173554.png)
	  
	  ![](Attachments/Pasted%20image%2020260701173821.png)
	- **Tools**: In tools we can configure the system further using the many tools listed in this tab, there are also descriptions displayed for each.
	  
	  ![](Attachments/Pasted%20image%2020260701173944.png)

### Advanced System Settings
- There are also additional configuration settings such as looking at the system properties, accessed by typing "view advanced system settings" opening System Properties
  
  ![](Attachments/Pasted%20image%2020260701174453.png)
- Here we can change things like the virtual memory we have, which i am actually going to change as i have recently done a factory reset and want my virtual ram to reflect my physical by 1.5x so i have 32GB we will make it have 48GB as it has defaulted to around 8GB
	- Click settings
	  
	  ![](Attachments/Pasted%20image%2020260701174638.png)
	- Advanced
	  
	  ![](Attachments/Pasted%20image%2020260701174653.png)
	- Change `pagefile.sys`
	  
	  ![](Attachments/Pasted%20image%2020260701174727.png)
	- Now we can set our variables where we set the initial size 1.5x Ram and max size 3x Ram
	  
	  ![388](Attachments/Pasted%20image%2020260701174823.png)
- Another config we can look at is Startup and Recovery where windows creates crash dump files when it encounters errors such as the "blue screen of death". We can select what kind of dump file we want to configure for the system such as: Automatic memory dump, kernel memory dump, small memory dump (256kb) and Complete memory dump or just none.
  
  ![](Attachments/Pasted%20image%2020260701181402.png)
  
  ![](Attachments/Pasted%20image%2020260701181534.png)

---

### Change UAC Settings
- User account Control can be changed or turned off, you can move the slider to select a level of security notification
  
  ![](Attachments/Pasted%20image%2020260701183130.png)
  
  ![](Attachments/Pasted%20image%2020260701183135.png)

---

### Computer Management
- Computer management is a utility tool accessible via start menu or run `compmgmt.msc` It has 3 sections System tools, Storage, Services & applications
  
  ![](Attachments/Pasted%20image%2020260701190444.png)
- **System Tools**:
	-  Task Scheduler: Here we can create and manage tasks for our computer to automatically carry out at specific times
	- We can also make tasks run 1 time aswell like the entry below
	  
	  ![](Attachments/Pasted%20image%2020260701191432.png)
- **Event Viewer**:
	- Event viewer lets us see events and trails of events to understand activity on a system to diagnose and analyze problems.
	- There are 3 sections: list of event folders, overview of events, actions as seen below
	  
	  ![](Attachments/Pasted%20image%2020260701192037.png)
	- Here are the types of events that can be logged
	  
	  ![](Attachments/Pasted%20image%2020260701192151.png)
	- And in windows logs there are 4 sections for each kind of log
	  
	  ![](Attachments/Pasted%20image%2020260701192220.png)
- **Shared folders**
	- In shared folders you can see a list of shares and folders other can connect to. We have ones such as the default shares made by windows.
	  
	  ![](Attachments/Pasted%20image%2020260701202157.png)
	- You can manage permissions of who has access to the shared resource.
	- In sessions you can see a list of users who are currently connected to the share
	- All the folders that connected users access are listed under open files
- **Performance/performance manager**
	- We can see the performance manager listed also accessible by run with `perfmon` 
	- Allows us to see system performance and summary
	  
	  ![](Attachments/Pasted%20image%2020260701202750.png)
- **Device Manager**
	- Device manager allows us to view and configure the hardware such as disabling hardware and viewing the properties
- **Storage**
	- Here we can look at disk management which allows us to do a few things such as setting up a drive, partitioning, changing drive values.
- **Services and Applications**
	- Here you can right click a service and click properties to see additional details and other relevant information
	- We can also see startup type to see when the service is setup to start like manual, boot, automatic, disabled etc.
	- There is WMI which is short for Windows Management Instrumentation service which is used to manage computers and servers locally and remotely

---

### System Information
- System information also `msinfo32` in run displays information about our system.
	- Hardware resources
	- Components where you can see information on components on the system
	- Software environment shows information such as environment variable and network connections that and information baked into the system. There is also a search function
	  
	  ![](Attachments/Pasted%20image%2020260701204754.png)

---

### Resource Monitor 
- Resource monitor aka `resmon` accessible via run
- Overview in the overview we can see information on what processes are using what resources exactly such as:
	- CPU
	- Memory
	- Disk
	- Network
- They also have their own tabs to view them better. It also has a graphical view to get a more visual view of the resource

---

### Command Prompt
- Command Prompt aka `cmd` accessible via run or search is a cli interface to communicate with the operating system rather than using the GUI
- A few basic commands
	- `hostname`: displays current computer name
	- `whoami`: displays the currently logged user
	- `ipconfig`: shows network address settings for the computer
	- `netstat`: display protocol statistics and current TCP/IP network connections
- Getting help with commands requires the command followed with the word `help` or `/?` so `netstat help` or `netstat /?` 

---

### Registry Editor
- Registry Editor aka `regedit` in run or search
- Requires advanced knowledge as making some changes can brick a computer in the worst case
- its where we can configure things for one or more user, application, or hardware devices:
	- profiles for each user
	- Applications installed on the computer and the types of documents that each can create
	- Property sheet settings for folders and application icons
	- Hardware existing on the system
	- Ports being used