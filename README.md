## Ex. No: 3  DHCP Configuration Using a Router
Date:21/10/26

________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>

<img width="1636" height="917" alt="Screenshot 2026-10-28 124718" src="https://github.com/user-attachments/assets/2510fc6c-bce4-4c20-a4bf-8c1124f6e433" />

________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
•	DHCP IP configuration shown in PC0 and PC1<br>
•	Router configuration screen<br>
•	Successful ping test between the two PCs<br>
________________________________________

CONFIGURATION

<img width="1637" height="921" alt="Screenshot 2026-10-28 124805" src="https://github.com/user-attachments/assets/ae241ce7-2d39-4a08-b4d8-3490b3d6d8a9" />

<img width="1632" height="921" alt="Screenshot 2026-10-28 124816" src="https://github.com/user-attachments/assets/53757b6d-46d3-4f1d-b120-82d22ba0fc1f" />

SWITCH 

<img width="1628" height="921" alt="Screenshot 2026-10-28 124831" src="https://github.com/user-attachments/assets/399242a2-7f99-4187-b023-a2c12ba3b92f" />

ROUTER

<img width="1640" height="916" alt="Screenshot 2026-10-28 124846" src="https://github.com/user-attachments/assets/4a7080e8-c347-4abf-8936-c5bf0fa1565c" />

Successful ping test between the two PCs

<img width="1620" height="925" alt="Screenshot 2026-10-28 124924" src="https://github.com/user-attachments/assets/668d53f3-7410-450d-92c6-770390e1618d" />

<img width="1641" height="922" alt="Screenshot 2026-10-28 124937" src="https://github.com/user-attachments/assets/77b3c930-e7fc-459a-8a10-b82b566abd6e" />

SWITCH CONFIG

<img width="1632" height="916" alt="Screenshot 2026-10-28 124900" src="https://github.com/user-attachments/assets/5b7c5243-5e93-4c2e-8ac9-6cf684bdd9cb" />

ROUTER CONFIG

<img width="1632" height="913" alt="Screenshot 2026-10-28 124912" src="https://github.com/user-attachments/assets/25dba98c-62c8-4ba3-a88c-a07cdf3da194" />


# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
