### What Are Packets & Frames
- A packet is a piece of data from Layer 3 with information such as a IP header
- A frame is used at Layer 2 which encapsulates a packet and adds information such as MAC address
- Like sending a letter, the packet is the information within the letter, the frame is the envelope with information on where it needs to go
- This is called encapsulation
- When we are talking about things like IP addresses we can assume we are talking about a packet
- When encapsulating information is stripped we are talking about the frame
- Packets are a efficient way of communicating data across devices, because the data is small there is less chance of bottlenecking
- Packets have different structures that depend on the packet type, since we have billions of devices there needs to be a way to standardise the data which we call standardisation 
- Here are some headers used to route the information correctly
	- **Time to Live**: A expiry timer, a number set that decreases at every hop, used so that when it reaches zero it is gone so that it doesn't clog up a network
	- **Checksum**: Provides integrity checking for protocols like TCP/IP. if data is changed, the value will be different than what is expected and therefore corrupt
	- **Source Address**: The IP of the device the packet is sent from so the data knows where to return
	- **Destination Address**: The address of where the packet is being sent so the data knows where to travel next

---

### TCP/IP (Three Way Handshake)

### What TCP is
- A set pf networking rules for sending data reliably, a connection must be established with the client and server before data is sent which is what makes TCP guarantee delivery
- There are 4 layers
	- Application
	- Transport
	- Internet
	- Network Interface
- Data moves through each layer adding its own information called encapsulation
- The reverse of this is called encapsulation - stripping information
- Here are some Pros and cons:
	- Pros: Guarantees integrity as it syncs machines so packets aren't flooded or in the wrong order
	- Cons: Needs reliable connection (one missing chunk = whole chunk re sent) much slower than UDP as it requires a good connection

### TCP Headers
- TCP packets contain information known as headers that are added from the encapsulation process:
	- **Source Port**: The value of the port used by the denser to send TCP packets. Chosen at random from the 0-65535 ports that aren't already in use at the time
	- **Destination Port**: The value of report that a app or service is running (the receiving host) E.g. port 80, not chosen at random
	- **Source IP** The IP of the device sending the packet
	- **Destination IP** The IP of the device the packet is designated for.
	- **Sequence Number**: A number given to the first piece of data transmitted given at random
	- **Acknowledgement Number**: After a Sequence number is sent the Acknowledgement number will be on the next piece of data as Sequence number + 1
	- **Checksum**: The value for TCP integrity, calculated by the sender and added to the data to verify integrity, confirming data arrived without corruption unless there is a mismatch which the receiver calculates
	- **Data**: The actual stored bytes of the file being transmitted
	- **Flag**: Determines how the packet should be handled by either device during the handshake process determining specific behaviours

### Flags - Three way handshake
- The three way handshake is the term given to establish a connection between devices
	- **SYN**: Initial package sent from the client in a handshake, used to initiate a connection and sync devices 
	- **SYN/ACK**: Acknowledgement sent by receiving device to acknowledge sync attempt from client
	- **ACK**: Acknowledgment packet can be used either by client or receiver to acknowledge a series of packets have been successfully received 
	- **DATA**: Once a connection is established data is send such as bytes for a file
	- **FIN**: Used to cleanly close the connection after it is complete
	- **RST**: Abruptly closes and ends communication, a last resort for when a app or service isn't working correctly 
	  
	  ![](Attachments/Pasted%20image%2020260703192144.png)
- We use the Sequence number to sync devices devices, agreed upon by the devices to send packets in the correct sequence,
	- SYN: Initial sequence number
	- SYN/ACK: acknowledge Initial sequence number
	- ACK:  acknowledge sequence number with some data, sequence number + 1
	  
	  ![](Attachments/Pasted%20image%2020260703192508.png)

### Closing TCP Connection
- To initiate a closure of TCP connection the device sends a FIN packet which the other device has to acknowledge
- It is important to close a connection as soon as data is received as TCP reserves a connection and we want to close it to save resources
  
  ![](Attachments/Pasted%20image%2020260703192745.png)

---

### UDP/IP
- UDP is much simpler than TCP as it doesn't require a constant connection and just fires off packets at the target with no validation, very useful for things that need to be delivered fast

### Headers
- **TTL (Time to Live)**: Expiry number for the packet, so it doesn't clog the network if it can't reach the destination (Decreases by 1 per hop)
- **Source address**: IP of device packet is sent from so data knows where to return
- **Destination Address**: IP of where the packet is being sent so data know where to travel next
- **Source Port** Chosen randomly to send the UDP packet from (0-65535) for its port
- **Destination Port**: Value of what port number the data needs to go, not chosen at random
- **Data**: header for the actual data being sent
  
  ![](Attachments/Pasted%20image%2020260703194141.png)

---

### Ports
- Ports are like docks on a harbour, the harbour being the device or server and the port being the dock
- They are numbered from 0-65535
- Once a connection is established all data passes through the established ports
- They enforce what connects and where, if a connection isn't compatible with the ports rules it can't communicate there

### Standardisation 
- We standardise ports so we don't lose track of which apps use which ports, so applications, protocols and behaviours are tied to standard sets of ports
- Common Ports (0-1024):
	- FTP: Port 21: Download files from a central location
	- SSH: Port 22: Securely login and manage a system via text interface
	- HTTP: Port 80: Powers WWW. browsers use it to download data
	- HTTP: Port 443: Same as HTTP but encrypted
	- SMB: Port 445: Like FTP but also shares to devices such as printers
	- RDP: Port 3389: Like SSH but allows us to login via a visual interface onto the desktop
- The Port assignments are only defaults, apps can run on non standard ports, other software assumes the standard so to reach a non standard port you must specify it