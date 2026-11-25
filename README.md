# VLAN Network Segmentation, Inter-VLAN Routing & Access Control Using Cisco Packet Tracer

## 📌 Project Overview

This project demonstrates the design and implementation of a segmented enterprise network using Cisco Packet Tracer.

The network consists of two Cisco routers and two Layer 2 switches, connecting multiple departments through separate Virtual Local Area Networks (VLANs).

Inter-VLAN communication is enabled using Router-on-a-Stick configuration, while static routing provides communication between the two routers. Extended Access Control Lists (ACLs) are implemented to control traffic between VLANs and restrict unauthorized communication.

The primary objective is to provide secure, organized, and controlled communication between different departments within an organization.

## 🎯 Project Objectives

- Design an enterprise network using Cisco Packet Tracer.
- Create and configure multiple VLANs.
- Assign different departments to separate VLANs.
- Configure trunk links between switches and routers.
- Implement Inter-VLAN Routing using Router-on-a-Stick.
- Configure static routing between two routers.
- Implement Extended ACLs to control network traffic.
- Allow communication only between authorized VLAN pairs.
- Verify network connectivity using ICMP ping tests.

## 🛠️ Technologies & Tools Used

| Technology | Purpose |
|---|---|
| Cisco Packet Tracer | Network simulation |
| Cisco ISR 4331 | Routing |
| Cisco Catalyst 2960 | Layer 2 switching |
| VLAN | Network segmentation |
| 802.1Q | VLAN trunking |
| Router-on-a-Stick | Inter-VLAN routing |
| Static Routing | Communication between routers |
| Extended ACL | Traffic filtering and access control |
| IPv4 | Network addressing |
| ICMP | Connectivity testing |

## 🏗️ Network Topology

The network consists of:

- 2 Cisco ISR4331 routers
- 2 Cisco Catalyst 2960 switches
- 12 end devices (PCs)
- 6 VLANs
- Router-to-router connectivity

### Network Architecture

The network is divided into two sections:

**Network 1 – Router0 and Switch0**
- VLAN 10 – HR
- VLAN 20 – Operations
- VLAN 30 – Sales

**Network 2 – Router1 and Switch1**
- VLAN 60 – Testing
- VLAN 70 – Administration
- VLAN 80 – Development

## 🌐 IP Addressing and VLAN Configuration

| VLAN ID | Department | Network Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| 10 | HR | 172.16.10.0/24 | 255.255.255.0 | 172.16.10.1 |
| 20 | Operations | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1 |
| 30 | Sales | 10.10.10.0/24 | 255.255.255.0 | 10.10.10.1 |
| 60 | Testing | 172.16.20.0/24 | 255.255.255.0 | 172.16.20.1 |
| 70 | Administration | 192.168.20.0/24 | 255.255.255.0 | 192.168.20.1 |
| 80 | Development | 10.10.20.0/24 | 255.255.255.0 | 10.10.20.1 |

## ⚙️ Network Configuration

### 1. VLAN Creation and Switch Configuration

Created six VLANs across two switches and assigned access ports to their respective departments.

Configured trunk ports to carry multiple VLANs between switches and routers.

### 2. Inter-VLAN Routing

Implemented Router-on-a-Stick using subinterfaces on both routers.

Configured:
- IEEE 802.1Q encapsulation.
- VLAN-specific IP addresses.
- Default gateways for each VLAN.

### 3. Static Routing

Configured static routes between Router0 and Router1 to enable communication between networks connected to different routers.

### 4. Extended Access Control Lists (ACLs)

Implemented Extended ACLs to permit communication between selected VLAN pairs while blocking other inter-VLAN traffic.

## 🔐 Communication and Access Control Policy

The following communication rules are implemented:

### Allowed Communication

| Source VLAN | Destination VLAN | Action |
|---|---|---|
| VLAN 10 (HR) | VLAN 60 (Testing) | PERMIT |
| VLAN 60 (Testing) | VLAN 10 (HR) | PERMIT |
| VLAN 70 (Administration) | VLAN 30 (Sales) | PERMIT |
| VLAN 30 (Sales) | VLAN 70 (Administration) | PERMIT |
| VLAN 80 (Development) | VLAN 10 (HR) | PERMIT |
| VLAN 10 (HR) | VLAN 80 (Development) | PERMIT |

### Restricted Communication

All other inter-VLAN communication is denied through Extended ACL rules and the implicit deny mechanism.

**Note:** The access control policy applies to inter-VLAN IPv4 traffic. Communication within the same VLAN is not restricted by these router ACLs.

## 🧪 Testing and Verification

The following commands are used to verify the network configuration.

### VLAN Verification

```bash
show vlan brief
```

### Trunk Verification

```bash
show interfaces trunk
```

### Router Interface Verification

```bash
show ip interface brief
```

### Routing Table Verification

```bash
show ip route
```

### ACL Verification

```bash
show access-lists
```

### Connectivity Testing

```bash
ping <destination-ip-address>
```

### Expected Results

| Test Scenario | Expected Result |
|---|---|
| VLAN 10 ↔ VLAN 60 | Successful |
| VLAN 30 ↔ VLAN 70 | Successful |
| VLAN 80 ↔ VLAN 10 | Successful |
| VLAN 10 ↔ VLAN 70 | Blocked |
| VLAN 20 ↔ VLAN 10 | Blocked |
| VLAN 60 ↔ VLAN 70 | Blocked |
| VLAN 30 ↔ VLAN 80 | Blocked |

*Connectivity results should be verified in the Packet Tracer simulation.*

## 📂 Project Structure

```text
VLAN-Network-Segmentation-ACL/
│
├── README.md
│
├── screenshots/
│   └── network-topology.png
│
├── configurations/
│   ├── Switch0.txt
│   ├── Switch1.txt
│   ├── Router0.txt
│   └── Router1.txt
│
└── Packet-Tracer/
    └── project.pkt
```

## 💡 Key Learning Outcomes

Through this project, I gained practical experience in:

- Understanding VLANs and network segmentation.
- Configuring Cisco switches and routers.
- Implementing Router-on-a-Stick.
- Configuring 802.1Q trunking.
- Understanding and implementing static routing.
- Creating and applying Extended ACLs.
- Controlling communication between different departments.
- Troubleshooting network connectivity using Cisco CLI commands.
- Understanding basic enterprise network security.

## 🚀 Future Improvements

- Implement DHCP for automatic IP address assignment.
- Configure OSPF dynamic routing.
- Implement SSH for secure device management.
- Configure port security on access switches.
- Implement centralized network monitoring.
- Introduce redundancy and high availability.

## 👨‍💻 Author

**Computer Science and Engineering Graduate**

Interested in Cloud Computing, Networking, Linux, AWS and DevOps.

## 📌 Project Status

Completed – Network topology designed and configurations implemented in Cisco Packet Tracer.

---

**If you find this project useful, feel free to star ⭐ this repository!**
