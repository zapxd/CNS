# **Chenglya bole kuhu**

# **Application Layer Deep Dive** 

### **Core Functions**
- **User Interface**: Provides network services directly to user applications
- **Protocol Implementation**: HTTP, FTP, SMTP, DNS, DHCP, etc.
- **Data Representation**: Handles encoding/decoding, encryption, compression

### **Key Protocols**
1. **DNS (Domain Name System)**
   - Hierarchical distributed database
   - Resolution process: Recursive → Root → TLD → Authoritative servers
   - Record types: A, AAAA, MX, CNAME, NS

2. **Email Protocols**
   - **SMTP** (Port 25/587):
     - Push protocol for sending mail
     - Uses MIME for attachments (extends ASCII format)
   - **POP3** (Port 110/995):
     - Simple download-and-delete model
     - No server-side folder synchronization
   - **IMAP** (Port 143/993):
     - Maintains server state
     - Supports multiple mailboxes and flags

3. **File Transfer**
   - **FTP** (Port 21 control, 20 data):
     - Two-channel operation (control + data)
     - Modes: Active (server initiates data), Passive (client initiates)
   - **TFTP** (UDP 69):
     - No authentication or directory listing
     - Used for network booting (PXE)

# **Network Layer In-Depth**

### **Routing Fundamentals**
- **Path Determination**:
  - Static: Manual routes (admin-configured)
  - Dynamic: RIP (distance-vector), OSPF (link-state), BGP (path-vector)
- **Packet Forwarding**:
  - Longest prefix match in routing tables
  - Process switching vs Fast switching

### **Protocol Details**
1. **OSPF (Open Shortest Path First)**
   - Link-state protocol (Dijkstra's algorithm)
   - Areas hierarchy (Backbone Area 0)
   - LSA flooding for topology updates

2. **NAT (Network Address Translation)**
   - Types: Static, Dynamic, PAT (Port Address Translation)
   - NAT Table maintains mappings (local IP:port ↔ public IP:port)

3. **IP Addressing**
   - Subnetting: VLSM (Variable Length Subnet Mask)
   - Supernetting: CIDR (Classless Inter-Domain Routing)
   - Special addresses: Loopback (127.0.0.0/8), APIPA (169.254.0.0/16)

# **Transport Layer Explained**

### **TCP vs UDP Comparison**
| Feature        | TCP                      | UDP                      |
|---------------|--------------------------|--------------------------|
| Reliability   | ACKs, retransmissions    | Best-effort delivery     |
| Ordering      | Sequence numbers         | No ordering              |
| Flow Control  | Sliding window           | None                     |
| Congestion    | AIMD (Additive Increase Multiplicative Decrease) | No control |
| Header Size   | 20-60 bytes              | 8 bytes                  |

### **Connection Management**
- **TCP 3-Way Handshake**:
  1. SYN → 
  2. SYN-ACK ← 
  3. ACK →
- **TCP Teardown**: FIN-ACK sequence

### **Port Ranges**
- Well-known: 0-1023 (HTTP 80, HTTPS 443)
- Registered: 1024-49151
- Dynamic: 49152-65535

# **Data Link Layer Essentials**

### **Frame Structure**
```
| Preamble | SFD | Dest MAC | Src MAC | Length | Payload | FCS |
```
- **FCS (Frame Check Sequence)**: CRC error detection

### **Ethernet Technologies**
- **MAC Addressing**: 48-bit (OUI + NIC)
- **Switching**:
  - Store-and-forward vs Cut-through
  - MAC learning/flooding/forwarding

### **WAN Protocols**
1. **PPP (Point-to-Point Protocol)**
   - LCP (Link Control Protocol): Establishes link
   - NCP (Network Control Protocol): IP assignment
   - Authentication: PAP, CHAP

2. **HDLC (High-Level Data Link Control)**
   - Bit-oriented synchronous protocol
   - Frame types: I-frames, S-frames, U-frames

# **Wireless Networking**

### **802.11 Standards**
| Standard | Freq  | Speed   | Range   |
|----------|-------|---------|---------|
| 802.11a | 5GHz  | 54Mbps  | Short   |
| 802.11g | 2.4GHz| 54Mbps  | Medium  |
| 802.11n | Dual  | 600Mbps | Long    |

### **Security Protocols**
- **WEP** (Broken, RC4 cipher)
- **WPA** (TKIP encryption)
- **WPA2** (CCMP/AES, 4-way handshake)
- **WPA3** (Simultaneous Authentication of Equals)
