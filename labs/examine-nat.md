# Examining NAT on a Wireless Router

## Setup
In this exercise I learned how to examine NAT on a wireless router, as well as to simulate a routing situation.

I added 4 PCs and connected them to the wireless router with a copper straight-through cable, then I configured each and every one of them to be connected via DHCP.

![Screenshot](/assets/12-logical.png)

After that, I went to the Web Browser of PC0 and entered the IP Address to inspect the Status. Here I was able to see information such as:
- Router Information
- Internet Connection
- Local Network Information
- DHCP Information
 
![Screenshot](/assets/12-status.png)
![Screenshot](/assets/12-status2.png)

Then, in the simulation panel I opened the filter and selected HTTP, and TCP under the Misc section.
![Screenshot](/assets/12-filter.png)

## PDU Creation
I clicked the Create PDU icon and selected PC0, I configured the settings as shown in the image below.
![Screenshot](/assets/12-creatpdu.png)

I ran the simulation, and took note of the events on the event list inside the simulation panel on the right side of the screen. From PC0 the packet was sent to the Wireless Router then to the switch, and finally reaching the server. After a short while, the packet was sent back to PC0.
![Screenshot](/assets/12-panel.png)

I also inspected both the inbound and outbound PDU Details.
![Screenshot](/assets/12-inbound.png)
![Screenshot](/assets/12-outbound.png)

---

### Result
![Screenshot](/assets/12-result.png)
