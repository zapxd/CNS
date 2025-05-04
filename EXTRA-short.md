## MANJAR BOLE MYA VS RAAS PYALA YE MHATLA MAAI!!

# **Comprehensive Networking Notes**

## **ACLs (Access Control Lists)**
### **Wildcard Masks**
- **Function**: Inverse of subnet masks (0=exact match, 1=ignore bit)
- **Example**: 
  - To match 192.168.1.0/24: `0.0.0.255`
  - Single host: `0.0.0.0`

### **ACL Implementation**
```cisco
! Standard ACL (blocks source)
access-list 10 deny 192.168.1.5 0.0.0.0
access-list 10 permit any

! Extended ACL (blocks FTP)
access-list 110 deny tcp 192.168.1.0 0.0.0.255 any eq 21
access-list 110 permit ip any any
```

### **Placement Strategies**
- **Standard ACLs**: Near destination (no destination filtering)
- **Extended ACLs**: Near source (granular control)
- **Implicit Deny**: Always ends with `deny all` (add explicit permit!)

## **NAT Deep Dive**
### **Translation Types**
| Type | Description | Use Case | Command Example |
|------|-------------|----------|-----------------|
| **Static** | 1:1 fixed mapping | Servers | `ip nat inside source static 192.168.1.5 203.0.113.5` |
| **Dynamic** | Pool-based translation | Medium networks | `ip nat pool MYPOOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0` |
| **PAT** | Port-based overload | Home/SMB | `ip nat inside source list 1 interface Gig0/0 overload` |

### **NAT Troubleshooting**
```cisco
show ip nat translations
debug ip nat
clear ip nat translation *
```

## **Routing Protocols**
### **EIGRP vs OSPF**
| Feature | EIGRP | OSPF |
|---------|-------|------|
| **Type** | Advanced Distance Vector | Link-State |
| **Metric** | Composite (BW+Delay) | Cost (10^8/BW) |
| **Tables** | Neighbor/Topology/Routing | LSDB/Route |
| **Convergence** | Fast (DUAL) | Faster (Dijkstra) |

### **Key Configuration**
```cisco
! EIGRP
router eigrp 100
 network 192.168.1.0
 metric weights 0 1 0 1 0 0

! OSPF
router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 auto-cost reference-bandwidth 1000
```

## **Transport Layer Protocols**
### **TCP Reliability**
1. **3-Way Handshake**
   - SYN → 
   - SYN-ACK ← 
   - ACK →
2. **Flow Control**: Sliding window adjusts based on receiver capacity
3. **Error Recovery**: Selective ACKs (SACK) for packet loss

### **UDP Advantages**
- Lower latency (no handshake)
- Smaller header (8 bytes vs TCP's 20+)
- Ideal for: VoIP, DNS, streaming

## **Application Services**
### **FTP Operation Modes**
- **Active**: Server connects to client (PORT)
- **Passive**: Client connects to server (PASV)
- **Security**: Prefer SFTP (SSH) or FTPS (SSL)

### **HTTP/HTTPS**
- **HTTP Methods**: GET, POST, PUT, DELETE
- **HTTPS Setup**:
  ```cisco
  crypto key generate rsa
  ip http secure-server
  ```

## **Wireless Networking**
### **Security Evolution**
1. **WEP** (Broken): RC4 cipher, static keys
2. **WPA**: TKIP encryption (temporary fix)
3. **WPA2**: AES-CCMP (mandatory since 2006)
4. **WPA3**: SAE handshake, 192-bit encryption

### **Enterprise Setup**
```cisco
dot11 ssid CORPORATE
 authentication open 
 authentication key-management wpa2
 mbssid guest-mode
 wpa-psk ascii 7 MyStrongPassword
```

## **Socket Programming**
### **TCP Server Lifecycle**
```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('0.0.0.0', 8080))  # All interfaces
s.listen(5)  # Queue of 5 connections
while True:
    conn, addr = s.accept()  # Blocks here
    data = conn.recv(1024)
    conn.send(b"HTTP/1.1 200 OK\r\n\r\nHello")
    conn.close()
```

### **UDP Considerations**
- No connection state
- Must handle packet ordering/loss manually
- Common uses: DNS lookups, IoT sensors

## **Best Practices**
1. **ACLs**: 
   - Order rules from specific to general
   - Log denied packets: `deny ip any any log`
2. **NAT**: 
   - Use timeout tweaks for PAT: `ip nat translation timeout 300`
3. **Routing**: 
   - OSPF: Stub areas reduce LSA flooding
   - EIGRP: Offset lists for metric manipulation
4. **Security**:
   - Disable unused services: `no ip http server`
   - Use SSH: `transport input ssh`
