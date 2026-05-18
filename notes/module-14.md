# Module 14 - Routing Between Networks
Routing is a process to determine the best path to a destination.

1. The Core Problem
Local vs. Remote: If a source and destination host are on different networks (their IP network portions do not match, like 1.1.1.0 and 5.5.5.0), they cannot communicate directly using standard local switching. They are considered remote hosts.

2. The Role of the Router
Layer 3 Forwarding: While switches use Layer 2 MAC addresses to move data within a local network, routers use Layer 3 IP addresses to move data between completely different networks.

Path Determination: The router reads the destination IP address in a packet to identify the best path to reach that remote network.

3. The Step-by-Step Process
When you send data to a remote network, the router handles it through a process of stripping and rebuilding data headers:

- Handoff: The sending host sends the message to its local router (the Default Gateway).
- De-encapsulation: The router receives the data and strips away the outer Layer 2 Ethernet frame.
- Inspection: The router looks inside at the Layer 3 IP packet to read the destination IP address.
- Re-encapsulation: The router finds the correct outbound path, wraps the packet in a brand-new Ethernet frame (with new source and destination MAC addresses), and forwards it toward the destination.

### Reasons to divide a network
- Increase network security
- To maintain smaller broadcast domains

Routers are used to divide networks into smaller networks.

---
### Local Network Communication Process (Same Subnet)
When a host sends data to a destination on the same local network, the communication happens directly at Layer 2 without involving a router.

<b>Step 1: Packet Creation (Layer 3)</b>
- Source Host (H1): 192.168.1.10 (MAC: AA:AA:AA:AA:AA:AA)

- Destination Host (H2): 192.168.1.20 (MAC: BB:BB:BB:BB:BB:BB)

- H1 builds the IPv4 packet, inserting its own IP as the source and H2's IP as the destination.

<b>Step 2: Subnet Determination</b>
H1 applies its own Subnet Mask to both its IP address and the destination IP address.

- It determines that both hosts share the same network prefix (192.168.1.0/24).

- Decision: Because they are on the same network, H1 can send the data directly to H2 and bypasses its default gateway (router).

<b>Step 3: Address Resolution (ARP)</b>
- To encapsulate the packet into an Ethernet frame, H1 needs H2's physical MAC address.

- H1 checks its local ARP table for the IP 192.168.1.20.

    - If found: It retrieves the corresponding MAC address (BB:BB).

    - If missing: H1 would dynamically discover it by broadcasting an ARP request and waiting for H2's ARP reply.

<b>Step 4: Frame Encapsulation & Delivery (Layer 2)</b>
- H1 builds the Ethernet frame using:
    - Source MAC: AA:AA (H1's NIC)
    - Destination MAC: BB:BB (H2's NIC)

The frame is transmitted onto the local medium, passing through the switch, which delivers it directly to H2.

---

### Remote Network Communication Process (Different Subnet)

When a host sends data to a destination on a different network, communication must pass through a router (Default Gateway). Layer 3 IP addresses remain constant end-to-end, while Layer 2 MAC addresses change at every router hop.

<b>Step 1: Packet Creation & Subnet Check (Source Host H1)</b>

- Initial Setup: * Source Host (H1): IP 192.168.1.10 | MAC AA-AA
    - Destination Host (H3): IP 192.168.2.50 | MAC CC-CC

- Subnet Decision: H1 uses its subnet mask to compare its own IP network prefix with H3's IP. It determines that H3 is on a different network (192.168.2.0).

- The Rule: Because the target is remote, H1 <b>cannot</b> send the frame directly to H3. It must forward the packet to its Default Gateway (Router R1, IP 192.168.1.1).

<b>Step 2: H1-to-Router Handoff (First Hop)</b>

- Address Resolution: H1 checks its ARP cache for the Router's IP (192.168.1.1) to find its MAC address (11-11). (If missing, it sends an ARP request).

- Frame Encapsulation: H1 wraps the IP packet into a Layer 2 Ethernet frame:
    - Source MAC: AA-AA (H1)
    - Destination MAC: 11-11 (Router R1's incoming interface)

- Delivery: The frame is sent through the local switch to Router R1.

<b>Step 3: Router Processing & Routing Decision (Layer 3 Forwarding)</b>

- De-encapsulation: R1 receives the frame, sees its own MAC address (11-11), accepts it, and strips off the Layer 2 Ethernet header.

- Routing Table Lookup: R1 examines the inner Layer 3 packet's destination IP (192.168.2.50). It checks its routing table and finds that the 192.168.2.0 network is directly attached to its outbound interface (FastEthernet 0/2).

<b>Step 4: Router-to-H3 Delivery (Second Hop)</b>

- Address Resolution: R1 needs the physical MAC address of the final destination (192.168.2.50). It checks its own ARP cache and finds H3's MAC address (CC-CC).

- Re-encapsulation: R1 creates a brand-new Ethernet frame around the original packet:
    - Source MAC: 22-22 (Router R1's outbound interface Fa0/2)
    - Destination MAC: CC-CC (Destination Host H3)

- Delivery: R1 forwards the new frame out of interface Fa0/2. The local switch on that segment delivers it directly to H3.

<b>Step 5: Final Destination Processing (Target Host H3)</b>
- H3 receives the frame, verifies the destination MAC (CC-CC) matches its own NIC, and strips the Ethernet header.
- H3 verifies the destination IP (192.168.2.50) matches its own IP address and fully accepts the payload.

---

## Routing Table Entries
Routers move information between local and remote networks. To do this, routers must use routing tables to store information.

Routing tables are not concerned with the addresses of individual hosts. Routing tables contain the addresses of networks, and the best path to 
reach those networks. 

Entries can be made to the routing table in two ways: 
- Dynamically updated by information received from other routers in the network.
- Manually entered by a network administrator. 

Routers use the routing tables to determine which interface to use to forward a message to its intended destination.

If the router cannot determine where to forward a message, <b>it will drop it.</b>

## The Default Gateway
When a host needs to send a message to another host located on the <b>same network</b>, it will forward the message directly. A host will use ARP to discover the MAC address of the destination host. The IPv4 packet contains the destination IPv4 address and encapsulates the packet into a frame containing the MAC address of the destination and forwards it out.

When a host needs to send a message to a <b>remote network</b>, it must use the router. The host includes the IP address of the destination host within the packet just like before. However, when it encapsulates the packet into a frame, it uses the MAC address of the router as the destination for the frame. In this way, the router will receive and accept the frame based on the MAC address.

### How Source Hosts determine the MAC Address of the Router
A host is given the IPv4 address of the router through the default gateway address configured in its TCP/IP settings. 
-  The default gateway address is the address of the router interface connected to the same local network as the source host. 
- All hosts on the local network use the default gateway address to send messages to the router. 

When the host knows the default gateway IPv4 address, it can use ARP to determine the MAC address. The MAC address of the router is then placed in the frame, destined for another network.

Note: It is important that the correct default gateway be configured on each host on the local network. If no default gateway is configured in the host TCP/IP settings, or if the wrong default gateway is specified, messages addressed to hosts on remote networks <b>cannot be delivered.</b>

## Local Area Network
LAN refers to a local network, or a group of interconnected local networks that are under the same administrative control.

All the local networks within a LAN are under one administrative control. Other common characteristics of LANs are that they typically use Ethernet or wireless protocols, and they support high data rates.

The term intranet is often used to refer to a private LAN that belongs to an organization, and is designed to be accessible only by the members of the organization, employees, or others with authorization.
