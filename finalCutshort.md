# Application Layer

- **Purpose**: Enables user-network interaction via protocols for email, file transfer, web browsing.
- **Protocols**:
  - HTTP (HyperText Transfer Protocol)
  - FTP (File Transfer Protocol)
  - SMTP (Simple Mail Transfer Protocol)
  - POP3 (Post Office Protocol v3)
  - IMAP (Internet Message Access Protocol)
  - DNS (Domain Name System)
  - DHCP (Dynamic Host Configuration Protocol)
  - Telnet (Remote terminal access)

### Key Concepts:
- **DNS**: Resolves domain names to IP addresses hierarchically.
- **DHCP**: Automates IP assignment via DORA process (Discover-Offer-Request-Acknowledge).
- **Email Protocols**:
  - SMTP: Sends emails (client→server or server→server).
  - POP3: Retrieves emails (downloads to client, deletes from server).
  - IMAP: Syncs emails across devices (retains on server).
- **MIME**: Extends email to support multimedia attachments.
- **FTP**: Transfers files (Port 21 control, Port 20 data).
- **TFTP**: Simplified FTP (UDP port 69, no auth).
- **HTTP**: Stateless web protocol over TCP (3-way handshake).
- **TCP vs UDP**:
  - TCP: Reliable, connection-oriented (e.g., phone call).
  - UDP: Fast, connectionless (e.g., letter).
- **URL Components**: Scheme (http/https), domain, port, path, query.
- **Stateful vs Stateless**: Stateful remembers client data; stateless treats each request independently.

---

# Network Layer

- **Functions**: Routing, forwarding, logical addressing (IP), fragmentation, congestion control.
- **Devices**: Routers operate here.
- **Routing Protocols**:
  - RIP: Hop count (max 15), distance-vector.
  - OSPF: Link-state, cost based on bandwidth.
  - EIGRP: Hybrid (bandwidth + delay), Cisco proprietary.
- **Key Terms**:
  - **Virtual Circuit**: Pre-established path (e.g., ATM).
  - **Datagram Network**: Independent packet routing (e.g., IP).
  - **Static Routing**: Manual paths.
  - **Dynamic Routing**: Auto-updates (e.g., OSPF).
  - **NAT**: Maps private IPs to public (Static/Dynamic/PAT).
- **IP Classes**:
  - Class A: 1.0.0.0–126.0.0.0 (large networks).
  - Class B: 128.0.0.0–191.255.0.0 (medium).
  - Class C: 192.0.0.0–223.255.255.0 (small).
- **Subnet Mask**: Identifies network vs host bits (e.g., 255.255.255.0).
- **Loopback Address**: 127.0.0.1 (self-testing).

---

# Transport Layer

- **Purpose**: End-to-end communication (reliable/unreliable).
- **Protocols**:
  - TCP: Connection-oriented, reliable (e.g., HTTP).
  - UDP: Connectionless, fast (e.g., streaming).
- **Ports**: Logical endpoints (0–65535).
- **Socket**: IP + Port + Protocol (TCP/UDP). Full-duplex in TCP.
- **Flow Control**:
  - **Sliding Window**: Multiple frames sent before ACK.
  - **Stop-and-Wait**: One frame at a time.
- **Error Handling**:
  - **Go-Back-N**: Retransmits all frames after error.
  - **Selective Repeat**: Retransmits only failed frames.

---

# Data Link Layer

- **Functions**: Framing, error detection, flow control, MAC addressing.
- **Protocols**:
  - **HDLC**: Bit-oriented, point-to-point/multipoint.
  - **PPP**: Serial links (auth/encryption, e.g., dial-up).
- **Framing Methods**: Byte stuffing, bit stuffing.

---

# Router Configuration & Protocols

- **Packet Tracer**: Simulates networks (copper straight-through cables).
- **CLI Commands**:
  - `enable`: Privileged mode.
  - `configure terminal`: Global config.
  - `ip address <IP> <mask>`: Assigns IP to interface.
  - `no shutdown`: Activates interface.
- **RIP**:
  - Distance-vector, max 15 hops, UDP port 520.
  - Config: `router rip` + `network <IP>`.
- **ACLs**:
  - **Standard**: Filters by source IP (1–99, 1300–1999).
  - **Extended**: Filters by src/dest IP + port (100–199, 2000–2699).
  - Wildcard mask: 0=exact, 1=ignore (e.g., 0.0.0.255 for a /24 subnet).
  - `ip access-group`: Applies ACL to interface.

---

# NAT (Network Address Translation)

- **Types**:
  - **Static NAT**: 1-to-1 private-public mapping.
  - **Dynamic NAT**: Pool of public IPs.
  - **PAT (Overload)**: Many-to-1 with port mapping.
- **Commands**:
  - `ip nat inside source static`: Static NAT.
  - `ip nat inside source list <ACL> interface <intf> overload`: PAT.
- **Advantages**: Saves IPs, adds security.
- **Disadvantages**: Delays, breaks some protocols (e.g., IPsec).

---

# Advanced Routing (EIGRP/OSPF)

- **EIGRP**:
  - Hybrid protocol (Cisco).
  - Tables: Neighbor, Topology, Routing.
  - Metric: Bandwidth + delay (default K1=1, K3=1).
  - Multicast: 224.0.0.10.
- **OSPF**:
  - Link-state, AD=110.
  - Cost = 100 Mbps / Interface BW.
  - Areas must connect to Area 0 (backbone).
  - Multicast: 224.0.0.5 (all), 224.0.0.6 (DR/BDR).

---

# Wireless & DHCP

- **DHCP Setup**: Enable in router GUI, set IP pool.
- **WLAN Security**: WPA/WPA2 + pre-shared key.
- **Static IP on PC**: Manually assign IP/gateway.

---

# Socket Programming (Python)

- **TCP Socket**:
  - `socket(AF_INET, SOCK_STREAM)`.
  - Methods: `bind()`, `listen()`, `accept()`, `send()`, `recv()`.
- **UDP Socket**:
  - `socket(AF_INET, SOCK_DGRAM)`.
  - Methods: `sendto()`, `recvfrom()`.

---

# FTP & Web Servers

- **FTP Commands**:
  - `put`: Upload.
  - `get`: Download.
  - `cd`: Change directory.
- **Web Server**:
  - Hosts HTML (Port 80/443).
  - Access via `http://<IP>` in browser.
