# Reproducible Splunk Searches

These lab-focused searches accompany the SOC Detection & Investigation Lab. They use the Sysmon Operational source and raw XML event markers documented in the investigation report. They are investigation pivots, not production-ready detection rules. Validate field extraction, index, time range, escaping and event coverage before reuse.

## 1. PowerShell process creation (Sysmon Event ID 1)
```spl
index=* source="WinEventLog:Microsoft-Windows-Sysmon/Operational" "<EventID>1</EventID>" "powershell.exe"
```

## 2. PowerShell spawning Windows Command Shell
```spl
index=* source="WinEventLog:Microsoft-Windows-Sysmon/Operational" "<EventID>1</EventID>" "cmd.exe" "ParentImage" "powershell.exe"
```

## 3. User and network discovery
```spl
index=* source="WinEventLog:Microsoft-Windows-Sysmon/Operational" "<EventID>1</EventID>" ("whoami.exe" OR "ipconfig.exe" OR "netstat.exe")
```

## 4. Controlled TCP/4444 network activity (Sysmon Event ID 3)
```spl
index=* source="WinEventLog:Microsoft-Windows-Sysmon/Operational" "<EventID>3</EventID>" "4444"
```

## 5. PowerShell web/DNS investigation pivot
```spl
index=* source="WinEventLog:Microsoft-Windows-Sysmon/Operational" ("Invoke-WebRequest" OR "example.com")
```

## Analyst workflow
1. Set a time window around the controlled test.
2. Inspect `Image`, `CommandLine`, `ParentImage`, `ParentCommandLine`, `ProcessId`, `ParentProcessId` and `ProcessGuid` in Sysmon Event ID 1.
3. Pivot on the observed `ProcessGuid` to examine related Sysmon Event ID 22 DNS queries and Event ID 3 network connections where present.
4. Compare parent/child relationships and timestamps before treating events as one sequence.
5. Document the benign context: `example.com` is a demonstration domain; TCP/4444 used `127.0.0.1` loopback.

**Important:** A command match, port number, or MITRE ATT&CK technique alignment is not proof of compromise. These SPL examples are transcribed from the final investigation report and are not represented as newly executed or independently re-tested queries.
