# SOC 2 Control Matrix — Type I Prep

Built as if preparing Meridian Payments (same fictional company as the ISO 27001 exercise) for a first SOC 2 Type I audit, scoped to the Security and Availability Trust Services Criteria. I left out Confidentiality and Privacy here since they'd need actual data flow mapping I didn't have inputs for — no point faking that part.

## Security (Common Criteria)

| TSC | Control Description | Implementation | Status |
|---|---|---|---|
| CC6.1 | Logical access controls restrict access to system resources | Role-based access via Okta, MFA enforced on all SaaS apps | Implemented |
| CC6.2 | New user access is authorized before provisioning | Access requests go through manager approval in the ticketing system | Implemented |
| CC6.3 | Access is removed in a timely manner upon termination | Offboarding checklist, verified same-day for last 5 departures | Implemented |
| CC6.6 | Boundary protections restrict unauthorized access | AWS security groups + NACLs, but rules haven't been reviewed since initial setup | Partially implemented |
| CC6.7 | Data transmission is protected | TLS 1.2+ enforced on all external endpoints | Implemented |
| CC6.8 | System is protected against malicious code | Endpoint protection on laptops, none on EC2 instances | Partially implemented |
| CC7.2 | Anomalies are monitored and evaluated | No centralized alerting; CloudWatch exists but nobody's assigned to watch it | Not implemented |
| CC7.3 | Security incidents are evaluated and responded to | IR runbook drafted but never tested with a tabletop exercise | Partially implemented |
| CC8.1 | Changes to infrastructure are authorized and tested | No formal change management; deploys go straight from a dev's laptop | Not implemented |

## Availability

| TSC | Control Description | Implementation | Status |
|---|---|---|---|
| A1.1 | Capacity is monitored to meet availability commitments | Basic CloudWatch metrics, no forecasting or capacity planning | Partially implemented |
| A1.2 | Environmental protections, backup, and recovery are in place | Daily DB backups exist, restore has never been tested | Partially implemented |
| A1.3 | Recovery plans are tested | No DR test has ever been performed | Not implemented |

## Readiness summary

Of the 12 controls scoped, **4 are fully implemented**, **6 are partial**, and **2 are effectively absent**. An auditor doing a Type I assessment (design of controls, at a point in time) would likely flag CC8.1 (no change management) and CC7.2 (no monitoring) as the two biggest blockers — those aren't things you can paper over with a policy doc, they need actual process and tooling before an assessor would sign off.

## What I'd recommend before scheduling an actual audit
- Stand up basic change management first — even a lightweight PR-approval requirement is a big jump from "no process"
- Get someone explicitly assigned to review alerts/logs on a cadence, and document that assignment
- Run one DR restore test and one IR tabletop exercise before the audit, not after — auditors ask for evidence these happened, not just that a plan exists

This exercise is really where I noticed GRC and hands-on engineering overlap the most: half of these gaps aren't policy problems, they're "nobody built the tooling yet" problems.
