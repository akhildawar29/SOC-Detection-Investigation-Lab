# Essential Eight — Relevance and Gap Mapping

**Scope:** Mapping the SOC Detection & Investigation Lab to the Australian Cyber Security Centre (ACSC) Essential Eight mitigation strategies. This is a **conceptual alignment and gap assessment**, not an Essential Eight compliance audit, maturity-level claim or record of eight implemented controls.

| Essential Eight strategy | Relationship to this lab | Demonstrated? / Gap |
|---|---|---|
| Application control | Process-creation telemetry could help investigate execution of unapproved programs. | **Monitoring concept only.** No application allowlisting policy was implemented or tested. |
| Patch applications | Up-to-date applications reduce exploitable exposure. | **Not assessed.** The lab did not audit application patch coverage or patch SLAs. |
| Configure Microsoft Office macro settings | Macro restrictions help limit malicious code execution through Office documents. | **Not assessed.** No Office macro control was configured or tested. |
| User application hardening | Browser and application restrictions can reduce attack surface. | **Not assessed.** Network inspection is not proof of application hardening. |
| Restrict administrative privileges | Process ancestry and command-line evidence can help investigate potentially privileged activity. | **Investigation relevance only.** No least-privilege design or privileged access review was validated. |
| Patch operating systems | Operating-system updates are a core mitigation. | **Partial lab maintenance context only.** No formal OS patch-compliance assessment or remediation SLA evidence. |
| Multi-factor authentication | MFA reduces risk from compromised credentials. | **Not assessed.** The lab did not deploy or test MFA. |
| Regular backups | Tested recoverability helps restore systems after incidents. | **Not assessed.** VMware snapshots support lab recovery but are not a substitute for a tested backup strategy. |

## What the project does demonstrate
The project demonstrates **security monitoring and investigation capabilities** that may support detection and validation around several mitigation strategies: Sysmon telemetry, Splunk searches, parent-child process analysis, DNS/network correlation, ATT&CK behavioural mapping, and cautious analyst reporting. These are complementary capabilities, not evidence that Essential Eight controls have been implemented.

## Suggested follow-on validation (not performed)
To assess an organisation's Essential Eight maturity, separately gather policy and configuration evidence for each mitigation strategy, test implementation against the applicable ACSC maturity model, document gaps, and obtain control-owner validation. In particular, test application allowlisting, privileged access, patch compliance, MFA and restoration from backups using authorised systems and documented criteria.

**Reference:** Australian Cyber Security Centre (ACSC), *Essential Eight* and *Essential Eight Maturity Model*. Consult the current official guidance before using this note in a formal assessment: https://www.cyber.gov.au/resources-business-and-government/essential-cyber-security/essential-eight
