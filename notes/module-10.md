# Module 10 - IPv4 Issues

## IPv4 Exhaustion
IPv6 is designed to be the successor to IPv4. IPv6 has a larger 128-bit address space, providing 340 undecillion possible addresses.

The depletion of IPv4 address space has been the motivating factor for moving to IPv6. As Africa, Asia and other areas of the world become more connected to the internet, there are not enough IPv4 addresses to accommodate this growth.

IPv4 has a theoretical maximum of 4.3 billion addresses. Private addresses in combination with Network Address Translation (NAT) have been instrumental in slowing the depletion of IPv4 address space. However, NAT is problematic for many applications, creates latency, and has limitations that severely impede peer-to-peer communications.

## Coexistence
Both IPv4 and IPv6 will coexist in the near future and the transition will take several years. The IETF has created various protocols and tools to help network administrators migrate their networks to IPv6. The migration techniques can be divided into three categories:
- Dual Stack: Allows IPv4 and IPv6 to coexist on the same network segment. 
- Tunneling: a method of transporting an IPv6 packet over an IPv4 network. The IPv6 packet is encapsulated inside an IPv4 packet, similar to other types of data.
- Translation: Network Address Translation 64 (NAT64) allows IPv6-enabled devices to communicate with IPv4-enabled devices using a translation technique similar to NAT for IPv4. An IPv6 packet is translated to an IPv4 packet and an IPv4 packet is translated to an IPv6 packet.

Only dual stack uses native IPv6 connectivity.

<b>Tunneling and translation are for transitioning to native IPv6 and should only be used where needed. The goal should be native IPv6 communications from source to destination.</b>

## Hexadecimal Number System
IPv6 uses these 16 digits represented as hextets, making them presentable in a readable format:

0 1 2 3 4 5 6 7 8 9 A B C D E F

### Rules in reducing the number of hexadecimal digits

Original address: 0db8:acad:a088:0000:0000:7000:0123

- Omit Leading 0s: Leading zeroes in any 16-bit segment (hextet) do not have to be written.
    - db8:acad:a088:0:0:7000:123
- Double Colon: Any single contiguous string of one or more 16-bit segments consisting of ALL zeroes (0000:0000) can be represented with a double colon. <b> This rule can only be used once in an address. Use it on the longest string in case of multiple contiguous 0 hextets.</b>
    - db8:acad:a088::7000:123
    
Applying both rules at once with the address <b>0db8:acad:000a:0000:0000:0000:0001</b>

would result into
<b>db8:acad:a::1</b>
