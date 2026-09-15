# System and Network Discovery Investigation

## Objective

Investigate system and network discovery activity using Microsoft Sysmon telemetry in Splunk Enterprise and identify commands that could be used to enumerate host and network information.

## Data Sources

- Microsoft Sysmon
- Sysmon Event ID 1 — Process Creation
- Splunk Enterprise
- Windows 11 endpoint

## Investigation

Process creation telemetry was reviewed in Splunk to identify commands associated with system and network discovery.

The investigation focused on command-line execution that can reveal information about the endpoint's network configuration. Sysmon process creation events provided visibility into the executable, command line, user context, and related process information.

## Key Findings

- System and network discovery commands were visible through Sysmon process telemetry.
- Command-line information provided context about the discovery activity performed.
- Splunk enabled the activity to be searched and investigated centrally.
- Discovery commands can be legitimate administrative activity but may also appear during attacker reconnaissance.
- Process telemetry provides useful evidence for distinguishing and investigating this behaviour.

## MITRE ATT&CK Mapping

**T1016 — System Network Configuration Discovery**

This technique covers activity used to identify network configuration and settings on a compromised system. Monitoring process creation and command-line activity can help analysts identify potentially suspicious network discovery behaviour.

## Analyst Takeaway

System and network discovery is important to monitor because attackers frequently collect environmental information after gaining access to an endpoint. Sysmon and Splunk provide analysts with the process and command-line visibility required to investigate this behaviour and place it within the broader incident timeline.
