# Module 2

## Client and Server Roles
- All computers connected to a network are classified as hosts.
- Hosts can send and receive messages on the network.
- Modern computer hosts can act as a client, a server, or both.

### Servers
- Hosts that have software installed which enable them to provide information to other hosts network.
- Each service requires separate server software.

### Clients
- Computer hosts that have software installed that enables the hosts to request and display information obtained from the server.
    - Types:
        - Email: Runs email server software, such as Microsoft Outlook to access email on the server.
        - Web: Runs web ser software, such as Firefox, and Chrome.
        - File: Stores files in a central location. Accessed through client software such as File Explorer.
        
## Peer-to-Peer Networks.
- Instead of having separate computers for client and server, one computer runs both of it.
- In small homes, many computers function as both, making it a peer-to-peer (P2P) network.

Example:
- Two directly connected computers using either wired or wireless connection. Both computers can send and receive data with each other.

Advantage:
- Easy to access
- Simple setup, not complex
- Lower cost since dedicated servers aren't required

Disadvantage:
- Less security
- Does not scale well
- Performance may slow down if all devices act as clients and servers

## Peer-to-Peer Applications
- Allows a device to act as both client and server.
- P2P apps require that each end device provide a UI and run a background service.
- Some use a hybrid system where resource sharing is decentralized.

Example:
- Cash App is used for fast, direct money transfers, often bypassing traditional banking infrastructure.
- Zoom uses a hybrid approach, using P2P for 1-on-1 calls, but relies on servers for almost all group conferences.

---

A single computer can run multiple types of server software, the same goes for running client software. However, there must be a client software for every service required.

An example is that a user can view a web page, while messaging someone and listening to their playlist uploaded on another application.

---

## Network Infrastructure
- Contains three categories:
    - End Devices: Phone, laptop, printer
    - Intermediary: Wireless Router, LAN Switch, 
    - Network Media: Wireless, LAN, WAN

### End Devices
- Computers, printers, telephones, and mobile devices.
- Either the source or destination of a message transmitted over the network.
- Addresses are used to uniquely identify hosts, these addresses are used to specify where the messages should be sent.

### Internet Service Provider (ISP) Services
- Provides the link between the home networks and the internet.
- Can be the local cable provider, the landline telephone service provider, and the cellular network on a smartphone.
- Critical to communications across the global internet. IPSs are connected in a hierarchical manner that ensures that internet traffic takes the shortest path from source to destination.

### ISP Connections
- On a one on one connection, an end device can directly connect to a modem.
- On a many to one connection, generally, a router is needed to manage traffic for multiple end devices.

### Cable and DSL Connections
- Cable: Provides an always on high bandwidth connection to the internet. The internet signal is carried on the same coaxial cable that delivers cable television. Much faster than DSL, often reaching 1000 Mbps (1 Gbps) or more.

- DSL: Uses existing copper telephone lines. Dedicated line to your home; speeds are more consistent and don't slow down based on neighbor usage.
