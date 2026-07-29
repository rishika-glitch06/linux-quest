# 🐧 Linux Quest — Level 02
# Lesson 07: Linux Networking Basics

> Understand how Linux communicates with other systems through networks, IP addresses, interfaces, DNS, ports, and networking commands.

---

# 🎯 Learning Objectives

By the end of this lesson, you will understand:

- What a computer network is
- How Linux connects to a network
- Network interfaces
- IP addresses
- IPv4 and IPv6
- MAC addresses
- Loopback addresses
- Public and private IP addresses
- Subnet masks
- Default gateways
- DNS
- DHCP
- Ports
- TCP and UDP
- Basic Linux networking commands
- Network troubleshooting basics

---

# 1. 🌐 What Is a Network?

A network is a collection of devices connected together so they can communicate and exchange data.

Example:

```text
        Laptop
           │
           │
           ▼
        Router
           │
           │
           ▼
        Internet
           │
           ▼
       Web Server
```

A network can contain:

- Computers
- Servers
- Routers
- Switches
- Phones
- IoT devices
- Printers

---

# 2. 🐧 Linux Networking

Linux provides tools and commands to:

- Configure network interfaces
- View IP addresses
- Test connectivity
- Check routes
- Resolve domain names
- Inspect network connections
- Troubleshoot network problems

Common commands include:

```bash
ip
ping
ss
ip route
ip neigh
curl
dig
nslookup
traceroute
```

---

# 3. 🔌 Network Interface

A network interface is the connection point through which a device communicates with a network.

Examples:

```text
eth0
ens33
enp0s3
wlan0
lo
```

Typical interfaces:

```text
Ethernet
    ↓
Wired network

Wi-Fi
    ↓
Wireless network

Loopback
    ↓
Local machine communication
```

View network interfaces:

```bash
ip link
```

View IP addresses:

```bash
ip addr
```

Shortcut:

```bash
ip a
```

---

# 4. 🆔 IP Address

An IP address identifies a device or network interface on an IP network.

Example IPv4 address:

```text
192.168.1.10
```

An IP address allows devices to communicate with each other.

Example:

```text
Laptop
192.168.1.10
     │
     │ Network
     ▼
Server
192.168.1.20
```

---

# 5. 4️⃣ IPv4

IPv4 uses **32-bit addresses**.

An IPv4 address is usually written as four decimal numbers separated by dots.

Example:

```text
192.168.1.10
```

Each section is called an octet.

```text
192 . 168 . 1 . 10
 │     │    │    │
 ▼     ▼    ▼    ▼
Octet Octet Octet Octet
```

Each octet can have a value from:

```text
0 to 255
```

---

# 6. 6️⃣ IPv6

IPv6 uses **128-bit addresses**.

Example:

```text
2001:db8::1
```

IPv6 was introduced to provide a much larger address space than IPv4.

Comparison:

```text
IPv4
32-bit
Example:
192.168.1.10


IPv6
128-bit
Example:
2001:db8::1
```

---

# 7. 🔗 MAC Address

A MAC address is a hardware-level address associated with a network interface.

Example:

```text
00:1A:2B:3C:4D:5E
```

It is commonly associated with the network interface at the data-link layer.

View MAC addresses:

```bash
ip link
```

Example:

```text
link/ether 00:1A:2B:3C:4D:5E
```

---

# 8. 🔄 IP Address vs MAC Address

```text
                 NETWORK IDENTIFICATION
                          │
             ┌────────────┴────────────┐
             │                         │
             ▼                         ▼
          IP Address              MAC Address
             │                         │
             ▼                         ▼
       Logical Address          Interface Address
             │                         │
             ▼                         ▼
        Network Layer            Data Link Layer
```

Simple idea:

```text
IP
↓
Where the device is on the network

MAC
↓
Which network interface is involved
```

---

# 9. 🔁 Loopback Address

The loopback interface allows a computer to communicate with itself.

The interface is usually:

```text
lo
```

IPv4 loopback:

```text
127.0.0.1
```

IPv6 loopback:

```text
::1
```

Test it:

```bash
ping 127.0.0.1
```

or:

```bash
ping localhost
```

The loopback interface is useful for:

- Testing networking
- Running local services
- Application development
- Local server communication

---

# 10. 🏠 Private IP Addresses

Private IP addresses are used inside private networks.

Common IPv4 private ranges include:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

Example:

```text
192.168.1.10
```

A home network may look like:

```text
             Internet
                │
                ▼
             Router
                │
        ┌───────┼───────┐
        │       │       │
        ▼       ▼       ▼
      Laptop  Phone    TV
192.168.1.10  .11     .12
```

---

# 11. 🌍 Public IP Address

A public IP address is an address reachable across the public Internet, subject to routing and security controls.

Example:

```text
203.0.113.10
```

Conceptually:

```text
Private IP
    │
    ▼
Home / Office Network
    │
    ▼
Router / NAT
    │
    ▼
Public Internet
```

---

# 12. 🔀 Private vs Public IP

```text
             IP ADDRESS
                  │
          ┌───────┴───────┐
          │               │
          ▼               ▼
       Private           Public
          │               │
          ▼               ▼
   Local Network      Internet-facing
          │
          ▼
    192.168.x.x
    10.x.x.x
    172.16.x.x
```

---

# 13. 🧮 Subnet Mask

A subnet mask determines which part of an IP address represents the network and which part represents hosts.

Example:

```text
IP Address:
192.168.1.10

Subnet Mask:
255.255.255.0
```

CIDR notation:

```text
192.168.1.10/24
```

The `/24` indicates that the first 24 bits represent the network prefix.

---

# 14. 🚪 Default Gateway

A default gateway is the device used to reach networks outside the local network.

Usually, the default gateway is a router.

Example:

```text
Laptop
192.168.1.10
     │
     ▼
Default Gateway
192.168.1.1
     │
     ▼
Internet
```

View routing information:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
```

Meaning:

```text
default
    ↓
Use this route when no more specific route exists

via 192.168.1.1
    ↓
Send traffic through this gateway

dev eth0
    ↓
Use the eth0 interface
```

---

# 15. 🧭 Routing

Routing determines where network packets should be sent.

View routing table:

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0
```

Conceptually:

```text
Application
    │
    ▼
IP Packet
    │
    ▼
Routing Table
    │
    ▼
Choose Route
    │
    ▼
Network Interface
    │
    ▼
Destination
```

---

# 16. 🧠 DNS

DNS stands for:

```text
Domain Name System
```

DNS converts domain names into IP addresses.

Example:

```text
example.com
     │
     ▼
DNS
     │
     ▼
93.184.216.34
```

Without DNS, users would need to remember IP addresses instead of domain names.

---

# 17. 🔍 DNS Resolution

The basic process:

```text
User enters:

www.example.com
       │
       ▼
DNS Resolver
       │
       ▼
Find IP Address
       │
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

or:

```bash
dig example.com
```

---

# 18. ⚙️ DHCP

DHCP stands for:

```text
Dynamic Host Configuration Protocol
```

DHCP can automatically provide network configuration such as:

- IP address
- Subnet information
- Default gateway
- DNS server information

Conceptually:

```text
Client
   │
   │ DHCP Request
   ▼
DHCP Server
   │
   │ Network Configuration
   ▼
Client
```

---

# 19. 🔢 Ports

A port identifies a specific network service or endpoint on a host.

Port numbers range from:

```text
0 to 65535
```

Examples of commonly used ports:

```text
22   → SSH
53   → DNS
80   → HTTP
443  → HTTPS
25   → SMTP
```

Conceptually:

```text
                  SERVER
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
       Port 22    Port 80    Port 443
          │          │          │
          ▼          ▼          ▼
         SSH        HTTP      HTTPS
```

---

# 20. 🔐 TCP

TCP stands for:

```text
Transmission Control Protocol
```

TCP provides reliable, connection-oriented communication.

Characteristics:

- Connection-oriented
- Reliable delivery
- Ordered data
- Error checking
- Flow control

Examples:

```text
HTTP
HTTPS
SSH
```

---

# 21. ⚡ UDP

UDP stands for:

```text
User Datagram Protocol
```

UDP is connectionless and has lower overhead than TCP.

Characteristics:

- Connectionless
- Lower overhead
- No guarantee of delivery
- No guarantee of ordering

Common use cases include:

- DNS queries
- Streaming
- Real-time communication
- Online gaming

---

# 22. 🔄 TCP vs UDP

```text
                 TRANSPORT PROTOCOLS
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
             TCP                   UDP
              │                     │
              ▼                     ▼
        Connection-based       Connectionless
              │                     │
              ▼                     ▼
          Reliable              Low overhead
              │                     │
              ▼                     ▼
          Ordered              No ordering guarantee
```

---

# 23. 📡 `ip` Command

The `ip` command is a modern tool for managing and inspecting networking.

Show interfaces:

```bash
ip link
```

Show IP addresses:

```bash
ip addr
```

Show routes:

```bash
ip route
```

Show neighbors:

```bash
ip neigh
```

---

# 24. 🔍 `ip addr`

Run:

```bash
ip addr
```

or:

```bash
ip a
```

This can show:

- Network interfaces
- IPv4 addresses
- IPv6 addresses
- Interface state
- MAC addresses

Look for:

```text
inet
```

for IPv4 addresses.

Look for:

```text
inet6
```

for IPv6 addresses.

---

# 25. 🔌 `ip link`

Run:

```bash
ip link
```

This shows network interfaces and their states.

Example:

```text
lo
eth0
```

Possible states:

```text
UP
DOWN
```

---

# 26. 📶 `ping`

`ping` tests network reachability using ICMP Echo messages.

Test localhost:

```bash
ping 127.0.0.1
```

Test a domain:

```bash
ping example.com
```

Stop the command using:

```text
Ctrl + C
```

A successful response may show:

```text
64 bytes from ...
```

---

# 27. 🔎 `ss`

`ss` displays socket information.

Show listening TCP and UDP sockets:

```bash
ss -tuln
```

Common options:

```text
-t
↓
TCP

-u
↓
UDP

-l
↓
Listening

-n
↓
Numeric addresses and ports
```

---

# 28. 🧭 `ip route`

View the routing table:

```bash
ip route
```

Look for:

```text
default via
```

This usually indicates the default gateway.

---

# 29. 🖥️ `ip neigh`

The neighbor table stores information about nearby network devices.

Run:

```bash
ip neigh
```

It may show:

```text
192.168.1.1 dev eth0 lladdr 00:11:22:33:44:55 REACHABLE
```

This connects IP addresses with link-layer addresses such as MAC addresses.

---

# 30. 🌐 `curl`

`curl` is commonly used to transfer data from or to a server.

Test a website:

```bash
curl https://example.com
```

View only HTTP headers:

```bash
curl -I https://example.com
```

It is useful for:

- Testing HTTP connectivity
- Calling APIs
- Downloading data
- Troubleshooting web services

---

# 31. 🔍 `nslookup`

`nslookup` queries DNS servers.

Example:

```bash
nslookup example.com
```

It can help determine:

```text
Domain
   │
   ▼
DNS Server
   │
   ▼
IP Address
```

---

# 32. 🔬 `dig`

`dig` is a detailed DNS lookup tool.

Example:

```bash
dig example.com
```

For a concise answer:

```bash
dig +short example.com
```

---

# 33. 🛣️ `traceroute`

`traceroute` shows the path packets take toward a destination.

Example:

```bash
traceroute example.com
```

On some systems:

```bash
tracepath example.com
```

Conceptually:

```text
Your Computer
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
Destination
```

---

# 34. 🧰 Basic Network Troubleshooting

When network connectivity fails, follow a logical process.

```text
1. Check Interface
       │
       ▼
2. Check IP Address
       │
       ▼
3. Check Routing
       │
       ▼
4. Ping Gateway
       │
       ▼
5. Test DNS
       │
       ▼
6. Test Internet
       │
       ▼
7. Check Application
```

Useful commands:

```bash
ip addr
```

```bash
ip route
```

```bash
ping 127.0.0.1
```

```bash
ping <gateway-ip>
```

```bash
ping example.com
```

```bash
nslookup example.com
```

```bash
curl -I https://example.com
```

---

# 35. 🧠 Network Troubleshooting Logic

```text
Can I access localhost?
       │
       ├── NO → Check local networking stack
       │
       ▼ YES

Do I have an IP address?
       │
       ├── NO → Check DHCP / interface configuration
       │
       ▼ YES

Can I reach the gateway?
       │
       ├── NO → Check local network / route
       │
       ▼ YES

Can I resolve a domain?
       │
       ├── NO → Check DNS
       │
       ▼ YES

Can I reach the Internet?
       │
       ├── NO → Check routing / firewall / upstream network
       │
       ▼ YES

Can the application connect?
       │
       ├── NO → Check application / port / service
       │
       ▼ YES

Network Working ✅
```

---

# 36. 🔥 Important Networking Commands

| Command | Purpose |
|---|---|
| `ip addr` | Show IP addresses |
| `ip link` | Show network interfaces |
| `ip route` | Show routing table |
| `ip neigh` | Show neighbor table |
| `ping` | Test reachability |
| `ss` | Inspect sockets |
| `curl` | Test HTTP / transfer data |
| `nslookup` | DNS lookup |
| `dig` | Detailed DNS lookup |
| `traceroute` | Trace network path |
| `tracepath` | Trace network path |

---

# 37. 🗺️ Complete Linux Networking Map

```text
                         LINUX NETWORKING
                                │
          ┌─────────────────────┼─────────────────────┐
          │                     │                     │
          ▼                     ▼                     ▼
      INTERFACE                IP                    MAC
          │                     │                     │
          ▼                     ▼                     ▼
       eth0 /                 IPv4 /               Hardware
       wlan0                  IPv6                  Address
          │                     │
          └──────────────┬──────┘
                         │
                         ▼
                       ROUTE
                         │
                         ▼
                     GATEWAY
                         │
                         ▼
                      INTERNET
                         │
                         ▼
                        DNS
                         │
                         ▼
                      DOMAIN
                         │
                         ▼
                       SERVER
                         │
                  ┌──────┴──────┐
                  │             │
                  ▼             ▼
                 TCP           UDP
                  │             │
                  ▼             ▼
                PORTS         PORTS
```

---

# 38. 🎯 Network Communication Flow

```text
User Application
       │
       ▼
Transport Layer
   TCP / UDP
       │
       ▼
IP Layer
   IPv4 / IPv6
       │
       ▼
Network Interface
  Ethernet / Wi-Fi
       │
       ▼
Router / Gateway
       │
       ▼
Internet
       │
       ▼
Destination Server
```

---

# 39. 🧠 Example: Opening a Website

Suppose you open:

```text
https://example.com
```

The simplified process is:

```text
1. Browser receives domain name
          │
          ▼
2. DNS resolves domain
          │
          ▼
3. IP address is obtained
          │
          ▼
4. Routing table determines path
          │
          ▼
5. TCP connection is established
          │
          ▼
6. HTTPS communication occurs
          │
          ▼
7. Server responds
          │
          ▼
8. Browser displays webpage
```

---

# 40. 🧩 Network Layers — Simplified

```text
Application
     │
     ▼
HTTP / HTTPS / DNS / SSH
     │
     ▼
Transport
     │
     ▼
TCP / UDP
     │
     ▼
Internet
     │
     ▼
IP
     │
     ▼
Network Access
     │
     ▼
Ethernet / Wi-Fi
```

---

# 41. 🔐 Firewall and Network Access

A firewall controls network traffic based on configured rules.

Conceptually:

```text
Incoming Traffic
       │
       ▼
    Firewall
       │
   ┌───┴───┐
   │       │
   ▼       ▼
 Allow    Block
   │       │
   ▼       ▼
Service   Reject
```

A service may be running but still inaccessible if a firewall blocks its port.

---

# 42. 🧪 Network Troubleshooting Example

Suppose a website cannot be opened.

Check:

```bash
ip addr
```

If no IP address:

```text
Check interface / DHCP
```

If IP exists:

```bash
ip route
```

Check gateway.

Then:

```bash
ping <gateway-ip>
```

If gateway works:

```bash
ping example.com
```

If domain ping fails:

```bash
nslookup example.com
```

Finally:

```bash
curl -I https://example.com
```

This helps isolate the problem.

---

# 43. 🎯 Quick Memory Map

```text
ip addr
    ↓
IP Address

ip link
    ↓
Network Interface

ip route
    ↓
Routing Table

ip neigh
    ↓
Neighbor / MAC Information

ping
    ↓
Reachability

ss
    ↓
Sockets and Ports

nslookup / dig
    ↓
DNS

curl
    ↓
HTTP / Network Request

traceroute
    ↓
Network Path
```

---

# 44. 🏆 Key Takeaways

```text
IP Address
    ↓
Identifies a device/interface at the IP layer

MAC Address
    ↓
Identifies a network interface at the link layer

Gateway
    ↓
Connects local network to other networks

DNS
    ↓
Resolves domain names to IP addresses

DHCP
    ↓
Automatically provides network configuration

TCP
    ↓
Reliable, connection-oriented communication

UDP
    ↓
Connectionless, low-overhead communication

Port
    ↓
Identifies a network service endpoint
```

---

# 45. 📝 Lesson 07 Summary

Linux networking provides tools for inspecting and troubleshooting network connectivity.

The most important concepts are:

```text
Network Interface
        ↓
IP Address
        ↓
Subnet
        ↓
Gateway
        ↓
Routing
        ↓
DNS
        ↓
TCP / UDP
        ↓
Ports
        ↓
Applications
```

The most important commands to remember are:

```bash
ip addr
ip link
ip route
ip neigh
ping
ss
curl
nslookup
dig
traceroute
```

Understanding these commands gives you a foundation for Linux system administration, DevOps, cloud computing, cybersecurity, and backend engineering.

---

# 🎯 Lesson 07 Completion Checklist

- [ ] Understand computer networks
- [ ] Understand Linux network interfaces
- [ ] Understand IP addresses
- [ ] Understand IPv4
- [ ] Understand IPv6
- [ ] Understand MAC addresses
- [ ] Understand loopback
- [ ] Understand private IP addresses
- [ ] Understand public IP addresses
- [ ] Understand subnet masks
- [ ] Understand default gateways
- [ ] Understand routing
- [ ] Understand DNS
- [ ] Understand DHCP
- [ ] Understand ports
- [ ] Understand TCP
- [ ] Understand UDP
- [ ] Use `ip addr`
- [ ] Use `ip link`
- [ ] Use `ip route`
- [ ] Use `ip neigh`
- [ ] Use `ping`
- [ ] Use `ss`
- [ ] Use `curl`
- [ ] Use `nslookup`
- [ ] Use `dig`
- [ ] Understand `traceroute`
- [ ] Perform basic network troubleshooting

---

## 🔗 Related Resources

🖼️ [Linux Networking Diagram](../../assets/diagrams/linux-networking-basics.md)

💼 [Linux Networking Interview Preparation](../../interview-prep/linux-file-system.md)

🧪 [Linux Networking Hands-on Lab](../../labs/07-linux-networking-basics-lab.md)

🏠 [Back to Linux Quest](../../README.md)

---

> 🐧 **Linux Quest — Level 02, Lesson 07**

> *Understand the network. Trace the connection. Troubleshoot the system.*