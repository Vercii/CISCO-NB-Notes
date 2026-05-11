# Module 8 - Internet Protocol

## IPv4 Address
A host needs an IPv4 address to participate on the internet. It is a logical network address that identifies a particular host.

It must be properly configured and unique in the world. 

An IPv4 address is assigned to the network interface connection for a host. This connection is usually a NIC installed in the device.

Every packet sent across the internet has a source and destination IPv4 address. This information is required by networking devices to ensure the information gets to the destination and any replies are returned to the source.

IPv4 addresses are 32 bits in length. Here is an IPv4 address in binary:
11010001101001011100100000000001

The 32 bits are grouped into four 8-bit bytes called octets like this:
11010001.10100101.11001000.00000001

We convert each octet into its decimal value, separated by a decimal point or period becoming this dotted-decimal representation:
209.165.200.1

---
A host with an IPv4 address 192.168.5.11 with a subnet mask of 255.255.255.0.
- Network portion: 192.168.5
- Host: 11

### IPv4 Address Structure
An IPv4 address is composed of a network and a host.

In a local network the network portion has to be the same, but the host portion has to be unique.
