# STAR TOPOLOGY (ED-6)

## Student Details

| Field | Details |
|---------|---------|
| Name | GUDIVADA GOWTHAM |
| Register No. | 212223060074 |
| Department | Electronics and Communication Engineering |
| Subject Code | 19EC412 |
| Subject Name | Communication Networks |
| Slot | T2-T22 |
| Submission Date | 16/05/2026 |

---

# Introduction

In computer networking, the physical and logical arrangement of devices is known as **network topology**. It determines performance, fault tolerance, scalability, and network management.

Among LAN topologies, **Star Topology** is the most widely used. In this topology, all end devices are connected to a central device such as a switch or hub.

This report presents a Cisco Packet Tracer simulation consisting of six PCs connected through a central switch to demonstrate MAC-address-based switching and frame forwarding.

---

# Concept of Star Topology

Star topology is a network configuration where every device connects to a single central device.

## Key Characteristics

### Centralized Architecture
- All devices connect to a central switch or hub.
- No direct communication links exist between end devices.

### Point-to-Point Links
- Each device has a dedicated cable.
- Provides collision-free communication.

### MAC Address-Based Forwarding
- Switches learn source MAC addresses.
- MAC addresses are stored in the CAM (Content Addressable Memory) table.

### Unicast, Broadcast and Flooding
- Known destination MAC → Unicast forwarding.
- Unknown destination MAC → Frame flooding.
- Broadcast traffic → Sent to all ports.

---

# Network Design and Architecture

## Central Device
- Cisco Catalyst 2960 Layer-2 Switch

## End Devices
- PC0 to PC5
- Static IPv4 addressing
- Subnet: `192.168.1.0/24`

## Broadcast Domain
- All hosts belong to one Layer-2 broadcast domain.

## Transmission Media
- UTP Copper Straight-Through Cables

---

# Cisco Packet Tracer Simulation

The simulation consists of:

- One Cisco 2960 switch.
- Six PCs connected through FastEthernet ports.
- Static IP configuration.
- ICMP Ping testing.
- Packet Tracer Simulation Mode used for packet analysis.

---

# Components Required

## Hardware Components

### End Devices
- 6 PCs (PC0 – PC5)

### Central Switch
- Cisco Catalyst 2960 Layer-2 Switch

### Transmission Media
- 6 Copper Straight-Through Cables

### Protocols Used
- IPv4
- ICMP
- ARP

---

# IP Address Configuration Table

| Device | IP Address | Subnet Mask | Switch Port |
|----------|-------------|-------------|-------------|
| PC0 | 192.168.1.2 | 255.255.255.0 | Fa0/1 |
| PC1 | 192.168.1.3 | 255.255.255.0 | Fa0/2 |
| PC2 | 192.168.1.4 | 255.255.255.0 | Fa0/3 |
| PC3 | 192.168.1.5 | 255.255.255.0 | Fa0/4 |
| PC4 | 192.168.1.6 | 255.255.255.0 | Fa0/5 |
| PC5 | 192.168.1.7 | 255.255.255.0 | Fa0/6 |

---

# Working Principle and Data Encapsulation

## 1. ARP Resolution

Before communication:

- Source host broadcasts an ARP Request.
- Switch floods the request.
- Destination host replies with ARP Reply.

## 2. Frame Construction

Ethernet frame contains:

- Destination MAC Address
- Source MAC Address
- EtherType
- IP Datagram
- Frame Check Sequence (FCS)

## 3. MAC Learning

The switch:

- Reads source MAC address.
- Stores it in the MAC Address Table.
- Associates it with the incoming port.

## 4. Frame Forwarding

- Known MAC → Unicast forwarding.
- Unknown MAC → Flooding.

## 5. Reception and Reply

Destination host:

- Receives frame.
- Processes payload.
- Sends ICMP Echo Reply if required.

---

# Real-Time Scenario and Packet Analysis

## Initial ARP Broadcast

- PC0 pinged PC3.
- Switch flooded ARP Request.
- Only PC3 replied.

## MAC Table Population

- Switch learned MAC addresses of PC0 and PC3.
- Future communication used direct forwarding.

## Unicast Forwarding Verification

- Ping between PC1 and PC4.
- Frames delivered directly.

## Bidirectional Connectivity

Successful communication verified between:

- PC0 ↔ PC5
- PC2 ↔ PC5
- PC1 ↔ PC4

and all other hosts.

---

# Advantages

- Easy fault isolation
- High performance
- Collision-free communication
- Scalability
- Centralized management
- Dedicated bandwidth per node
- Consistent network performance

---

# Disadvantages

- Single point of failure
- Higher cabling cost
- Switch port limitation
- Cable length restrictions

---

# Applications in Modern Networking

## Enterprise Office Networks
Corporate LANs using switches.

## Home Networks
Wi-Fi routers acting as central devices.

## Data Centers
Leaf-Spine architecture.

## Educational Laboratories
Computer labs and training centers.

## Industrial Automation
PLC, HMI and sensor communication networks.

---

# Comparison: Star vs Other Topologies

| Feature | Star | Bus | Ring |
|-----------|------|------|------|
| Central Device | Required (Switch) | Not Required | Not Required |
| Fault Isolation | Excellent | Poor | Poor |
| Single Point of Failure | Yes (Switch) | Yes (Cable) | Yes (Ring Break) |
| Scalability | High | Low | Moderate |
| Cabling | High | Low | Moderate |
| Collision Domain | Per Port | Shared | Token Controlled |

---

# Conclusion

The Cisco Packet Tracer simulation successfully demonstrated the operation of a star topology network using six PCs connected through a Cisco 2960 switch.

The experiment verified:

- MAC address learning
- ARP operation
- Unicast forwarding
- ICMP communication
- Full network connectivity

The simulation proved that star topology provides efficient, collision-free communication and remains the preferred topology for modern LAN environments.

---

# Questions on Star Topology

## Fill in the Blanks

1. In a star topology, all end devices are connected to a central _________ device.
2. Star topology operates primarily at the _________ layer of the OSI model.
3. The central switch builds a _________ table.
4. If destination MAC is unknown, the switch _________ the frame.
5. Failure of a single end device affects _________ other devices.
6. Ethernet switches operate in _________ duplex mode.
7. ARP resolves the target's _________ address.
8. The switch is a single point of _________.
9. Cisco Packet Tracer uses _________ cables to connect PCs to a switch.
10. A star topology forms a single _________ domain.

### Answers

1. Switch (or Hub)
2. Data Link Layer (Layer 2)
3. MAC Address / CAM
4. Floods
5. No
6. Full
7. MAC
8. Failure
9. Straight-Through
10. Broadcast

---

# Multiple Choice Questions

### 1. What is the central device in a star topology?

- A) Router
- B) Switch or Hub
- C) Modem
- D) Repeater

**Answer:** B

---

### 2. What happens when a switch receives a frame with an unknown destination MAC address?

- A) Drops the frame
- B) Sends an error
- C) Floods the frame
- D) Forwards to gateway

**Answer:** C

---

### 3. In a star topology with 6 PCs and 1 switch, how many cable segments are required?

- A) 3
- B) 5
- C) 6
- D) 15

**Answer:** C

---

### 4. What is the primary disadvantage of star topology?

- A) Collisions occur frequently
- B) Switch is a single point of failure
- C) Expansion disrupts network
- D) No unicast communication

**Answer:** B

---

### 5. Which protocol resolves MAC addresses?

- A) ICMP
- B) DNS
- C) ARP
- D) DHCP

**Answer:** C

---
