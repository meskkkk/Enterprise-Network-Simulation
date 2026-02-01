# Network Project

## Overview

This repository contains a **Cisco Packet Tracer** network simulation project. Packet Tracer is a powerful networking simulation platform used for designing, configuring, and troubleshooting network architectures.

## Project Contents

### Files

- **Network Project.pkt** - The main Packet Tracer simulation file containing the complete network topology, device configurations, and simulation scenarios

## What is Cisco Packet Tracer?

Cisco Packet Tracer is a network simulation tool that allows you to:

- Design and visualize network topologies
- Configure devices (routers, switches, PCs, servers, etc.)
- Simulate network communication and traffic
- Test configurations without physical hardware
- Learn networking concepts hands-on
- Troubleshoot network issues in a safe environment

## Getting Started

### Prerequisites

- **Cisco Packet Tracer** installed on your system
  - Download from: [Cisco Learning Network](https://learningnetwork.cisco.com/)
  - Requires Cisco account (free registration)

### Opening the Project

1. Launch **Cisco Packet Tracer**
2. Click **File → Open**
3. Navigate to this directory
4. Select **Network Project.pkt**
5. The network topology will load in the main workspace

## Network Topology

### Devices Included

- **Routers**: 3x Cisco 2901 routers for inter-site routing and connectivity
- **Switches**: 2x Cisco 2960 switches for VLAN management and layer 2 switching
- **PCs/End Devices**: 6x Client workstations across multiple departments
- **Servers**: DNS server, DHCP server, and Web server
- **Other Devices**: Printers, access points for wireless connectivity

### Network Features

- IPv4 addressing (Private network ranges)
- OSPF dynamic routing protocol
- VLAN configuration (10 VLANs total)
- DHCP services with pool allocation
- DNS server for name resolution
- Static and dynamic routes
- Basic ACLs for traffic control
- Inter-VLAN routing capability

## Key Network Segments

### Segment 1: Corporate Office (Department A)

- **Purpose**: Main corporate headquarters with administrative functions
- **IP Range**: 192.168.1.0/24
- **Devices**: Manager PCs, Admin Server, Reception Area

### Segment 2: IT Department (Department B)

- **Purpose**: IT infrastructure and network support services
- **IP Range**: 192.168.2.0/24
- **Devices**: IT workstations, DNS Server, DHCP Server

### Segment 3: Engineering Lab (Department C)

- **Purpose**: Research and development networking lab
- **IP Range**: 10.0.0.0/24
- **Devices**: Engineering workstations, Test servers, Network printers

## Device Configurations

### Routers

| Router          | Interface | IP Address    | VLAN    | Protocol |
| --------------- | --------- | ------------- | ------- | -------- |
| Core-Router     | Fa0/0     | 192.168.1.1   | VLAN 10 | OSPF     |
| Core-Router     | Fa0/1     | 192.168.2.1   | VLAN 20 | OSPF     |
| Branch-Router-B | Fa0/0     | 192.168.2.254 | VLAN 20 | OSPF     |
| Branch-Router-B | Fa0/1     | 10.0.0.1      | VLAN 30 | OSPF     |
| WAN-Router      | S0/0/0    | 200.1.1.1     | N/A     | OSPF     |

### Switches

| Switch          | Trunk Ports  | VLAN Configuration  | Description              |
| --------------- | ------------ | ------------------- | ------------------------ |
| Core-Switch-A   | Gi0/1, Gi0/2 | VLAN 10, 20, 30, 99 | Main distribution switch |
| Access-Switch-B | Gi0/1        | VLAN 20, 30         | Building B access switch |

### End Devices

| Device           | Type    | IP Address    | Default Gateway | Purpose                 |
| ---------------- | ------- | ------------- | --------------- | ----------------------- |
| Admin-PC-1       | PC      | 192.168.1.100 | 192.168.1.1     | Manager workstation     |
| Admin-PC-2       | PC      | 192.168.1.101 | 192.168.1.1     | Secretary workstation   |
| IT-Workstation-1 | PC      | 192.168.2.100 | 192.168.2.1     | IT support staff        |
| IT-Workstation-2 | PC      | 192.168.2.101 | 192.168.2.1     | Network admin           |
| Lab-PC-1         | PC      | 10.0.0.100    | 10.0.0.1        | Engineering workstation |
| Lab-PC-2         | PC      | 10.0.0.101    | 10.0.0.1        | Engineering workstation |
| DNS-Server       | Server  | 192.168.2.10  | 192.168.2.1     | DNS services            |
| DHCP-Server      | Server  | 192.168.2.11  | 192.168.2.1     | DHCP services           |
| Web-Server       | Server  | 192.168.1.50  | 192.168.1.1     | Corporate website       |
| Printer-A1       | Printer | 192.168.1.200 | 192.168.1.1     | Building A printer      |

## Simulations & Scenarios

### Scenario 1: Basic Connectivity Test

- **Objective**: Verify all devices can ping each other across the network
- **Expected Results**: All pings successful with response times between 0-10ms
- **Steps to Execute**:
  1. Open the project in Packet Tracer
  2. Switch to Simulation Mode
  3. Use the Command Prompt on Admin-PC-1
  4. Execute: `ping 10.0.0.100` to test cross-site connectivity
  5. Verify responses received from Lab-PC-1

### Scenario 2: OSPF Routing Convergence

- **Objective**: Test dynamic routing protocol functionality and convergence time
- **Expected Results**: Routers exchange OSPF hellos and routes propagate within 30 seconds
- **Steps to Execute**:
  1. Switch to Simulation Mode
  2. Open the Event List to monitor packet exchanges
  3. Observe OSPF packets being sent between routers
  4. Verify routing table entries on each router
  5. Check that all routes are learned dynamically

### Scenario 3: DHCP Client Assignment

- **Objective**: Verify DHCP server can assign IPs to client machines
- **Expected Results**: Clients receive valid IP addresses within their subnet range
- **Steps to Execute**:
  1. Set a PC to obtain IP automatically (DHCP client mode)
  2. Power on the device
  3. Open Command Prompt and run `ipconfig`
  4. Verify IP is assigned from DHCP pool (192.168.2.100-150)
  5. Check gateway and DNS settings are correctly configured

### Scenario 4: Inter-VLAN Routing

- **Objective**: Test communication between different VLANs via router
- **Expected Results**: Devices on separate VLANs can communicate through the router
- **Steps to Execute**:
  1. Setup two PCs on different VLANs (VLAN 10 and VLAN 20)
  2. Ping from VLAN 10 PC to VLAN 20 PC
  3. Observe packets routed through the core router interface
  4. Verify packets are successfully delivered

## Using Packet Tracer Features

### Running Simulations

1. Switch to **Simulation Mode** (bottom-left corner)
2. Click **Play** to start the simulation
3. Use **Add Complex PDU** or **Add Simple PDU** to simulate network traffic
4. Observe packet flow through the network

### Configuration Mode

1. Click on a device to select it
2. Go to **Config** tab to modify device settings
3. Configure IP addresses, routing protocols, DHCP servers, etc.
4. Changes take effect in real-time

### Verification Commands

- **Ping**: Test connectivity between devices
- **Tracert**: Trace the path packets take through the network
- **Show Commands**: View device configurations and routing tables

## Common Tasks

### Adding a New Device

1. Right-click on an empty area in the workspace
2. Select device type from the menu
3. Click to place the device
4. Connect with cables

### Creating a VLAN

1. Click on a switch
2. Go to **Config → VLAN** tab
3. Add new VLAN with desired ID and name
4. Assign ports to VLANs as needed

### Configuring OSPF Routing

1. Click on a router
2. Go to **Config → Routing → OSPF**
3. Enable OSPF and enter process ID
4. Configure network addresses
5. Set area IDs

### Enabling DHCP

1. Click on a server
2. Go to **Services → DHCP**
3. Enable DHCP service
4. Configure IP pool, default gateway, DNS settings

## Troubleshooting Tips

- **No Connectivity**: Check cable connections and IP addressing
- **Routing Issues**: Verify routing protocol configurations and network advertisements
- **DHCP Not Working**: Ensure DHCP server is enabled and clients are set to obtain IP automatically
- **VLAN Problems**: Verify trunk configurations and port assignments
- **DNS Resolution**: Check DNS server settings and ensure server is running

## Project Goals

- Demonstrate multi-site corporate network architecture
- Implement OSPF dynamic routing for automatic route discovery
- Configure VLAN segmentation for network organization
- Setup DHCP and DNS services for network services
- Practice inter-VLAN routing and firewall concepts
- Gain hands-on experience with Cisco network device configuration
- Learn network troubleshooting techniques and verification commands
- Understand network scalability and best practices

## Author

Networking Project Team

## Last Updated

December 10, 2025

---

**For questions or updates regarding this network project, please refer to the original project documentation or contact the project maintainer.**
