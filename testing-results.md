# Testing Results

| Test | Expected | Result |
|---|---|---|
| Corporate PC -> POS Server 192.168.20.10 | Allowed | PASS |
| Corporate PC -> CCTV Server 192.168.30.10 | Allowed | PASS |
| Guest PC -> VLAN 40 Gateway 192.168.40.1 | Allowed | PASS |
| Guest PC -> POS Server after ACL | Blocked | PASS |
| Guest PC -> CCTV Server after ACL | Blocked | PASS |
| ACL counters increment during guest tests | Yes | PASS |

## Notes
The Guest PC was assigned `192.168.40.50/24` with gateway `192.168.40.1` for final wireless testing. The final ACL output showed matches on the POS/CCTV deny entries and the permit entry, confirming that test traffic was processed by the ACL.
