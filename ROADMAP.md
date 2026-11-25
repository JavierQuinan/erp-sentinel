# ERP Sentinel roadmap

Status: proposed; no scanner implemented. Each phase requires review before release.

| Phase | Deliverable | Exit gate |
|---|---|---|
| P0 | Competitive research, threat model, ADRs, Odoo 18 Community lab, license inventory | Documented gap analysis; reproducible pinned lab; approved scope |
| P1 | Python CLI, AST/XML/CSV parsers, rule SDK, 10 initial rules | Positive/negative fixtures for each rule; deterministic JSON/SARIF; no code execution during scan |
| P2 | Effective access testing, ACL/record rules, multi-company boundaries | Isolated lab tests with least-privilege users; no production writes |
| P3 | CI integration, packaging, v0.1 public release | Lint, types, tests, dependency audit, reproducible package and documented limitations |
| P4 | Agent/MCP governance | Deny-by-default policies, scoped identity, approvals, audit and adversarial tests |
| P5 | Forensic evidence | Redacted event collection, signed manifests, verification and chain-of-custody documentation |
| P6 | Web console | Local-first API/dashboard, RBAC, tenant isolation, retention controls |
| P7 | Expansion | Verified Odoo version matrix; migration/compliance rules; other ERP adapters only after demand |

## MVP non-goals
No cloud, LLM dependency, automatic remediation, production runtime scanning, SAP integration, or compliance certification. Start with Odoo 18 only.

## Delivery
One issue and reviewable PR per work packet. Tests and docs accompany changes. Independent review precedes merge; no claims of coverage without evidence. Reassess scope after P3.
