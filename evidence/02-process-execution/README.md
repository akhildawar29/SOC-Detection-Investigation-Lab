# Process Execution Investigation

## Objective

Investigate Windows process execution activity using Microsoft Sysmon telemetry ingested into Splunk Enterprise.

## Data Source

- Microsoft Sysmon
- Sysmon Event ID 1 — Process Creation
- Splunk Enterprise
- Windows 11 endpoint

## Investigation

Sysmon Event ID 1 was used to identify process creation activity and examine command-line execution, parent-child process relationships, and user context.

The investigation focused on potentially suspicious command-line activity including PowerShell execution and system discovery commands.

## Key Findings

The telemetry successfully captured:

- PowerShell process execution
- Command-line arguments
- Parent process information
- User context
- Process identifiers
- File hashes

This demonstrates how Sysmon process creation telemetry can support SOC analysts in identifying and investigating suspicious endpoint activity.

## Evidence

Supporting screenshots for this investigation are stored in this directory.
