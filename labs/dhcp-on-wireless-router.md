# DHCP on Wireless Router

## Setting Up
The first step was to place three generic PCs and connect them to the wireless router using straight-through cables.  
![Screenshot](/assets/11-logical.png)

Next, the IP configuration of each PC was set to DHCP so that the devices could automatically obtain IP addresses from the router.  
![Screenshot](/assets/11-ip.png)

Afterward, the router’s DHCP settings were configured through the web browser interface by manually changing the IP Address, Starting IP Address, and Maximum Number of Users.  
![Screenshot](/assets/11-webbrowser.png)

## Issue Encountered
The activity completion status did not initially reach 100%. After checking the assessment results, it was discovered that the IP address configuration of PC0 was incorrect.  
![Screenshot](/assets/11-mistake.png)

To resolve the issue, the network configuration of PC0 was refreshed by switching the IP configuration from **Static** back to **DHCP**.

## Result
After refreshing the configuration, the PCs successfully received the correct IP addresses from the router, and the activity was completed successfully.  
![Screenshot](/assets/11-result.png)
