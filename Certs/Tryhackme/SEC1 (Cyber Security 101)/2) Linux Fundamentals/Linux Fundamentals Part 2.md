### Accessing Our Linux Machine Using SSH
- SSH or Secure Shell is a protocol to connect devices in an encrypted form using cryptography
- Any input we send is sent in a human-readable format and is encrypted for travelling over a network where it is unencrypted once it reaches the remote machine.
  
  ![](Attachments/Pasted%20image%2020260630014920.png)
- We use it to communicate with the command line of a remote machines.
- To login we need to provide 2 things: The IP and the correct credentials to a valid account on the remote machine.
- in this case we use `ssh tryhackme@10.80.162.22`, this is the machine we want to get into in the format `ssh username@IP`, the password we need to provide in this case is `"tryhackme"`
  
  ![](Attachments/Pasted%20image%2020260630015548.png)

---

### Introduction to Flags and Switches (Prefixes)
- A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.
- This room teaches us 1 prefixes for ls:
	- `ls -a` short for `ls --all`
- This room also teaches us how to properly use the man command (manual) for example `man ls`, this will list all info related to `ls`, we can navigate it using the arrow keys

---

### Filesystem Interaction Continued
- In this section we go over further commands to interact with our filesystem
- With all of these we can provide locations to output etc.

### touch & mkdir
- `touch`: used to create files `touch coolfilename`, this will create a file called "coolfilename"
- `mkdir`: used to create a directory `mkdir cooldirectoryname`, this creates a directory called "cooldirectoryname"

### rm (Remove)
- `rm`: deletes files, if we want to delete a directory we use the prefix `-R`, running `rm coolfilename` deletes a the file with that name, `rm -R cooldirectoryname` will delete the directory with that name and its subfolders and files.

### cp & mv (Copy & Move)
- `cp`: copies the entirety of a files contents or a directory output can be selected if not it will make the copy in the current directory `cp coolfilename ~/home` this will create a copy of "coolfilename" in `~/home` if we want to change the name we simply add that to the location as what we want so `cp coolfilename ~/home/boringfile`
- `mv`: operates exactly the same as `cp` however it moves files

### file
- `file`: determines file type so if "coolfilename" was a .txt file `file coolfilename` would return ASCII text or a variation of that based on the contents.

### Task
- Very simple
  
  ![](Attachments/Pasted%20image%2020260630032324.png)

---

### Permissions 101
- We can use `ls -l` to view further information on text files in a directory `ls -lh` outputs information in human readable format.
- The first 3 columns are the most important to us
	- 
	  ![](Attachments/Pasted%20image%2020260630030925.png)
	- Column 1 - displays `drwxrwxrwx` this can be simplified to `d,rwx,rwx,rwx` displaying the permission of who can do what to the file, `d`: States weather it is a directory `r`: read, `w`: write, `x`: execute. The first 3 correlate to the owner, the second for the group and the last for others. Simply showing who can do what to the file
	- Column 2 - displays who owns the file
	- Column 3 - displays which group the file belongs to

### su (Switch User)
- `su`: is used to switch users, quite simply if we want to login to user2's account we do `su user2`
- If you want to inherit the environment variables and properties of the user you use the flag `-l` so `su -l user2`
  
  ![](Attachments/Pasted%20image%2020260630031828.png)

### File Permissions as Numbers
- Each combination of `rwxrwxrwx` returns a different value
  
  ![](Attachments/Pasted%20image%2020260630031957.png)
- This way it is easy to change file permissions, so we can do something like `chmod 777 file` and that will give full permissions to absolutely anyone.

### Task
- Very simple
  
  ![](Attachments/Pasted%20image%2020260630032403.png)

---

### Common Directories
- Here we will go over various common directories and their use and purpose.

### /etc
- `/etc` short for etcetera, is a common location to store system files such as:
	- `sudoers`: which contains a list of the users & groups that have permission to run sudo or commands as the root user
	- `passwd` and `shadow`: which contain the passwords for each user encrypted in SHA-512 format

### /var
- `/var` short for variable data, stores data frequently accessed by services or applications running on the system such as log files which are written in `/var/log` 

### /root
- There is nothing special to `/root` it is simply a home folder for root and its subsequent files.

### /tmp
- `/tmp`: short for temporary, is for data that is volatile and or only needs to be accessed once or twice.
- Once the computer is restarted the contents are deleted.