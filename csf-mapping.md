# NIST CSF 2.0 Control Mapping — Sample Exercise

Scenario: Fictional mid-size fintech company ("Meridian Payments") preparing for its first formal cybersecurity maturity assessment.

| Function | Category | Subcategory | Current State | Target State | Gap / Notes |
|---|---|---|---|---|---|
| Identify | Asset Management | ID.AM-01: Inventory of hardware assets maintained | Spreadsheet, manually updated | Automated CMDB | No real-time visibility; laptops go untracked after issue |
| Identify | Risk Assessment | ID.RA-01: Vulnerabilities identified and documented | Ad hoc scans, no central log | Scheduled scans + tracked remediation SLAs | No formal vuln management program |
| Protect | Identity Mgmt | PR.AA-01: Identities and credentials managed | Local AD, no MFA on legacy apps | MFA enforced org-wide | Legacy finance app blocks MFA rollout |
| Protect | Data Security | PR.DS-01: Data-at-rest protected | Partial (DB encryption only) | Full disk + DB + backup encryption | Backups stored unencrypted on NAS |
| Detect | Continuous Monitoring | DE.CM-01: Network monitored for anomalies | Firewall logs only | SIEM with correlation rules | No centralized log aggregation |
| Respond | Incident Response | RS.MA-01: IR plan exists and is tested | Written plan, never tested | Annual tabletop exercise | Plan is 2 years old, contact list outdated |
| Recover | Recovery Planning | RC.RP-01: Recovery plan tested | Backups exist, restore untested | Quarterly restore test | Unknown actual RTO/RPO |

## How I scored current state
Each subcategory was rated against a simple 0–4 maturity scale (0 = nonexistent, 4 = optimized/automated), based on the kind of evidence an auditor would typically ask for — documented process, actual tooling, and proof of testing.

## Takeaway
The biggest gaps clustered in Detect and Recover — the org had reasonable preventive controls but almost no way to know if something went wrong or to prove recovery would actually work. This is a common pattern in smaller orgs that spend their whole security budget on prevention.
