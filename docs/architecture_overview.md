# Architecture Overview

## Overview

This document describes a conceptual OPC UA-based machine data flow for a PLC-controlled production environment.

The goal is to show how selected machine and production data can be made available to SCADA, historians, MES, dashboards, databases, and IT/OT systems in a structured and controlled way.

## Example Factory Scenario

A production line contains one PLC-controlled machine cell. The machine cell includes a PLC, HMI, drives, robot controller, sensors, actuators, and industrial I/O devices.

Selected machine data should be available for SCADA monitoring, alarm handling, historian storage, MES reporting, dashboard visualization, and production data analysis.

The main design goal is to make useful production data available without allowing uncontrolled direct access to the PLC.

## Zone-Based Architecture

```text
Machine Cell Zone
PLC / HMI / Drives / Robot
        ↓
OT Production Zone
SCADA / Historian / OPC UA Server
        ↓
Industrial DMZ
OPC UA Gateway / Data Broker
        ↓
IT / MES Layer
MES / Database / Dashboard
```

## Example Systems

| System | Zone | Role |
|---|---|---|
| PLC-LINE1-01 | Machine Cell | Machine control |
| HMI-LINE1-01 | Machine Cell | Operator interface |
| OT-SCADA-01 | OT Production | Monitoring and alarms |
| OT-HIST-01 | OT Production | Time-series storage |
| DMZ-OPCUA-GW-01 | Industrial DMZ | Controlled data exchange |
| MES-SRV-01 | IT / MES Layer | Production order and traceability |
| DASHBOARD-01 | IT / MES Layer | Production KPI visualization |

## OPC UA Server / Client Roles

| Connection | OPC UA Server | OPC UA Client | Access | Purpose |
|---|---|---|---|---|
| PLC to SCADA | PLC or PLC gateway | SCADA | Read / Subscribe | Monitoring and alarms |
| SCADA to Historian | SCADA | Historian | Subscribe | Store time-series values |
| Gateway to MES | OPC UA Gateway | MES | Read + Limited Write | Production tracking |
| Gateway to Dashboard | OPC UA Gateway | Dashboard | Read / Subscribe | KPI visualization |

## Design Principle

Higher-level systems should access selected machine data through controlled paths. Direct uncontrolled access from office PCs, unknown laptops, or external networks to PLCs should be blocked.
