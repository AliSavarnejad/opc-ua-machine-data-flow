# Security and Access Control

## Overview

OPC UA can expose machine and production data to higher-level systems. This is useful, but it must be controlled.

A secure OPC UA design should define who can connect, what data can be accessed, what the client is allowed to do, which communication paths are allowed, and which communication paths are blocked.

## Authentication and Authorization

| Concept | Meaning | Example |
|---|---|---|
| Authentication | Verifies identity | User login, certificate |
| Authorization | Defines permissions | Read-only, limited write, admin |
| Access control | Controls what can be accessed | Selected nodes only |

## Certificates

Certificates can be used to establish trust between OPC UA applications.

```text
OPC UA Client
        ↓ certificate trust
OPC UA Server
        ↓ secure channel
Allowed communication
```

## OPC UA Transport Security

OPC UA security is not only based on firewall rules, network segmentation, and user permissions. OPC UA also includes its own application-level security model.

| Concept | Meaning | Example |
|---|---|---|
| Security Mode | Defines whether OPC UA messages are protected | None, Sign, SignAndEncrypt |
| Security Policy | Defines the cryptographic algorithms used | Basic256Sha256, Aes128-Sha256-RsaOaep |
| Application Certificates | Establish trust between OPC UA client and server applications | Client and server certificates |
| Trust List | Defines which client/server certificates are trusted | Approved OPC UA clients only |

In a production environment, insecure modes such as `None` should be avoided unless there is a specific controlled reason. A stronger setup should use signed or encrypted communication, trusted application certificates, approved client/server relationships, and documented certificate handling.

This project is conceptual and does not include full certificate deployment, certificate lifecycle management, or vendor-specific OPC UA configuration.

## Access Types

| Access Type | Meaning | Risk |
|---|---|---|
| Read | Client reads the current value | Lower |
| Subscribe | Client receives value changes | Lower to medium |
| Write | Client changes a value | High |

## Recommended Access Principle

Monitoring systems should usually be read-only. Write access should be limited, documented, role-based where possible, validated inside the PLC, and restricted to selected production context values.

## Good Limited Write Examples

- OrderNumber
- RecipeNumber
- BatchNumber
- ProductionTarget
- OperatorMessage

## Dangerous Write Examples

- StartCommand
- StopCommand
- DriveEnable
- RobotStart
- ManualOverride
- Safety-related values
- Internal PLC bits

## Network Security

OPC UA security should be supported by firewall rules, network segmentation, approved client lists, blocked direct access from office IT to PLCs, blocked internet access to PLCs, and communication matrix documentation.
