# Data Flow Explanation

## Main Data Flow

```text
PLC / Machine Controller
        ↓
OPC UA Server
        ↓
OPC UA Client
        ↓
SCADA / Historian / MES / Dashboard / Database
```

A more controlled architecture can use a gateway or data broker:

```text
PLC / Machine Controller
        ↓
SCADA / Edge Device / Gateway
        ↓
OPC UA Gateway or Data Broker
        ↓
MES / Dashboard / Database
```

## PLC / Machine to SCADA

Typical data: MachineStatus, Running, FaultActive, AlarmCode, PartCounter, CycleTime, RobotStatus, DriveStatus.

Purpose: monitoring, alarm handling, operator visibility, and diagnostics.

Access type: Read / Subscribe.

## SCADA / PLC to Historian

Typical data: CycleTime, PartCounter, RejectCounter, EnergyConsumption, Temperature, Pressure, OperatingHours, FaultActive.

Purpose: trend storage, time-series analysis, downtime analysis, energy analysis, and quality history.

Access type: Subscribe.

## Gateway / Data Broker to MES

Typical data: OrderNumber, RecipeNumber, PartCounter, RejectCounter, ProductionStatus, BatchNumber, QualityStatus.

Purpose: production tracking, traceability, order management, and quality reporting.

Access type: Read + Limited Write.

## Gateway / Data Broker to Dashboard

Typical data: MachineStatus, ProductionCount, RejectCount, CycleTime, EnergyConsumption, OEE-related values, DowntimeStatus.

Purpose: visualization, KPI monitoring, and management overview.

Access type: Read / Subscribe.
