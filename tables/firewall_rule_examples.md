# Firewall Rule Examples

These rules are conceptual examples. Exact firewall rules must be validated for the real plant network, real OPC UA endpoints, actual ports, and vendor-specific configuration.

OPC UA commonly uses port 4840, but real systems may use configured or vendor-specific ports. The actual project configuration should always be documented.

| Rule | Source Zone | Source | Destination Zone | Destination | Protocol / Port | Action | Reason |
|---:|---|---|---|---|---|---|---|
| 1 | OT Production | OT-SCADA-01 | Machine Cell | PLC-LINE1-01 | OPC UA / 4840 example | Allow controlled | SCADA monitoring |
| 2 | OT Production | OT-HIST-01 | OT Production | OT-SCADA-01 | OPC UA / configured port | Allow | Historian storage |
| 3 | IT / MES | MES-SRV-01 | Industrial DMZ | DMZ-OPCUA-GW-01 | OPC UA / configured port | Allow controlled | MES production data |
| 4 | IT / MES | DASHBOARD-01 | Industrial DMZ | DMZ-OPCUA-GW-01 | OPC UA / configured port | Allow controlled | Dashboard visualization |
| 5 | Enterprise IT | Office PC | Machine Cell | PLC-LINE1-01 | Any | Block | No direct office-to-PLC access |
| 6 | External | Internet | Machine Cell | PLC-LINE1-01 | Any | Block | PLC must not be internet-accessible |
| 7 | Unknown | Unknown laptop | OT / Machine Cell | Any OPC UA Server | Any | Block | Unauthorized device |

## Firewall Principle

Allow only required communication. Block uncontrolled direct access to PLCs and machine-cell devices.
