### Introducing LAN Topologies 
- There are various Network designs for a LAN network
- We refer to their design as a topology and there are advantages and disadvantages of each

### Star Topology
- Devices in a star topology are individually connected to a central networking device such as a hub or switch
	- Pros: much more scalable in nature which means its very easy to add more devices as the demand increases.
	- Cons: Much more expensive than any other topology and maintenance the more the network grows the more cost, if a hub or switch breaks devices won't be able to send data
	  
	  ![](Attachments/Pasted%20image%2020260702232202.png)

### Bus Topology
- A bus topology relies on a single connection which is known as a backbone cable and devices connect like branches on a tree all connected to the central cable
	- Pros: much cheaper than other topologies and is sufficient for small networks
	- Cons: Central cable can become bottlenecked due to all the traffic flowing through it, the fact that all data is flowing through it makes it difficult to identify and troubleshoot problems, also a single point of failure/break in the backbone can stop the entire network
	  
	  ![](Attachments/Pasted%20image%2020260702232210.png)

### Ring Topology
- Ring/Token topology is similar to a Bus topology however instead it forms a loop between all devices like a circle
- It works by sending data through each machine across the loop forwarding info until it reaches the designated device
- Data flows in one direction across this topology
	- Pros: super cheap, little cabling requirement and less dependence on dedicated hardware such as a switch. It is also easy to troubleshoot problems as data only flows 1 way, it is also less prone to bottlenecks as large amounts of traffic are not travelling across the network at 1 time
	- Cons: It isn't the most efficient way to send data across a network as it must jump from device to device, if 1 cable breaks the entire network will also be down.
	  
	  ![](Attachments/Pasted%20image%2020260702233216.png)

### What Is A Switch?
- Switches are dedicated devices within a network designed to connect multiple devices into a central location which plugin via Ethernet.
- Devices like computers printers etc. connect to this
- It is used is larger networks such as businesses, schools or similar sizes of network
- Switches can connect a large number of devices from 4, 8, 16, 24, 32, 64 so on and so forth
- They are more efficient than "hubs/repeaters" as a switch keeps track of what device is connected to what port where a hub/repeater does not
- This means when data is sent it will be sent to the correct device in the correct port rather than what a hub does which is send a packet to every port connected.
- Switches and routers can be connected to one another, this is to increase reliability creating multiple paths for data to take if 1 path went down.
  
  ![](Attachments/Pasted%20image%2020260702234109.png)

### What Is A Router
- A routers job is to connect networks and pass data between them. it does this via a process called routing
- Routing is the process of data travelling across networks, creating paths between networks so data can be delivered
  
  ![](Attachments/Pasted%20image%2020260702234430.png)

---

### Intro To Subnetting
- Subnetting is the act of splitting up a network into smaller miniature networks within itself.
- For example we are in a company with 3 departments, accounting, finance and human resources 
  
  ![](Attachments/Pasted%20image%2020260702235643.png)
- The network needs to know where to send information, network admins use subnetting to categorise and assign specific parts of a network to reflect this.
- An IP address is made up of 4 octets. The same goes for the subnet mask which is represented the same way in 4 bytes (octets) ranging from 0-255 (binary)
  
  ![](Attachments/Pasted%20image%2020260703000102.png)
- Subnets use IP addresses in 3 different ways
	- Identify the network address
	- Identify the host address
	- Identify the Default gateway
- #### Network Address
	- Identifies the start of the actual network to identify its existence 
	- Example: like a street name if a device has a IP of 192.168.1.100 on a network, and the identifier of the network is 192.168.1.0 will be used to find the device on the network
- #### Host address
	- Used to identify a device on a subnet
	- Example: like a number on the street a device will have the network address of 192.168.1.1 on the network address 192.168.1.0
- #### Default Gateway
	- The Gateway address is assigned to a device that is capable of sending information to another network such as the router
	- Example: any data that needs to go to a device that isn't on the local network will use the gateway usually either .1 or .254
- Subnetting is crucial for networks that have more than 254 devices such as businesses. notice its 254 and not 255 as the .0 is reserved for the network device and the .255 is reserved for the broadcast address. (not learned yet)

---

### ARP
- ARP aka Address Resolution Protocol
- ARP is responsible for allowing devices to identify themselves on a network
- ARP allows a device to associate its MAC with an IP on the network, each device will keep a log of MAC addresses associated with other devices
- When devices want to communicate with another it will send a broadcast to the entire network to locate the specific device. Devices can user ARP to find the MAC address (physical identifier) of a device for communication

### How Does ARP Work
- Each device has a ledger called a cache to store information on, in the ARP context the cache stores the identifiers of other devices on the network
- In order to map the 2 identifiers together (IP/MAC) ARP sends 2 types of messages
	- **ARP request**: a message is broadcasted on the network to the others asking "what is the mac address that owns this IP address"
	- **ARP reply**: If a device has the IP address from the request it will send back its MAC address.
- The device asking for the identifier will now remember the mapping and store it in its ARP cache for future use
  
  ![](Attachments/Pasted%20image%2020260703003826.png)

---

### DHCP
- We can assign IP's manually by entering them physically into a device or we can do them automatically via DHCP
- DHCP aka Dynamic Host Configuration Protocol
- When a device connects to a network and is not assigned a IP it undergoes these actions
	- **DHCP Discover**: Sends a request to see if any DHCP servers are on the network.
	- **DHCP Offer**: DHCP server replies with an IP the device can use
	- **DHCP Request**: The device sends a reply confirming it wants the offered IP
	- **DHCP ACK**: DHCP server replies acknowledging this it is completed and the device can start using the IP address
	  
	  ![](Attachments/Pasted%20image%2020260703005029.png)