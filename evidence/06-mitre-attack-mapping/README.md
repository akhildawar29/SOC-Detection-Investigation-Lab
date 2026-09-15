# MITRE ATT&CK Mapping

## Objective

Map the Windows endpoint activity observed during the SOC investigation to relevant MITRE ATT&CK techniques and document the evidence supporting each mapping.

## Identified Techniques

| MITRE ATT&CK ID | Technique | Evidence Observed |
|---|---|---|
| T1059.001 | PowerShell | PowerShell execution was identified through Sysmon Event ID 1 and analysed in Splunk. |
| T1059.003 | Windows Command Shell | Command-line execution activity was observed through Windows process creation telemetry. |
| T1016 | System Network Configuration Discovery | Network discovery commands were identified during investigation of endpoint activity. |
| T1571 | Non-Standard Port | Network-related activity was reviewed for communication occurring over non-standard ports. |
| T1105 | Ingress Tool Transfer | `curl.exe` was observed retrieving remote content. This behaviour is consistent with T1105 when used to transfer files or tools from an external system. |

## Evidence Sources

The ATT&CK mapping was supported by:

- Sysmon Event ID 1 — Process Creation
- Sysmon Event ID 22 — DNS Query
- Splunk process and command-line searches
- PowerShell investigation
- DNS and network correlation
- System and network discovery analysis

## Analysis

The investigation identified multiple behaviours that can be mapped to MITRE ATT&CK techniques. PowerShell and Windows command-shell activity demonstrate command and scripting interpreter usage, while system and network discovery activity reflects host reconnaissance behaviour.

Network telemetry was correlated with process activity to provide additional context around outbound communication. The observed `curl.exe` activity involved retrieval of remote content and was therefore assessed as behaviour consistent with Ingress Tool Transfer (T1105). However, the presence of `curl.exe` alone does not establish malicious intent; process context, destination, command-line arguments, and related telemetry must be considered before classifying the activity as malicious.

## Analyst Assessment

The observed activity demonstrates how endpoint process telemetry, DNS events, and network evidence can be correlated within a SOC investigation. Mapping the findings to MITRE ATT&CK provides a standard framework for describing the behaviours observed while maintaining a distinction between suspicious activity and confirmed malicious activity.
