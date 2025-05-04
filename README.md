## Application Layer - Samajne Wale ko ishara cofee haii!! aa meri jaann!!!

**1. What is the job of Application Layer?**  
The Application Layer enables user interaction with the network by providing protocols and services to applications like email, file transfer, and web browsing.

---

**2. Which protocol is used at Application Layer?**  
Protocols include HTTP, FTP, SMTP, POP3, IMAP, DNS, DHCP, Telnet, etc.
HTTP – HyperText Transfer Protocol
FTP – File Transfer Protocol
SMTP – Simple Mail Transfer Protocol
POP3 – Post Office Protocol version 3
IMAP – Internet Message Access Protocol
DNS – Domain Name System
DHCP – Dynamic Host Configuration Protocol
---

**3. What is DNS? How it works?**  
DNS (Domain Name System) resolves human-readable domain names into IP addresses using a hierarchical system of name servers.

---

**4. What is DHCP? How it works?**  
DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses to devices on a network through a discover-offer-request-acknowledge (DORA) process.

---

**5. What protocols are used in email?**  
SMTP (sending), POP3/IMAP (retrieving).

---

**6. Where to use SMTP protocol?**  
SMTP is used to send emails from clients to servers and between servers.

---

**7. Where to use POP protocol?**  
POP is used by email clients to retrieve messages from the server and usually download them for offline use.

---

**8. What is MIME and where is it used?**  
MIME (Multipurpose Internet Mail Extensions) allows emails to include multimedia content like images, audio, and attachments.

---

**9. What is the difference between POP and IMAP?**  
POP downloads emails and typically deletes them from the server; IMAP synchronizes emails across multiple devices and retains them on the server.

---

**10. Give the detailed sequence of events when we click on SEND button?**  
Email client formats message → Encodes with MIME → Contacts SMTP server → Authenticates → SMTP transmits message → Mail server stores/delivers → Recipient retrieves via POP/IMAP.

---

**11. What is FTP? Which port is used by FTP?**  
FTP (File Transfer Protocol) transfers files between client and server. It uses port 21 (control) and port 20 (data).

---

**12. What is TFTP? Which port is used by TFTP?**  
TFTP (Trivial FTP) is a simplified version of FTP without authentication, using UDP port 69.

---

**13. What is HTTP? Permanent connection, Three-way handshaking?**  
HTTP (HyperText Transfer Protocol) is stateless and used for web communication. It runs over TCP, which uses three-way handshaking to establish connections.

---

**14. Difference between TCP & UDP?**  
TCP is reliable, connection-oriented; UDP is faster, connectionless, and used for time-sensitive applications like streaming.

---

**15. What do you mean by connection-oriented & connectionless service & real world example?**  
Connection-oriented (e.g., TCP) ensures reliable delivery (like phone calls); connectionless (e.g., UDP) sends data without setup (like sending a letter).

---

**16. What is TELNET? Which port is used by TELNET?**  
Telnet allows remote terminal access to another device, using port 23.

---

**17. Difference between TELNET & SSH?**  
Telnet transmits data in plaintext; SSH is secure and encrypted.

---

**18. What is URL? What activities are carried out when we type URL and press ENTER?**  
URL (Uniform Resource Locator) specifies the address of a resource. When entered: DNS resolves the domain → TCP connection via HTTP/HTTPS → Request sent → Server responds with page data → Browser renders it.

---

**19. What information must we provide in a URL?**  
Scheme (http/https), domain name/IP, optional port, path, query, and fragment.

---

**20. What is difference between stateful and stateless server?**  
Stateful servers remember client data between requests; stateless servers treat each request independently.

---

**21. Which protocol is used when we access any web page?**  
HTTP or HTTPS is used, typically over TCP.

---

## Network Layer Questions and Answers

**RIP, OSPF, EIGRP Routing Protocols & Their Distance Metric**  
- **RIP (Routing Information Protocol):** Uses hop count as the metric. Maximum of 15 hops.  
- **OSPF (Open Shortest Path First):** Uses cost based on link bandwidth. A link with higher bandwidth has a lower cost.  
- **EIGRP (Enhanced Interior Gateway Routing Protocol):** Uses a composite metric based on bandwidth, delay, load, and reliability.

---

**22. List the activities of Network Layer.**  
- Routing of packets  
- Forwarding packets to the next hop  
- Logical addressing (assigning IP addresses)  
- Fragmentation and reassembly of packets  
- Congestion control

---

**23. What is routing?**  
Routing is the process of selecting the best path for data to travel from source to destination across networks.

---

**24. Which are the major two activities Network Layer Device has to carry out?**  
- Routing (path determination)  
- Forwarding (actual movement of packets)

---

**25. Which device works at network layer?**  
Routers operate at the network layer.

---

**26. What is difference between routing and forwarding?**  
- **Routing:** Determines the best path; occurs in control plane.  
- **Forwarding:** Moves packets based on routing table; occurs in data plane.

---

**27. What is virtual circuit network?**  
A network where a logical path is established before data transfer, resembling a dedicated connection (e.g., ATM).

---

**28. What is datagram network?**  
A network where each packet is routed independently, without a pre-established path (e.g., the Internet using IP).

---

**29. What is difference between virtual circuit and datagram network?**  
- **Virtual Circuit:** Connection-oriented, fixed path, guaranteed order.  
- **Datagram:** Connectionless, dynamic path, no guaranteed order.

---

**30. What is difference between static and dynamic routing? Which is better?**  
- **Static Routing:** Manually configured, simple but inflexible.  
- **Dynamic Routing:** Automatically adjusts using protocols like OSPF, RIP.  
Dynamic routing is better for large and scalable networks.

---

**31. What is adaptive routing?**  
Routing that changes paths based on current network conditions (e.g., congestion, link failure).

---

**32. What is non-adaptive routing?**  
Routing that does not adjust based on network conditions; uses fixed paths.

---

**33. How shortest path routing algorithm works?**  
It calculates the shortest (least-cost) path between nodes using algorithms like Dijkstra's or Bellman-Ford.

---

**34. What is flooding?**  
A routing technique where every incoming packet is sent out on every outgoing link except the one it arrived on.

---

**35. Explain distance vector routing.**  
Routers share their routing tables with neighbors periodically. Each router updates its table based on neighbors’ info. Example: RIP.

---

**36. Explain link state routing.**  
Routers share information about their direct links with all routers in the network. Each builds a complete map and calculates paths using Dijkstra’s algorithm. Example: OSPF.

---

**37. What is congestion? How to control congestion?**  
Congestion occurs when network traffic exceeds capacity. Controlled by traffic shaping, load balancing, congestion avoidance algorithms like RED, and increasing bandwidth.

---

**38. What is Jitter? How to control Jitter?**  
Jitter is the variation in packet arrival times. Controlled by buffering, traffic prioritization (QoS), and using stable paths.

---

**39. What is NAT? Why it is used? How it works?**  
NAT (Network Address Translation) maps private IPs to a public IP to allow Internet access. It modifies IP headers at the router.

---

**40. What is range of Class A/B/C?**  
- **Class A:** 1.0.0.0 – 126.0.0.0  
- **Class B:** 128.0.0.0 – 191.255.0.0  
- **Class C:** 192.0.0.0 – 223.255.255.0

---

**41. How to select class of the network?**  
Based on the number of hosts:  
- **Class A:** Large networks  
- **Class B:** Medium-sized networks  
- **Class C:** Small networks

---

**42. What is loopback address? What is mean by loopback address?**  
Loopback address (127.0.0.1) is used to test local network stack functionality. It refers to the host itself.

---

**43. What is subnet? What is subnet mask?**  
- **Subnet:** A logically segmented part of a network.  
- **Subnet Mask:** Identifies which part of the IP is network vs host (e.g., 255.255.255.0).

---

**44. Whether IP is connection-less or connection-oriented?**  
IP is a connectionless protocol; each packet is routed independently.

---


**45. Why transport layer is called End-to-End layer?**  
Because it provides direct communication between processes on the source and destination hosts, ensuring reliable data transfer end-to-end.

---

**46. What is job of Transport Layer?**  
To provide reliable or unreliable data transfer, flow control, error detection and correction, and segmentation and reassembly of data.

---

**47. What is port? Is port logical or physical? How many max. Ports we can use?**  
A port is a logical endpoint for communication used to identify specific processes. It's logical, and there are 65,536 (0–65535) ports.

---

**48. What is difference between TCP and UDP? Which is better?**  
TCP is connection-oriented and reliable; UDP is connectionless and faster. TCP is better for accuracy; UDP for speed and low overhead.

---

**49. What is socket?**  
A socket is an endpoint for sending or receiving data across a network, defined by an IP address and port number.

---

**50. What we need to create socket?**  
We need an IP address, a port number, and the protocol type (TCP or UDP).

---

**51. Whether socket we create from client to server is Full duplex?**  
Yes, TCP sockets support full-duplex communication, meaning data can be sent and received simultaneously.

---

**52. List the protocols used in transport layer.**  
TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).

---


**53. What is job of Data Link Layer?**  
It provides node-to-node data transfer, framing, error detection, flow control, and access control over a physical link.

---

**54. What is Framing? How it is done?**  
Framing is the process of dividing the data stream into manageable units (frames). It is done using methods like byte count, byte stuffing, bit stuffing, and physical layer coding violations.

---

**55. What is flow control? How it is done?**  
Flow control manages the rate of data transmission to prevent buffer overflow. It is done using protocols like Stop-and-Wait and Sliding Window.

---

**56. Explain sliding window protocol.**  
It allows multiple frames to be sent before needing an acknowledgment, maintaining a "window" of acceptable frame numbers to improve efficiency.

---

**57. Explain stop and wait protocol.**  
In this protocol, the sender transmits one frame and waits for an acknowledgment before sending the next. It's simple but inefficient for high-latency links.

---

**58. Explain Go-back-n protocol.**  
The sender can transmit several frames before needing an acknowledgment. If an error occurs, the receiver discards that frame and all subsequent ones; the sender must retransmit them.

---

**59. Explain selective repeat protocol.**  
Like Go-Back-N but more efficient. Only erroneous or lost frames are retransmitted, and the receiver stores out-of-order frames until all are received correctly.

---

**60. Explain HDLC protocol.**  
High-Level Data Link Control (HDLC) is a bit-oriented protocol that supports both point-to-point and multipoint configurations. It uses framing, flow control, and error detection.

---

**61. Explain PPP protocol.**  
Point-to-Point Protocol (PPP) is used to establish a direct connection between two nodes over serial links. It provides authentication, encryption, and compression.

---

**62. Where we can use PPP protocol?**  
PPP is commonly used for dial-up connections, DSL links, and VPNs over serial and point-to-point links.

---
