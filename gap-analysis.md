# ISO/IEC 27001:2022 Gap Analysis

**Scope:** Fictional company "Meridian Payments" (50-person fintech), assessed against Annex A controls ahead of a planned certification push.

## Methodology
I scored each applicable Annex A control on a 0-4 maturity scale:

- **0** — Not implemented
- **1** — Ad hoc / undocumented
- **2** — Documented but inconsistently applied
- **3** — Consistently applied, some monitoring
- **4** — Fully embedded, monitored, and improved over time

Scores are based on what evidence would realistically exist — a policy doc alone doesn't get you past a 2 if nobody can show it's actually followed.

## Findings by control theme

### A.5 Organizational controls
| Control | Score | Evidence / Gap |
|---|---|---|
| A.5.1 Policies for information security | 2 | Policies exist but haven't been reviewed since being written 18 months ago |
| A.5.9 Inventory of information and assets | 1 | No formal asset inventory beyond an IT-maintained laptop list |
| A.5.23 Cloud services security | 1 | AWS account has no documented shared-responsibility mapping; nobody owns cloud security config review |
| A.5.30 ICT readiness for business continuity | 0 | No BC/DR plan exists for the core payment processing system |

### A.6 People controls
| Control | Score | Evidence / Gap |
|---|---|---|
| A.6.3 Security awareness training | 2 | Onboarding covers it once; no recurring/refresher training |
| A.6.5 Responsibilities after termination | 3 | Offboarding checklist exists and is followed, verified via sample of 5 recent departures |

### A.8 Technological controls
| Control | Score | Evidence / Gap |
|---|---|---|
| A.8.2 Privileged access rights | 2 | Admin access granted case-by-case, no periodic recertification |
| A.8.8 Management of technical vulnerabilities | 1 | Ad hoc scanning only after incidents, no scheduled cadence |
| A.8.12 Data leakage prevention | 0 | No DLP tooling; sensitive data flows are essentially untracked |
| A.8.16 Monitoring activities | 1 | Firewall and cloud logs exist but nothing centralizes or reviews them |
| A.8.24 Use of cryptography | 2 | TLS enforced externally, but database backups sit unencrypted on a NAS |

## Overall maturity
Average score across scoped controls: **1.5 / 4**

The pattern that stood out to me is fairly typical for a company this size: individual pieces of security exist (TLS, an offboarding checklist, basic firewalling) but there's no connective tissue — nobody owns the program end to end, nothing gets reviewed on a schedule, and there's no way to prove any of it is still working six months from now.

## Top 5 remediation priorities (by risk-reduction per effort)
1. Encrypt backups on the NAS — low effort, closes a real exposure (A.8.24)
2. Stand up a scheduled vulnerability scan with a tracked remediation SLA (A.8.8)
3. Build a real asset inventory, even a spreadsheet with an owner is better than nothing (A.5.9)
4. Write a minimum-viable BC/DR plan for the payment processing system specifically, not a generic template (A.5.30)
5. Centralize logging into one place someone actually looks at weekly (A.8.16)

## What I'd tell leadership
Certification readiness isn't really about hitting a score on every control — it's about being able to demonstrate the program is alive. Meridian could pass on paper with policies alone, but an auditor doing interviews would find the gaps fast. I'd push for fixing the monitoring and vulnerability management gaps before anything else, since those are the ones that actually reduce breach risk, not just audit risk.
