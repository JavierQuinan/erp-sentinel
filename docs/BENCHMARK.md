# Benchmark protocol v1 (not executed)
Use pinned Odoo 18 Community and PostgreSQL images, synthetic addon(s), deterministic fixtures and trusted test oracle. Each scenario has a clean baseline and controlled candidate; evaluate actual allow/deny, expected policy and static findings separately. Record commands, version/commit/digest, environment, exit codes, raw sanitized artifacts and elapsed time.
| ID | Scenario | Baseline expectation | Candidate change / expected regression |
|---|---|---|---|
| B01 | Model ACL read | deny | grant read to test group / unexpected allow |
| B02 | Additive ACL | allow | remove sole effective grant / unexpected deny |
| B03 | Global rule intersection | deny | remove limiting rule / unexpected allow |
| B04 | Group rule union | deny | add broad applicable group rule / unexpected allow |
| B05 | Implied group | deny | imply privileged group / unexpected allow |
| B06 | Company A user vs B record | deny | weaken company rule / unexpected allow |
| B07 | Shared record (company false) | allow | exclude shared records / unexpected deny |
| B08 | Allowed companies context | deny for B with A-only context | broaden context/rule under authorized test identity / unexpected allow; unauthorized company context must be rejected separately |
| B09 | Restricted field read | deny | remove field groups restriction / unexpected allow |
| B10 | Write | deny | grant write plus applicable rule / unexpected allow |
| B11 | Create | deny | grant create on otherwise valid payload / unexpected allow |
| B12 | Unlink | deny | grant unlink on disposable fixture / unexpected allow |
Include negative controls, missing fixture, invalid context, unexpected exception, unchanged baseline and malformed output. Each expected baseline must be confirmed by actual ORM tests before scoring. Fixture payloads must be valid so validation errors do not masquerade as authorization denials.
Compare odooscan (pin verified version), pylint-odoo and Security Scanner Suite if legally and technically accessible; report unsupported/not run separately. Static warnings are not equivalent to runtime proof. Per tool report TP/FP/FN/TN only for comparable cases, coverage denominator, unknowns, setup effort and repeated-run consistency. Do not penalize tools for documented out-of-scope capabilities; do not claim novelty without results.
Gate: 12 scenario oracles and controls executed; reproducible logs, independent review; missing competitor access documented. Name clearance and user discovery tracked separately. No fabricated scores.
