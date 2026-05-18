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
