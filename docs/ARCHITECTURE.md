# Architecture proposal
Authorization-first, local-first, Odoo 18 Community adapter; see ADR 0001. Standalone Python 3.11+ core, Typer, pytest, Ruff and mypy (validate compatible versions). Core does not import Odoo.
Pipeline: strict policy validation -> trusted fixture resolution -> isolated Odoo ORM runner -> versioned observations -> policy evaluation -> baseline/candidate comparison -> JSON/text report and CI gate. Optional SARIF for source-located findings only. No network or telemetry by default.
Separate disposable baseline/candidate databases; synthetic data only. Test actual operation with non-superuser identity and explicit company context; never use sudo in probes. Unknown and error fail closed. See POLICY_CONTRACT.md and THREAT_MODEL.md.
Optional static adapters import normalized findings from existing engines after license review; no executing scanned code in static analysis. Runtime addon execution is isolated and not treated as trusted attestation. Avoid causal claims based solely on correlated warnings.
Layout: src/erp_sentinel/{core,cli,adapters/odoo,reporters}; lab/odoo18; tests/{unit,fixtures,integration}; docs/adr. One package initially; no web infrastructure.
