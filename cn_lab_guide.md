# Computer Networks (CL3001) - Complete Labs Revision Guide
## Fall 2026 | FAST-NUCES
 
---
 
## Table of Contents
1. [Lab 01: Networking Fundamentals](#lab-01-networking-fundamentals)
2. [Lab 02: Cisco Packet Tracer](#lab-02-cisco-packet-tracer)
3. [Lab 03: Socket Programming](#lab-03-socket-programming)
4. [Lab 04: HTTP/HTTPS, DNS, Routers](#lab-04-httphttps-dns-routers)
5. [Lab 05: Email, FTP, Wireshark](#lab-05-email-ftp-wireshark)
6. [Lab 06: Telnet and SSH](#lab-06-telnet-and-ssh)
7. [Quick Reference Tables](#quick-reference-tables)
8. [Key Formulas & Calculations](#key-formulas--calculations)
9. [Common Exam Questions](#common-exam-questions)
---
 
# Lab 01: Networking Fundamentals
 
## 1.1 Network Types
 
### LAN (Local Area Network)
- **Range:** Small area (single building/office)
- **Speed:** 10 Mbps - 1 Gbps
- **Examples:** Office networks, home networks
- **Devices:** PCs, printers, servers in one location
### MAN (Metropolitan Area Network)
- **Range:** City-wide or campus-wide
- **Speed:** Moderate speed
- **Examples:** Multiple office buildings in a city
- **Devices:** Connected through routers and switches
### WAN (Wide Area Network)
- **Range:** Geographically dispersed (continents)
- **Speed:** Lower than LAN/MAN
- **Examples:** Internet, international corporate networks
- **Connection:** Via ISP, leased lines, satellite
---
 
## 1.2 Network Topologies
 
| Topology | Description | Advantages | Disadvantages |
|----------|-------------|-----------|-----------------|
| **Bus** | All devices on single cable | Simple, cheap | Single failure breaks network |
| **Star** | Devices connect to central hub/switch | Easy to manage, isolates failures | Central device failure breaks network |
| **Ring** | Devices form a ring | Good bandwidth sharing | One failure breaks network |
| **Mesh** | Every device connected to every other | Highly redundant, reliable | Expensive, complex |
| **Tree** | Hierarchical arrangement | Good for large networks | Complex, expensive |
 
---
 
## 1.3 RJ45 Connector & Cable Types
 
### T568A Wiring Order (Straight Cable)
```
1. White-Green
2. Green
3. White-Orange
4. Blue
5. White-Blue
6. Orange
7. White-Brown
8. Brown
```
 
### T568B Wiring Order
```
1. White-Orange
2. Orange
3. White-Green
4. Blue
5. White-Blue
6. Green
7. White-Brown
8. Brown
```
 
### Straight Cable
- **Usage:** Connect DIFFERENT device types
  - Computer ↔ Switch/Hub normal port
  - Computer ↔ Modem
  - Router WAN ↔ Modem
- **Wiring:** Both ends use SAME standard (568A-568A OR 568B-568B)
### Crossover Cable
- **Usage:** Connect SAME device types
  - Computer ↔ Computer (directly)
  - Router LAN ↔ Switch normal port
  - Hub ↔ Switch normal ports
- **Wiring:** One end 568A, other end 568B
- **Note:** Modern devices support Auto MDI-X (automatic detection)
---
 
## 1.4 Network Terminologies
 
| Term | Definition |
|------|-----------|
| **NIC** | Network Interface Card - hardware interface from host to network |
| **MAC Address** | Medium Access Control - physical address (00:C0:9F:9B:D5:46) |
| **Hub** | Broadcasts data to all ports (no intelligence) |
| **Switch** | Sends data only to destination port (intelligent) |
| **Router** | Layer 3 device - determines path outside network |
| **IP Address** | Logical address (e.g., 192.168.0.1) |
| **Port Address** | Application identification (65,535 ports per host) |
| **Gateway** | Router address connecting network to other networks/Internet |
| **Domain Name** | Human-readable name mapped to IP (www.google.com) |
| **DNS Server** | Converts domain names to IP addresses |
| **DHCP** | Assigns IP addresses dynamically |
 
---
 
## 1.5 OSI Model (7 Layers)
 
### Layer Breakdown
 
| # | Name | Function | Devices | Data Unit |
|---|------|----------|---------|-----------|
| 7 | **Application** | User applications, services | PC, Server | Data |
| 6 | **Presentation** | Encryption, compression, formatting | - | Data |
| 5 | **Session** | Connection management | - | Data |
| 4 | **Transport** | End-to-end communication (TCP/UDP) | - | Segment |
| 3 | **Network** | Routing, IP addressing | Router | Packet |
| 2 | **Data Link** | MAC addressing, switching | Switch, Bridge | Frame |
| 1 | **Physical** | Physical transmission, cables | Hub | Bit |
 
### Key Points
- **Peer-to-Peer Protocol:** Same layer communicates with same layer on other device
- **Encapsulation:** Each layer adds its own header
- **De-capsulation:** Each layer removes its header on receiving end
---
 
## 1.6 IP Address Classes
 
### IPv4 Address Classes
 
| Class | Range | Leading Bits | Network Bits | Host Bits | Subnet Mask |
|-------|-------|--------------|--------------|-----------|-------------|
| **A** | 0-127 | 0 | 8 | 24 | 255.0.0.0 |
| **B** | 128-191 | 10 | 16 | 16 | 255.255.0.0 |
| **C** | 192-223 | 110 | 24 | 8 | 255.255.255.0 |
| **D** | 224-239 | 1110 | Reserved for multicast | - |
| **E** | 240-255 | 1111 | Reserved for experimental | - |
 
### Private Address Spaces (RFC 1918)
 
```
Class A:  10.0.0.0 to 10.255.255.255
Class B:  172.16.0.0 to 172.31.255.255
Class C:  192.168.0.0 to 192.168.255.255
```
 
### Special Addresses
- **127.0.0.1:** Loopback (localhost)
- **0.0.0.0:** Default network
- **255.255.255.255:** Broadcast
---
 
## 1.7 Basic Network Commands
 
### Linux vs Windows Commands
 
| Purpose | Linux | Windows |
|---------|-------|---------|
| IP Address | `ifconfig` | `ipconfig` |
| Hostname | `hostname` | `hostname` |
| DNS Info | `nslookup` | `nslookup` |
| Test Connectivity | `ping` | `ping` |
| Trace Route | `traceroute` | `tracert` |
| Network Status | `netstat` | `netstat` |
 
### Command Examples
```bash
# Get IP address
ifconfig  (Linux)
ipconfig  (Windows)
 
# Test connectivity
ping 8.8.8.8
ping google.com
 
# Trace route to destination
traceroute google.com
tracert google.com
 
# Check DNS
nslookup google.com
 
# Check network status
netstat -an
```
 
---
 
# Lab 02: Cisco Packet Tracer
 
## 2.1 Packet Tracer Overview
 
- **Tool:** Network simulator by Cisco Systems (developed by Dennis Frezzo)
- **Purpose:** Simulate networking protocols and topologies
- **Protocols Supported:** Ethernet, PPP, IP, ICMP, ARP, TCP, UDP, routing protocols
- **Modes:** Real Time (actual speed) and Simulation (step-by-step)
---
 
## 2.2 Building a Topology in Packet Tracer
 
### Step-by-Step Process
 
#### Step 1: Start Packet Tracer
- Launch application
- New empty project
#### Step 2: Select Devices & Connections
- **End Devices:** PC, Laptop, Server
- **Networking Devices:** Hub, Switch, Router
- **Connection Types:** 
  - Copper Straight-through (for different devices)
  - Copper Crossover (for same devices)
#### Step 3: Add Devices to Topology
- Click on device category
- Click specific device
- Click in topology area to place device
- Cursor becomes '+' sign when ready to place
#### Step 4: Connect Devices
- Select connection type (Copper Straight or Crossover)
- Click source device → Choose port (FastEthernet)
- Drag to destination device
- Click destination → Choose port
#### Step 5: Configure IP Addresses
- Click device → Config tab → Settings
- Click Interface → FastEthernet
- Assign IP Address
- Subnet Mask (default: 255.255.0.0)
- Gateway and DNS (optional)
#### Step 6: Test Connectivity
- **Realtime Mode:** Switch to Realtime tab
- **Simulation Mode:** Switch to Simulation tab
- Select "Add Simple PDU" tool
- Click source PC → Click destination PC
- Check "Last Status" = Successful
---
 
## 2.3 Connecting Different Devices
 
### Hub to Switch Connection
- Use **Crossover cable** (same device types)
- Select Port (any port number is fine)
### PC to Hub
- Use **Straight cable**
- Green link light = active connection
### PC to Switch
- Use **Straight cable**
- Green link light = active connection
- Amber light = Spanning Tree Protocol (STP) processing (~30 seconds)
---
 
## 2.4 IP Configuration in Packet Tracer
 
### Static IP Assignment
 
```
PC0:  IP: 172.16.1.10    Subnet: 255.255.0.0
PC1:  IP: 172.16.1.11    Subnet: 255.255.0.0
PC2:  IP: 172.16.1.12    Subnet: 255.255.0.0
PC3:  IP: 172.16.1.13    Subnet: 255.255.0.0
```
 
### Configuration Steps
1. Click on PC
2. Desktop tab → IP Configuration
3. Select "Static"
4. Enter IP Address
5. Enter Subnet Mask
6. Click X to save (auto-saves)
---
 
## 2.5 DHCP Configuration
 
### What is DHCP?
- **Dynamic Host Configuration Protocol**
- Server automatically assigns IP addresses from a pool
- Process: DHCP Discover → DHCP Offer → DHCP Request → IP Assignment
### Server Setup
1. Add Server device to topology
2. Click Server → Config tab
3. Click DHCP service
4. Configure:
   - Starting IP address
   - Subnet mask
   - Maximum number of users
   - Default Gateway (if needed)
   - DNS Server address
### Client Setup
1. Click each PC → Desktop → IP Configuration
2. Select "DHCP" (instead of Static)
3. PC automatically gets IP from DHCP server
---
 
## 2.6 Testing & Verification
 
### Add Simple PDU Tool
- Simulates ping/ICMP message
- Click source → destination
- In Realtime: Shows green checkmark for success
- In Simulation: Shows packet movement step-by-step
### Troubleshooting
- Check link lights (green = active, red = down, amber = processing)
- Verify IP addresses are in same subnet
- Wait for STP process to complete (~30 seconds)
- Check subnet masks match
---
 
## 2.7 Simulation Modes
 
### Realtime Mode
- **Speed:** Actual/real-time speed
- **Use:** Quick connectivity verification
- **Result:** Shows pass/fail status immediately
### Simulation Mode
- **Speed:** Step-by-step with control
- **Use:** See packet movement in detail
- **Features:**
  - Capture/Forward button controls
  - Event List shows all packets
  - Can filter by protocol (ICMP, TCP, UDP, etc.)
  - Visual representation of packet flow
---
 
# Lab 03: Socket Programming
 
## 3.1 Socket Basics
 
### What is a Socket?
- Endpoint for network communication
- Combination of IP address + Port number
- Originated from Berkeley sockets (1983)
### Socket Types
 
| Type | Protocol | Characteristics |
|------|----------|-----------------|
| **SOCK_STREAM** | TCP | Reliable, connection-oriented, ordered |
| **SOCK_DGRAM** | UDP | Unreliable, connectionless, fast |
 
---
 
## 3.2 Socket Creation
 
### Python Socket Syntax
```python
import socket
 
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
#                  socket_family, socket_type, protocol=0
```
 
### Socket Family Options
- `AF_INET` - IPv4 internet protocol
- `AF_INET6` - IPv6 internet protocol
- `AF_UNIX` - Local Unix socket
---
 
## 3.3 Server-Side Socket Methods
 
| Method | Purpose | Example |
|--------|---------|---------|
| `s.bind(address)` | Bind to port | `s.bind(('192.168.1.1', 5000))` |
| `s.listen(n)` | Listen for connections (queue n pending) | `s.listen(5)` |
| `s.accept()` | Accept client connection | `client_socket, addr = s.accept()` |
| `s.send(data)` | Send data (TCP) | `s.send(b'Hello')` |
| `s.recv(1024)` | Receive data (max 1024 bytes) | `data = s.recv(1024)` |
| `s.close()` | Close socket | `s.close()` |
 
### Server Code Template
```python
import socket
 
# Create socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
 
# Bind to address and port
server.bind(('0.0.0.0', 5000))
 
# Listen for connections
server.listen(5)
 
print("Server listening on port 5000...")
 
while True:
    # Accept client connection
    client, addr = server.accept()
    print(f"Client connected: {addr}")
    
    # Receive data
    data = client.recv(1024).decode()
    print(f"Received: {data}")
    
    # Send response
    client.send(b"Server received your message")
    
    # Close client connection
    client.close()
```
 
---
 
## 3.4 Client-Side Socket Methods
 
| Method | Purpose |
|--------|---------|
| `s.connect(address)` | Connect to server |
| `s.send(data)` | Send data |
| `s.recv(1024)` | Receive data |
| `s.close()` | Close connection |
 
### Client Code Template
```python
import socket
 
# Create socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
 
# Connect to server
client.connect(('192.168.1.1', 5000))
 
# Send data
client.send(b"Hello Server")
 
# Receive response
response = client.recv(1024).decode()
print(f"Response: {response}")
 
# Close connection
client.close()
```
 
---
 
## 3.5 UDP Socket Methods (Connectionless)
 
### Differences from TCP
- No `listen()` or `accept()`
- Use `sendto()` and `recvfrom()`
- No connection establishment
- Faster but unreliable
### Methods
```python
# Server
server.bind(('0.0.0.0', 5000))
data, addr = server.recvfrom(1024)
server.sendto(b"Response", addr)
 
# Client
client.sendto(b"Message", ('192.168.1.1', 5000))
response, addr = client.recvfrom(1024)
```
 
---
 
## 3.6 Socket Helper Functions
 
### Get Own IP Address
```python
hostname = socket.gethostname()
ip = socket.gethostbyname(hostname)
print(f"Your IP: {ip}")
```
 
### Resolve Domain Name to IP
```python
ip = socket.gethostbyname("www.google.com")
print(f"google.com IP: {ip}")
```
 
### Reverse DNS Lookup
```python
hostname, aliases, ip_list = socket.gethostbyaddr('8.8.8.8')
print(f"Hostname: {hostname}")
```
 
### Get Service by Port
```python
service = socket.getservbyport(80, 'tcp')
print(f"Port 80: {service}")  # Output: http
```
 
### Port Scanner
```python
import socket
 
def scan_port(host, port):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    result = sock.connect_ex((host, port))
    if result == 0:
        print(f"Port {port}: OPEN")
    else:
        print(f"Port {port}: CLOSED")
    sock.close()
 
scan_port('192.168.1.1', 80)
```
 
---
 
## 3.7 TCP Handshake Flow
 
```
CLIENT                          SERVER
  |                               |
  |-------- SYN (seq=x) -------->|
  |                               |
  |<--- SYN+ACK (seq=y,ack=x+1)---|
  |                               |
  |------ ACK (seq=x+1,ack=y+1)-->|
  |                               |
  |<====== CONNECTION OPEN ======>|
  |                               |
  |------ DATA TRANSFER --------->|
  |<----- DATA TRANSFER ----------|
  |                               |
  |------ FIN (close) ----------->|
  |<----- FIN+ACK (close) --------|
```
 
---
 
# Lab 04: HTTP/HTTPS, DNS, Routers
 
## 4.1 Router Basics
 
### What is a Router?
- **Layer 3** device (Network layer)
- Routes packets between networks
- Reads destination IP address
- Consults routing table
- Forwards to next hop
### Router Functions
1. **Path Determination** - RIP, OSPF, EIGRP routing protocols
2. **Packet Forwarding** - Send data to correct interface
3. **Traffic Filtering** - ACL (Access Control Lists)
4. **Network Segmentation** - Separate broadcast domains
---
 
## 4.2 Basic Router Configuration
 
### Access Router CLI
```
Router> enable
Router# config t
Router(config)#
```
 
### Configure Interface
```
Router(config)# interface FastEthernet0/0
Router(config-if)# ip address 10.10.10.1 255.0.0.0
Router(config-if)# no shutdown
Router(config-if)# exit
```
 
### Verify Configuration
```
Router# show ip interface brief
Router# show running-config
```
 
---
 
## 4.3 HTTP vs HTTPS
 
### HTTP (HyperText Transfer Protocol)
 
| Aspect | Detail |
|--------|--------|
| **Port** | 80 |
| **Security** | None (plain text) |
| **Encryption** | No |
| **Speed** | Faster (no encryption overhead) |
| **Use** | Public websites (no sensitive data) |
| **Protocol** | Application Layer (L7) |
 
### HTTPS (HTTP Secure)
 
| Aspect | Detail |
|--------|--------|
| **Port** | 443 |
| **Security** | SSL/TLS encryption |
| **Encryption** | Yes (encrypted communication) |
| **Speed** | Slightly slower (encryption overhead) |
| **Use** | Banking, email, sensitive data |
| **Certificate** | Required (public key infrastructure) |
| **Protocol** | Transport Layer (L4) uses TLS |
 
### Key Difference
```
HTTP:  Client --[plain text]--> Server (visible to anyone)
HTTPS: Client --[encrypted]---> Server (only client/server can read)
```
 
---
 
## 4.4 HTTP Status Codes
 
### 4xx Client Errors (Client's Fault)
 
| Code | Meaning | Cause |
|------|---------|-------|
| **400** | Bad Request | Malformed syntax |
| **401** | Unauthorized | Authentication required |
| **403** | Forbidden | Access denied |
| **404** | Not Found | Resource doesn't exist |
| **408** | Request Timeout | Request took too long |
 
### 5xx Server Errors (Server's Fault)
 
| Code | Meaning | Cause |
|------|---------|-------|
| **500** | Internal Server Error | Server error/bug |
| **501** | Not Implemented | Feature not supported |
| **502** | Bad Gateway | Gateway error |
| **503** | Service Unavailable | Server down/overloaded |
 
---
 
## 4.5 DNS (Domain Name System)
 
### What is DNS?
- Translates domain names to IP addresses
- **Port:** 53 (UDP)
- Hierarchical distributed system
- Example: www.google.com → 142.250.185.46
### DNS Record Types
 
| Record | Purpose | Example |
|--------|---------|---------|
| **A** | IPv4 address | fast-ai.com → 35.0.0.1 |
| **AAAA** | IPv6 address | fast-ai.com → 2001:db8::1 |
| **CNAME** | Alias (canonical name) | www.fast.com → fast-ai.com |
| **NS** | Authoritative nameserver | Identifies DNS server for zone |
| **SOA** | Start of Authority | Zone admin info, serial, refresh |
| **MX** | Mail exchange | Email server for domain |
| **TXT** | Text record | SPF, DKIM records |
 
### DNS Configuration Example
 
**Add A Record:**
```
Name: fast-ai
Address: 35.0.0.1
```
 
**Add CNAME Record:**
```
Name: fast
Host (points to): fast-ai
```
 
### DNS Resolution Process
```
1. User types: www.google.com
2. Browser queries DNS server
3. DNS server resolves to IP: 142.250.185.46
4. Browser connects to 142.250.185.46
5. Webpage loads
```
 
---
 
## 4.6 DNS Configuration in Packet Tracer
 
### Server Setup
1. Select Server device
2. Go to **Services** tab
3. Click **DNS** → Turn ON
4. Add A Record: (domain name → IP)
5. Add CNAME Record: (alias → canonical name)
### Client Testing
1. Open Web Browser on PC
2. Type domain name (e.g., http://fast-ai)
3. DNS resolves the name
4. Webpage loads (if server is running HTTP service)
---
 
# Lab 05: Email, FTP, Wireshark
 
## 5.1 SMTP (Simple Mail Transfer Protocol)
 
### Overview
- **Purpose:** SENDING emails
- **Port:** 25 (server-to-server), 587 (client-to-server), 465 (deprecated)
- **Protocol:** TCP-based
- **Security:** Plain text (vulnerable)
- **Note:** SMTP only sends; POP3/IMAP receive emails
### SMTP Configuration in Packet Tracer
 
#### Server Setup
1. Click Server → Services tab
2. Click **EMAIL** → Turn ON SMTP
3. Set **Domain Name:** fast.com
4. Add users:
   - User: cs, Password: 123
   - User: ee, Password: 456
   - User: bba, Password: 789
#### Client Setup
1. Click PC → Desktop → **Email**
2. Enter:
   - Display Name: Computer Science
   - Email Address: cs@fast.com
   - Incoming Server: 10.0.0.2 (server IP)
   - Outgoing Server: 10.0.0.2
   - Username: cs
   - Password: 123
3. Compose and send email
---
 
## 5.2 POP3 (Post Office Protocol)
 
### Overview
- **Purpose:** RECEIVING/RETRIEVING emails
- **Port:** 110 (TCP)
- **Behavior:** Downloads emails, deletes from server
- **Use Case:** Single device access
- **Limitation:** Can't access from multiple devices easily
### POP3 vs IMAP
 
| Feature | POP3 | IMAP |
|---------|------|------|
| **Port** | 110 | 143 |
| **Email Location** | Local device | Server |
| **Multiple Devices** | Poor | Excellent |
| **Offline Access** | Yes | No |
| **Storage** | Local | Server-based |
| **Bandwidth** | Lower | Higher |
 
---
 
## 5.3 FTP (File Transfer Protocol)
 
### Overview
- **Purpose:** File transfer between computers
- **Control Port:** 21 (commands)
- **Data Port:** 20 (active mode) or dynamic (passive)
- **Protocol:** TCP-based
- **Security:** Plain text (insecure)
- **Credentials:** Sent unencrypted (vulnerability!)
### FTP Modes
 
#### Active Mode
```
Client connects to server on port 21
Client: PORT 192.168.1.100,5000
Server connects to client on port 5000 (back connection)
Data transfers on port 20/5000
```
- **Problem:** Firewall blocks server's back connection
- **Rarely used** in modern networks
#### Passive Mode
```
Client: PASV
Server: 227 Entering Passive Mode (192,168,1,1,20,0)
Server: Listening on 192.168.1.1:5120
Client: Connect to 192.168.1.1:5120
Data transfers on that connection
```
- **Advantage:** Client initiates all connections
- **Firewall-friendly:** More compatible
- **Standard mode** used today
### Basic FTP Commands
 
| Command | Purpose | Example |
|---------|---------|---------|
| **ftp** | Connect to server | `ftp 10.0.0.2` |
| **user** | Enter username | (prompted during login) |
| **pass** | Enter password | (prompted during login) |
| **put** | Upload file | `put test.bin` |
| **get** | Download file | `get filename` |
| **dir** / **ls** | List files | `dir` or `ls` |
| **cd** | Change directory | `cd uploads` |
| **pwd** | Print working directory | `pwd` |
| **quit** | Disconnect | `quit` |
 
### FTP Security Issues
 
```
VULNERABILITY:
FTP sends credentials in PLAIN TEXT
Attacker sniffing traffic can capture:
- Username
- Password
- Downloaded/uploaded file contents
```
 
### Secure Alternatives
 
| Alternative | Port | Security |
|-------------|------|----------|
| **FTPS** | 990 | FTP over SSL/TLS |
| **SFTP** | 22 | FTP over SSH (encrypted) |
| **SCP** | 22 | Secure Copy Protocol |
 
---
 
## 5.4 Wireshark - Packet Analysis
 
### What is Wireshark?
- Free, open-source packet analyzer
- Captures and displays network packets
- Used for troubleshooting and security analysis
- Shows all network protocols in detail
### Wireshark Interface
 
| Component | Purpose |
|-----------|---------|
| **Packet List** | Shows all captured packets |
| **Packet Details** | Shows headers/fields of selected packet |
| **Packet Bytes** | Shows raw packet data (hex) |
| **Filter Field** | Filter by protocol or criteria |
 
### Packet Structure (Encapsulation)
 
```
Frame (Layer 1 - Physical)
├── Ethernet II (Layer 2 - Data Link)
│   ├── Destination MAC
│   ├── Source MAC
│   └── Type: IP
├── IP (Layer 3 - Network)
│   ├── Source IP
│   ├── Destination IP
│   └── Protocol: TCP
├── TCP (Layer 4 - Transport)
│   ├── Source Port
│   ├── Destination Port
│   └── Flags: SYN, ACK, FIN
└── HTTP (Layer 7 - Application)
    ├── Method: GET, POST
    ├── URL
    └── Headers
```
 
### Common Filters
 
| Filter | Purpose |
|--------|---------|
| `tcp` | Show only TCP packets |
| `http` | Show only HTTP packets |
| `ftp` | Show only FTP packets |
| `smtp` | Show only SMTP packets |
| `ip.addr == 192.168.1.1` | Packets from/to specific IP |
| `tcp.port == 80` | Packets on port 80 |
| `dns` | DNS queries/responses |
 
### Analyzing HTTP Packets
 
**Vulnerability Example:**
- Open Wireshark → Start capturing
- Browse website with HTTP (unencrypted)
- Filter: `http`
- Expand HTTP packet
- Can see in plain text:
  - Username (if form POST)
  - Password (if form POST)
  - Cookies
  - All form data
**Why HTTPS is important:**
- HTTPS encryption prevents packet inspection
- Even with Wireshark, encrypted data is unreadable
---
 
## 5.5 Protocol Port Summary
 
| Protocol | Port | Transport | Security | Function |
|----------|------|-----------|----------|----------|
| HTTP | 80 | TCP | None | Web browsing |
| HTTPS | 443 | TCP | SSL/TLS | Secure web |
| SMTP | 25/587 | TCP | None | Send email |
| POP3 | 110 | TCP | None | Receive email |
| IMAP | 143 | TCP | None | Receive (keep on server) |
| FTP | 21/20 | TCP | None | File transfer |
| FTPS | 990 | TCP | SSL/TLS | Secure FTP |
| SFTP | 22 | TCP | SSH | Secure file transfer |
| Telnet | 23 | TCP | None | Remote terminal |
| SSH | 22 | TCP | Encrypted | Secure remote access |
| DNS | 53 | UDP | None | Name resolution |
 
---
 
# Lab 06: Telnet and SSH
 
## 6.1 Telnet (Telecommunications Network)
 
### Overview
- **Purpose:** Remote terminal emulation
- **Port:** 23 (TCP)
- **Layer:** Application Layer (L7)
- **Security:** NO ENCRYPTION (plain text)
- **Status:** DEPRECATED (obsolete)
- **History:** Old technology, still used for network device management
### Telnet Vulnerabilities
 
```
PLAIN TEXT TRANSMISSION:
telnet 192.168.1.1
  ↓ (unencrypted)
Password: cisco
  ↓ (transmitted in plain text)
⚠️ Attacker can see: username, password, all commands
```
 
### VLAN 1 (Vlan Interface)
 
**Problem:**
- All switch ports are in VLAN 1 by default
- VLAN 1 interface (Vlan1) has NO IP by default
- PCs can't reach switch via IP for management
**Solution:**
- Assign IP address to Vlan1 interface
- Enables in-band management
---
 
## 6.2 Telnet Configuration (Cisco Switch)
 
### Complete Configuration
 
```cisco
Switch> enable
Switch# configure terminal
Switch(config)# 
 
# Step 1: Assign IP to Vlan1
Switch(config)# interface vlan 1
Switch(config-if)# ip address 192.168.1.1 255.255.255.0
Switch(config-if)# no shutdown
Switch(config-if)# exit
 
# Step 2: Configure Telnet (VTY lines)
Switch(config)# line vty 0 15
Switch(config-line)# password cisco
Switch(config-line)# login
Switch(config-line)# exit
 
# Step 3: Set enable password
Switch(config)# enable password cs
Switch(config)# exit
 
Switch#
```
 
### Configuration Explanation
 
| Command | Purpose |
|---------|---------|
| `interface vlan 1` | Manage VLAN 1 (default) |
| `ip address 192.168.1.1 255.255.255.0` | Assign management IP |
| `no shutdown` | Bring interface up |
| `line vty 0 15` | Configure 16 virtual terminal lines |
| `password cisco` | Telnet login password |
| `login` | Require password to login |
| `enable password cs` | Password for privileged mode |
 
### Connecting via Telnet
 
```
PC:C:\> telnet 192.168.1.1
 
Trying 192.168.1.1...
Connected to 192.168.1.1
Escape character is '^]'
Password: cisco        ← Enter telnet password
Switch>
Switch> enable        ← Enter privileged mode
Password: cs          ← Enter enable password
Switch#
```
 
---
 
## 6.3 SSH (Secure Shell)
 
### Overview
- **Purpose:** Secure remote access (Telnet replacement)
- **Port:** 22 (TCP)
- **Layer:** Application Layer (L7)
- **Security:** FULL ENCRYPTION (all data encrypted)
- **Status:** MODERN STANDARD
- **Authentication:** Password or RSA key-pair
### SSH vs Telnet Comparison
 
| Feature | Telnet | SSH |
|---------|--------|-----|
| **Port** | 23 | 22 |
| **Encryption** | None (plain text) | Full encryption |
| **Authentication** | Password only | Password + Key-pair |
| **Security** | Weak (DEPRECATED) | Strong (SECURE) |
| **Speed** | Slightly faster | Slightly slower |
| **Data Visible** | YES (vulnerable) | NO (encrypted) |
 
---
 
## 6.4 SSH Configuration (Cisco Switch)
 
### Prerequisites
- **Hostname** (required for key generation)
- **Domain Name** (required for FQDN)
### Complete SSH Configuration
 
```cisco
Switch> enable
Switch# configure terminal
Switch(config)#
 
# Step 1: Set hostname and domain
Switch(config)# hostname lab01
lab01(config)# ip domain name fast-cn
lab01(config)#
 
# Step 2: Generate RSA keypair
lab01(config)# crypto key generate rsa
The name for the keys will be: lab01.fast-cn
How many bits in the modulus [512]: 1024
% Generating 1024 bit RSA keys, keys will be non-exportable...
[OK] (some key values saved in flash)
 
# Step 3: Enable SSH version 2
lab01(config)# ip ssh version 2
 
# Step 4: Create local user account
lab01(config)# username CS-FAST secret abc
lab01(config)#
 
# Step 5: Configure VTY lines
lab01(config)# line vty 0 15
lab01(config-line)# transport input ssh
lab01(config-line)# login local
lab01(config-line)# exit
 
lab01(config)# exit
lab01#
```
 
### Configuration Explanation
 
| Command | Purpose |
|---------|---------|
| `hostname lab01` | Set device hostname |
| `ip domain name fast-cn` | Set domain name |
| `crypto key generate rsa` | Generate 1024-bit RSA keypair |
| `ip ssh version 2` | Use SSHv2 (more secure than v1) |
| `username CS-FAST secret abc` | Create local user with password |
| `transport input ssh` | Only allow SSH (no Telnet) |
| `login local` | Use local user database |
 
### Connecting via SSH
 
```
From Windows:
C:\> ssh -l CS-FAST 192.168.1.1
Password: abc
lab01>
lab01> enable
lab01#
 
From Linux:
$ ssh CS-FAST@192.168.1.1
CS-FAST@192.168.1.1's password: abc
lab01>
lab01> enable
lab01#
```
 
---
 
## 6.5 SSH Authentication Methods
 
### Password-Based Authentication
```
ssh user@host
Enter password: ****
```
- Simple but less secure
- Password visible if intercepted (but still encrypted due to SSH)
### Key-Based Authentication (RSA Keypair)
 
**Generate keypair on client:**
```bash
ssh-keygen -t rsa -b 2048
# Generates: id_rsa (private key), id_rsa.pub (public key)
```
 
**Upload public key to server:**
- Server stores public key in ~/.ssh/authorized_keys
- Client has private key
**Connect without password:**
```bash
ssh user@host
# Authenticates automatically using RSA keypair
# No password prompt
```
 
**Advantages:**
- No password transmitted
- More secure than password-based
- Convenient (no password entry needed)
- Industry standard for production systems
---
 
# Quick Reference Tables
 
## Layer-Protocol Mapping
 
| Layer | Name | Protocols | Devices |
|-------|------|-----------|---------|
| **L1** | Physical | Signals, cables | Hub, Repeater |
| **L2** | Data Link | Ethernet, MAC | Switch, Bridge |
| **L3** | Network | IP, ICMP, ARP | Router |
| **L4** | Transport | TCP, UDP | - |
| **L7** | Application | HTTP, HTTPS, DNS, SMTP, FTP, SSH, Telnet | Server, Client |
 
---
 
## All Protocols Summary
 
| Protocol | Port(s) | Layer | Security | Purpose |
|----------|---------|-------|----------|---------|
| **HTTP** | 80 | L7 | None | Web browsing |
| **HTTPS** | 443 | L7 | SSL/TLS | Secure web |
| **DNS** | 53 | L7 | None | Domain → IP |
| **SMTP** | 25/587 | L7 | None | Send email |
| **POP3** | 110 | L7 | None | Receive email |
| **IMAP** | 143 | L7 | None | Email (keep server) |
| **FTP** | 21/20 | L7 | None | File transfer |
| **FTPS** | 990 | L7 | SSL/TLS | Secure FTP |
| **SFTP** | 22 | L7 | SSH | Secure file transfer |
| **Telnet** | 23 | L7 | None | Remote terminal |
| **SSH** | 22 | L7 | Encrypted | Secure remote |
| **HTTP** | 80 | L7 | None | Web |
| **TCP** | - | L4 | - | Reliable connection |
| **UDP** | - | L4 | - | Fast, unreliable |
| **IP** | - | L3 | - | Routing |
| **ICMP** | - | L3 | - | Ping, tracert |
| **ARP** | - | L3 | - | IP ↔ MAC mapping |
| **Ethernet** | - | L2 | - | Frame format |
 
---
 
## IP Addressing Quick Reference
 
### Class Details
 
```
CLASS A:  0-127 (but 0 and 127 reserved)
  Network bits: 8
  Host bits: 24
  Format: N.H.H.H
  Example: 10.0.0.0/8
 
CLASS B:  128-191
  Network bits: 16
  Host bits: 16
  Format: N.N.H.H
  Example: 172.16.0.0/16
 
CLASS C:  192-223
  Network bits: 24
  Host bits: 8
  Format: N.N.N.H
  Example: 192.168.0.0/24
```
 
### Subnet Mask Patterns
 
```
/8  = 255.0.0.0           (Class A)
/16 = 255.255.0.0         (Class B)
/24 = 255.255.255.0       (Class C)
/25 = 255.255.255.128
/26 = 255.255.255.192
/27 = 255.255.255.224
/28 = 255.255.255.240
/29 = 255.255.255.248
/30 = 255.255.255.252
/31 = 255.255.255.254
/32 = 255.255.255.255
```
 
### Host Calculation
 
```
For /24 network (255.255.255.0):
  Total addresses: 2^8 = 256
  Network address: 1 (cannot use)
  Broadcast address: 1 (cannot use)
  Usable hosts: 254
 
For /30 network (255.255.255.252):
  Total addresses: 2^2 = 4
  Network address: 1
  Usable hosts: 2
  Broadcast address: 1
  Common use: Router-to-router links
```
 
---
 
# Key Formulas & Calculations
 
## Subnet Calculations
 
### Calculate Number of Hosts
```
Formula: 2^(host bits) - 2
 
Example (/24):
Bits per octet: 8
Host bits: 8
Hosts: 2^8 - 2 = 256 - 2 = 254
```
 
### Calculate Network Address
```
Example: 192.168.1.130 with /25
 
/25 = 255.255.255.128
Last octet binary of 255.128:
  255 = 11111111
  128 = 10000000
 
130 binary = 10000010
AND 128 = 10000000 = 128
 
Network: 192.168.1.128/25
```
 
### Calculate Broadcast Address
```
Last address of network
Example: 192.168.1.128/25
  Usable range: 192.168.1.129 - 192.168.1.254
  Broadcast: 192.168.1.255
```
 
---
 
# Common Exam Questions
 
## Lab 01 Questions
 
### Q1: What is the difference between a hub and a switch?
**A:** Hub broadcasts data to all ports (no intelligence), while switch sends data only to destination port (intelligent). Switch reduces collisions and improves performance.
 
### Q2: When should you use straight cable vs crossover cable?
**A:** 
- **Straight:** Different device types (PC ↔ Switch, Router ↔ Modem)
- **Crossover:** Same device types (PC ↔ PC, Hub ↔ Switch)
### Q3: What is the default subnet mask for Class C?
**A:** 255.255.255.0
 
### Q4: What command checks your IP address in Windows?
**A:** `ipconfig`
 
### Q5: What are the 7 layers of OSI model?
**A:** Physical, Data Link, Network, Transport, Session, Presentation, Application
 
---
 
## Lab 02 Questions
 
### Q1: What does PDU stand for?
**A:** Protocol Data Unit - used in Packet Tracer to test connectivity (like ping)
 
### Q2: What does STP stand for?
**A:** Spanning Tree Protocol - prevents loops in switched networks, causes amber light on port during transition (~30 seconds)
 
### Q3: How do you configure IP on a device in Packet Tracer?
**A:** Click device → Config tab → Interface → FastEthernet → Enter IP Address and Subnet Mask
 
### Q4: What's the difference between Realtime and Simulation mode?
**A:** 
- **Realtime:** Actual speed, quick results
- **Simulation:** Step-by-step, can see packet movement, useful for debugging
---
 
## Lab 03 Questions
 
### Q1: What method does server call first?
**A:** `bind()` - attach to IP and port
 
### Q2: What's the difference between TCP and UDP sockets?
**A:** TCP is reliable and connection-oriented (SOCK_STREAM), UDP is unreliable and connectionless (SOCK_DGRAM)
 
### Q3: What does `accept()` return?
**A:** Tuple with two elements: (client_socket, client_address). client_address is (IP, port).
 
### Q4: How do you receive max 1024 bytes from socket?
**A:** `data = socket.recv(1024)`
 
### Q5: What's a port scanner?
**A:** Program that tests if ports are open on a host using `socket.connect_ex()` - returns 0 if open, non-zero if closed
 
---
 
## Lab 04 Questions
 
### Q1: What's the difference between HTTP and HTTPS?
**A:**
- HTTP: Port 80, no encryption, plain text
- HTTPS: Port 443, SSL/TLS encryption, certificates required
### Q2: What is DNS?
**A:** Domain Name System - translates domain names to IP addresses on port 53 (UDP)
 
### Q3: What does CNAME record do?
**A:** Creates an alias - makes one domain name point to another (canonical) domain name
 
### Q4: What port does DNS use?
**A:** Port 53 (UDP)
 
### Q5: What does 404 error mean?
**A:** Not Found - requested resource doesn't exist on server
 
---
 
## Lab 05 Questions
 
### Q1: What's the difference between SMTP and POP3?
**A:** SMTP sends emails (port 25/587), POP3 receives emails (port 110)
 
### Q2: What are FTP active and passive modes?
**A:**
- **Active:** Server initiates back connection to client (firewall issues)
- **Passive:** Client initiates all connections (firewall-friendly)
### Q3: What's the main security issue with FTP?
**A:** Credentials are sent in plain text - attackers can sniff username/password
 
### Q4: What command uploads file in FTP?
**A:** `put filename`
 
### Q5: What can Wireshark do?
**A:** Capture and analyze network packets, show all protocol headers, useful for troubleshooting and security analysis
 
---
 
## Lab 06 Questions
 
### Q1: What's the main difference between Telnet and SSH?
**A:** Telnet is unencrypted (port 23, deprecated), SSH is encrypted (port 22, modern)
 
### Q2: What does VLAN 1 do?
**A:** Default management VLAN on switches - needs IP address for remote management
 
### Q3: Why do you need hostname and domain name before SSH?
**A:** Required for RSA keypair generation - creates FQDN (Fully Qualified Domain Name)
 
### Q4: What command generates RSA key?
**A:** `crypto key generate rsa`
 
### Q5: What's the advantage of key-based SSH authentication?
**A:** More secure than password, no password transmitted, convenient (automatic), industry standard
 
---
 
## Scenario-Based Questions
 
### Scenario 1: Device Connectivity Issue
**Q:** You connected two PCs with a cable but they can't communicate. Link light is amber on switch port. What's happening?
**A:** Spanning Tree Protocol (STP) is processing. Wait ~30 seconds for port to go green (forwarding stage).
 
### Scenario 2: Missing Website
**Q:** You type www.example.com but website doesn't load. What could be wrong?
**A:** Multiple possibilities:
- DNS not resolving (configure DNS server)
- No route to web server (configure router)
- Web server offline (check server status)
- Wrong IP address on web server
### Scenario 3: Slow FTP Transfer
**Q:** FTP transfer is very slow. How can you check what's wrong?
**A:** Use Wireshark to capture FTP packets:
- Filter: `ftp`
- Check if data is transferring on correct port
- Verify no retransmissions
- Check bandwidth/duplex settings
### Scenario 4: Remote Management
**Q:** Network admin needs to manage switch from computer in different building. What protocol should they use?
**A:** SSH (port 22) - encrypted, secure, modern standard. NOT Telnet (unencrypted, insecure).
 
### Scenario 5: IP Assignment
**Q:** You have 10 PCs connecting to network. Would you use static or DHCP?
**A:** DHCP is better for multiple devices:
- Reduces manual configuration
- Prevents IP conflicts
- Easy to manage
- Scalable
---
 
## Configuration Checklists
 
### Telnet Configuration Checklist
- [ ] Set hostname
- [ ] Assign IP to Vlan1
- [ ] Bring Vlan1 up (`no shutdown`)
- [ ] Configure VTY lines (line vty 0 15)
- [ ] Set Telnet password
- [ ] Enable login
- [ ] Set enable password
- [ ] Test: `telnet <switch-ip>`
### SSH Configuration Checklist
- [ ] Set hostname
- [ ] Set domain name
- [ ] Generate RSA keypair
- [ ] Enable SSH version 2
- [ ] Create local user account
- [ ] Configure VTY lines
- [ ] Set transport to SSH only
- [ ] Set login to local
- [ ] Test: `ssh -l user <switch-ip>`
### Packet Tracer Setup Checklist
- [ ] Add end devices (PCs, servers)
- [ ] Add networking devices (switch, hub)
- [ ] Connect devices with appropriate cables
- [ ] Configure static IPs or DHCP
- [ ] Set subnet masks
- [ ] Test connectivity with PDU
- [ ] Wait for link lights to go green
- [ ] Save topology (.pkt file)
---
 
## Memory Tips & Mnemonics
 
### OSI Layers (Bottom to Top)
**PDN TSPA** → Physical, Data Link, Network, Transport, Session, Presentation, Application
- Or: **All People Seem To Need Data Processing**
### IP Classes
**ABC = 0-223**
- A: 0-127
- B: 128-191
- C: 192-223
### Subnet Masks
**255 = All bits ON**
- Class A: 255.0.0.0
- Class B: 255.255.0.0
- Class C: 255.255.255.0
### Protocol Ports (Common)
**DNS=53, HTTP=80, SMTP=25, HTTPS=443, Telnet=23, SSH=22, FTP=21, POP3=110**
 
### SSH Setup
**Hostname → Domain → RSA → SSHv2 → User → VTY**
1. Hostname
2. Domain name
3. Generate RSA key
4. SSH version 2
5. Create local user
6. Configure VTY lines
---
 
## Last-Minute Reminders
 
✅ **Lab 01:** Learn topologies, cable types, OSI model, IP addressing
✅ **Lab 02:** Understand Packet Tracer workflow, static vs DHCP, connectivity testing
✅ **Lab 03:** Socket programming patterns (server: bind→listen→accept, client: connect)
✅ **Lab 04:** HTTP:80 vs HTTPS:443, DNS (port 53), router configuration
✅ **Lab 05:** SMTP sends, POP3 receives, FTP security issues, Wireshark filtering
✅ **Lab 06:** Telnet (unencrypted, port 23) vs SSH (encrypted, port 22)
 
---
 
**Good luck on your exam! Study hard, practice the configurations, and remember the port numbers and security implications! 🎯**
 