# PowerShell Activity Investigation

## Objective

Investigate PowerShell execution activity using Microsoft Sysmon telemetry in Splunk Enterprise and identify suspicious command-line behaviour, child-process activity, and related network events.

## Data Sources

- Microsoft Sysmon
- Sysmon Event ID 1 — Process Creation
- Sysmon Event ID 22 — DNS Query
- Splunk Enterprise
- Windows 11 endpoint

## Investigation

PowerShell activity was investigated in Splunk using Sysmon telemetry. Process creation events were reviewed to identify PowerShell execution and inspect command-line arguments, parent-child process relationships, and associated system activity.

The investigation was expanded by correlating PowerShell execution with DNS telemetry to determine whether the process generated related network activity.

## Key Findings

- PowerShell execution was successfully identified through Sysmon process creation telemetry.
- Command-line activity was visible within Splunk and could be used to investigate execution behaviour.
- Parent-child process relationships provided additional context around process execution.
- Sysmon DNS telemetry provided visibility into network activity associated with the investigation.
- Correlating process and network telemetry demonstrated how multiple Sysmon event types can be used to reconstruct endpoint activity.

## MITRE ATT&CK Mapping

**T1059.001 — Command and Scripting Interpreter: PowerShell**

PowerShell is a legitimate Windows administration tool that can also be abused by threat actors to execute commands and scripts. Monitoring PowerShell process creation and command-line arguments can help identify suspicious execution patterns.

## Analyst Takeaway

A single process event provides useful evidence, but stronger investigation comes from correlating process execution, command-line information, parent-child relationships, and network telemetry. This demonstrates a practical SOC workflow for moving from an initial execution event to broader endpoint investigation.
