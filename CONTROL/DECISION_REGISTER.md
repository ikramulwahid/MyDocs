# MyDocs — Stage 2 Decision Register

Repository: ikramulwahid/MyDocs
Branch: main
Stage: 2 — Final Document Architecture and Identifier Control

## Resolved architecture decisions

| ID | Issue | Resolution | Evidence |
|---|---|---|---|
| RES-01 | QSP_15 identity | QSP_15 = Control of Non–Conforming Work | Current QSP filename/title |
| RES-02 | QSP_18 identity | QSP_18 = Risk Assessment | Current QSP filename/title |
| RES-03 | QSP_20 identity | QSP_20 = Internal Audit | Current QSP filename/title |
| RES-04 | QSP_21 identity | QSP_21 = Management Review | Current QSP filename/title |
| RES-05 | QSP_22 identity | QSP_22 = Procedure for Use of NABL Symbol | Current QSP filename/title |
| RES-06 | Legacy QSP namespace | Treat SMJ/QMS/QSP/... as legacy/inconsistent; target SMJ/QSP/... | Current repository naming convention |
| RES-07 | QSP_13 risk reference | Risk context targets QSP_18 | QSP_18 process identity |
| RES-08 | QSP_11 nonconforming-work reference | Nonconforming-work context targets QSP_15 | QSP_15 process identity |
| RES-09 | QSP_10 LAB placeholders | Known concrete candidates are SMJ/FRM/LAB/01/01 and SMJ/FRM/LAB/02/01 | Current Tier 4 inventory |
| RES-10 | QSP_04 OPN placeholder | Concrete candidates are SMJ/FRM/OPN/01/01–04 | Four existing equipment forms |

## Human decisions — APPROVED

The following human decisions were provided by the project owner on 6 October 2026 and are now the approved architecture decisions for execution planning. Approval here changes CONTROL artifacts only; no controlled QMS document is modified in Stage 2.

| ID | Approved decision |
|---|---|
| DEC-01 | Keep the Moisture in Coal SOP located in `SOP LAB/` as the active survivor. The duplicate Tier 3-root copy is to be removed from the active controlled tree during execution, subject to retention rules. |
| DEC-02 | Keep the Volatile Matter in Coal SOP located in `SOP LAB/` as the active survivor. The duplicate Tier 3-root copy is to be removed from the active controlled tree during execution, subject to retention rules. |
| DEC-03 | Keep the Total Ash in Coal SOP located in `SOP LAB/` as the active survivor. The duplicate Tier 3-root copy is to be removed from the active controlled tree during execution, subject to retention rules. |
| DEC-04 | Keep `FRM-SYS-17 - Risk Register new.docx` as the authoritative active Risk Register. The other `FRM-SYS-17` file is to be dispositioned as the non-authoritative duplicate during execution. |
| DEC-05 | Both existing HRD-04 competence documents are considered obsolete for the final architecture. Create a new competence document later. For the interim, keep `FRM_HRD_04_Personnel Competence Record.docx` available until the replacement is created and approved. |
| DEC-06 | Keep the DOCX as the controlled master/template for the applicable document function(s). PDF is not a second master document; it may remain only as issued/generated output where operationally required. XLSX is not treated as a separate controlled master unless its independent operational role is explicitly established. |
| DEC-07 | `SMJ/FRM/MKT/01` = Customer Feedback; `SMJ/FRM/MKT/02` = Complaint Report. The complaint form's internal identifier is to be corrected to MKT/02 during execution. |
| DEC-08 | Create `SMJ/SOP/SYS/09` as the operational internal-audit procedure. Keep Internal Audit Program as the planning/programme document and Internal Audit Plan as the individual-audit planning document. |
| DEC-09 | `SMJ/FRM/SYS/04` = Corrective Action Report. All conflicting corrective-action references are to be reconciled to this identifier during execution. |
| DEC-10 | Keep `EXB-SYS-01` for calibration rules/frequency and create `SMJ/FRM/SYS/10` as the actual equipment calibration schedule/register. |
| DEC-11 | Approve the reconciled Master List architecture as the authoritative document-control architecture before controlled-document execution. |
| DEC-12 | No dedicated procurement Tier 3 SOP unless the actual laboratory workflow demonstrates a need for a lower-level implementation document. |
| DEC-13 | The laboratory does not perform method validation. Create `SMJ/FRM/MTH/01` as the Method Verification Report. Do not create a separate Method Validation Report for this laboratory architecture. A validated/approved methods list remains a separate control if needed. |
| DEC-14 | Create one generic `SMJ/FRM/QCD/05` equipment intermediate-check record containing: Equipment ID, Equipment type, Parameter checked, Reference value, Observed value, Acceptance criterion, Result, Date, Performed by, Reviewed by, and Action for failure. |
| DEC-15 | Prefer an integrated sampling/COC architecture where practical; create separate preservation/transport records only where required by the actual laboratory process and not already captured. |
| DEC-16 | Establish a dedicated controlled PT/ILC evidence record. Exact identifier is to be assigned consistently with the approved QCD namespace during execution. |
| DEC-17 | `SMJ/FRM/SYS/14` = Management Review Record/Minutes. |
| DEC-18 | `SMJ/FRM/SYS/07` = Internal Audit Record. This is separate from the audit programme and individual audit plan. |
| DEC-19 | Establish a dedicated External Standards Register as a controlled external-reference register. |

## Execution gate

Mass editing may begin only against the approved decisions above and the frozen Final Document Register. Execution agents must use FINAL_DOCUMENT_REGISTER.xlsx, this register, and the migration plan as the authoritative architecture worklist. CONTROL artifacts may be updated during execution planning; controlled QMS documents are to be modified only under the approved execution stage.