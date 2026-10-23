# Executive Summary — SOC Detection & Investigation Lab

**Analyst:** Akhil Dawar  
**Environment:** Windows 11 virtual endpoint (`CYBER-LAB`) in VMware Workstation  
**Tools:** Microsoft Sysmon, Splunk Enterprise, Wireshark  
**Classification:** Controlled training exercise; no real compromise

## Objective and scope
Demonstrate a junior Security Operations Center (SOC) workflow by collecting endpoint telemetry, investigating controlled command-line and network activity, correlating events, mapping supported behaviour to MITRE ATT&CK, and producing an evidence-based assessment. The scope was one Windows 11 virtual endpoint, not an enterprise deployment.

## Approach
Sysmon Operational events were ingested into Splunk. Event ID 1 supported process creation and ancestry analysis; Event ID 3 supported process-associated network-connection review; Event ID 22 supported DNS investigation. Wireshark supplied separate packet-level DNS, HTTP and ICMP visibility. The analyst used process IDs, parent process IDs, ProcessGuid, command lines and timestamps to reconstruct related activity.

## Key findings
- Correlated controlled discovery activity (`whoami.exe`, `ipconfig.exe /all`, `NETSTAT.EXE -ano`) with shared PowerShell parent context.
- Reconstructed a `powershell.exe → cmd.exe → whoami.exe` process chain associated with the `INCIDENT-LAB-01` test marker.
- Investigated PowerShell web/DNS activity involving the benign `example.com` domain and pivoted between process creation and DNS events using process identifiers.
- Detected PowerShell-associated TCP/4444 traffic to loopback `127.0.0.1`; this was a separate test, **not** evidence of external command-and-control.

## Assessment and outcome
The activity was intentionally generated and did not establish malicious compromise. The principal result was a defensible investigation method: interpreting events in context, connecting related process and DNS telemetry, separating distinct tests, and avoiding conclusions based on isolated commands or ports. The report includes MITRE ATT&CK mappings, investigation limitations, production-response recommendations and a 34-screenshot appendix.

## Limitations and next steps
This was a single-host training lab without production EDR, identity, email, cloud, proxy or threat-intelligence corroboration. A production implementation would require tuned searches, field validation, baselines, risk-based alerting, broader telemetry and an approved incident-response process.

**Full evidence:** See the final PDF in `report/`, the curated screenshots in `evidence/`, and the queries in `queries/README.md`.
