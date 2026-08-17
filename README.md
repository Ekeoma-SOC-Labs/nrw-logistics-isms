# NRW Logistics GmbH — ISO/IEC 27001:2022 ISMS Implementation

A full Information Security Management System (ISMS) build for a fictional mid-size logistics company, developed as a hands-on GRC analyst portfolio project. The goal was to build every core ISMS artifact the way an organization actually would — starting from scope, driving a risk assessment, mapping that risk assessment into a Statement of Applicability, and closing the loop with the policies those controls require — rather than producing disconnected, templated documents.

**Fictional scenario:** NRW Logistics GmbH is a road freight and warehousing company headquartered in Dortmund, with a distribution center in Witten, Germany. It relies on a Warehouse Management System, a cloud-hosted ERP platform (Azure), and a fleet telematics system for daily operations.

## Why this project

Most portfolio projects show a single tool or a single document. This one is deliberately structured to demonstrate **traceability** — the thing auditors, hiring managers, and interviewers actually look for in a GRC candidate: can you show *why* a control was selected, not just that it exists?

Every artifact in this repo links back to the one before it:

```
ISMS Scope  →  Risk Register  →  Statement of Applicability  →  Policies
 (Ph. 1)         (Ph. 2)              (Ph. 3)                   (Ph. 4)
```

A risk identified in Phase 2 (e.g. *R-011 — VPN without MFA*) is treated by a specific Annex A control in Phase 3 (*8.5 — Secure authentication*), which is implemented by a specific policy statement in Phase 4 (*Access Control Policy, §3.3*). Nothing in this repo exists in isolation.

## Repository structure

```
nrw-logistics-isms/
├── phase1-scope-document/
│   ├── NRW-Logistics-ISMS-Scope.docx
│   └── scope-boundary.png
├── phase2-risk-assessment/
│   └── NRW-Logistics-Risk-Register.xlsx
├── phase3-statement-of-applicability/
│   └── NRW-Logistics-Statement-of-Applicability.xlsx
├── phase4-policies/
│   ├── Information-Security-Policy.docx
│   ├── Access-Control-Policy.docx
│   ├── Acceptable-Use-Policy.docx
│   ├── Incident-Management-Policy.docx
│   └── Backup-and-Recovery-Policy.docx
└── screenshots/
```

## Phase 1 — ISMS Scope Document

Defines the ISMS boundary per Clause 4.3: organizational context, interested parties (Clause 4.2), the four in-scope systems (HQ network, WMS, fleet telematics, cloud ERP), and three explicitly justified exclusions (outsourced payroll, guest Wi-Fi, third-party customs broker), each with a boundary diagram.

**Skills demonstrated:** scope definition, stakeholder analysis, exclusion justification (a common audit weak point when done poorly).

## Phase 2 — Risk Register

A quantitative risk assessment covering 12 risks across every in-scope system, using **SLE × ARO methodology**:

- Single Loss Expectancy (SLE) = Asset Value × Exposure Factor
- Annualized Loss Expectancy (ALE) = SLE × Annualized Rate of Occurrence

Every risk carries both an **inherent** rating (before treatment) and a **residual** rating (after the recommended control), with live formulas — not hardcoded values — so the workbook recalculates if assumptions change. Includes a full methodology tab explaining the reasoning behind quantitative risk scoring and the four ISO 27001 treatment options (Mitigate, Transfer, Accept, Avoid).

**Skills demonstrated:** quantitative risk analysis, financial risk framing, treatment decision-making (including a documented risk *acceptance*, not just mitigation).

## Phase 3 — Statement of Applicability

All **93 Annex A controls** from ISO/IEC 27002:2022, each with an applicability decision, a justification, an implementation status, and — where relevant — a direct reference back to the risk register entry it treats. 83 controls are applicable; 10 are excluded, all clustered around software development activities NRW Logistics doesn't perform (no in-house coding, so SDLC, secure coding, and dev/test/prod separation controls don't apply). Includes a formula-driven summary dashboard.

**Skills demonstrated:** Annex A control mapping, defensible applicability reasoning, audit-ready documentation structure.

## Phase 4 — Policies

Five core ISMS policies, each structured with purpose, scope, numbered policy statements, roles and responsibilities, and an explicit **Related Risks and Controls** table linking back to Phases 2 and 3:

| Policy | Primary risks addressed |
|---|---|
| Information Security Policy | All (top-level governance) |
| Access Control Policy | R-004, R-006, R-010, R-011 |
| Acceptable Use Policy | R-001, R-005 |
| Incident Management Policy | R-001, R-002, R-006, R-009, R-011 |
| Backup and Recovery Policy | R-002, R-009 |

**Skills demonstrated:** policy writing, regulatory awareness (GDPR Article 33's 72-hour breach notification clock is reflected directly in the Incident Management Policy), translating technical controls into operational requirements.

## Methodology notes

Both the Risk Register and Statement of Applicability include a dedicated "Methodology & Notes" tab explaining the reasoning behind the numbers and decisions — these were built as part of the learning process for this project and are included for transparency into the thinking behind each artifact, not just the output.

## Disclaimer

NRW Logistics GmbH is a fictional entity created for this portfolio project. All figures, risks, and organizational details are illustrative.

## Author

Built by Ekeoma Eneogwe as part of a cybersecurity/GRC portfolio, alongside a related [ServiceNow IRM implementation project](https://github.com/Ekeoma-SOC-Labs/servicenow-irm-risk-assessment) and a [SOC blue-team lab](https://github.com/Ekeoma-SOC-Labs/SOC-Blue-Team-Lab).
