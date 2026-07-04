### What Is HTTP/HTTP
- HTTP is used wherever you view a website, developed by Tim Berners-Lee. HTTP is the set of rules used for communicating with web servers for transmitting of seepage data.
- HTTP is the secure version of HTTP as it is encrypted to stop people form seeing your data you are sending and receiving and also gives assurance you are talking to the correct web server

---

### Request and Response
- When accessing a website your browser needs to make requests for assets such as HTML, images and download the responses
- before that you need to tell the browser specifically how and where to access the resources which is where URL's work

### What Is A URL
- AKA Uniform resource locator
  
  ![](Attachments/Pasted%20image%2020260704020519.png)
- It is made up of up to 7 parts if all features are used
	- **Scheme**: Instructs what protocol to use for accessing resource such as HTTP, HTTP, FTP
	- **User**: Some services require authentication where you can put your username and password into the URL
	- **Host**: The domain name or IP of the server to access
	- **Port**: The port that we are using to connect usually 80 for HTTP or 443 for HTTPS but can be on any port
	- **Path**: The file name or location of what to access
	- **Query String** Extra bits of info that can be sent to the requested path e.g. /blog?**id=1** would mean we want to access the blog article with the id of 1
	- **Fragment**: Reference to a location on the actual page requested when it is long and we have a certain part already linked to it

### Making A Request
- It is possible to make a request to a web server with just 1 line `GET / HTTP/1.1`
  
  ![](Attachments/Pasted%20image%2020260704021357.png)
- For a much richer experience we need to send other data as well called headers which contain extra information to give the web server we are communicating with
  
  ![](Attachments/Pasted%20image%2020260704021512.png)
- To break down each line
	- Line 1: this request is sending the GET method to request the home page (index) which is located in  / and we tell the server we are using HTTP 1.1
	- Line 2: We tell the server the host we want to access so tryhackme.com
	- Line 3: We tell the web server we are using Firefox venison 87 browser
	- Line 4: We tell the web server the web page that referred us to this one is tryhackme.com
	- Line 5: HTTP requests end with a blank line to indicate the request has finished

### Response

![](Attachments/Pasted%20image%2020260704021911.png)
- To break down each line
	- Line 1: Tells us what version of HTTP protocol the server is using followed by the Status code which in this case is 200 OK which means the request was successful
	- Line 2: tells us the web server software and version
	- Line 3: the current date and timezone of the web server
	- Line 4: Tells the client what type of information is going to be sent
	- Line 5: Tells the client how long the response is to ensure no data is missing
	- Line 6: Confirms end of HTTP response
	- Line 7-14: The information that has been requested (the homepage)

---

### HTTP methods
- Methods are a way for client to show their intended action when making requests
- There are a lot but we cover the basics here
	- GET: used to get information from a web server
	- POST: used to submit data to a web server potentially creating new records
	- PUT: For submitting data to update information
	- DELETE: for deleting records from a web server

---

### HTTP Status Codes
- We use status codes to indicate the outcome of a request and how to handle it
- they are broken up into 5 different ranges

| Code range | Type                 | Description                                                                                                |
| ---------- | -------------------- | ---------------------------------------------------------------------------------------------------------- |
| 100-199    | Information Response | Tells client first part of request is accepted and they should continue sending the rest of their requests |
| 200-299    | Success              | Tells the client the request was successful                                                                |
| 300-399    | Redirection          | To redirect clients requests to another resource to a different webpage or a different site                |
| 400-499    | Client Errors        | Informs the client there was a error in the request                                                        |
| 500-599    | Server Errors        | Reserved for Server side errors and usually indicate major problems for the server                         |


### Common Status Codes

| Code | Type                   | Description                                                                                                               |
| ---- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| 200  | OK                     | Request Successfull                                                                                                       |
| 201  | Created                | Resource has been created                                                                                                 |
| 301  | Moved Permanently      | Redirects clients browser to a new webpage or tells client page has moved                                                 |
| 302  | Found                  | Similar to 301 but is temporary and may change in future                                                                  |
| 400  | Bad Request            | Tells browser their is something wrong or missing in the request, like a certain parameter the client didn't send.        |
| 401  | Not Authorised         | Not allowed to view resource until authorized by the web application such as with a user and pass                         |
| 403  | Forbidden              | Not allowed to view resource whether you are logged in or not                                                             |
| 405  | Method Not Allowed     | The resource doesn't allow the method of request such as sending a GET when you want to do a POST when creating a account |
| 404  | Page Not Found         | Page or resource does not exist                                                                                           |
| 500  | Internal Service Error | The server ran into a error with the request and doesn't know how to handle the request                                   |
| 503  | Service Unavailable    | Server overloaded or down for maintenance and can't handle request                                                        |

---

### Headers
- Headers are additional information you can send to a web server when making a request
- no headers are required when making requests however it makes a website difficult to view without it

### Common Headers