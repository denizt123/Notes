### What Is Networking?
- Simply Networks are things connected together such as public transport, power infrastructure, people you know in your circle, the paper mail system.
- In computing it's the same idea of how our devices communicate with each other
- A network can be anything from 2 devices to billions, anything like cameras, traffic lights, phones etc.
- It is part of our everyday life like gathering info for weather, deliveries, sending data, delivering electricity to houses etc.
- They come in all shapes and sizes
  
  ![](Attachments/Pasted%20image%2020260702211530.png)

---

### What Is the Internet
- The internet is a giant global network of many small networks within itself
- Example:
	- Alice, Bob and Jim communicate together however Alice made some friends called Zayn and Toby who speak the same language as Alice but not as bob and Jim
	- Alice now acts as a translator for messages sent to Zayn and Toby or vice versa
	  
	  ![](Attachments/Pasted%20image%2020260702212254.png)
- The first version of the internet was a US project in the 1960s called ARPANET designated for organizations and US departments and was the first way networks were able to communicate with each other
- In 1989 the WWW aka World Wide Web was invented by a man called Tim Berners-Lee
- From this point the WWW was able to be used as a repository for storing and sharing information
- The internet is made up of many small networks joined together, the small networks are called private networks, networks connecting these small networks together is called a public network - forming the internet
  
  ![](Attachments/Pasted%20image%2020260702212903.png)

---

### Identifying Devices on a Network
- To communicate with each other devices need to be able to identify and be identifiable on a network. Much like our Names and Fingerprints
- We can change our names but not our fingerprints, devices operate the same way we have:
	- IP addresses: Internet protocol addresses
	- MAC addresses: media access control addresses (like serial numbers)

### IP addresses
- IP aka Internet protocol are used to identify a host on a network
- An IP address is split into 4 sets of numbers known as octets, which summarises the IP address of a device on a network
- The number is calculated with a technique known as subnetting (more advanced)
- No 2 devices have the same IP on a network at a time.
- IP addresses follow a set of standards known as protocols, they are the backbone of
- A device can be given a public or a private IP address depending on what it is for and where it is on a network
	- Private IP: to identify devices among other devices on a network
	- Public IP: to identify a device on the internet 
	  
	  ![](Attachments/Pasted%20image%2020260702220810.png)
- The 2 devices listed will be able to use their private IP to communicate with each other, however any data sent to the internet uses the same public IP (discussed later ports etc.) given out by the ISP
- This brings us to the issue, we have 8.3 billion people on the planet and not enough IP addresses, we use the IPv4 IP addressing scheme which uses a number system with 2^32 combinations (addresses) (4.29 billion) so we have a shortage in today's world
- IPv6 is a new iteration of the IP addressing scheme which can support up to 2^128 IP addresses (340 trillion +)
  
  ![](Attachments/Pasted%20image%2020260702221746.png)

### MAC Addresses 
- Devices all have a physical network interface which is a microchip on the motherboard
- The interface is assigned unique addresses at the factory it was built known as a MAC address (12 hexadecimal characters) split into to 2 parts
- The first 6 represent the company that made the interface and the last 6 are unique to the device
  
  ![](Attachments/Pasted%20image%2020260702222225.png)
- These values can be changed, called spoofing, you can change the mac address to trick networks into thinking you are a different device

---

### Ping (ICMP)
- Ping is a fundamental tool of networking.
- Ping uses ICMP (Internet control message protocol) to determine performance of connections or to check if a connection exists or is reliable
- It uses ICMP echo packets to get a reply from the target device
- It comes installed on most OS's by default
- simply running `ping "ip" or "url"` executes the command and allows us to see information such as the average time it took to send a packet
  
  ![](Attachments/Pasted%20image%2020260702222919.png)