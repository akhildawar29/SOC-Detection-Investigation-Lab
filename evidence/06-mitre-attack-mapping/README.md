# MITRE ATT&CK Mapping

## Objective

Map the observed Windows endpoint activity identified during the SOC investigation to relevant MITRE ATT&CK techniques.

## Identified Techniques

| MITRE ATT&CK ID | Technique | Evidence Observed |
|---|---|---|
| T1059.001 | PowerShell | PowerShell execution identified through Sysmon Event ID 1 and analysed in Splunk. |
| T1059.003 | Windows Command Shell | Command-line execution activity observed through Windows process creation telemetry. |
| T1016 | System Network Configuration Discovery | Network discovery commands were identified during investigation of endpoint activity. |
| T1571 | Non-Standard Port | Network-related activity was reviewed for communication over non-standard ports. |
| T1105 | Ingress Tool Transfer | `curl.exe` activity demonstrated command-line retrieval of remote content and was correlated with Sysmon telemetry. |

## Evidence Sources

The ATT&CK mapping was supported by:

- Sysmon Event ID 1 — Process Creation
- Sysmon Event ID 22 — DNS Query
- Splunk process and command-line searches
- PowerShell investigation
- DNS and network correlation
- System and network discovery analysis

## Analysis

The investigation demonstrates how endpoint telemetry can be translated into behavioural indicators rather than relying only on individual alerts.

Process creation, command-line activity, PowerShell execution, DNS queries, and network-related events were correlated to reconstruct activity on the Windows endpoint. These behaviours were then mapped to relevant MITRE ATT&CK techniques to provide a standardized framework for describing the observed activity.

MITRE ATT&CK mapping helps SOC analysts communicate findings consistently and connect technical evidence with adversary behaviours and detection opportunities.

## Conclusion

The investigation identified multiple behaviours relevant to MITRE ATT&CK, including PowerShell execution, command-shell activity, network discovery, network communication, and remote content retrieval. Correlating these behaviours across Sysmon and Splunk provides stronger investigative context than analysing individual events in isolation.
