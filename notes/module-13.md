# Module 13 - MAC and IP
There are two primary addresses assigned to a device on an Ethernet LAN:

- Physical address (the MAC address) – Used for NIC-to-NIC communications on the same Ethernet network.
- Logical address (the IP address) – Used to send the packet from the source device to the destination device. The destination IP address may be on the same IP network as the source, or it may be on a remote network.

Layer 2 physical addresses (i.e., Ethernet MAC addresses) are used to deliver the data link frame with the encapsulated IP packet from one NIC to another NIC that is on the same network. If the destination IP address is on the same network, the destination MAC address will be that of the destination device.

## Destination on Remote Network
When the destination IP address (IPv4 or IPv6) is on a remote network, the destination MAC address will be the address of the host default gateway (i.e., the router interface).

---

When sending a frame to another device on the same local network, the device sending the frame will use the MAC address of the destination device.

---

Address Resolution Protocol (ARP) is used to determine the device MAC address of a known destination device IPv4 address. Neighbor Discovery (ND) is used to determine the MAC address of a known destination device IPv6 address.

---

## Broadcast Domains
When a host sends a broadcast message, switches forward it to every device on the same local network (Local Area Network). Receiving hosts process this message as if it were sent directly to them.

Because of this behavior, a local network connected by switches is called a broadcast domain.

As more hosts join the network, broadcast traffic increases. If the network grows too large, this traffic can overwhelm the switches, degrading overall performance.

To maintain performance in a growing network, the single large local network must be divided into smaller networks. Routers are used to split the network into multiple, isolated broadcast domains.

## Access Layer Communication
Problem: A receiving NIC only accepts frames matching its own MAC address or the broadcast MAC address. If a sending host only knows the destination IP address, it cannot deliver the frame.

Solution (IPv4): The host uses ARP (Address Resolution Protocol) to broadcast a request into the local network, asking the device with that specific IP address to reply with its MAC address.

Solution (IPv6): The host uses Neighbor Discovery Protocol (NDP), which uses targeted multicast messages instead of broadcasts to achieve the same result.

## ARP
Uses a three step process to discover and store the MAC address of a host on the local network when only the IPv4 address of the host is known:

1. The sending host creates and sends a frame addressed to a broadcast MAC address. Contained in the frame is a message with the IPv4 address of the intended destination host.
2. Each host on the network receives the broadcast frame and compares the IPv4 address inside the message with its configured IPv4 address. The host with the matching IPv4 address sends its MAC address back to the original sending host.
3. The sending host receives the message and stores the MAC address and IPv4 address information in a table called an ARP table.

When the sending host has the MAC address of the destination host in its ARP table, it can send frames directly to the destination without doing an ARP request. Because ARP messages rely on broadcast frames to deliver the requests, all hosts in the local IPv4 network must be in the same broadcast domain.

The destination MAC address for an Ethernet broadcast is FFFF.FFFF.FFFF.
