# Sentinel Defender Sysmon

This project recreates Microsoft Defender XDR Advanced Hunting tables using Sysmon telemetry collected into Microsoft Sentinel.

## Supported Tables

- DeviceProcessEvents
- DeviceNetworkEvents
- DeviceFileEvents
- DeviceRegistryEvents

## Prerequisites

- A Windows machine onboarded to Azure using Azure Monitor Agent (AMA)
- Sysmon installed and configured on the Windows machine
- A Data Collection Rule (DCR) configured to collect Sysmon events into the **Event** table of a Microsoft Sentinel Log Analytics workspace

## Installation

1. Install Sysmon on the Windows machine.
2. Install and configure the Azure Monitor Agent (AMA).
3. Onboard the Windows machine to Azure.
4. Create a Data Collection Rule (DCR) to collect:
   - Sysmon events into the **Event** table
5. In Microsoft Sentinel, create the following KQL functions:
   - `SysmonBase()`
   - `DeviceProcessEvents_Sysmon()`
   - `DeviceNetworkEvents_Sysmon()`
   - `DeviceFileEvents_Sysmon()`
   - `DeviceRegistryEvents_Sysmon()`

## Architecture

```
Sysmon Events
      │
      ▼
   Event Table
      │
      ▼
 SysmonBase()
      │
      ├── DeviceProcessEvents_Sysmon()
      ├── DeviceNetworkEvents_Sysmon()
      ├── DeviceFileEvents_Sysmon()
      └── DeviceRegistryEvents_Sysmon()
```

## Supported Sysmon Events

| Sysmon Event ID | Description | Defender Table |
|----------------:|------------|----------------|
| 1 | Process Create | DeviceProcessEvents_Sysmon |
| 3 | Network Connection | DeviceNetworkEvents_Sysmon |
| 11 | File Create | DeviceFileEvents_Sysmon |
| 12 | Registry Object Create/Delete | DeviceRegistryEvents_Sysmon |
| 13 | Registry Value Set | DeviceRegistryEvents_Sysmon |

## Notes

- The functions are designed to provide a Defender-like schema using Sysmon telemetry.
- Some Defender fields are populated with placeholder values where equivalent Sysmon telemetry is unavailable.
- Additional Sysmon Event IDs can be added in future releases to improve compatibility.