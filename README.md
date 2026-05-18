# IPv6-Static-Routing-Implementation-in-Cisco-Packet-Tracer


**Cisco Packet Tracer Project**

![Network Topology]([topology.png](https://raw.githubusercontent.com/sarowarhosen01/IPv6-Static-Routing-Implementation-in-Cisco-Packet-Tracer/refs/heads/main/Configurations/Screenshots/Screenshot-topology.jpg))  

## Project Overview

This project demonstrates the design, configuration, and verification of **IPv6 Static Routing** in a multi-router enterprise network using Cisco Packet Tracer. 

The main goal was to establish full end-to-end IPv6 connectivity between different LAN segments using only static routes, without relying on dynamic routing protocols. This lab strengthens foundational understanding of IPv6 addressing, router configuration, and manual routing in modern IP networks.

**Project Objective:**  
Configure IPv6 addresses on all devices and implement static routes so that PCs in different LANs can communicate successfully.

## Key Features

- Complete IPv6 addressing scheme using Global Unicast addresses
- Static route configuration (specific network routes + default routes)
- Inter-router connectivity via point-to-point links
- Full network reachability verification
- Proper use of link-local addresses for next-hop routing
- Clean and professional network documentation

## Network Topology

The network consists of **three routers** connecting multiple LAN segments.

### Network Topology Table

| Device | Interface          | Connected To          | Link Type       | Purpose                  |
|--------|--------------------|-----------------------|-----------------|--------------------------|
| R1     | G0/0               | Switch1               | Ethernet        | LAN-1                    |
| R1     | S0/0/0             | R2 (S0/0/0)           | Serial          | R1-R2 Link               |
| R2     | S0/0/0             | R1                    | Serial          | R1-R2 Link               |
| R2     | S0/0/1             | R3 (S0/0/1)           | Serial          | R2-R3 Link               |
| R3     | S0/0/1             | R2                    | Serial          | R2-R3 Link               |
| R3     | G0/0               | Switch2               | Ethernet        | LAN-2                    |
| PC1    | NIC                | Switch1               | Ethernet        | End Device (LAN-1)       |
| PC2    | NIC                | Switch2               | Ethernet        | End Device (LAN-2)       |

**Topology Summary:**  
R1 ↔ R2 ↔ R3 forms the backbone. LAN-1 is attached to R1 and LAN-2 is attached to R3.

## IP Addressing Scheme

### IP Addressing Table

| Device | Interface     | IPv6 Address               | Prefix Length | Default Gateway     |
|--------|---------------|----------------------------|---------------|---------------------|
| R1     | G0/0          | 2001:db8:1::1/64          | /64           | -                   |
| R1     | S0/0/0        | 2001:db8:12::1/64         | /64           | -                   |
| R2     | S0/0/0        | 2001:db8:12::2/64         | /64           | -                   |
| R2     | S0/0/1        | 2001:db8:23::1/64         | /64           | -                   |
| R3     | S0/0/1        | 2001:db8:23::2/64         | /64           | -                   |
| R3     | G0/0          | 2001:db8:3::1/64          | /64           | -                   |
| PC1    | NIC           | 2001:db8:1::10/64         | /64           | 2001:db8:1::1       |
| PC2    | NIC           | 2001:db8:3::10/64         | /64           | 2001:db8:3::1       |

*(Update this table with exact addresses from your Packet Tracer file if they differ)*

## Technologies & Protocols Used

- **IPv6** (Internet Protocol version 6)
- **Static Routing** (IPv6 Static Routes)
- **Global Unicast Addresses**
- **Link-Local Addresses** (FE80::/10)
- **Cisco IOS CLI** configuration
- **Ethernet & Serial Links**
- Verification Tools: `ping`, `traceroute`, `show ipv6 route`, `show ipv6 interface brief`

## Project Files

- `Ipv6 Static Routing01.pkt` → Main Packet Tracer Project File
- `README.md` → Project Documentation (this file)
- `topology.png` → Network Topology Diagram (recommended)
- `configuration.txt` → (Optional) Backup of all router configurations

## How to Use

1. Download the project file `Ipv6 Static Routing01.pkt`
2. Open it using **Cisco Packet Tracer** (Version 8.0 or higher recommended)
3. Start all devices
4. Verify connectivity:
   - Ping from PC1 to PC2
   - Ping from PC2 to PC1
   - Use `traceroute` to observe the path
5. Explore router configurations using CLI commands

**Expected Result:** 100% successful communication between all devices.

## Skills Demonstrated

- IPv6 address planning and subnetting
- Router interface configuration (IPv6)
- Static route implementation and troubleshooting
- Understanding of routing tables and administrative distance
- Network documentation and professional reporting
- End-to-end connectivity testing and verification
- CLI proficiency on Cisco devices

## Author

**SAROWAR**  
Network Engineering Student / IT Enthusiast  
Location: Dhaka, Bangladesh  

---

**This project is perfect for CCNA, Network Engineering, and IT Infrastructure portfolios.**

Feel free to customize any section. Would you like me to add **Configuration Snippets**, **Challenges Faced**, or **Screenshots Recommendations** sections as well? Just let me know!

## Configuration Highlights

### 1. Enable IPv6 Routing
```cisco
Router(config)# ipv6 unicast-routing
