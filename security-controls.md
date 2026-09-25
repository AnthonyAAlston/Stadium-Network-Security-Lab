# Security Controls

## VLAN Segmentation
Corporate, POS, CCTV/security, and guest devices are separated into four VLANs.

## 802.1Q Trunk
The switch-to-router connection carries VLANs 10, 20, 30, and 40.

## Extended ACL
`GUEST_ISOLATION` blocks VLAN 40 from initiating traffic to VLANs 10, 20, and 30.

## Addressing
Infrastructure servers use predictable static addresses. End-user wired systems use DHCP. The Guest PC used a static address for the final wireless test after Packet Tracer wireless DHCP did not complete successfully.

## Validation
Connectivity tests confirmed authorized internal routing and blocked guest-to-sensitive-network access. ACL match counters provided additional evidence that the filtering rules processed the test traffic.
