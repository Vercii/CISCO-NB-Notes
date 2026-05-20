# Module 15 - TCP and UDP

## Transport Layer Protocols

### TCP vs UDP (Transport Layer Protocols)
The Transport Layer is responsible for taking large amounts of data (such as webpages, emails, videos, or voice calls) and breaking them into smaller pieces called segments before sending them across a network.

Each segment contains:

A source port number (where the data came from)
A destination port number (where the data is going)

These port numbers help devices keep track of conversations between applications.

---
### UDP (User Datagram Protocol)
UDP is mainly used for:
- Streaming
- Voice calls (VoIP)
- Online gaming
- Real-time communication

UDP is considered fast and lightweight because it has very little overhead.

<b>Characteristics of UDP</b>
- No acknowledgements
- No sequence numbers
- No retransmission of lost packets
- -Packets may arrive out of order
- Some packets may be lost

In real-time communication, losing a few packets usually does not matter. For example, during a voice call or livestream, missing a tiny amount of data is less disruptive than waiting for lost packets to be resent.

<b>UDP prioritizes:</b>
- Speed
- Low delay
- Continuous communication

Instead of checking whether every packet arrived correctly, UDP simply sends the data as quickly as possible.

---
### TCP (Transmission Control Protocol)
TCP is used when reliability is extremely important.

Examples:
- Web browsing
- File transfers
- Banking transactions
- Emails

TCP includes mechanisms to ensure data arrives correctly and in order.

Characteristics of TCP
- Uses acknowledgements (ACKs)
- Uses sequence numbers
- Retransmits lost packets
- Reorders packets correctly
- Provides reliable communication

Each TCP segment contains:
- Source port
- Destination port
- Sequence number

The sequence number allows the receiving device to:
1. Check if packets are missing
Reassemble packets in the correct order
2. After receiving packets successfully, the destination sends an acknowledgement back to the sender requesting the next sequence of packets.

---

### Main Differences
| TCP                      | UDP                             |
| ------------------------ | ------------------------------- |
| Reliable                 | Faster but less reliable        |
| Uses acknowledgements    | No acknowledgements             |
| Uses sequence numbers    | No sequence numbers             |
| Retransmits lost packets | Does not retransmit packets     |
| Packets arrive in order  | Packets may arrive out of order |
| More overhead            | Less overhead                   |

---

### Transport Layer Port Numbers
Transport layer port numbers are used to identify:

Specific applications
Communication sessions (conversations)
The source and destination of data transmissions

They allow multiple applications to communicate over the network at the same time without interfering with each other.

---
### Servers and Port Numbers
When a server is configured to provide services over a network, applications are installed on it.

Examples:
- Web server
- FTP server
- Mail server

Each application is assigned a specific transport layer port number.

<b>Well-Known Ports:</b>
Port numbers below 1024 are called well-known ports because they are commonly used standard ports.

Some examples include:
| Service            | Port Number |
| ------------------ | ----------- |
| Web Server (HTTP)  | 80          |
| FTP Server         | 21          |
| Mail Server (SMTP) | 25          |

Clients already know these standard ports automatically.

For example:
- A web browser automatically knows that web servers listen on port 80.
- Users only type the URL because the browser already knows the destination port.

---

### How Servers Listen for Requests
A server “listens” on a specific port by waiting for requests addressed to:
1. Its IP address
2. A particular port number

For example:
- Web server listens on TCP port 80
- FTP server listens on TCP port 21

This allows one server to run many services simultaneously.

---

### Dynamic Port Numbers on Hosts
Client devices (hosts) use dynamic ports, also called ephemeral ports.

Characteristics:
- Usually above port 1024
- Randomly assigned
- Used temporarily as source ports

For example:
- A web browser may randomly receive source port 5305
- It then sends traffic to destination port 80

| Source Port | Destination Port |
| ----------- | ---------------- |
| 5305        | 80               |

---

## How Communication Works
### Step 1: Client Sends Request

The client:
- Uses a random source port
- Sends data to the server’s known destination port

Example:
- Source port: 5305
- Destination port: 80

The server sees port 80 and forwards the request to the web server application.

### Step 2: Server Sends Response
The server reverses the ports:
- Source port becomes 80
- Destination port becomes 5305

Example:
| Source Port | Destination Port |
| ----------- | ---------------- |
| 80          | 5305             |

When the client receives the response, it knows the data belongs to the web browser session because of port 5305.

---

### Multiple Actions at the Same Time
Port numbers allow devices to run multiple network applications simultaneously.

Example:
- Web browser uses source port 5305 - destination port 80
- FTP client uses source port 5307 - destination port 21

Because each application uses different port numbers, the device can correctly identify which data belongs to which application.
