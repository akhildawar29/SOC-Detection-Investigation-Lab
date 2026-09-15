# SOC Incident Investigation Report

## SOC Detection & Investigation Lab

**Analyst:** Akhil Dawar  
**Environment:** Windows 11 Cyber Lab  
**SIEM:** Splunk Enterprise  
**Endpoint Telemetry:** Microsoft Sysmon  
**Investigation Type:** Simulated SOC Incident Investigation

---

## Report Overview

This directory contains the formal incident investigation report produced as part of the SOC Detection & Investigation Lab.

The investigation uses Windows Sysmon telemetry ingested into Splunk Enterprise to reconstruct simulated suspicious endpoint activity. Analysis focused on process execution, parent-child process relationships, PowerShell and command-line activity, system and network discovery, DNS/network telemetry, and supporting Windows endpoint events.

The investigation findings were correlated into an evidence-based incident timeline and mapped to relevant MITRE ATT&CK techniques.

## Investigation Report

The complete professional investigation report documents:

- Executive Summary / Incident Overview
- Investigation Scope & Environment
- Detection and Investigation Methodology
- Incident Timeline
- Technical Findings & Evidence
- Process-Chain Analysis
- Network/DNS Analysis
- MITRE ATT&CK Mapping
- Indicators of Compromise / Observables
- Analyst Assessment
- Containment & Remediation Recommendations
- Conclusion
- Evidence Appendix

The supporting screenshots and investigation artefacts referenced by the report are maintained separately within the repository's evidence directory.

---

**Author:** Akhil Dawar  
**Project:** SOC Detection & Investigation Lab
