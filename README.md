# Stadium Network Security Lab

A Cisco Packet Tracer cybersecurity project that models a segmented stadium network and demonstrates how network access controls can isolate public guest Wi-Fi from sensitive internal systems.

## Project Objective

The goal of this project was to design a small stadium network with separate security zones for corporate staff, ticketing/POS systems, security/CCTV systems, and public guest Wi-Fi. The project then tests an insecure state in which guest traffic can reach internal resources and applies an extended ACL to prevent that access.

## Network Segmentation

| VLAN | Name | Subnet | Purpose |
|---|---|---|---|
| 10 | CORPORATE | 192.168.10.0/24 | Corporate/staff systems |
| 20 | TICKETING_POS | 192.168.20.0/24 | Ticketing and point-of-sale systems |
| 30 | SECURITY_CCTV | 192.168.30.0/24 | Security and CCTV systems |
| 40 | GUEST_WIFI | 192.168.40.0/24 | Public stadium Wi-Fi |

Router-on-a-stick provides inter-VLAN routing through `STADIUM-R1`. The switch-to-router link is configured as an 802.1Q trunk.

## Final Switch Port Mapping

| Switch Port | Device | VLAN |
|---|---|---|
| Fa0/1 | CORP-PC | 10 |
| Fa0/2 | POS-SERVER | 20 |
| Fa0/3 | SECURITY-PC | 30 |
| Fa0/4 | POS-PC | 20 |
| Fa0/5 | CCTV-SERVER | 30 |
| Fa0/6 | GUEST-AP | 40 |
| Gi0/1 | STADIUM-R1 | Trunk |

## Security Control

An extended ACL named `GUEST_ISOLATION` is applied inbound to the VLAN 40 router subinterface. It denies guest traffic destined for the Corporate, Ticketing/POS, and Security/CCTV networks while permitting other guest traffic.

```text
ip access-list extended GUEST_ISOLATION
 deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255
 deny ip 192.168.40.0 0.0.0.255 192.168.20.0 0.0.0.255
 deny ip 192.168.40.0 0.0.0.255 192.168.30.0 0.0.0.255
 permit ip 192.168.40.0 0.0.0.255 any
```

## Testing and Results

Authorized internal routing was verified from the Corporate VLAN to the POS server (`192.168.20.10`) and CCTV server (`192.168.30.10`).

After the ACL was applied:

- Guest Wi-Fi -> POS server: **Blocked**
- Guest Wi-Fi -> CCTV server: **Blocked**
- Guest Wi-Fi -> VLAN 40 gateway (`192.168.40.1`): **Allowed**
- ACL counters recorded matches against the deny and permit rules.

The Guest PC used static address `192.168.40.50/24` during final wireless security testing.

## Evidence

### VLAN Segmentation
![VLAN segmentation](screenshots/vlan-segmentation.png)

### Router Interfaces
![Router interfaces](screenshots/router-interfaces.png)

### Authorized Internal Traffic
![Authorized traffic](screenshots/authorized-traffic.png)

### Guest Isolation ACL
![ACL verification](screenshots/acl-verification.png)

### Blocked Guest Access
![Blocked guest access](screenshots/guest-access-blocked.png)

## Security Concepts Demonstrated

- VLAN segmentation
- Router-on-a-stick inter-VLAN routing
- 802.1Q trunking
- Extended access control lists
- Least-privilege network access
- Guest network isolation
- Static and DHCP IPv4 addressing
- Connectivity and security-control validation

## Files

- `Stadium-Network-Security-Lab.pkt` — completed Cisco Packet Tracer lab
- `configurations/` — router, switch, and ACL configurations
- `documentation/` — threat model, security controls, and test results
- `network-design/` — addressing and network design
- `screenshots/` — evidence captured from the completed lab

## Author

Anthony Alston
