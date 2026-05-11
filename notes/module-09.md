# Module 9 - IPv4, Unicast, Broadcast, and Multicast

## Unicast
IP Packet is destined to a single device. It goes from a single device to a single device.

A source IP Address can only be unicast, meaning the source can only come from a single device.

Unicast is a one-to-one communication.

## Broadcast
When a device sends out a packet, the switch floods out all the ports, except the incoming port. Received by every device on the network.

Broadcast means that every device will receive the IPv4 packet.

Broadcast is one-to-all communication.

<b> IPv4 uses broadcast packets. There are no broadcast packets for IPv6.</b>

## Multicast
Multicast is used for sending out packets from a single device to selected multiple devices. Only the members of the multicast group will process the sent packet.

## Types of IPv4 Addresses
Public:
- Globally routed between ISP routers.

Private:
- Introduced because of the depletion of IPv4 address space.
- Not unique, can be used internally within any network.
- Used by most organizations to assign IPv4 addresses to internal hosts.

<b> The long-term solution to IPv4 address depletion was IPv6. </b>

IP Addresses:
- <b>10.0.0.0 - 10.255.255.255:</b> For large internal networks.
- <b>172.16.0.0 - 172.31.255.255: For enterprise network. </b>
- <b>192.168.0.0 - 192.168.255.255: For home routers. </b>

### Routing
Private addresses are <b> not </b> globally routable.

Packets with a private address must be translated to a public address before forwarding the packet to an ISP.

Network Address Translation (NAT) is used to translate between private IPv4 and public IPv4 public addresses.

## Special Use IPv4 Addresses
There are certain addresses, such as the network address and broadcast address, that cannot be assigned to hosts. There are also special addresses that can be assigned to hosts, but with restrictions on how those hosts can interact within the network.

### Loopback Addresses
Loopback addresses (127.0.0.0 /8 or 127.0.0.1 to 127.255.255.254) are more commonly identified as only 127.0.0.1. These are special addresses used by a host to direct traffic to itself. 

For example, the ping command is commonly used to test connections to other hosts. But you can also use the ping command to test if the IP configuration on your own device.

### Link-Local Addresses
Link-local addresses (169.254.0.0 /16 or 169.254.0.1 to 169.254.255.254) are more commonly known as the Automatic Private IP Addressing (APIPA) addresses or self-assigned addresses.

They are used by a Windows client to self-configure in the event that the client cannot obtain an IP addressing through other methods. Link-local addresses can be used in a peer-to-peer connection but are not commonly used for this purpose.

### Experimental Addresses
Experimental IP addresses, often called Class E addresses, are a reserved range from 240.0.0.0 to 255.255.255.254 (or 240.0.0.0/4).

## Legacy Classful Addressing
In 1981, IPv4 addresses were assigned using classful addressing as defined in RFC 790 Assigned Numbers.
- Class A (0.0.0.0/8 to 127.0.0.0/8): Extremely large networks with more than 16 million host addresses.
- Class B (128.0.0.0/16 to 191.255.0.0/16): Moderate to large size networks with up to approximately 65,000 host addresses.
- Class C (192.0.0.0 /24 to 223.255.255.0 /24): Small networks with a maximum of 254 hosts.

