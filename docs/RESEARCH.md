# P0-01 competitive research — 2026-11-25

Status: desk research completed; benchmark and naming clearance pending. Conditional GO: prioritize authorization regression verification rather than another general SAST engine.

## Evidence matrix
| Project / source | License evidence | Observed capability | Decision |
|---|---|---|---|
| [avanserv/odooscan](https://pypi.org/project/odooscan/) / [rules](https://avanserv.github.io/odooscan/rules/) | MIT per PyPI | 0.16.0 released 2026-11-20; cross-module indexing, Python/XML/CSV/JS, access and data-flow rules | Highest priority benchmark; evaluate external adapter, not a rewrite |
| [OCA/pylint-odoo](https://github.com/OCA/pylint-odoo) | Verify pinned LICENSE | Odoo-specific lint checks, including version awareness | Compare rule overlap |
| [Cyberwave OdooScan](https://github.com/cyberwave-odoo/odooscan) | Noncommercial use described in documentation; verify terms | Black-box scanning and vulnerability database | Reference only pending license review |
| [Security Scanner Suite](https://apps.odoo.com/apps/modules/18.0/security_scanner_suite) | LGPL-3.0 per listing | Access verification, source scanning and insecure route detection | Benchmark exact runtime capabilities |
| [Odoomap](https://github.com/kamikazewinner/odoomap) | Unverified | Modular external vulnerability scanning | Not MVP scope |
| [Odoo security skill](https://github.com/odoo/odoo/blob/20.0/skills/odoo-security/SKILL.md) | Verify file/repository terms | AI-assisted security review guidance | Reference; not deterministic proof |
| [OCA auditlog](https://apps.odoo.com/apps/modules/18.0/auditlog) | AGPL-3 | Model operation logging, Odoo 18 | Future integration, no copying |
| [OpenUpgrade](https://github.com/OCA/OpenUpgrade) | Module-specific licenses | Migration analysis and scripts | Future complementary integration |
| [Bandit](https://github.com/PyCQA/bandit) | Apache-2.0 | Python security analysis | Optional adapter |
| [Semgrep CE](https://github.com/semgrep/semgrep) | LGPL-2.1 engine; [maintained rule restrictions](https://semgrep.dev/blog/2024/important-updates-to-semgrep-oss) | Pattern-based analysis | Own rules only unless separately licensed; optional external engine |
| [erpipe MCP](https://github.com/erpipe-org/mcp-odoo/blob/main/llms-install.md) | Unverified | Read-only default, gated writes | Future benchmark; approvals alone not novel |
| [ivnvxd MCP](https://github.com/ivnvxd/mcp-server-odoo) | Unverified | MCP permission controls and development bypass modes | Future benchmark |

Except odooscan release above, current releases and exact supported versions have not been pinned. Documentation claims are not independent execution results.

## Differentiation hypothesis
Define expected access as policy-as-code (role, user, company, model, operation, record fixture, expected allow/deny). Run isolated Odoo ORM checks using actual identities; compare baseline vs candidate addons; correlate unexpected grants/denials to ACL/group/rule configuration and static findings. Emit deterministic evidence and CI gates. Do not claim causality where unsupported. Unknown or skipped cases must not count as passes. Odoo's [security semantics](https://www.odoo.com/documentation/18.0/developer/reference/backend/security.html) and [multi-company guidance](https://www.odoo.com/documentation/18.0/developer/howtos/company.html) are normative inputs for the adapter. No production writes; synthetic lab only for mutation tests.

## Benchmark gate
Pin versions and licenses; create 12 synthetic policy scenarios including global/group rule composition, implied groups, shared records, company context, field restrictions and expected denials. Compare detection, false positives, unknown coverage and reproducibility against odooscan and Security Scanner Suite where legally/technically feasible. Document commands and results; no fabricated metrics. Seek feedback from at least three Odoo maintainers/partners before claiming demand.

## Name
GitHub search returned existing akshayareddy13/ERP-Sentinel and nsandovala/erp_sentinel, among others. Exact PyPI URL could not be fetched; availability is unknown. A related US mark, SENTINEL SOFTWARE (registration 5394543), covers ERP/security software per https://trademarks.justia.com/873/95/sentinel-87395751.html ; current status and confusing similarity not verified. Keep existing repo name provisional; check official USPTO, EUIPO, WIPO and SENADI records and PyPI before release. No trademark clearance inferred.

## Decision
Retain Apache-2.0 for original code; no third-party redistribution until pinned license review. Propose moving policy regression vertical slice into P1, with minimal static import/normalization, rather than requiring ten duplicated SAST rules. P0-01 remains open until benchmark and clearance gates are satisfied. No code or tests executed in this desk research.
