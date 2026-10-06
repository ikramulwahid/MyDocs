# MyDocs — Stage 2 Document Architecture

Repository: ikramulwahid/MyDocs
Branch: main
Baseline: 79428117f4d6b8280a78e25d6e4fb65150c25e65
Stage: 2 — Final Document Architecture and Identifier Control

## 1. Governing architecture

Preserve the repository hierarchy:

- Tier 1 — Quality Manual
- Tier 2 — Quality System Procedures (QSP_00–QSP_22)
- Tier 3 — Exhibits, system SOPs, HRD documents and laboratory SOPs
- Tier 4 — Forms, formats, registers, worksheets, templates and records

Target dependency:

Requirement → Tier 1 → Tier 2 → Tier 3 → Tier 4 → Evidence

Tier changes are not approved for cosmetic reasons.

## 2. Identifier architecture

Proposed authoritative namespaces:

- Tier 1: SMJ/QM/01
- Tier 2: SMJ/QSP/00 through SMJ/QSP/22
- Exhibits: SMJ/EXB/HRD/... and SMJ/EXB/SYS/...
- HRD SOPs: SMJ/SOP/HRD/...
- System SOPs: SMJ/SOP/SYS/...
- Laboratory SOPs: SMJ/SOP/LAB/01/01 onward
- Forms: SMJ/FRM/<function>/...

These are architecture targets. No new identifier is assigned to an ambiguous file solely to remove a collision.

## 3. QSP mapping verified

| QSP | Process |
|---|---|
| QSP_01 | Maintaining Impartiality of Laboratory Activities |
| QSP_02 | Personnel Selection, Training and Competency Management |
| QSP_03 | Maintaining Laboratory Environmental Conditions |
| QSP_04 | Handling, Transport, Storage, Use, and Planned Maintenance of Equipment |
| QSP_05 | Intermediate Checks |
| QSP_06 | Traceability of Measurements |
| QSP_07 | Control of Reference Standards, Materials, and Critical Consumables |
| QSP_08 | Procurement of Externally Provided Products and Services |
| QSP_09 | Method Verification and Validation |
| QSP_10 | Transportation, Receipt, Handling, Protection, Storage, Retention, and Disposal or Return of Test Items |
| QSP_11 | Estimation and Expression of Measurement Uncertainty |
| QSP_12 | Ensuring and Monitoring of Validity of Result |
| QSP_13 | Review of Requests, Tenders and Contracts |
| QSP_14 | Receive, Evaluate and Make Decisions on Complaints |
| QSP_15 | Control of Non–Conforming Work |
| QSP_16 | Document and Data Control |
| QSP_17 | Control of Records |
| QSP_18 | Risk Assessment |
| QSP_19 | Corrective Action |
| QSP_20 | Internal Audit |
| QSP_21 | Management Review |
| QSP_22 | Procedure for Use of NABL Symbol |

No QSP number is being changed.

## 4. Verified legacy reference targets

- SMJ/QMS/QSP/15 → SMJ/QSP/15
- SMJ/QMS/QSP/21 → SMJ/QSP/20
- SMJ/QMS/QSP/22 → SMJ/QSP/21
- QSP_13 risk-context QSP_14 → SMJ/QSP/18
- QSP_11 nonconforming-work QSP_14 → SMJ/QSP/15

These are migration mappings for later execution only.

## 5. Tier 3 parentage

| Tier 3 document family | Parent QSP(s) |
|---|---|
| EXB-HRD-01 | QSP_02 |
| EXB-SYS-01 | QSP_04/QSP_05/QSP_06 |
| EXB-SYS-02 | QSP_01/QSP_10/QSP_16/QSP_17 |
| EXB-SYS-03 | QSP_13/QSP_14/QSP_15/QSP_21/QSP_22 |
| EXB-SYS-04 | QSP_01 |
| EXB-SYS-05 | QSP_10 |
| EXB-SYS-06 | QSP_05/QSP_09/QSP_12/QSP_15/QSP_18/QSP_19/QSP_20 |
| SOP_HRD_01 | QSP_01/QSP_02/QSP_18/QSP_20/QSP_21 |
| SOP-SYS-01 | QSP_16/QSP_17 |
| SOP-SYS-02 | QSP_03/QSP_04/QSP_18 |
| SOP-SYS-03 | QSP_10 |
| SOP-SYS-04 | QSP_05/QSP_06/QSP_07 |
| SOP-SYS-05 | QSP_05/QSP_07/QSP_12 |
| SOP-SYS-06 | QSP_04/QSP_05/QSP_06 |
| SOP-SYS-07 | QSP_03/QSP_04/QSP_05 |
| SOP-SYS-08 | QSP_02 |
| Laboratory SOPs | QSP_09/QSP_10/QSP_11/QSP_12, plus specific dependencies |

## 6. Laboratory architecture

The active laboratory SOP family is proposed as SMJ/SOP/LAB/01/01–08 in this order:

01 Moisture in Coal
02 Volatile Matter in Coal
03 Total Ash in Coal
04 Fixed Carbon in Coal
05 Calorific Value of Coal
06 Ash in Solid Biofuels
07 Calorific Value in Solid Biofuels
08 Moisture Content in Solid Biofuels

The root-level duplicate copies of subjects 01–03 remain UNRESOLVED pending content, revision and approval comparison.

Fixed Carbon retains the known dependency on Moisture, Volatile Matter and Total Ash SOPs.

## 7. Tier 4 architecture

Tier 4 is the evidence layer. Existing principal mappings are:

- Master List → QSP_16/QSP_17
- Training Report → QSP_02
- Chain of Custody → QSP_10
- Sample Inward Register → QSP_10
- Equipment PM forms → QSP_04/QSP_05
- Nonconforming Work form → QSP_15
- IQC Plan → QSP_12
- Environment Monitoring → QSP_03
- MVR-Coal → QSP_09/QSP_12
- Reference Material Log → QSP_06/QSP_07
- Test Report → QSP_22/reporting controls
- Customer Feedback / Complaint → QSP_14/QSP_21

## 8. Control principles for execution

1. One active controlled document = one unique identifier.
2. Prefer existing valid identity over cosmetic renumbering.
3. Prefer consolidation over proliferation.
4. A completed record instance is not a second template.
5. A PDF or spreadsheet output is not automatically a second active template.
6. Duplicate subjects remain unresolved until content/approval evidence selects the survivor.
7. Missing forms are created only after confirming no existing document fulfils the function.
8. Legacy references are migrated only after the final target is approved.
9. Unresolved architectural decisions block execution for the affected document group.

## 9. Stage boundary

Stage 2 authorizes architecture and migration planning only. It does not authorize edits to the controlled documents.