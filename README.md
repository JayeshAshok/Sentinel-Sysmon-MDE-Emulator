# Sentinel Defender Sysmon

This project recreates Microsoft Defender XDR Advanced Hunting tables using Sysmon logs collected into Microsoft Sentinel.

## Supported Tables

- DeviceProcessEvents
- DeviceNetworkEvents
- DeviceFileEvents
- DeviceRegistryEvents
- DeviceImageLoadEvents

## Requirements

- Azure Monitor Agent
- Sysmon
- WindowsEvent table

## Installation

1. Install Sysmon
2. Configure AMA
3. Enable WindowsEvent collection
4. Create all KQL functions