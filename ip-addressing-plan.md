# IP Addressing Plan

| Zone | VLAN | Subnet | Gateway | Key Host |
|---|---:|---|---|---|
| Corporate | 10 | 192.168.10.0/24 | 192.168.10.1 | CORP-PC via DHCP |
| Ticketing/POS | 20 | 192.168.20.0/24 | 192.168.20.1 | POS-SERVER 192.168.20.10 |
| Security/CCTV | 30 | 192.168.30.0/24 | 192.168.30.1 | CCTV-SERVER 192.168.30.10 |
| Guest Wi-Fi | 40 | 192.168.40.0/24 | 192.168.40.1 | GUEST-PC 192.168.40.50 (final test) |

## Topology
`STADIUM-R1` connects to `STADIUM-SW1` over an 802.1Q trunk. End devices connect to access ports assigned to their functional VLAN. `GUEST-AP` bridges the wireless guest client into VLAN 40.
