# Network Design and Configuration for Hotel Chain

## Overview
This project involves designing and implementing a comprehensive network solution for a local hotel chain consisting of five interconnected hotels in the Los Angeles area. The network ensures secure, efficient, and scalable communication between the hotels while accommodating staff, guests, management, and financial operations.

## Objectives
- Design a network topology connecting five hotels, each with its own subnet.
- Configure VLANs for logical segmentation and enhanced security.
- Implement OSPF as the routing protocol for dynamic and efficient routing.
- Set up DHCP to assign IP addresses dynamically within each hotel’s VLANs.
- Configure switches and routers for VLAN access and inter-VLAN routing.
- Apply security measures using Access Control Lists (ACLs) and wireless security configurations.

## Key Features
### 1. **Network Topology Design**
Each hotel is represented by a unique router and subnet:
- **H1**: 192.168.1.0/24
- **H2**: 192.168.2.0/24
- **H3**: 192.168.3.0/24
- **H4**: 192.168.4.0/24
- **H5**: 192.168.5.0/24

**Interconnecting Subnet**: 10.0.0.0/24 to link all hotels.

### 2. **VLAN Configuration**
Each hotel has VLANs tailored for different operational areas:
- **VLAN 10 (Guests)**: IP range 192.168.X.0/24
- **VLAN 20 (Staff)**: IP range 192.168.X.0/26
- **VLAN 30 (Rooms)**: IP range 192.168.X.0/27
- **VLAN 40 (Finance)**: IP range 192.168.X.0/28
- **VLAN 99 (Management)**: IP range 192.168.X.0/29

### 3. **Routing Protocol**
**OSPF (Open Shortest Path First)** was chosen for its efficiency in dynamic routing and support for larger, complex networks. Each router was configured with OSPF using commands such as:
```bash
router ospf 1
network 192.168.X.0 0.0.0.255 area 0
```

### 4. **DHCP Configuration**
Each router's DHCP configuration ensures IP addresses are dynamically assigned to devices:
```bash
ip dhcp pool VLAN10
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
```
Excluded addresses ensure essential services remain static:
```bash
ip dhcp excluded-address 192.168.10.1 192.168.10.10
```

### 5. **Switch Configuration**
Switches were configured to support VLANs and trunking for inter-switch communication:
```bash
vlan 10
name guests
vlan 20
name staff
...
int range fa0/4-8
switchport mode access
switchport access vlan 10
```

### 6. **Security Implementations**
- **ACLs** were set up to restrict access and segment traffic.
- **Wireless Security**: WPA2-PSK was configured for guest and staff networks.
- **VPN** and **IPSec** configurations ensure secure remote access and data encryption.

### 7. **Documentation and Testing**
Screenshots of the configurations and successful test results showing communication between VLANs and routers are provided in the Appendix.

## Technologies Used
- **Cisco Packet Tracer** for simulation and testing
- **Cisco 1841 Routers** and **Cisco 2950-24 Switches**
- **Cat 7 Ethernet Cables** for future-proofing and enhanced speed

## Challenges and Solutions
- **Complexity in VLAN configuration**: Detailed planning and structured subnetting were used to overcome this.
- **Ensuring security**: ACLs and secure wireless configurations minimized vulnerabilities.

## Future Improvements
- Upgrading to Layer 3 switches for more seamless inter-VLAN routing.
- Integrating advanced monitoring tools for real-time performance tracking.

## Conclusion
This project showcases a scalable, secure, and efficient network design that meets the unique needs of the hospitality industry, ensuring seamless communication, enhanced security, and future expandability.

