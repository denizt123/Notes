### Intro to Port Forwarding
- Is essential component in connecting apps and services to the internet
- Without it Apps and services are only available to devices on the same network. in the example only devices on this network will be able to connect to the device on port 80
  
  ![](Attachments/Pasted%20image%2020260703201824.png)
- If the admin wanted the website accessible to the public they would implement port forwarding:
  
  ![](Attachments/Pasted%20image%2020260703201946.png)
- In this network 2 can now connect to network 1 using the public IP of the network

---

### Firewalls 101
- A firewall is a device in a network responsible for determining what traffic is allowed in and out of a network, kind of like border security
- An admin can configure a firewall to permit or deny traffic from entering or exiting a network based on a few factors:
	- Where is traffic coming from?
	- Where is the traffic going to?
	- What port is the traffic for?
	- What protocol is the traffic for?
	- What protocol is the traffic using?
- Firewalls come in all shapes and sizes, it can be dedicated hardware for handling massive amounts of traffic or software they can be in 2-5 categories:
	- Stateful: This type of firewall uses the entire information from a connection rather than the individual packets and determines the behaviour of device based on the entire connection
	  It consumes many resources in comparison to a stateless firewall, it could allow the first part of a TCP handshake that would later fail
	  If a connection from a host is bad it will block the entire device
	- Stateless: Uses a static set of rules to determine if a individual packet is acceptable or not, a bad packet will not necessarily mean the entire device is blocked
	  They use less resources than the alternatives although they are much dumber and are only effective with the specific rules defined within them, if the firewall rule is not set correctly it is effectively useless
	  They are great to prevent DOS attacks and when receiving large amounts of data
	  

---

### VPN Basics
- VPN aka Virtual Private Network
- Allows devices on separate networks to communicate securely by creating a dedicated path between each other over the internet known as a tunnel. devices connected in the tunnel form their own private network
- E.g. only devices in the same network can communicate directly, with a  vpn connecting 2 offices they can communicate as if they were on the same network
- In this example it might be better to think of the network 3 as 1 thing that both routers of both networks connect to
  
  ![](Attachments/Pasted%20image%2020260703233121.png)
- Devices on network 1 and network 2 still have their own network but network 3 allows them to communicate over a private network
- Benefits of VPN:
	- Allows networks in different Locations to be connected: resources like servers and infrastructure can be accessed from another building
	- Offers Privacy: VPN's use encryption to protect data meaning it can only be understood between devices it was sent and destined for so data isn't vulnerable to sniffing
	- Offers anonymity: Journalists and activists depend on VPN's to report on issues in countries where freedom of speech is limited
	  Without a VPN your ISP and other services can see your traffic and track it
	  The level of anonymity is only as much as other devices on the VPN network respect privacy, a VPN that logs your data/history is the same as not using a VPN as there is a log of your requests out there
- VPN technology has grown over the years, here are some examples
	- PPP: The tech used by PPTP to allow authentication and provide encryption like ssh, a private key and cert must mach for you to connect.
	  PPP is unable to leave the network by itself as it is non routable 
	- PPTP: point to point tunneling protocol, allows ppp to travel and leave the network, PPTP is easy to setup and is highly compatible however it is weakly encrypted compared to the alternatives 
	- IPSec: encrypts data using the existing IP framework, It is difficult to setup in comparison to others, however if successful it has strong encryption and is highly compatible

---

### LAN Networking Devices

### What Is A Router?
- A routers job is to connect networks and pass data between them known as routing
- Routing is the process of creating paths so that the data can successfully be delivered, it operates on the third layer 
- Routers often have a GUI to interact with them and configure them
- Routers help find the shortest most reliable path between 2 networks and decides using 3 main factors
	- What is the shortest path?
	- What path is the most reliable?
	- Which path has the faster medium? (copper or fibre)

### What Is A Switch?
- A switch is a dedicated networking device that provides a means of connecting multiple devices and can support from 3-63 or more
- They operate on layer 2 and 3, layer 2 switches do not operate on both only 1

### Layer 2 Switch
- A layer 2 switch forward frames onto the connected devices using MAC addresses
  
  ![](Attachments/Pasted%20image%2020260704004202.png)

### Layer 3 Switch
- More sophisticated than layer 2 layer 3 switches perform some of the responsibility of a router like sending frames to devices and route packets to other devices using IP protocol
- We can use technology called VLAN (Virtual Local Area Network)
- In this example the network is split up into 2 sub networks via VLAN and are treated seperately with different IP's this is so we can set different rules for both departments
  
  ![](Attachments/Pasted%20image%2020260704004620.png)