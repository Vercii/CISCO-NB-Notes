# Creating a LAN
In this exercise, I setup a LAN connection between two PCs, one printer, and the server.
![Screenshot](/assets/14-logical.png)

## Connections
The connection configurations are as follows:
| Device | Interface/Port | Connected to Device | Connection Interface/Port |
| :--- | :--- | :--- | :--- |
| Office Router | G0/0 | ISP1 | G0/0 |
| Office Router | G0/1 | Switch | G0/1 |
| Admin PC | NIC (F/0) | Switch | F0/1 |
| Manager PC | NIC (F/0) | Switch | F0/2 |
| Printer | NIC (F/0) | Switch | F0/24 |

Interfaces designated with G are GigabitEthernet interfaces. Interfaces that are designated with F are FastEthernet interfaces.

Prior to the connections I made sure that every device is turned on. As for the switch, it automatically turned on after initiating connection.
![Screenshot](/assets/14-physical.png)

## IPv4 Configuration
For the two PCs, I was able to fetch the proper IP using DHCP. As for the printer, I had to manually set it up and based the IP from the addressing table provided.
![Screenshot](/assets/14-manual.png)

## Confirmation
All that's left to do is to confirm the connection of the devices. So from the Admin PC I pinged the Manager PC.
![Screenshot](/assets/14-ping.png)

On the desktop tab, I opened web browser and looked up the server based on its IP address as well.
![Screenshot](/assets/14-webbrowser.png)

## Results
![Screenshot](/assets/14-result.png)
