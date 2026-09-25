# Threat Model

## Assets
- Corporate staff systems
- Ticketing and point-of-sale systems
- CCTV/security infrastructure
- Network devices and management interfaces
- Public guest wireless network

## Key Threats
1. A guest device attempts to reach internal POS systems.
2. A guest device attempts to access CCTV/security infrastructure.
3. A compromised public device scans internal stadium networks.
4. Poor segmentation allows movement from a low-trust wireless network into higher-trust systems.

## Security Approach
The design separates systems into VLANs based on business function and trust level. An extended ACL at the VLAN 40 gateway prevents the public guest network from initiating traffic toward internal stadium VLANs.

## Residual Risk
This lab focuses on Layer 3 segmentation and ACL enforcement. A production stadium would additionally use firewalls, NAC, secure wireless authentication, endpoint security, centralized logging/SIEM, IDS/IPS, redundant infrastructure, and dedicated management networks.
