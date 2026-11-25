# ERP Sentinel roadmap
Status: authorization-first proposal, pending PR #1 review and benchmark evidence. No functional release.
| Phase | Deliverable | Exit gate |
|---|---|---|
| P0 | Competitive benchmark, threat model, ADR, license review, isolated Odoo 18 lab | 12 scenario oracles and controls; documented competitor results and limitations; approved scope |
| P1 | Strict policy contract, CLI and effective authorization runner | Real ORM assertions, deterministic evidence, fail-closed errors, isolated fixtures |
| P2 | Baseline/candidate Security Diff | Comparable provenance, regression classification and reproducible tests |
| P3 | Optional SAST adapters, CI and first public release | License/name clearance, independent review, lint/types/tests, packaging and documented coverage |
| P4 | Agent/MCP governance | Scoped identities, approvals, deny-by-default and adversarial tests |
| P5 | Forensic evidence | Redacted events, signed manifests, verification and custody documentation |
| P6 | Web console | Local-first dashboard, RBAC, tenant isolation and retention |
| P7 | Expansion | Validated versions, migration/compliance rules and additional ERP adapters only after demand |
MVP non-goals: cloud, LLM dependency, automatic remediation, production scanning, generic SAST rewrite, SAP integration or compliance certification.
Delivery: one scoped issue and reviewable PR per work packet. No unverified coverage claims. Name clearance before public package release; demand validation separately tracked. See docs/BENCHMARK.md and docs/POLICY_CONTRACT.md.
