# Address Space and Data Model

## Overview

OPC UA should expose machine data in a structured and meaningful way.

Instead of exposing unclear internal PLC memory addresses or all PLC tags, the OPC UA Address Space should organize selected data into understandable machine-related groups.

## Example Address Space

```text
ProductionLine_01
│
└── Machine_01
    │
    ├── Status
    │   ├── Running
    │   ├── FaultActive
    │   ├── AlarmCode
    │   └── Mode
    │
    ├── Production
    │   ├── PartCounter
    │   ├── RejectCounter
    │   ├── CycleTime
    │   └── RecipeNumber
    │
    ├── Energy
    │   ├── PowerConsumption
    │   ├── Current
    │   └── Voltage
    │
    └── Robot
        ├── Ready
        ├── Fault
        └── ProgramNumber
```

## Node Types

| Node Type | Meaning | Example |
|---|---|---|
| Object Node | Represents a machine, device, line, or subsystem | Machine_01 |
| Variable Node | Represents a value | Machine_01.Status.Running |
| Folder / Group | Organizes nodes | Status, Production, Energy |

## PLC View vs OPC UA View

| PLC View | OPC UA View |
|---|---|
| DB100.DBX0.0 | Machine_01.Status.Running |
| DB100.DBX0.1 | Machine_01.Status.FaultActive |
| DB100.DBW2 | Machine_01.Status.AlarmCode |
| DB101.DBD10 | Machine_01.Production.PartCounter |
| DB101.DBD14 | Machine_01.Production.CycleTime |
| DB102.DBD20 | Machine_01.Energy.PowerConsumption |

## Design Principle

Expose structured machine data with context. Do not expose the whole PLC project or unclear internal memory.
