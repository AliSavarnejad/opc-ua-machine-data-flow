# Assumptions and Limitations

## Assumptions

- One representative PLC-controlled production line
- One machine cell
- SCADA and historian located in the OT production zone
- OPC UA gateway or data broker located in the Industrial DMZ
- MES and dashboard systems located in the IT / MES layer
- OPC UA used for selected machine and production data exchange
- Higher-level systems do not need uncontrolled direct PLC access

## Limitations

This project is conceptual and does not include vendor-specific PLC configuration, detailed OPC UA certificate setup, full cybersecurity implementation, switch configuration, routing configuration, NAT rules, redundancy design, full IEC 62443 zone/conduit analysis, real plant validation, or production-ready deployment procedures.

## Important Note

This project is intended for educational and portfolio documentation purposes. A real implementation requires plant-specific engineering validation, cybersecurity review, firewall rule validation, change management, and operational approval.
