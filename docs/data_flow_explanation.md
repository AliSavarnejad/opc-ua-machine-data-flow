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

## Subscription and Data Update Considerations

In OPC UA, clients can subscribe to selected values instead of continuously polling all data. Subscription-based communication helps reduce unnecessary communication load and allows clients to receive updates based on configured parameters.

Important configuration concepts include:

| Parameter | Meaning |
|---|---|
| SamplingInterval | How often the server checks the value of a monitored item |
| PublishingInterval | How often the server publishes notifications to the client |

The correct values depend on the use case. Fast-changing process values, alarms, counters, and reporting data may require different update rates. A real implementation must balance data freshness, network load, server load, and operational requirements.

Purpose: visualization, KPI monitoring, and management overview.

Access type: Read / Subscribe.
