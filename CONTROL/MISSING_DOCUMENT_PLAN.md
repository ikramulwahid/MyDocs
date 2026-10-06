# MyDocs — Stage 2 Missing Document Plan

Purpose: classify candidate documentation gaps from Run 0 without creating any controlled document.

## Classification

- Genuinely required / PLANNED_NEW_DOCUMENT: no existing file currently fulfils the evidenced function.
- Already satisfied by existing document: an existing controlled document can fulfil the function.
- Unresolved: evidence is insufficient to decide safely.
- Not required: no repository evidence supports a separate document.

| Candidate | Tier | Parent | Classification | Proposed identifier | Reason |
|---|---:|---|---|---|---|
| Internal Audit SOP / SOP-SYS-09 | 3 | QSP_20 | PLANNED_NEW_DOCUMENT | SMJ/SOP/SYS/09 | Project owner approved SOP-SYS-09 as the operational internal-audit procedure; Internal Audit Program and Plan remain planning documents |
| Purchase Requisition | 4 | QSP_08 | PLANNED_NEW_DOCUMENT | SMJ/FRM/PRC/01 or approved equivalent | No clear existing controlled procurement-initiation record |
| Supplier Evaluation / Selection | 4 | QSP_08 | PLANNED_NEW_DOCUMENT | SMJ/FRM/PRC/02 or approved equivalent | No clear supplier-evaluation record |
| Supplier Monitoring / Re-evaluation | 4 | QSP_08 | PLANNED_NEW_DOCUMENT | SMJ/FRM/PRC/03 or approved equivalent | No clear monitoring/re-evaluation record |
| Method Validation Report | 4 | QSP_09 | NOT REQUIRED FOR THIS LAB | N/A | Project owner confirmed the laboratory does not perform method validation |
| Method Verification Report | 4 | QSP_09 | PLANNED_NEW_DOCUMENT | SMJ/FRM/MTH/01 | Project owner approved MTH/01 as the Method Verification Report; no separate validation report is required |
| Validated Methods List | 4 | QSP_09 | PLANNED_NEW_DOCUMENT | SMJ/LST/MTH/01 or approved list namespace | No matching controlled method-status list identified |
| Equipment Intermediate Check Record | 4 | QSP_03/QSP_05/QSP_06 | PLANNED_NEW_DOCUMENT | SMJ/FRM/QCD/05 | Approved as a generic record with defined equipment/check/result fields |
| Internal Audit Record | 4 | QSP_20/QSP_15 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/07 | Approved audit record identity; separate from Program and Plan |
| Management Review Minutes | 4 | QSP_21 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/14 | Approved management review record/minutes identity |
| Annual Training Plan | 4 | QSP_02 | PLANNED_NEW_DOCUMENT | SMJ/FRM/TRG/01 | No clear equivalent identified |
| Induction Training Report | 4 | QSP_02 | PLANNED_NEW_DOCUMENT | SMJ/FRM/TRG/03 | No clear equivalent identified |
| Employee Competence Assessment | 4 | QSP_02 | PLANNED_NEW_DOCUMENT | Final HRD identifier TBD | Existing HRD-04 documents are obsolete for final architecture; create a new competence document. Keep Personnel Competence Record only as interim reference until replacement approval |
| Confidentiality Agreement | 4 | QSP_01/QSP_02 | PLANNED_NEW_DOCUMENT | SMJ/FRM/TRG/06 | Secrecy policy exists, but no acknowledgement record is identified |
| Corrective Action Report | 4 | QSP_19 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/04 or approved equivalent | No clear controlled CAPA record identified |
| Record Archive / Retention Register | 4 | QSP_17 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/02 or approved equivalent | Referenced archive evidence not present |
| PT/ILC Record | 4 | QSP_12 | PLANNED_NEW_DOCUMENT where applicable | Final QCD/PT-ILC identifier TBD | Project owner approved a dedicated PT/ILC evidence mechanism |
| Calibration Schedule | 4 | QSP_04/QSP_06 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/10 | EXB-SYS-01 remains the rules/frequency document; project owner approved a separate equipment calibration schedule/register | Avoid unnecessary duplicate schedule |
| Sampling Field Record | 4 | SOP-SYS-03/QSP_10 | UNRESOLVED_BY_DECISION | TBD | Prefer integrated sampling/COC; create a separate record only if actual process evidence cannot be captured within the integrated design |
| Sample Preservation Record | 4 | SOP-SYS-03/QSP_10 | UNRESOLVED_BY_DECISION | TBD | Prefer integration into sampling/COC; separate record only where operationally justified |
| Contract / Request Review Record | 4 | QSP_13 | PLANNED_NEW_DOCUMENT | SMJ/FRM/PRC/04 or approved equivalent | No clear controlled review record identified |
| Backup Verification / Restoration Record | 4 | QSP_16/QSP_17/SOP-SYS-01 | PLANNED_NEW_DOCUMENT | SMJ/FRM/SYS/XX after final family decision | Evidence of backup verification is not clearly represented |
| Controlled Communication / Report Issue Record | 4 | QSP_13/QSP_14/QSP_22 | UNRESOLVED | TBD | Communication exhibit may define the process; evidence mechanism needs confirmation |
| External Standards Register | 4 | QSP_09/QSP_16/QSP_17/QSP_22 | PLANNED_NEW_DOCUMENT | Final ID TBD under approved external-reference namespace | Project owner approved a dedicated controlled external standards register |

## Creation gate

Do not create a proposed new document until the execution agent has confirmed that no existing controlled document can perform the same function and that the final identifier is approved.