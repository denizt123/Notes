### Intro
- This room covers the basics of Linux and essential commands to operate the filesystem 

---

### Linux Background
- Linux seems more intimidating than other OS's such as windows
- They both have pros and cons
- Linux is lightweight and is used on many devices and systems such as Websites, Control panels, Tills, and point of sales machines and critical infrastructure's
- It is also open-source meaning that all its code is publicly accessible
 
### Flavours of Linux
- Linux is an umbrella term for multiple OS's that are based on UNIX
- Since Linux is open-source variants come in all shapes and sizes so you can choose which flavour suits your purposes best
- Ubuntu & Debian are the most common distributions of Linux 

### Task
- Q: What year was the first release of a Linux operating system
- A: 1991

---

### Running Your First Few Commands
- A large selling point of Linux is how lightweight it can be, of course the disadvantage for that is there is often no GUI (Graphical User Interface) or desktop environment (unless installed on the distribution)
- We communicate with the computer via the terminal (CLI)
- The first 2 commands we learn in the module are `echo` and `whoami`
	- echo: Outputs any text provided, if spaces are present we must use `""` (this is not the case in my example it must have updated capabilities or something like that)
	- whoami: show the user we are currently logged in as
	  
	   ![](Attachments/Pasted%20image%2020260630003036.png)
### Task
- I did them originally on the machine in my previous run through of the module
- Pretty simple stuff
  
  ![](Attachments/Pasted%20image%2020260630003223.png)

---

### Interacting with the Filesystem
- This section is fairly simple so i will just list the commands and the uses
	- `ls`: lists files in current directories
	- `cd`: changing directory
	- `cat`: concatenate (output the contents of a file) 
	- `pwd`: (AKA print working directory) prints which directory we are currently located in.

### Task
- Pretty simple I'm not going to say much. These were done while on the web lab.
  
  ![](Attachments/Pasted%20image%2020260630004413.png)

---

### Searching for Files
- In this section we go over basic commands to find what we need to whether it is something in a file or a file name
	- `find`: it can be used quite simply or complex depending on what we need
	- `grep`: is the most common search utility in Linux, it can be used to search for specific things within files. quite powerful.
	- `wc`: an extra command that displays the number of rows, words and characters in a file or multiple. `wc -l` prints only the number of lines in a file there are many other prefixes to use.

### Find
- Purely the basics it can be used pretty simply `find -name *.txt` this will find any file with the extension `.txt` where `*` means wildcard meaning `any` so in plain English it would be `find --"the name" "any".txt`
- On the lab it looks like this:
  
  ![](Attachments/Pasted%20image%2020260630005736.png)

### Grep
- The basic concept is that it can search the contents of a file so for the example we use `grep "target info" "filename"`:
  
  ![](Attachments/Pasted%20image%2020260630012346.png)
- This example only searches one file, however we can use the recursive prefix -R to search the entirety of the subdirectories and files for example `grep -R "PRETTY_NAME" /etc/`:
  
  ![](Attachments/Pasted%20image%2020260630012859.png)
- Sudoers permission was denied - this is normal as it requires escalated privileges

### Task
- Pretty simple not much explanation needed
  
  ![](Attachments/Pasted%20image%2020260630013034.png)

---

### Intro to Shell Operators
- Operators allow us to combine commands or output things to for specific purposes
- A few simple ones include:
	- `&`: Which allows us to run commands in the background such as copying large files while we do something else.
	- `&&`: This allows us to combine multiple commands to run one after another.
	- `>`: Allows us to take output from a command and direct it elsewhere. This will rewrite a file (if there is one) with the output of the command.
	  
	  ![](Attachments/Pasted%20image%2020260630013940.png)
	- `>>`: does the same as `>` but instead appends the output rather than replace what is in the destination
	  
	  ![](Attachments/Pasted%20image%2020260630013958.png)
	- `|`: Strangely not listed on TryHackMe is used to redirect the output of one command into another

### Task
- Fairly simple - ran in the attack box.
  
  ![](Attachments/Pasted%20image%2020260630014041.png)