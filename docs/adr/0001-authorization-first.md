# ADR 0001 — Authorization-first assurance
Status: proposed for PR #1 review.
Context: existing Odoo SAST tools already cover many source patterns. Differentiation in effective authorization and regression evidence remains a hypothesis.
Decision: prioritize a policy-as-code vertical slice and isolated Odoo ORM observations. Keep static analysis optional and adapter-based. Core must not import Odoo; use a versioned JSON boundary to an in-lab runner. One Python package until justified.
Consequences: requires real Odoo integration fixtures; no claims about arbitrary business methods, controllers, SQL bypass or production coverage. Benchmark may invalidate the hypothesis. Apache-2.0 original code; review Odoo addon distribution and dependency licenses separately.
