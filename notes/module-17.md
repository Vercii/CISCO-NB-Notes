# Module 17 - Network Testing Utilities
A number of software utility programs are available that can help identify network problems. Most of these utilities are provided by the operating system as command line interface (CLI) commands. The syntax for the commands may vary between operating systems.

Some of the available utilities include:

- ipconfig - Displays IP configuration information.
- ping - Tests connections to other IP hosts.
- netstat - Displays network connections.
- tracert - Displays the route taken to the destination.
- nslookup - Directly queries the name server for information on a destination domain.

## The "ipconfig" Command
When a device does not get an IP address, or has an incorrect IP configuration, it cannot communicate on the network or access the internet. On Windows devices, you can view the IP configuration information with the ipconfig command at the command prompt. The ipconfig command has several options that are helpful including /all, /release, and /renew.

## The "ping" Command
Most IP enabled devices support some form of the ping command in order to test whether or not network devices are reachable through the IP network.

If the IP configuration appears to be correctly configured on the local host, next, test network connectivity by using ping. The ping command can be followed by either an IP address or the name of a destination host. In the example, the user pings the default gateway at 10.10.10.1 and then pings ww​w.cisco.com.

---

### Ping Results
If ping commands to both the name and IP address are successful, but the user is still unable to access the application, then the problem most likely resides in the application on the destination host. For example, it may be that the requested service is not running.

If neither ping is successful, then network connectivity along the path to the destination is most likely the problem. If this occurs, it is common practice to ping the default gateway. If the ping to the default gateway is successful, the problem is not local. If the ping to the default gateway fails, the problem resides on the local network.

In some cases, the ping may fail but network connectivity is not the problem. A ping may fail due to the firewall on the sending or receiving device, or a router along the path that is blocking the pings.

The basic ping command usually issues four echoes and waits for the replies to each one. It can, however, be modified to increase its usefulness. The options listed in the figure display additional features available.
