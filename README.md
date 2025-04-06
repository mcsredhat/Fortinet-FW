# Fortinet-FW
# Fortinet Network & Security Implementation Project

## Project Overview
This project demonstrates a comprehensive network implementation using Fortinet Firewalls (FortiGate) and Palo Alto firewalls to create a secure, segmented network environment with multiple zones and VPN connectivity. The implementation includes firewall configurations, routing protocols, NAT/PAT implementations, VLAN trunking, DHCP services, and site-to-site VPN between FortiGate and Palo Alto devices.

## Network Architecture

The network consists of:

- **Multiple FortiGate Firewalls (FW1, FW2, FW3, FW4)** - Providing network segmentation and security
- **Router (R1)** - Connecting the internal network to the internet
- **Multiple VLANs** - For network segmentation
- **DMZ Zone** - For web and publicly accessible services
- **Site-to-Site VPN** - Between FortiGate and Palo Alto firewalls

### Network Segments
- **Internet Zone**: 23.1.2.0/24 
- **Internal Networks**:
  - 10.123.0.0/24 (Management)
  - 10.2.0.0/24
  - 10.3.0.0/24
  - 10.4.0.0/24
- **DMZ Network**: 172.16.1.0/24
- **Palo Alto Network**: 99.1.0.0/16

## Configuration Components

### 1. Basic Firewall Configuration
- Initial bootstrap configurations
- Interface configurations
- Management access setup
- Idle timeout settings

### 2. Network Address Translation (NAT/PAT)
- Source NAT/PAT for internal networks to access internet
- Destination NAT for external access to internal services
- Virtual IP configurations

### 3. Routing
- Static routing
- RIP protocol implementation
- OSPF routing protocol
- BGP routing between firewalls

### 4. DHCP Services
- DHCP server configuration
- IP address reservation
- DHCP relay setup

### 5. VLAN Configuration
- VLAN creation and trunking
- Interface assignment
- Switch configuration

### 6. Security Policies
- Firewall rule configuration
- Security profiles
- Application control

### 7. VPN Implementation
- Site-to-Site VPN between FortiGate and Palo Alto
- IKE/IPSec configuration
- Tunnel interface setup
- VPN security policies

## Implementation Steps

### Initial Setup
1. Basic FortiGate configuration
2. Interface and IP address assignment
3. Static route configuration for internet access

### NAT/PAT Configuration
1. Configure Source NAT for outbound traffic
2. Configure Destination NAT for inbound services
3. Test connectivity

### Routing Protocol Implementation
1. Configure RIP on internal networks
2. Set up OSPF areas and networks
3. Configure BGP between FW1 and FW4

### DHCP Server and Relay
1. Configure DHCP server on FW1
2. Set up IP address reservations
3. Configure DHCP relay on other firewalls

### VLAN Configuration
1. Create VLANs on FortiGate firewalls
2. Configure VLAN trunking with switches
3. Assign interfaces to appropriate security zones

### VPN Configuration
1. Configure FortiGate side of the VPN tunnel
2. Configure Palo Alto side of the VPN tunnel
3. Create security policies for VPN traffic

## Testing and Verification

### Basic Connectivity
```
ping 8.8.8.8
ping 10.123.0.71
execute traceroute 8.8.8.8
```

### NAT/PAT Testing
```
get system session list
```

### Routing Table Verification
```
get router info routing-table all
get router info routing-table database
get router ospf
get router info bgp network
```

### VLAN Verification
```
show vlan brief
show interfaces trunk
```

### VPN Testing
Test connectivity between networks on both sides of the VPN:
```
ping 99.1.0.100 (from FortiGate side)
ping 10.2.0.100 (from Palo Alto side)
```

## Security Considerations
- All administrative access is restricted to secure protocols
- Firewall policies follow the principle of least privilege
- Regular verification of security logs is recommended
- All sensitive data (like pre-shared keys) should be changed in production

## Troubleshooting Tips
- Verify interface status and IP addresses
- Check routing tables
- Examine security policy logs
- Use packet capture for detailed analysis
- Test connectivity at each network segment

---

