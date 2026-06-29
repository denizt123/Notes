### What is Offensive Security

- The core idea of offensive security is breaking into computer systems, exploiting bugs and finding loopholes in systems to gain access to sensitive information or areas
- The purpose of this is to understand hackers tactics to enhance defensive security on systems.

---
### First practical (Fake Bank THM)

1) The first practical we encounter is pretty basic - *No SSH into machine available - only web attack box*
   
2) We start on webpage where we are asked for the first task - *"What is our bank account number"* - It is displayed at the top right as 8881
   ![](Attachments/Pasted%20image%2020260629191452.png)
3) We then use the tool **dirbuster** (one of a few tools used to brute force search for hidden URL's or quickly find urls rather than manually searching for common page names)
   
   We use the command = `dirb http://fakebank.thm` normally we add a wordlist on top of this however for this lab the default wordlist will do in this case common.txt wordlists folder under dirbuster /usr/share/dirb/wordlists/common.txt
   ![](Attachments/Pasted%20image%2020260629191442.png)
   
4) The output found 2 URL's marked with the `+` sign
	1) the first is `/images`
	2) the second is `/bank-deposits` - this is the one we are after
	   
5) We head on to /bank-deposits and we are tasked to add 2000 into our bank account
	1) `firefox http://fakebank.thm/bank-deposit`
	2) We are in the admin portal
	   ![](Attachments/Pasted%20image%2020260629191438.png)
	3) Transfer complete
	   ![](Attachments/Pasted%20image%2020260629191434.png)
	   
	4) And we submit the flag
	   ![](Attachments/Pasted%20image%2020260629191424.png)