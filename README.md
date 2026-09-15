# SOC-Detection-Investigation-Lab
SOC investigation lab using Splunk and Sysmon to analyze Windows endpoint telemetry, reconstruct process and network activity, map findings to MITRE ATT&amp;CK, and document incident-response evidence.

**Author:** Akhil Dawar  
**Focus:** SOC Analysis | Threat Detection | Incident Investigation | SIEM | Windows Endpoint Security

---

## Project Overview

This project demonstrates a structured Security Operations Center (SOC) investigation using **Splunk Enterprise** and **Sysmon telemetry** from a Windows 11 endpoint.

The objective was to investigate simulated suspicious activity, reconstruct the associated process and network behaviour, correlate endpoint events, map observed techniques to the **MITRE ATT&CK framework**, and document the investigation using an incident-response methodology.

Rather than relying on individual alerts, the investigation correlates process creation, parent-child relationships, command-line activity, DNS/network telemetry, and supporting Sysmon events to build an evidence-based timeline.

> **Lab Notice:** All activity documented in this repository was generated in an isolated cybersecurity lab for defensive security training and portfolio demonstration.

---

## Investigation Scenario

The investigation focused on suspicious Windows activity involving:

- PowerShell execution
- Command-shell activity
- Parent-child process relationships
- System and network discovery
- DNS/network activity
- Non-standard port activity
- Event correlation across Sysmon telemetry

A controlled marker, `INCIDENT-LAB-01`, was used during portions of the lab to distinguish simulated investigation activity from unrelated Windows background events.

---

## Lab Environment

| Component | Purpose |
|---|---|
| Windows 11 | Monitored endpoint |
| VMware Workstation | Virtualized lab environment |
| Sysmon | Endpoint telemetry collection |
| Splunk Enterprise | SIEM ingestion, search and investigation |
| PowerShell | Controlled activity generation and analysis |
| Windows Command Prompt | Process-chain testing |
| MITRE ATT&CK | Behaviour classification framework |

Primary telemetry source:

`WinEventLog:Microsoft-Windows-Sysmon/Operational`

---

## Investigation Workflow

The investigation followed a repeatable SOC workflow:

**Detect → Triage → Scope → Correlate → Reconstruct → Map → Assess → Recommend**

### 1. Detection

Sysmon telemetry was ingested into Splunk and reviewed for security-relevant Windows activity.

### 2. Triage

Initial searches focused on suspicious process execution and command-line behaviour.

### 3. Scoping

Events were narrowed using process names, Sysmon Event IDs, process relationships, command-line content, network activity, and the controlled incident marker.

### 4. Correlation

Related events were correlated using fields including:

- `ProcessGuid`
- `ProcessId`
- `ParentProcessGuid`
- `ParentProcessId`
- `Image`
- `ParentImage`
- `CommandLine`
- network and DNS fields

### 5. Timeline Reconstruction

The resulting telemetry was ordered chronologically to reconstruct the sequence of activity.

### 6. ATT&CK Mapping

Observed behaviour was mapped to relevant MITRE ATT&CK techniques based on the available evidence.

### 7. Analyst Assessment

The investigation separated confirmed telemetry from analyst interpretation and documented appropriate containment and remediation considerations.

---

## Key Findings

### PowerShell Execution

Sysmon process-creation telemetry identified PowerShell execution on the monitored Windows endpoint. Command-line evidence provided additional context for the activity and enabled subsequent event correlation.

### Process-Chain Reconstruction

Parent-child process relationships were used to reconstruct execution flow between:

`powershell.exe → cmd.exe → whoami.exe`

This demonstrated how Sysmon process metadata can be used to identify execution ancestry rather than reviewing processes in isolation.

### System / User Discovery

`whoami.exe` activity was identified during the investigation, providing evidence of user-context discovery.

### Network and DNS Activity

The investigation examined network-related Sysmon telemetry associated with the relevant process context. DNS/network evidence was correlated with process telemetry to determine which executable initiated the observed activity.

### Non-Standard Port Investigation

Network telemetry involving destination port `4444` was isolated and reviewed as part of the investigation.

The presence of a non-standard port was treated as an **investigative lead rather than standalone proof of malicious activity**, requiring correlation with process and surrounding telemetry.

---

## Selected Sysmon Telemetry

The lab examined several security-relevant Sysmon event categories, including:

| Event ID | Investigative Use |
|---:|---|
| 1 | Process creation |
| 3 | Network connection |
| 7 | Image/module load |
| 10 | Process access |
| 11 | File creation |
| 13 | Registry value modification |
| 17 | Named pipe creation |
| 22 | DNS query |
| 26 | File deletion detected |

Not every occurrence of these Event IDs represents malicious behaviour. Context and event correlation are required before reaching an analyst conclusion.

---

## MITRE ATT&CK Mapping

Observed lab behaviour was mapped to relevant ATT&CK techniques where supported by telemetry.

| Technique | ID | Evidence |
|---|---|---|
| PowerShell | T1059.001 | PowerShell process and command-line telemetry |
| Windows Command Shell | T1059.003 | `cmd.exe` execution |
| System Network Configuration Discovery | T1016 | Network configuration discovery activity |
| System Owner/User Discovery | T1033 | `whoami.exe` execution |
| Non-Standard Port | T1571 | Network activity involving port 4444 |

ATT&CK mappings in this project describe **observed behaviour** and do not independently establish malicious intent.

---

## Skills Demonstrated

This project demonstrates practical experience with:

- SOC alert triage and investigation
- Splunk Search Processing Language (SPL)
- Windows Sysmon telemetry
- SIEM-based event correlation
- Windows process analysis
- Parent-child process reconstruction
- Command-line analysis
- DNS and network investigation
- Timeline reconstruction
- MITRE ATT&CK mapping
- Indicators and observables documentation
- Evidence handling
- Incident-response reporting
- Defensive security analysis

---

## Repository Structure

```text
SOC-Detection-Investigation-Lab/
│
├── README.md
│
├── report/
│   └── SOC-Detection-Investigation-Lab-Akhil-Dawar.pdf
│
├── evidence/
│   └── splunk-screenshots/
│
├── queries/
│   └── investigation-queries.md
│
├── detections/
│   └── detection-use-cases.md
│
└── docs/
    └── investigation-notes.md
```

---

## Investigation Report

A detailed investigation report accompanies this repository and documents:

1. Executive Summary / Incident Overview
2. Investigation Scope & Environment
3. Detection and Investigation Methodology
4. Incident Timeline
5. Technical Findings & Evidence
6. Process-Chain Analysis
7. Network/DNS Analysis
8. MITRE ATT&CK Mapping
9. Indicators of Compromise / Observables
10. Analyst Assessment
11. Containment & Remediation Recommendations
12. Conclusion
13. Evidence Appendix

---

## Evidence

Supporting Splunk screenshots are maintained in the `evidence/` directory.

Evidence includes searches relating to:

- PowerShell activity
- Windows Command Shell activity
- Process ancestry
- System/user discovery
- DNS/network telemetry
- Non-standard port activity
- Sysmon event correlation
- Investigation timeline reconstruction

---

## Analyst Takeaway

The central lesson from this lab is that a suspicious event should not be assessed in isolation.

Process ancestry, command-line arguments, Sysmon Event IDs, DNS/network telemetry, timestamps, and surrounding endpoint activity must be correlated before assigning meaning to an event.

This evidence-driven approach reduces unsupported conclusions and produces a more defensible SOC investigation.

---

## Author

**Akhil Dawar**

Cybersecurity Portfolio Project  
SOC Detection & Investigation Lab
