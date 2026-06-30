### Terminal Text Editors
- So far we used `echo` and the pipe operators to write and handle data
- There are multiple text editors to use in Linux however we go over `VIM` and `nano` in this room

### nano
- `nano` is really simple to use, doing `nano "filename"` or `nano "path/to/file"` will launch nano's text editor, if a file does not exist it will create it.
- It has a few useful features such as:
	- Searching for text
	- Copy Paste
	- Jumping to line
	- Displaying line number
- Here is a view of the options and how the text editor looks

  ![](Attachments/Pasted%20image%2020260630180159.png)

### VIM
- `VIM` only gets mentioned here
- It has many advances features, its highly customizable and much more
- I haven't used it much as well i don't even know how to properly exit out of it i just put it in the background via T^z I'm sure ill learn it when it is relevant to me

### Task
- simple
  
  ![](Attachments/Pasted%20image%2020260630194424.png)

---

### General/Useful Utilities

### Downloading Files (Wget)
- `wget` allows us to download files from the web via HTTP simply by providing the web address of the file.
- `wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt` 

### Transferring Files from Your Host - SCP (SSH)
- `scp` aka Secure copy, allows us to securely copy files using the SSH protocol to provide authentication and encryption
- `scp` uses the model Source and Destination so for example
	- `scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt` This will copy the file `important.txt` from our machine to the target machine and name it `transferred.txt`
	- We can use it the other way around as well `scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt` in this example we copy `documents.txt` to our machine via ssh and call it `notes`

### Serving Files from Your Host - (HTTP Server)
- We can create our own server to allow access to a folder or file
- People can access the file simply by using curl or wget
- We cab use a feature in python3 to start an HTTP server using `python3 -m  http.server` which will start an HTTP server in our current directory if one isn't provided.
- However, if your machine does not have a public ip address only localhosts will be able to access it
- They would access it like this: `wget http://10.80.148.3:8000/myfile` where `10.80.143.3` is our ip and `/myfile` is the file in the directory in the HTTP server
  
  ![](Attachments/Pasted%20image%2020260630194316.png)

### Task
- Simple
  
  ![](Attachments/Pasted%20image%2020260630194500.png)

--- 

### Processes 101
- Processes are programmes running on the machine
- They are managed by the kernel where each process has its own ID associated with it known as `PID`
- The `PID` increases for the order in which the process starts so the 60yh machines will have the `PID 60` 

### Viewing Processes
- To view processes running we can use `ps`
- `ps` shows us running processes in our users current session, furthermore we can use the prefix `aux` so `ps aux`
	- `a` (all) all users on the system
	- `u` provides a human readable format showing specific users, cpu, and memory
	- `x` hidden processes such as background services daemons and tasks
	  
	  ![](Attachments/Pasted%20image%2020260630202506.png)
- We can also use the command `top` which provides real time statistics on running processes.
  
  ![](Attachments/Pasted%20image%2020260630202514.png)

### Managing Processes
- We can send signals to terminate processes which correlate to how cleanly it is dealt with by the kernel
- We can use `kill` to kill a process using its `PID` so `kill` 1337 will kill that correlating process
- We can also use other commands to determine how cleanly we kill a process
	- `SIGTERM` : kill the process but allow it to cleanup its tasks beforehand
	- `SIGKILL`: kill the process without any cleanup
	- `SIGSTOP`: stop/suspend the process

### How Do Processes Start?
- `namespaces` are used by the OS to split up the system resources spliting up the resources into many little chunks. Processes within those chunks have a certain amount of computing power.
- `namespaces` also act to separate processes from one another for security
- `systemd` is one of the first processes to start and sits between the OS and the user.
- Example: if a programme or a piece of software starts as a child process of systemd, this means it will run as its own process but share the resources of systemd as it easier to identify.
  
  ![](Attachments/Pasted%20image%2020260630210723.png)

### Getting Processes/Services to Start on Boot
- Some applications can be started on boot. e.g. web servers, database servers or file transfer servers setup by system admins.
- `systemctl`: allows us to interact with `systemd` processes/daemons. It uses the structure `systemctl [option] [service]` e.g. `systemctl start apache2` which will start apache. other options include: 
	- `Start`, `Stop`, `Enable`, `Disable`, `Status`

### Background and Foreground in Linux
- Programmes run in 2 states the `background` and the `foreground`
- For example, commands that run in your terminal will run in the `foreground` such as `echo` or `cp` unless told otherwise using something like the `&` pipe
- We can also use the command `T^Z` AKA `Ctrl+Z` which will background/pause a process until we bring it back to the foreground
- We can use the command `fg` to bring a process back to the foreground

### Task
- Simple follow along of the task
  
  ![](Attachments/Pasted%20image%2020260630212128.png)

---

#### Maintaining Your System: Automation (cron)
- If we want to schedule actions or tasks to take place at certain system evens such as boot or a specific time we can use cron along with other processes but for this room we use cron/crontab
  
  ![](Attachments/Pasted%20image%2020260630212416.png)
- The image above is a crontop file recognised by the cron process
- Its quite simple where we can list the time or event we want a process to do something and we put our command at the end.
  
  ![](Attachments/Pasted%20image%2020260630212538.png)
- The formatting for this is quite simple, say we wanted to backup files every 12 hours we would use `0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/` 
	- First we have minutes which is not a wildcard because if it were it would run every minute during that 12th hour
	- We then have a wildcard with /12 representing "every 12 hours" we then have wildcards for the day month and day of week as we want it to run every 12 hours on every day.
	- Finally the command which is copying recursively every file in /Documents to /Var/Backups
- We can run crontab -e to edit the file in our default editor at any time.

### Task
- Simple follow along
  
  ![](Attachments/Pasted%20image%2020260630213033.png)

---

### Maintaining Your System: Package Management (apt)
- When developers want to release software to the community they submit it to an apt repository where if approved their programs and tools will be released for everyone to use.
- This speaks to the merit of Linux where accessibility and open source tools really shine.
- OS's will maintain their own repositories however you can add community repositories to your list using `add-apt-repository`
- For example: My personal VM needs to use a different Kali repository that is closer to my geographical location otherwise i get 300kb/s

### Managing Your Repositories (Adding & Removing)
- We normally use `apt` to install software, `apt` is part of a management software also known as apt. It contains a suite of tools that let us manage packages ans sources of software along with removal and install.
- While we can use package installers such as dpkg, the benefit of apt means when we update our system our apt package also get updated alongside.
- There is also a guaranteed integrity provided by GPG (Gnu Privacy Guard) keys, the keys are safety checks where if we try to install something and the keys don't match up with what the developer used and our system trusts, the install will be aborted.
- Adding a repo is as simple as downloading the GPG key and apt-key to trust like this `wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -` which will add the keys
	- Then we can go ahead and update `sudo apt update`
	- Then install `apt install sublime-text`
- Removal is as easy as `add-apt-repository --remove "location"` to remove the keys and then `apt remove "software name"`

---

### Maintaining Your System: Logs
- Mentioned earlier log files are stored in `/var/log` containing logging information for applications and services on our OS. The process used to automatically manage these logs is known as "rotating"
- In the image below we see a list of logs and highlighted important areas such as: 
	- An `apache2` web server running on the machine
	- Logs for the `fail2ban` service logging attempted brute force for example
	- `UFW` service which is used as a firewall
	  
	  ![](Attachments/Pasted%20image%2020260630220103.png)
- These contain all information about every request allowing teams to analyze performance or log find suspicious activity

### Task
- This goes over what can be found in the logs
  
  ![](Attachments/Pasted%20image%2020260630220215.png)