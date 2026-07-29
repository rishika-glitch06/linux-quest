# 🌐 Linux Networking Basics — Visual Guide

> A visual guide to Linux networking concepts, network interfaces, IP addresses, MAC addresses, routing, DNS, DHCP, TCP, UDP, ports, and troubleshooting.

---

# 1. 🌐 What Is Computer Networking?

```text
                         NETWORK
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
       Laptop             Server            Phone
          │                 │                 │
          └─────────────────┼─────────────────┘
                            │
                            ▼
                       Communication
                            │
                            ▼
                     Data Exchange
```

A network allows devices to communicate and exchange data.

---

# 2. 🐧 Linux Networking Overview

```text
                    LINUX NETWORKING
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
      Interface           IP             MAC Address
          │                │                │
          └────────────────┼────────────────┘
                           │
                           ▼
                        Routing
                           │
                           ▼
                        Gateway
                           │
                           ▼
                         DNS
                           │
                           ▼
                      TCP / UDP
                           │
                           ▼
                         Ports
                           │
                           ▼
                       Services
```

---

# 3. 🔌 Network Interfaces

```text
                     NETWORK INTERFACES
                             │
            ┌────────────────┼────────────────┐
            │                │                │
            ▼                ▼                ▼
          eth0             wlan0              lo
            │                │                │
            ▼                ▼                ▼
        Ethernet           Wi-Fi           Loopback
            │                │                │
            ▼                ▼                ▼
         Wired           Wireless        Local System
```

Common interface names:

```text
eth0
ens33
enp0s3
wlan0
lo
```

Check interfaces:

```bash
ip link
```

---

# 4. 🆔 IP Address

```text
                       DEVICE
                          │
                          ▼
                     IP ADDRESS
                          │
              ┌───────────┴───────────┐
              │                       │
              ▼                       ▼
            IPv4                    IPv6
              │                       │
              ▼                       ▼
       192.168.1.10             2001:db8::1
```

An IP address provides logical network addressing.

---

# 5. 4️⃣ IPv4

```text
                    IPv4 ADDRESS
                         │
                         ▼
                   192.168.1.10
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
       Network         Subnet          Host
       Portion          Part           Portion
```

IPv4 uses:

```text
32 bits
```

Example:

```text
192 . 168 . 1 . 10
 │     │    │    │
 ▼     ▼    ▼    ▼
Octet Octet Octet Octet
```

Each octet ranges from:

```text
0 — 255
```

---

# 6. 6️⃣ IPv6

```text
                     IPv6
                      │
                      ▼
              128-bit Address
                      │
                      ▼
              2001:db8::1
```

Comparison:

```text
IPv4
│
└── 32-bit
    Example: 192.168.1.10


IPv6
│
└── 128-bit
    Example: 2001:db8::1
```

---

# 7. 🔗 MAC Address

```text
                 NETWORK INTERFACE
                         │
                         ▼
                    MAC ADDRESS
                         │
                         ▼
               00:1A:2B:3C:4D:5E
```

MAC addresses are associated with network interfaces at the data-link layer.

View with:

```bash
ip link
```

---

# 8. 🔄 IP vs MAC Address

```text
                 NETWORK ADDRESSING
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
          IP Address            MAC Address
              │                     │
              ▼                     ▼
        Logical Address       Link-Layer Address
              │                     │
              ▼                     ▼
         IPv4 / IPv6          Network Interface
```

Simple memory:

```text
IP
↓
Logical network identity

MAC
↓
Network interface identity
```

---

# 9. 🔁 Loopback Interface

```text
                      COMPUTER
                          │
                          ▼
                         lo
                          │
                          ▼
                     127.0.0.1
                          │
                          ▼
                    SAME COMPUTER
```

IPv4:

```text
127.0.0.1
```

IPv6:

```text
::1
```

Test:

```bash
ping 127.0.0.1
```

or:

```bash
ping localhost
```

---

# 10. 🏠 Private IP Addresses

```text
                    PRIVATE NETWORK
                           │
                           ▼
                         Router
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
          Laptop          Phone           TV
      192.168.1.10    192.168.1.11   192.168.1.12
```

Common private IPv4 ranges:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

---

# 11. 🌍 Public IP

```text
                    LOCAL NETWORK
                          │
                          ▼
                        Router
                          │
                     NAT / Routing
                          │
                          ▼
                     Public IP
                          │
                          ▼
                       Internet
```

Conceptually:

```text
Private IP
    ↓
Local Network
    ↓
Router
    ↓
Public Internet
```

---

# 12. 🔀 Private vs Public IP

```text
                       IP ADDRESS
                            │
                 ┌──────────┴──────────┐
                 │                     │
                 ▼                     ▼
              PRIVATE                PUBLIC
                 │                     │
                 ▼                     ▼
            Local Network        Internet-facing
                 │
                 ▼
          192.168.x.x
          10.x.x.x
          172.16.x.x
```

---

# 13. 🧮 Subnet Mask

```text
                 IP ADDRESS
                      │
                      ▼
                192.168.1.10
                      │
                      ▼
                 SUBNET MASK
                      │
                      ▼
                255.255.255.0
                      │
                      ▼
                 CIDR /24
```

Example:

```text
192.168.1.10/24
```

The `/24` represents the network prefix length.

---

# 14. 🚪 Default Gateway

```text
                    LAPTOP
                192.168.1.10
                       │
                       ▼
                DEFAULT GATEWAY
                 192.168.1.1
                       │
                       ▼
                    ROUTER
                       │
                       ▼
                   INTERNET
```

Check using:

```bash
ip route
```

---

# 15. 🧭 Routing

```text
                     PACKET
                       │
                       ▼
                 ROUTING TABLE
                       │
                       ▼
                Select Best Route
                       │
                       ▼
                 Network Interface
                       │
                       ▼
                    Gateway
                       │
                       ▼
                  Destination
```

Command:

```bash
ip route
```

---

# 16. 🗺️ Routing Table

Example:

```text
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0
```

Visual:

```text
                 ROUTING TABLE
                       │
          ┌────────────┴────────────┐
          │                         │
          ▼                         ▼
       Default                  Local Network
          │                         │
          ▼                         ▼
   192.168.1.1              192.168.1.0/24
          │                         │
          ▼                         ▼
       Gateway                     eth0
```

---

# 17. 🧠 DNS

```text
                    DOMAIN NAME
                  www.example.com
                          │
                          ▼
                     DNS SERVER
                          │
                          ▼
                      IP ADDRESS
                   93.184.216.34
                          │
                          ▼
                      WEB SERVER
```

DNS means:

```text
Domain Name System
```

---

# 18. 🔍 DNS Resolution

```text
User
 │
 │ Requests
 ▼
www.example.com
 │
 ▼
DNS Resolver
 │
 │ Finds IP
 ▼
93.184.216.34
 │
 ▼
Connect to Server
```

Useful commands:

```bash
nslookup example.com
```

```bash
dig example.com
```

---

# 19. ⚙️ DHCP

```text
                      CLIENT
                         │
                         │ DHCP Request
                         ▼
                    DHCP SERVER
                         │
                         │ Network Configuration
                         ▼
                      CLIENT
```

DHCP can provide:

```text
IP Address
     │
     ▼
Subnet Information
     │
     ▼
Default Gateway
     │
     ▼
DNS Server
```

---

# 20. 🔢 Ports

```text
                       SERVER
                          │
           ┌──────────────┼──────────────┐
           │              │              │
           ▼              ▼              ▼
        Port 22         Port 80       Port 443
           │              │              │
           ▼              ▼              ▼
          SSH            HTTP          HTTPS
```

Port numbers:

```text
0 — 65535
```

Common ports:

```text
22   → SSH
53   → DNS
80   → HTTP
443  → HTTPS
25   → SMTP
```

---

# 21. 🔐 TCP

```text
                       TCP
                        │
            ┌───────────┼───────────┐
            │           │           │
            ▼           ▼           ▼
      Connection     Reliable     Ordered
      Oriented       Delivery      Data
```

TCP provides reliable, connection-oriented communication.

Examples:

```text
HTTP
HTTPS
SSH
```

---

# 22. ⚡ UDP

```text
                       UDP
                        │
            ┌───────────┼───────────┐
            │           │           │
            ▼           ▼           ▼
      Connectionless  Low Overhead  Fast
```

UDP does not guarantee:

```text
Delivery
Ordering
Retransmission
```

Common uses:

```text
DNS
Streaming
Gaming
Real-time Communication
```

---

# 23. 🔄 TCP vs UDP

```text
                 TRANSPORT LAYER
                        │
             ┌──────────┴──────────┐
             │                     │
             ▼                     ▼
            TCP                   UDP
             │                     │
             ▼                     ▼
      Connection-oriented    Connectionless
             │                     │
             ▼                     ▼
          Reliable             Lightweight
             │                     │
             ▼                     ▼
           Ordered             No ordering
```

---

# 24. 📡 `ip` Command Family

```text
                         ip
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         ▼               ▼               ▼
      ip addr         ip link         ip route
         │               │               │
         ▼               ▼               ▼
      IP Address      Interfaces       Routing
         │
         └───────────────┐
                         ▼
                      ip neigh
                         │
                         ▼
                  Neighbor Information
```

---

# 25. 🔍 `ip addr`

```text
                     ip addr
                        │
                        ▼
                Network Information
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
       IPv4           IPv6           Interface
        inet          inet6            State
```

Command:

```bash
ip addr
```

Shortcut:

```bash
ip a
```

---

# 26. 🔌 `ip link`

```text
                     ip link
                        │
                        ▼
                Network Interfaces
                        │
             ┌──────────┼──────────┐
             │          │          │
             ▼          ▼          ▼
            lo         eth0       wlan0
             │          │          │
             ▼          ▼          ▼
         Loopback    Ethernet     Wi-Fi
```

Command:

```bash
ip link
```

---

# 27. 📶 `ping`

```text
                    YOUR COMPUTER
                          │
                          │ ICMP Echo
                          ▼
                    DESTINATION
                          │
                          │ Echo Reply
                          ▼
                    YOUR COMPUTER
```

Test localhost:

```bash
ping 127.0.0.1
```

Test domain:

```bash
ping example.com
```

---

# 28. 🔎 `ss`

```text
                        ss
                        │
                        ▼
                  Socket Information
                        │
             ┌──────────┴──────────┐
             │                     │
             ▼                     ▼
            TCP                   UDP
             │                     │
             └──────────┬──────────┘
                        │
                        ▼
                      Ports
```

Useful command:

```bash
ss -tuln
```

Meaning:

```text
-t → TCP
-u → UDP
-l → Listening
-n → Numeric
```

---

# 29. 🖥️ `curl`

```text
                    curl
                      │
                      ▼
                  HTTP Request
                      │
                      ▼
                    Server
                      │
                      ▼
                   Response
                      │
                      ▼
                  Terminal
```

Example:

```bash
curl https://example.com
```

Headers only:

```bash
curl -I https://example.com
```

---

# 30. 🔬 `nslookup` and `dig`

```text
                    DOMAIN
                      │
                      ▼
                nslookup / dig
                      │
                      ▼
                  DNS Server
                      │
                      ▼
                  IP Address
```

Commands:

```bash
nslookup example.com
```

```bash
dig example.com
```

Short result:

```bash
dig +short example.com
```

---

# 31. 🛣️ `traceroute`

```text
                 YOUR COMPUTER
                       │
                       ▼
                    Router 1
                       │
                       ▼
                    Router 2
                       │
                       ▼
                    Router 3
                       │
                       ▼
                  DESTINATION
```

Command:

```bash
traceroute example.com
```

Alternative:

```bash
tracepath example.com
```

---

# 32. 🔗 `ip neigh`

```text
                   ip neigh
                       │
                       ▼
                Neighbor Table
                       │
              ┌────────┴────────┐
              │                 │
              ▼                 ▼
          IP Address         MAC Address
              │                 │
              ▼                 ▼
       192.168.1.1       00:11:22:33:44:55
```

Command:

```bash
ip neigh
```

---

# 33. 🧰 Network Troubleshooting

```text
                 NETWORK PROBLEM
                        │
                        ▼
                 Check Interface
                        │
                        ▼
                  Check IP Address
                        │
                        ▼
                  Check Route
                        │
                        ▼
                Check Gateway
                        │
                        ▼
                    Check DNS
                        │
                        ▼
                Test Application
```

Commands:

```bash
ip addr
```

```bash
ip route
```

```bash
ping <gateway>
```

```bash
nslookup example.com
```

```bash
curl -I https://example.com
```

---

# 34. 🧠 Network Troubleshooting Decision Tree

```text
                  NETWORK NOT WORKING
                          │
                          ▼
                  Is Interface UP?
                     /         \
                   NO           YES
                   │             │
                   ▼             ▼
              Check Interface   Has IP?
                                  /  \
                                NO    YES
                                │      │
                                ▼      ▼
                           Check DHCP  Reach Gateway?
                                         /   \
                                       NO     YES
                                       │       │
                                       ▼       ▼
                                   Check Route  DNS Working?
                                                   /   \
                                                 NO     YES
                                                 │       │
                                                 ▼       ▼
                                            Check DNS  Test Service
```

---

# 35. 🌐 Complete Network Communication

```text
                       APPLICATION
                            │
                            ▼
                     TCP / UDP
                            │
                            ▼
                      PORT NUMBER
                            │
                            ▼
                       IP ADDRESS
                            │
                            ▼
                    NETWORK INTERFACE
                            │
                            ▼
                     MAC ADDRESS
                            │
                            ▼
                       ROUTER
                            │
                            ▼
                       GATEWAY
                            │
                            ▼
                       INTERNET
                            │
                            ▼
                     DESTINATION
```

---

# 36. 🧩 Opening a Website — Complete Flow

Example:

```text
https://example.com
```

```text
                  USER
                    │
                    ▼
                 BROWSER
                    │
                    ▼
              DNS Resolution
                    │
                    ▼
               IP Address
                    │
                    ▼
              Routing Table
                    │
                    ▼
              Default Gateway
                    │
                    ▼
                 Internet
                    │
                    ▼
              Remote Server
                    │
                    ▼
              TCP Connection
                    │
                    ▼
              HTTPS Request
                    │
                    ▼
                Response
                    │
                    ▼
               Web Page
```

---

# 37. 🗺️ Linux Networking Command Map

```text
                    LINUX NETWORKING
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ▼                ▼                ▼
       ip addr           ping              ss
          │                │                │
          ▼                ▼                ▼
     IP Address        Reachability      Sockets
          │
          ▼
       ip route
          │
          ▼
       Routing
          │
          ▼
      ip neigh
          │
          ▼
     Neighbors
          │
          ├───────────────┐
          │               │
          ▼               ▼
      nslookup           dig
          │               │
          └───────┬───────┘
                  ▼
                 DNS
                  │
                  ▼
                curl
                  │
                  ▼
             HTTP Request
```

---

# 38. 🔥 Quick Command Reference

| Command | Purpose |
|---|---|
| `ip addr` | Show IP addresses |
| `ip link` | Show interfaces |
| `ip route` | Show routing table |
| `ip neigh` | Show neighbor table |
| `ping` | Test connectivity |
| `ss` | Show sockets and ports |
| `curl` | Make network requests |
| `nslookup` | Query DNS |
| `dig` | Detailed DNS lookup |
| `traceroute` | Trace network path |
| `tracepath` | Trace network path |

---

# 39. 🧠 Quick Memory Map

```text
ip addr
    ↓
WHERE AM I?
    ↓
IP Address


ip link
    ↓
WHAT INTERFACES DO I HAVE?
    ↓
Network Interfaces


ip route
    ↓
WHERE SHOULD PACKETS GO?
    ↓
Routing Table


ping
    ↓
CAN I REACH IT?
    ↓
Connectivity


ss
    ↓
WHAT SERVICES ARE LISTENING?
    ↓
Sockets / Ports


nslookup / dig
    ↓
WHAT IP DOES THIS DOMAIN HAVE?
    ↓
DNS


curl
    ↓
CAN I TALK TO THE WEB SERVICE?
    ↓
HTTP / HTTPS


traceroute
    ↓
WHAT PATH DOES THE PACKET TAKE?
    ↓
Network Path
```

---

# 40. 🏆 Final Linux Networking Map

```text
                         LINUX NETWORKING
                                │
                                ▼
                       NETWORK INTERFACE
                                │
                 ┌──────────────┴──────────────┐
                 │                             │
                 ▼                             ▼
               MAC                           IP
                 │                             │
                 │                    ┌────────┴────────┐
                 │                    │                 │
                 │                    ▼                 ▼
                 │                  IPv4              IPv6
                 │                    │
                 │                    ▼
                 │                  Subnet
                 │                    │
                 │                    ▼
                 │                 Routing
                 │                    │
                 │                    ▼
                 │                 Gateway
                 │                    │
                 └────────────────────┤
                                      ▼
                                   Internet
                                      │
                                      ▼
                                     DNS
                                      │
                                      ▼
                                  TCP / UDP
                                      │
                                      ▼
                                    Ports
                                      │
                                      ▼
                                   Services
```

---

# 🎯 Key Takeaway

```text
INTERFACE
    ↓
IP ADDRESS
    ↓
SUBNET
    ↓
ROUTING
    ↓
GATEWAY
    ↓
DNS
    ↓
TCP / UDP
    ↓
PORT
    ↓
SERVICE
    ↓
COMMUNICATION
```

> 🌐 **Linux Quest — Level 02, Lesson 07**

> *Connect. Communicate. Trace. Troubleshoot.*