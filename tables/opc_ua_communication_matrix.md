# OPC UA Communication Matrix

| No. | Source | Destination | Source Zone | Destination Zone | Protocol | Access | Data | Purpose | Action |
|---:|---|---|---|---|---|---|---|---|---|
| 1 | OT-SCADA-01 | PLC-LINE1-01 | OT Production | Machine Cell | OPC UA | Read / Subscribe | Status, alarms, counters, cycle time | Monitoring and alarms | Allow controlled |
| 2 | OT-HIST-01 | OT-SCADA-01 | OT Production | OT Production | OPC UA | Subscribe | Process values, counters, energy data | Time-series storage | Allow |
| 3 | MES-SRV-01 | DMZ-OPCUA-GW-01 | IT / MES | Industrial DMZ | OPC UA | Read | Production status, part counter, reject counter, quality status | MES reporting and traceability | Allow controlled |
| 4 | MES-SRV-01 | DMZ-OPCUA-GW-01 | IT / MES | Industrial DMZ | OPC UA | Limited Write | Order number, recipe number, batch number | Production context transfer | Allow controlled |
| 5 | DASHBOARD-01 | DMZ-OPCUA-GW-01 | IT / MES | Industrial DMZ | OPC UA | Read / Subscribe | Machine status, OEE-related values, energy values | Visualization | Allow controlled |
| 6 | Office PC | PLC-LINE1-01 | Enterprise IT | Machine Cell | OPC UA / Any | None | None | No valid reason | Block |
| 7 | Unknown laptop | PLC-LINE1-01 | Unknown | Machine Cell | OPC UA / Any | None | None | Unauthorized access | Block |
| 8 | Internet | PLC-LINE1-01 | External | Machine Cell | Any | None | None | Unsafe direct access | Block |

## Documentation Principle

Every allowed OPC UA communication path should have a documented source, destination, zone, protocol, access type, data type, and purpose.

If a communication path is not required and documented, it should not be allowed.
