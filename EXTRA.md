Router Configuration & RIP  
63. What is the purpose of using Packet Tracer in router configuration?  
- Packet Tracer is a network simulation tool used to design, configure, and simulate network topologies, making it easier to test router and network configurations without needing actual physical hardware.  
---  

64. Which cable is used to connect PCs with routers in Packet Tracer?  
- A copper straight-through cable is typically used to connect PCs to routers in Packet Tracer.  
---  

65. What is the function of the no shutdown command in router configuration?  
- The `no shutdown` command is used to enable or activate the router interface. By default, router interfaces are in a shutdown state, and the `no shutdown` command turns them on.  
---  

66. What is the use of the enable and configure terminal commands in Cisco CLI?  
- The `enable` command enters privileged EXEC mode, giving the user access to configuration commands. The `configure terminal` command enters global configuration mode, where the router’s settings can be modified.  
---  

67. How do you assign an IP address to a router interface in CLI?  
- Use the following commands in global configuration mode:  
  `interface <interface_name>`  
  `ip address <IP_address> <subnet_mask>`  
  `no shutdown`  
---  

68. How can you verify connectivity between two PCs in Packet Tracer?  
- Use the `ping` command from one PC to the other to verify network connectivity. If the ping is successful, the connection is valid.  
---  

69. What is RIP? Why is RIP called a distance-vector routing protocol?  
- RIP (Routing Information Protocol) is a distance-vector routing protocol that uses hop count as the metric to determine the best path to a destination. It is called a distance-vector protocol because it shares the entire routing table with neighbors, which contains distances (metrics) and directions (vectors).  
---  

70. What is hop count in RIP? What is the maximum hop count allowed?  
- Hop count in RIP represents the number of routers a packet must pass through to reach its destination. The maximum allowed hop count in RIP is 15; any path with a hop count of 16 or more is considered unreachable.  
---  

71. On which port number does RIP operate?  
- RIP operates on UDP port number 520.  
---  

72. How do you configure RIP on a router? List the commands.  
- To configure RIP, follow these steps:  
  `router rip`  
  `network <network_address>`  
  `Ctrl+Z`  
---  

73. What is the significance of the command network under RIP configuration?  
- The `network` command specifies the network addresses that RIP will advertise. It tells the router which interfaces belong to RIP and which routes to include in the routing table.  
---  

74. What is the administrative distance (AD) of RIP?  
- The administrative distance of RIP is 120, which represents its trustworthiness compared to other routing protocols (a lower AD indicates higher trust).  
---  

Access Control Lists (ACLs)  
75. What is an Access Control List (ACL) and why is it used?  
- An ACL is a set of rules used to filter network traffic based on specific criteria, such as IP address, protocol, or port number. It is used to control access to network resources and secure the network by permitting or denying traffic.  
---  

76. What is the difference between Standard and Extended ACL?  
- Standard ACLs filter traffic based only on the source IP address, while Extended ACLs can filter based on both source and destination IP addresses, as well as protocols and port numbers.  
---  

77. Which IP address field(s) are used in Standard ACL?  
- Standard ACLs use only the source IP address to filter traffic.  
---  

78. What is the range of numbers used for Standard and Extended ACLs?  
- Standard ACLs use numbers in the range of 1-99 and 1300-1999. Extended ACLs use numbers in the range of 100-199 and 2000-2699.  
---  

79. What is the wildcard mask and how is it used in ACLs?  
- A wildcard mask is a 32-bit mask used to specify a range of IP addresses in ACLs. It is used to identify which bits of the IP address should be matched and which can vary.  
---  

80. What does the command ip access-group do?  
- The `ip access-group` command applies an ACL to an interface, either for incoming (inbound) or outgoing (outbound) traffic.  
---  

81. Where should Standard and Extended ACLs be placed: close to source or destination?  
- Standard ACLs are generally applied close to the destination network, while Extended ACLs are typically applied close to the source network to filter traffic early.  
---  

82. What is the command to deny a specific IP address in a standard ACL?  
- The command to deny a specific IP address in a standard ACL is:  
  `access-list <ACL_number> deny <IP_address> <wildcard_mask>`  
---  

83. How do you block FTP traffic from a source to destination using extended ACL?  
- The command to block FTP traffic is:  
  `access-list <ACL_number> deny tcp <source_IP> <wildcard_mask> <destination_IP> <wildcard_mask> eq 21`  
---  

84. What port number is used for Telnet?  
- Telnet uses port number 23.  
---  

85. What does the command permit ip any any do in an ACL configuration?  
- The command `permit ip any any` allows all IP traffic to pass through the ACL, regardless of source or destination IP address.  
---  

86. What happens if you forget to add a final permit rule in an ACL?  
- If a final permit rule is not added, the implicit deny rule at the end of the ACL will block any traffic that doesn’t match any of the rules, potentially causing unintended connectivity issues.  
---

1. **What is NAT (Network Address Translation)?**  
   NAT is the process of translating private IP addresses to public IP addresses to provide internet access for devices in a local network.  
   ---

2. **What are the types of NAT?**  
   The three types of NAT are:  
   - Static NAT  
   - Dynamic NAT  
   - Port Address Translation (PAT)  
   ---

3. **What is Static NAT?**  
   Static NAT maps a private IP address to a specific public IP address on a one-to-one basis. It is used when a fixed public address is needed for specific devices like web servers.  
   ---

4. **What is Dynamic NAT?**  
   Dynamic NAT uses a pool of public IP addresses and translates private IP addresses to an available public IP address from the pool. If the pool is exhausted, the packet is dropped.  
   ---

5. **What is Port Address Translation (PAT)?**  
   PAT allows multiple private IP addresses to be mapped to a single public IP address using different port numbers to distinguish the traffic. This is commonly known as NAT overload.  
   ---

6. **How does Static NAT work?**  
   Static NAT works by manually mapping a private IP address to a public IP address using the command `ip nat inside source static [private-address] [public-address]`.  
   ---

7. **How does Dynamic NAT work?**  
   Dynamic NAT works by creating a NAT pool of public IP addresses and using access control lists (ACLs) to specify which private IP addresses can be translated.  
   ---

8. **What is the purpose of ACL in Dynamic NAT?**  
   ACL (Access Control List) is used to specify which private IP addresses are eligible for NAT translation to public IP addresses from the NAT pool.  
   ---

9. **How does PAT differ from Dynamic NAT?**  
   PAT allows many private IP addresses to be mapped to a single public IP address by using different port numbers, while Dynamic NAT maps each private IP to a unique public IP from a pool.  
   ---

10. **What is the command to configure NAT overload (PAT)?**  
    The command to configure NAT overload (PAT) is `ip nat inside source list [ACL-number] interface [interface-name] overload`.  
    ---

11. **How do you configure NAT on router interfaces?**  
    Use the commands `ip nat inside` on the inside interface and `ip nat outside` on the outside interface to configure NAT.  
    ---

12. **What happens when a NAT table runs out of public IP addresses?**  
    If the NAT table runs out of public IP addresses, the packet is dropped, and an ICMP host unreachable message is sent to the source.  
    ---

13. **What is the advantage of using NAT?**  
    NAT conserves IP addresses, provides privacy, and eliminates the need for address renumbering when a network evolves.  
    ---

14. **What is a disadvantage of using NAT?**  
    NAT can introduce switching path delays, complicate tunneling protocols like IPsec, and affect some applications.  
    ---

15. **How does NAT protect the network?**  
    NAT hides the private IP addresses of devices on the network and only exposes the public IP address, providing a layer of security by preventing unauthorized access.  
    ---


1. What is EIGRP and what are its key characteristics?  
- Enhanced Interior Gateway Routing Protocol (EIGRP) is a hybrid routing protocol combining distance-vector and link-state features. It uses bandwidth, delay, reliability, and load for metric calculation.  

---

2. What are the neighbor requirements for EIGRP?  
- Same Autonomous System Number (ASN).  
- Matching K-values for metric calculation.  

---

3. How is EIGRP metric calculated?  
- Default uses bandwidth and delay (K1=1, K3=1). Formula:  
  Metric = 256*(K1*Bandwidth + K3*Delay).  

---

4. What are the three tables used by EIGRP?  
- Neighbor table: Stores neighbor information.  
- Topology table: Stores all learned routes.  
- Routing table: Stores best paths.  

---

5. What is the multicast address for EIGRP hello packets?  
- 224.0.0.10.  

---

6. What is OSPF and its administrative distance?  
- Open Shortest Path First is a link-state routing protocol with an AD of 110.  

---

7. What are OSPF neighbor requirements?  
- Same Area ID.  
- Matching hello/dead timers.  
- Authentication (if configured).  

---

8. How is OSPF cost calculated?  
- Cost = Reference Bandwidth (100 Mbps) / Interface Bandwidth.  

---

9. What multicast addresses does OSPF use?  
- 224.0.0.5 (All OSPF routers).  
- 224.0.0.6 (DR/BDR routers).  

---

10. What is the backbone area in OSPF?  
- Area 0, which all other areas must connect to.  

---

11. How to enable DHCP on a wireless router in Packet Tracer?  
- Access router GUI -> Setup -> Enable DHCP -> Set pool range -> Save.  

---

12. What is the default wireless router GUI login?  
- Username: `admin`, Password: `admin`.  

---

13. How to secure a WLAN in Packet Tracer?  
- Set SSID -> Enable WPA/WPA2 -> Configure pre-shared key.  

---

14. What is the purpose of the "maximum users" setting in DHCP?  
- Limits the number of IP addresses leased from the pool.  

---

15. How to configure static IP addressing on a PC in Packet Tracer?  
- PC -> Desktop -> IP Configuration -> Static -> Enter IP/Gateway.  

---


1. What is socket programming in Python?  
- Socket programming is a way to connect two nodes on a network to communicate using sockets (endpoints for bidirectional communication).  

---

2. What are the key differences between TCP and UDP sockets?  
- TCP (SOCK_STREAM): Connection-oriented, reliable, uses `connect()`, `send()`, `recv()`.  
- UDP (SOCK_DGRAM): Connectionless, unreliable, uses `sendto()`, `recvfrom()`.  

---

3. What parameters are used to create a socket in Python?  
- `socket.socket(socket_family, socket_type)`  
  Example: `s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`  

---

4. List the essential methods for a TCP server socket.  
- `bind()`: Binds to IP/port.  
- `listen()`: Starts TCP listener.  
- `accept()`: Accepts client connection.  
- `close()`: Closes socket.  

---

5. How does a TCP client connect to a server?  
- Uses `connect((host, port))` followed by `send()`/`recv()`.  

---

6. What is the purpose of `bind()` in socket programming?  
- Associates the socket with a specific IP address and port number.  

---

7. How does UDP communication differ from TCP in code?  
- UDP uses `sendto()` and `recvfrom()` instead of `send()`/`recv()`. No `listen()`/`accept()` needed.  

---

8. What is FTP and its primary use?  
- File Transfer Protocol (FTP) is used to transfer files between client and server over a network.  

---

9. How to configure an FTP server in Packet Tracer?  
- Enable FTP service on the server -> Create user with R/W permissions -> Use `ftp <server_ip>` from client.  

---

10. What are common FTP commands used in Packet Tracer?  
- `put`: Upload file.  
- `get`: Download file.  
- `delete`: Remove file.  
- `cd`: Change directory.  

---

11. How to upload a file via FTP in Packet Tracer?  
- From client: `ftp <server_ip>` -> `put filename.txt`.  

---

12. What is a web server's role in networking?  
- Hosts and delivers web pages/content to clients via HTTP/HTTPS protocols.  

---

13. How to host a custom webpage in Packet Tracer?  
- Server -> Services -> HTTP -> Edit `index.html` or create new HTML files.  

---

14. What is the default HTTP port?  
- Port 80 (unencrypted) or 443 (HTTPS).  

---

15. How to access a web server from a client in Packet Tracer?  
- Client -> Web Browser -> Enter server IP (e.g., `http://192.168.1.1`).  

---

