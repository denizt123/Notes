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
	- Stateful: 