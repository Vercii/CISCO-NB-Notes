# Module 16 - Application Layer Services

## Client and Server Interaction
The term server refers to a host running a software application that provides information or services to other hosts that are connected to the network. 

A well-known example of an application is a web server. There are millions of servers connected to the internet, providing services such as web sites, email, financial transactions, music downloads, etc. A crucial factor to enable these complex interactions to function is that they all use agreed upon standards and protocols.

---

# Web Client and Web Server Communication Using IP Protocols

When a web client (such as a browser) wants to retrieve a webpage from a web server, several networking processes happen in sequence.

The web server:

* Has its own IP address
* Has a domain name (URL)
* Listens for web requests on TCP port 80

---

# Step 1: User Enters the URL

The user enters a URL such as:

`www.learnip.com`

However, networks do not use domain names to forward data. They use **IP addresses** instead.

Because of this, the URL must first be translated into an IP address.

---

# Step 2: DNS Lookup

The client sends a request to a **DNS (Domain Name System) server**.

The purpose of the DNS lookup is to find the IP address associated with the domain name.

Example:

| Domain Name                               | IP Address   |
| ----------------------------------------- | ------------ |
| [www.learnip.com](http://www.learnip.com) | 172.16.10.50 |

After the DNS server responds, the client now knows the IP address of the web server.

---

# Step 3: Create a TCP Connection

Before data can be exchanged, a TCP connection must be established between the client and server.

Example client information:

* Client IP address: 192.168.10.15
* Random source port: 5507

Example server information:

* Server IP address: 172.16.10.50
* Destination port: 80

The TCP communication becomes:

| Component        | Value         |
| ---------------- | ------------- |
| Source IP        | 192.168.10.15 |
| Source Port      | 5507          |
| Destination IP   | 172.16.10.50  |
| Destination Port | 80            |

---

# Socket

This combination of:

* Source IP
* Source Port
* Destination IP
* Destination Port

is called a **socket**.

A socket uniquely identifies a conversation between two devices on a network.

---

# Step 4: Web Server Processes the Request

When the packet reaches the web server:

1. The server sees that the destination port is 80
2. The request is placed into the buffer/queue for the web service
3. The web server processes the request
4. The server prepares a response

---

# Step 5: Server Sends the Response

The server sends the response back using the opposite addressing information.

Response example:

| Component        | Value         |
| ---------------- | ------------- |
| Source IP        | 172.16.10.50  |
| Source Port      | 80            |
| Destination IP   | 192.168.10.15 |
| Destination Port | 5507          |

The client recognizes the response because it matches the original socket information.

---

# Maintaining the Conversation

All packets exchanged during the session use the same:

* Source and destination IP addresses
* Source and destination port numbers

This allows:

* Routers
* Firewalls
* Network devices

to identify that all packets belong to the same conversation between the web client and web server.

---

### URI, URN, and URL
Web resources and web services such as RESTful APIs are identified using a Uniform Resource Identifier (URI). A URI is a string of characters that identifies a specific network resource. URI has two specializations: 
- Uniform Resource Name (URN) - This identifies only the namespace of the resource (web page, document, image, etc.) without reference to the protocol.
- Uniform Resource Locator (URL) - This defines the network location of a specific resource on the network. HTTP or HTTPS URLs are typically used with web browsers. Other protocols such as FTP, SFTP, SSH, and others can be used as a URL. A URL using SFTP might look like: sftp://sftp.example.com.

<b>Components of a URI:</b>
Example: https://www.example.com/author/book.html#page155

URL: https://www.example.com/author/book.html
URN: www.example.com/author/book.html
Fragment: #page155

---

### Retrieving a Webpage from a Web Server (Packet Tracer Demonstration)

# Step 1: Open a Web Browser

To request a webpage, the PC uses a **web browser**, which acts as the web client.

The user:

1. Opens the web browser on PC0
2. Starts the packet capture utility
3. Enters the URL `www.learnip.com`

---

# Step 2: Generate the Web Request

After entering the URL:

* HTTP packets are created
* The packets travel from PC0 across the simulated internet
* The packets are sent to the web server

The communication uses:

* **HTTP** as the application protocol
* **TCP** as the transport protocol

---

# Step 3: Packet Details

When examining the captured packets, several important details can be seen.

## HTTP Request Packet

The request packet contains:

* Source IP address → PC0
* Destination IP address → Web server
* TCP transport protocol information

The packet is initially formatted as an **Ethernet frame** while traveling across the local Ethernet connection.

---

# Step 4: Web Server Responds

When the web server receives the request:

1. It processes the HTTP request
2. It generates a response
3. It sends the webpage data back to PC0

The response packet:

* Uses the web server as the source
* Uses PC0 as the destination

---

# Step 5: Continued Data Transfer

The process continues until all webpage components are delivered.

This includes:

* Webpage content
* Images
* Other related webpage data

Multiple packets may be transmitted back and forth until the webpage fully loads.

---

The process of retrieving a webpage involves:

1. Opening a web browser
2. Sending an HTTP request
3. Using TCP for reliable communication
4. Sending packets across the network
5. Receiving the webpage response from the server

---
| Protocol                                   | Compact Description                                                 |
| ------------------------------------------ | ------------------------------------------------------------------- |
| Domain Name System (DNS)                   | Translates domain names into IP addresses.                          |
| Secure Shell (SSH)                         | Provides secure remote access to devices and servers.               |
| Simple Mail Transfer Protocol (SMTP)       | Sends email messages between clients and mail servers.              |
| Post Office Protocol (POP)                 | Downloads emails from a mail server to a client device.             |
| Internet Message Access Protocol (IMAP)    | Accesses and manages emails directly on the mail server.            |
| Dynamic Host Configuration Protocol (DHCP) | Automatically assigns IP addresses and network settings to devices. |
| Hypertext Transfer Protocol (HTTP)         | Transfers web pages between web servers and browsers.               |
| File Transfer Protocol (FTP)               | Transfers files between computers over a network.                   |

---

## SSH
### Telnet
Telnet provides a standard method of emulating text-based terminal devices over the data network. Both the protocol itself and the client software that implements the protocol are commonly referred to as Telnet. Telnet servers listen for client requests on TCP port 23.

A connection using Telnet is called a virtual terminal (vty) session, or connection. Rather than using a physical device to connect to the server, Telnet uses software to create a virtual device that provides the same features of a terminal session with access to the server’s command line interface (CLI).

<b>Note: Telnet is not considered to be a secure protocol. SSH should be used in most environments instead of Telnet. </b>

