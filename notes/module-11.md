# Module 11 - Static and Dynamic Addressing

### Static IPv4 Address Assignment
IPv4 addresses can be assigned either statistically or dynamically.

With a static assignment, the network administrator must manually configure the network information for a host. At a minimum, this includes the following:

- IP address - This identifies the host on the network.
- Subnet mask - This is used to identify the network on which the host is connected.
- Default gateway - This identifies the networking device that the host uses to access the internet or another remote network. 

### Uses of Static Addresses
- Useful for printers, servers, and other devices that need to be accessible to clients on the network.
- Can provide increased control of network resources, but it can be time consuming to enter the information on each host.
- When using static IPv4 addressing, it is important to maintain an accurate list of which IPv4 addresses are assigned to which devices. Additionally, these are permanent addresses and are not normally reused.

The one responsible for setting up the static address is the network administrator.

### Dynamic IPv4 Address Assignment
On local networks it is often the case that the user population changes frequently.  Rather than have the network administrator assign IPv4 addresses for each workstation, it is easier to have IPv4 addresses assigned automatically. This is done using a protocol known as Dynamic Host Configuration Protocol (DHCP).

### Uses of DHCP
- Generally the preferred method of assigning IPv4 addresses to hosts on large networks because it reduces the burden on network support staff and virtually eliminates entry errors.
- An address is not permanently assigned to a host but is only leased for a period of time. If the host is powered down or taken off the network, the address is returned to the pool for reuse. This is especially helpful with mobile users that come and go on a network.

## DHCP Servers
DHCP makes it possible for you to access the internet. Various types of devices can be DHCP servers as long as they are running DHCP service software. With most medium to large networks, the DHCP server is usually a local dedicated PC-based server.

With home networks, the DHCP server may be located at the ISP and a host on the home network receives its IPv4 configuration directly from the ISP.

## DHCPv4 Operation
A host system sends out a packet called DHCP Discovery which looks for a DHCP server. 

It contains the MAC address and the destined device. The device could be a server, wireless router, and all sorts of devices. 

When the DHCP Discover goes out, in a case of a broadcast, any DHCP Server attached to the network will hear that.

DHCP Server then responds with a <b>DHC Offer</b> which contains an IP Address that the host could use if it accepts it.

If the host accepts it, it sends a DHCP Request packet that states that it accepts it. The device will then take the information (IP Address, Subnet Mask, Default Gateway) and enter it into its IP address settings.

Once the server receives the DHCP Request, the server will send back a DHCP acknowledgement that will indicate to the host that the server is placing the IP address into its table associated with the MAC address that was sent from the host.
