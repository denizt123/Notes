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
- I haven't used it much as well i don't even know how to properly exit out of it i just put it in the background via ^z I'm sure ill learn it when it is relevant to me

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

