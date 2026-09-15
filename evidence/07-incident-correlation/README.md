# Incident Correlation and Timeline Analysis

## Objective

Correlate process, PowerShell, DNS, and network telemetry to reconstruct the sequence of activity observed on the Windows 11 endpoint.

## Data Sources

- Microsoft Sysmon
- Sysmon Event ID 1 — Process Creation
- Sysmon Event ID 3 — Network Connection
- Sysmon Event ID 22 — DNS Query
- Splunk Enterprise
- Windows 11 endpoint telemetry

## Investigation

Individual security events provide limited context when analysed in isolation. The investigation therefore correlated process creation, command-line activity, DNS queries, and network connections to reconstruct related endpoint behaviour.

Process identifiers, parent-child relationships, timestamps, command-line data, and network indicators were used to connect activity across multiple Sysmon event types.

## Correlated Activity

| Investigation Stage | Evidence |
|---|---|
| Process Execution | Sysmon Event ID 1 identified process creation and command-line activity. |
| PowerShell Activity | PowerShell execution and associated child-process behaviour were investigated. |
| DNS Activity | Sysmon Event ID 22 identified DNS queries associated with endpoint processes. |
| Network Activity | Network telemetry was reviewed to identify outbound connections and destination information. |
| Process Correlation | Process GUIDs and related fields were used to connect activity across multiple events. |
| MITRE ATT&CK Mapping | Observed behaviours were mapped to relevant ATT&CK techniques for standardized classification. |

## Timeline Reconstruction

The investigation workflow reconstructed activity in the following sequence:

**Process Execution → Command-Line / PowerShell Activity → DNS Resolution → Network Communication → Event Correlation → MITRE ATT&CK Mapping**

This sequence demonstrates how a SOC analyst can pivot between endpoint events to develop a broader understanding of potentially suspicious behaviour.

## Key Finding

Correlation provided substantially more context than reviewing individual events independently. Process execution telemetry established what ran on the endpoint, while DNS and network telemetry helped identify subsequent communication activity.

Using timestamps and process identifiers allowed related events to be connected into a coherent investigative timeline.

## Conclusion

The investigation demonstrates a structured SOC workflow in which multiple telemetry sources are correlated to reconstruct endpoint activity. Combining Sysmon and Splunk enabled process, DNS, and network events to be analysed as part of a single investigation rather than as isolated security events.
