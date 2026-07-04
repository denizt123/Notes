### What Is DNS? 
- DNS aka Domain Name Service provides a way to communicate with devices on the internet without remembering complex numbers such as IP
- For example if we ant to connect to google we don't type 142.250.151.139 we type google.com. this is what DNS is, translating these numbers into domain names or host names

---

### Domain Hierarchy

![](Attachments/Pasted%20image%2020260704004954.png)
### TLD - Top Level Domain
- TLD is the right hand part of a domain name the .com or .gov etc.
- There are 2 types of TLD
	- gTLD: generic top level domain, it is meant to tell the websites purpose such as .com for commercial, .org for organizations, .edu for education so on and so fourth 
	- ccTLD: Country code top level domain, for websites based in countries so .ca for Canada, or .co.uk for the UK etc.

### Second Level Domain
- This is the left hand side of the domain where the actual selected name of the host applies it is limited to 63 characters a-z 0-9 with no hyphens at the start or end and no consecutive hyphens like tryhackme in tryhackme.com

### Subdomain
- sits on the left had side of the second level domain using a period to separate it, limited to 63 characters a-z 0-9 with no hyphens at the start or end and no consecutive hyphens

---

### Record Types
- DNS isn't just for websites and multiple types of DNS record exits
	- **A record**: resolves IPv4 addresses
	- **AAAA record**: Resolves IPv6 Addresses
	- **CNAME record**: resolve to another domain name so for example store.tryhackme.com returns a cname record for shops.shopfiy.com, another dns request is made to shops.showily.com to workout the IP address
	- **MX records**: resolve the IP address of server that handle the email for a domain you are querying so an MX record response for tryhackme.com would return something like alt1.aspmx.l.google.com they also come with a priory flag which tells the client in which order to try servers which is perfect for when a server goes down and email needs to be sent to the backup server.
	- **TXT records**: these are text fields where text based data can be stored, they have multiple uses such as storing emails that have the authority to send emails ion behalf of a domain which helps combat spoofed emails or spam some examples include 
		- `_acme-challenge.example.com TXT "token_value_here"`
		- `@ TXT "v=spf1 ip4:192.0.2.0/24 include:_spf.google.com include:amazonses.com ~all"`
		- `_dmarc.example.com TXT "v=DMARC1; p=reject; rua=mailto:dmarc-reports@example.com; adkim=s; aspf=s; pct=100"`
		- `@ TXT "MS=ms12345678"`
---

### Making a Request
- When you make a request for DNS your computer can take up to 5 steps
1) Your computer checks its local cache to see if your recently looked up the address if not it moves on
2) A recursive DNS Server is usually provided by your ISP but you can also choose your own. and has a cache with recent addresses, if it cannot find them locally here it moves on to the Internets root DNS servers.
3) The root server acts a as a DNS backbone of the internet, here its job is to redirect you to the correct server based on your TLD so for .com it will refer you to the server that stores these under that TLD
4) The TLD server holds records for where yo find the authoritative server to answer the DNS request, there are often multiple used as a backup in case one goes down
5) An authoritative DNS server is responsible for storing DNS records for a particular domain name where any updates to the domain name DNS records would be made. The server will sent back to the recursive DNS server where a local copy is cached along with a TTL to save space, now it is stored in cache you don't need to do the request again unless the TTL is gone
