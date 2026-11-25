# Architecture proposal

The core is ERP-independent; the first adapter targets Odoo 18 Community. Use Python 3.11+ for the standalone CLI (validate runtime compatibility separately). Proposed stack: Typer, pytest, Ruff, mypy; optional Semgrep integration only after license and distribution review.

Pipeline: local addon discovery -> safe static parsing (Python AST, XML with external entities disabled, CSV) -> normalized facts -> versioned rules -> findings -> JSON/SARIF/text. Never import or execute untrusted addon code. Bound file sizes, traversal, symlinks and parser resources. No network or telemetry by default.

Findings include rule ID, version, severity, confidence, location, explanation and remediation. Distinguish heuristics from confirmed vulnerabilities. Stable fingerprints and deterministic output. Exit codes: 0 below threshold, 1 findings at threshold, 2 execution/configuration failure.

Runtime adapter is later and isolated; least-privilege test accounts, explicit target, read-only default, no production writes. Evidence is sensitive and must be minimized and redacted. Threat model must cover malicious repositories, parser abuse, secret disclosure and compromised dependencies.

Proposed layout: src/erp_sentinel/{core,cli,adapters/odoo,rules,reporters}; tests/{unit,fixtures,integration}; docs/adr. A single package until modularization is justified.
