### What Is The OSI Model
- AKA Open Systems Interconnection Model
- This is the model used in networking and provides a framework dictating how all networks send, receive and interpret data.
- The benefit of the OSI model is that devices with different design and function can communicate with other devices across a network following the OSI model to be understood by other devices
- There are 7 layers each with their own responsibilities
- at every layer data travels through, specific processes take place and information is added to the date
  
  ![](Attachments/Pasted%20image%2020260703012233.png)

---

### Layer 1 - Physical
- This is pretty simple
- Communication from physical hardware used in networking transferring data using binary, such as Ethernet cables
  
  ![](Attachments/Pasted%20image%2020260703012431.png)
  
  ![](Attachments/Pasted%20image%2020260703012403.png)

---

### Layer 2 - Data Link
- Data link is the physical addressing of the transmissions
- It receives a packet from the network layer (including IP) and adds the physical MAC address of the receiving endpoint and vice versa
  
  ![](Attachments/Pasted%20image%2020260703012718.png)

---

### Layer 3 - Network
- This layer is where Routing and re-assembly of data takes place, taking small chunks of data and packaging them together then deciding how to route them
- Routing determines the optimal path for data to be sent
- There are protocols in place at this layer to dictate the path such as SPF (open shortest path first) and RIP (Routing information protocol) and decide things like
	- What path is shortest (least amount of devices)
	- What path is most reliable (has data been lost on this path before)
	- What path is faster (considers the speed such as the copper/fibre connection etc.)
- Everything in this layer is dealt with via IP
  
  ![](Attachments/Pasted%20image%2020260703013426.png)
  
  ![](Attachments/Pasted%20image%2020260703013417.png)

---

### Layer 4 - Transport
- Layer 4 handles transmitting data across a network
- When data is sent between devices it follows one of 2 different protocols based on the use case:
	- TCP
	- UDP

![](Attachments/Pasted%20image%2020260703014343.png)

### TCP
- TCP aka Transmission Control Protocol
- Designed to deliver information with reliability and a guarantee.
- It reserves a constant connection between devices for the amount of time it takes data to be sent and received
- It also incorporates error checking in its design, it guarantees that data sent from the chunks in Layer 5 has been received and reassembled in the same order
- It is used in situations like file sharing, browsing or sending emails. This is because the data we needs to be accurate and complete
	- Pros: Guaranteed data accuracy, Can sync devices to prevent each other from being flooded with data, Performs a lot more processes for reliability
	- Cons: Requires a reliable connection (if a small part of data is not received the entire chunk of data can't be used), Slow connection can cause another device to be bottlenecked (as the connection is reserved on the receiving device the whole time), TCP is slower than UDP because more work is done by the devices
	  
	  ![](Attachments/Pasted%20image%2020260703015514.png)

### UDP
- UDP aka User Datagram Protocol
- UDP sends data regardless of being received
- There are no complex features such as syncing devices or error checking
- It is used to load livestreams/videos or things of that nature where we need to receive information fast regardless of if the full information is there.
	- Pros: Much faster than TCP, UDP uses the application layer to decide how quickly packets are sent, No continuous connection for faster data
	- Cons: Doesn't validate if data is received, Flexible, Unstable connections result in a terrible experience
	  
	  ![](Attachments/Pasted%20image%2020260703020033.png)

---

### Layer 5 - Session
- Once data is correctly translated or formatted from the presentation layer, layer 5 will create and maintain the connection to the other computer for which the data is destined.
- When a connection is established a session is created
- The layer is also used for closing a connection if it hasn't been used in a while or if it is lost, a session can contain checkpoints where if data is lost only the newest pieces of data are required to be sent.
  
  ![](Attachments/Pasted%20image%2020260703020706.png)

---

### Layer 6 - Presentation
- This is where standardisation takes place
- Developers develop software such as email clients differently but the data needs to be handled the same way
- This layer is like a translator for data from Layer 7, The receiving computer will also understand data sent to a computer in another format.
- Example: you send a email, the recipient uses a different client to you but the data needs to display the same
- Security features such as HTTP when visiting a secure site happen at this layer
  
  ![](Attachments/Pasted%20image%2020260703021048.png)

---

### Layer 7 - Application
- This is where protocols and rules are in place to determine how a user interacts with data sent or received
- Applications usually have a GUI to interact with data sent and received where this layer works.
  
  ![](Attachments/Pasted%20image%2020260703171909.png)