# Module 12 - Gateways to Other Networks

## Gateway
A way for traffic to leave one local network and be forwarded to other remote networks.

The default gateway configured on a device is the router interface that the traffic would come to first on its path to the internet.

---
### Routers as Gateways
- A router acts as a gateway that connects one network to other networks.
- Each router interface is connected to a different network.
- Hosts (devices) on a network must use the router to communicate with devices on other networks.
- Every host needs to know the IPv4 address of the router interface on its own network.
- This address is called the default gateway.
- The default gateway can be set in two ways:
    - Manually (static configuration)
    - Automatically (via DHCP)
- When a wireless router is configured as a DHCP server:
    - It automatically assigns IP settings to devices on the network
    - It also provides the correct default gateway address
- This allows devices to:
    - Send traffic to other networks
    - Access the internet through the ISP
- Most wireless routers are set as DHCP servers by default.

---
### Routers as Boundaries Between Networks
- A wireless router can act as a DHCP server for all local devices (hosts), whether they are connected via:
    - Ethernet cable
    - Wi-Fi
- These local devices are part of the internal (inside) network.
- DHCP servers on internal networks usually assign private IP addresses, not public ones.
    - This helps keep the internal network not directly accessible from the internet by default.
- The router’s local interface IP address is usually:
    - The first usable host address in the network
- Devices on the internal network must:
    - Use IP addresses in the same network as the router
    - Be configured either:
        - Manually (static IP), or
        - Automatically (via DHCP)
- When DHCP is enabled:
    - The router assigns IP addresses to devices
    - It also provides:
        - Subnet mask
        - Default gateway (its own interface IP address)
- Internet Service Providers (ISPs) also use DHCP:
    - They assign an IP address to the router’s internet-facing interface
    - This is part of the external (outside) network
- On the internet side:
    - The router acts as a DHCP client (it receives an IP address from the ISP)
    - The ISP usually assigns a public (internet-routable) IP address
- This public IP allows internal devices to access the internet through the router.
- The wireless router acts as a boundary between:
    - Internal (local) network
    - External (internet) network

<b> Hosts on the same network will use the same default gateway address, but will have different MAC and IP addresses.</b>

---
## Private Address
Private Addressing are addresses that can be used within an organization. You can assign them hosts, and they can be routed between different networks.

However, you need to have a <b>registered public IP address</b> when going outside of your organization.

Certain networks are reserved, available for use within your enterprise, <b> but they will not route across the internet.</b> Those addresses are:
- 192.168.0.0 (32 bits for the network portion, only 254 possible host address)
- 172.16.0.0 (Uses 16 bits for the network portion, allowing for more host address)
- 10.0.0.0 (Used for very large enterprises since it only uses 8 bits for the network portion)

We would have difficulty sending traffic out if we have a network addressed with private addressing. This is where NAT comes into play.

## Network Address Translation (NAT)
In NAT, a private addressed host can send traffic across the internet.
- The router performs a function that keeps a table, and <b>presents</b> it with a publicly registered address.
    - Example: 192.168.2.1 -> 200.100.58.50
    - Example: 192.168.1.15 -> 200.100.58.51
        - Different networks connecting to the same router that performs the function.
        - The same process happens when it needs to be translated back to the original address.
