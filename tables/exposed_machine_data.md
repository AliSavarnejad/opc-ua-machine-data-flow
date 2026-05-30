# Exposed Machine Data

## Recommended Data to Expose

| Category | Data | Purpose | Typical Access |
|---|---|---|---|
| Status | Running | Machine monitoring | Read / Subscribe |
| Status | FaultActive | Alarm handling | Read / Subscribe |
| Status | AlarmCode | Diagnostics | Read / Subscribe |
| Status | Mode | Operator and system visibility | Read |
| Production | PartCounter | Production tracking | Read / Subscribe |
| Production | RejectCounter | Quality tracking | Read / Subscribe |
| Production | CycleTime | Performance monitoring | Read / Subscribe |
| Energy | PowerConsumption | Energy monitoring | Read / Subscribe |
| Energy | Current | Electrical monitoring | Read |
| Energy | Voltage | Electrical monitoring | Read |
| Robot | RobotReady | Robot status | Read / Subscribe |
| Robot | RobotFault | Robot diagnostics | Read / Subscribe |
| Robot | ProgramNumber | Production context | Read |
| MES Context | OrderNumber | Traceability | Read / Limited Write |
| MES Context | RecipeNumber | Production context | Read / Limited Write |
| MES Context | BatchNumber | Traceability | Read / Limited Write |

## Data That Should Not Be Exposed Openly

| Data | Reason |
|---|---|
| Safety logic internals | Safety-critical |
| Drive enable commands | Can affect movement |
| Robot start commands | Dangerous if uncontrolled |
| Manual override bits | High operational risk |
| Temporary PLC variables | Not useful for higher-level systems |
| Every DB tag | Lazy and unsafe design |
| Internal memory bits | Hard to understand and risky |
| Test bits | Can create confusion or risk |
| Unclear internal flags | Weak documentation and unclear purpose |

## Design Principle

Expose only useful, documented, necessary data. Do not expose the whole PLC project.
