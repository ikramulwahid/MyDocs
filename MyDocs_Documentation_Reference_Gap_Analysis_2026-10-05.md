# MyDocs — Documentation Hierarchy, Reference, Cross-Link and Gap Analysis

**Repository:** `ikramulwahid/MyDocs`  
**Branch reviewed:** `main`  
**Review date:** 5 October 2026  
**Repository:** https://github.com/ikramulwahid/MyDocs/tree/main

## 1. Executive Summary

The repository has materially changed since the previous review. It now contains a complete four-level document structure:

- **Tier 1:** Quality Manual
- **Tier 2:** Quality System Procedures (`QSP_00`–`QSP_22`)
- **Tier 3:** Exhibits, system SOPs, HRD documents, and laboratory test SOPs
- **Tier 4:** Forms, formats, templates, registers, worksheets, and records

The repository's own terminology should be preserved. It differs slightly from the generic hierarchy in the request: the repository places management-system procedures at Tier 2 and operational SOPs at Tier 3. This is internally logical and should not be changed merely for terminology.

The most important finding is that the repository has **many of the lower-level documents needed to support the Quality Manual and QSPs, but the document-control network is not yet reconciled**. The Master List contains documents that do not exist as files, existing files use identifiers different from the references in the QSPs/manual, several documents have duplicate identifiers, and several Tier 3 documents have no explicit parent QSP cross-reference.

The most significant problems are:

1. **Master List vs actual repository mismatch.** The Master List lists numerous Tier 3/Tier 4 codes that cannot currently be matched to a controlled file.
2. **Broken identifiers.** Examples include QSP19 using `SMJ/QMS/QSP/...` instead of the repository's `SMJ/QSP/...` convention, and references to QSP numbers that do not match the actual procedure.
3. **Missing evidence forms.** Purchase/supplier forms, method validation/verification forms, intermediate-equipment check record, internal-audit record, management-review minutes, training records, and several system records are referenced but absent.
4. **Duplicate/overlapping controlled documents.** Three coal laboratory SOPs occur in two locations. Two risk-register forms share the same `FRM-SYS-17` identifier. The competence documentation contains two overlapping `HRD-04` records. The report and retest forms also exist in multiple formats using the same conceptual identifier.
5. **Uncontrolled temporary file.** `~$P_06_Traceability of Measurements.docx` is a Microsoft Word lock/temporary file and should not exist in the controlled repository.
6. **Tier 3 parent-child relationships are incomplete.** For example, the Master List says `SMJ/SOP/SYS/09 – SOP for Internal Audit Program`, but no corresponding Tier 3 file exists; there is instead an un-coded `Internal Audit Program.docx` in Tier 4.
7. **Some forms have serious identifier/content inconsistencies.** The complaint form currently contains `SMJ/FRM/MKT/01`, while QSP14 explicitly calls the complaint form `SMJ/FRM/MKT/02`. The existing customer-feedback form also uses `SMJ/FRM/MKT/01`. These cannot both remain distinct controlled forms under the same identifier.
8. **Several procedures explicitly contain placeholders** such as `/XX`, which means the chain is not yet closed.

### Overall conclusion

The repository is now structurally much closer to a functioning controlled laboratory documentation system, but it should **not yet be regarded as a fully reconciled documentation hierarchy**.

The recommended target is:

**Requirement → Quality Manual → QSP → Tier 3 SOP/Exhibit → Tier 4 controlled form/record → completed evidence**

The biggest immediate task is not creating dozens of new documents indiscriminately. It is **reconciling identifiers, parent-child ownership, missing records, and cross-references first**. After that, only the genuinely missing operational documents should be created.

---

## 2. Repository Overview

The current `main` tree contains approximately:

| Category | Current content |
|---|---:|
| Tier 1 DOCX | 1 |
| Tier 2 substantive QSP DOCX | 23 including index (`QSP_00`–`QSP_22`) |
| Tier 3 DOCX | 28 |
| Tier 4 files | 33 |
| Total repository files | 87 |
| XLSX | 8 |
| PDF | 1 |
| Temporary Word lock file | 1 |

The repository is organized under:

```text
Quality Management/
├── Tier 1 - Quality Manual/
├── Tier 2 - Quality System Procedures/
├── Tier 3 - Exhibits, SOP's and other system documents/
└── Tier 4 - Forms, Formats and Records/
```

This is a good overall physical hierarchy.

---

## 3. Document Hierarchy / Tier Definitions

### Repository-defined hierarchy

| Tier | Repository meaning | Assessment |
|---|---|---|
| Tier 1 | Quality Manual | Appropriate |
| Tier 2 | Quality System Procedures | Appropriate management-system/process level |
| Tier 3 | Exhibits, system SOPs, HRD documents, laboratory SOPs | Appropriate implementation/operational level |
| Tier 4 | Forms, formats, registers, worksheets and records | Appropriate execution/evidence level |

### Difference from requested generic hierarchy

The requested hierarchy described Tier 2 as manuals, Tier 3 as procedures, and Tier 4 as work instructions/forms. The repository instead uses:

**Tier 2 = system procedures**  
**Tier 3 = operational SOPs/exhibits**

That is acceptable and should be preserved. The important point is not the label but the dependency:

> Tier 1 establishes the management-system framework; Tier 2 establishes the controlled process; Tier 3 tells personnel how the process is implemented; Tier 4 generates the evidence.

### Important distinction

An **exhibit/policy** is not automatically a lower-level procedure. For example:

- `EXB-SYS-04 - Impartiality Policy` supports `QSP_01`.
- `EXB-SYS-01 - Calibration Periodicity` supports equipment and traceability procedures.
- `EXB-SYS-05 - Sample Receipt Checklist` supports `QSP_10`, but it is a checklist/control aid, not a replacement for the procedure.

---

# 4. Complete Document Inventory

## Tier 1

1. `Quality Management/Tier 1 - Quality Manual/Quality Manual.docx`

## Tier 2

1. `QSP_00_Index.docx`
2. `QSP_01_Maintaining Impartiality of Laboratory Activities.docx`
3. `QSP_02_Personnel Selection, Training and Competency Management.docx`
4. `QSP_03_Maintaining Laboratory Environmental Conditions.docx`
5. `QSP_04_Handling, Transport, Storage, Use, and Planned Maintenance of Equipment.docx`
6. `QSP_05_Intermediate Checks.docx`
7. `QSP_06_Traceability of Measurements.docx`
8. `QSP_07_Control of Reference Standards, Materials, and Critical Consumables.docx`
9. `QSP_08_Procurement of Externally Provided Products and Services.docx`
10. `QSP_09_Method Verification and Validation.docx`
11. `QSP_10_Transportation, Receipt, Handling, Protection, Storage, Retention, and Disposal or Return of Test Items.docx`
12. `QSP_11_Estimation and Expression of Measurement Uncertainty.docx`
13. `QSP_12_Ensuring and Monitoring of Validity of Result.docx`
14. `QSP_13_Review of Requests, Tenders and Contracts..docx`
15. `QSP_14_Receive, Evaluate and Make Decisions on Complaints.docx`
16. `QSP_15_Control of Non–Conforming Work.docx`
17. `QSP_16_Document and Data Control.docx`
18. `QSP_17_Control of Records.docx`
19. `QSP_18_Risk Assessment.docx`
20. `QSP_19_Corrective Action.docx`
21. `QSP_20_Internal Audit.docx`
22. `QSP_21_Management Review.docx`
23. `QSP_22_Procedure for Use of NABL Symbol.docx`
24. `~$P_06_Traceability of Measurements.docx` — **temporary Word lock file; not a controlled document**

## Tier 3

### Exhibits

- `EXB-HRD-01 - Skill Requirements.docx`
- `EXB-SYS-01 - Calibration Periodicity.docx`
- `EXB-SYS-02 - Secrecy rules.docx`
- `EXB-SYS-03 - Communication Processes.docx`
- `EXB-SYS-04 - Impartiality Policy.docx`
- `EXB-SYS-05 - Sample Receipt Checklist.docx`
- `EXB-SYS-06 - Acceptance criteria for internal quality checks.docx`

### HRD/system SOPs

- `SOP_HRD_01_Organizational Structure & Job Descriptions.docx`
- `SOP-SYS-01 - Protection and Backup of Electronic Records.docx`
- `SOP-SYS-02 - Laboratory Safety.docx`
- `SOP-SYS-03 - Sampling.docx`
- `SOP-SYS-04 - Handling, Storage, and Use of Certified Reference Materials (CRMs).docx`
- `SOP-SYS-05 - Intermediate Check on Certified Reference Materials (CRMs).docx`
- `SOP-SYS-06 - Operation and Intermediate Checks – Weighing Balance.docx`
- `SOP-SYS-07 - Operation and Intermediate Checks – Oven_Furnace_Humidity Chamber.docx`
- `SOP-SYS-08 - Personnel Competence & Training.docx`

### Laboratory SOP index

- `SOP LAB/Index.docx`

### Laboratory SOPs in `SOP LAB/`

- `SOP-LAB-01-Moisture in Coal.docx`
- `SOP-LAB-02-Volatile Matter in Coal.docx`
- `SOP-LAB-03-Total Ash in Coal.docx`
- `SOP-LAB-04-Fixed Carbon in Coal.docx`
- `SOP-LAB-05-Calorific Value of Coal.docx`
- `SOP-LAB-06-Ash in Solid Biofuels.docx`
- `SOP-LAB-07-Calorific Value in Solid Biofuels.docx`
- `SOP-LAB-08-Moisture Content in Solid Biofuels.docx`

### Additional duplicate/older-looking laboratory SOPs

- `SOP-LAB-01-Moisture in Coal.docx`
- `SOP-LAB-02-Volatile Matter in Coal.docx`
- `SOP-LAB-03-Total Ash in Coal.docx`

These duplicate the first three laboratory SOP subjects and should be resolved before they are treated as separate controlled documents.

## Tier 4

- `FRM-HRD-04 - Employees Competence Report.docx`
- `FRM-SYS-01-02 - Master List.docx`
- `FRM-SYS-17 - Risk Register new.docx`
- `FRM-SYS-17 - Risk Register.docx`
- `FRM-TRG-02 - Training Report.docx`
- `FRM_COC_01_Chain of Custody - Coal.docx`
- `FRM_HRD_04_Personnel Competence Record.docx`
- `FRM_LAB_01_01_Rough Datasheet - Coal-Biofuel.docx`
- `FRM_LAB_02_01 - Final Test Worksheet - Coal-Biofuel.docx`
- `FRM_MKT_01_Customer Feedback Form.docx`
- `FRM_MKT_02_Complaint Report Format.docx`
- `FRM_MKT_03_Sample Inward Register.xlsx`
- `FRM_OPN_01_01_Preventive Maintenance Checkpoints - Digital Bomb Calorimeter.docx`
- `FRM_OPN_01_02_Preventive Maintenance Checkpoints - Muffle Furnace.docx`
- `FRM_OPN_01_03_Preventive Maintenance Checkpoints - Analytical Balance.docx`
- `FRM_OPN_01_04_Preventive Maintenance Checkpoints - Hot Air Oven.docx`
- `FRM_OPN_02_Control of Non–Conforming Work.docx`
- `FRM_OPN_03_01_Final Worksheet - Coal.docx`
- `FRM_QCD_01_Internal Quality Control Plan.docx`
- `FRM_QCD_02_Re-test Report.docx`
- `FRM_QCD_02_Re-test Report.pdf`
- `FRM_QCD_03_UoM - Coal.xlsx`
- `FRM_QCD_04_Re-test report – Coal.xlsx`
- `FRM_QCD_06 - Environment Condition Monitoring Report.xlsx`
- `FRM_QCD_07_MVR-Coal.xlsx`
- `FRM_QCD_09_CRM Consumption Report.docx`
- `FRM_QCD_10_Reference Material Log.docx`
- `FRM_RPT_01_Test report – Coal.docx`
- `FRM_RPT_01_Test report – Coal.xlsx`
- `Internal Audit Plan.docx`
- `Internal Audit Program.docx`
- `Sample Inward Register/2025-06.xlsx`
- `Sample Inward Register/2025-07.xlsx`

---

# 5. Manual-by-Manual Analysis

## Quality Manual

### Purpose and scope

The Quality Manual establishes the SMJ laboratory QMS for environmental and coal testing, covering:

- client requirements
- sampling
- sample preparation
- testing and analysis
- data interpretation
- reporting
- personnel
- equipment
- facilities
- quality controls
- records
- complaints
- nonconforming work
- audits
- management review
- accreditation-related controls

### Tier 2 documents that should support the manual

The manual should have explicit references to all QSPs relevant to its stated scope. At minimum:

`SMJ/QSP/01` through `SMJ/QSP/22`, except that explicit cross-reference should be made only where the manual establishes or summarizes the corresponding process.

A particularly important improvement is to add a **“Related Quality System Procedures”** table at the end of each major manual process section instead of scattering references inconsistently.

### Tier 3 references that should appear in the manual

The manual should explicitly link major operational controls to:

- `SMJ/EXB/HRD/01` — Skill Requirements
- `SMJ/EXB/SYS/01` — Calibration Periodicity
- `SMJ/EXB/SYS/02` — Secrecy Rules
- `SMJ/EXB/SYS/04` — Impartiality Policy
- `SMJ/EXB/SYS/05` — Sample Receipt Checklist
- `SMJ/EXB/SYS/06` — Acceptance Criteria for Internal Quality Checks
- `SMJ/SOP/HRD/01` — Organizational Structure & Job Descriptions
- `SMJ/SOP/SYS/01` — Protection and Backup of Electronic Records
- `SMJ/SOP/SYS/02` — Laboratory Safety
- `SMJ/SOP/SYS/03` — Sampling
- `SMJ/SOP/SYS/04` — CRM Handling
- `SMJ/SOP/SYS/05` — CRM Intermediate Checks
- `SMJ/SOP/SYS/06` — Weighing Balance
- `SMJ/SOP/SYS/07` — Oven/Furnace/Humidity Chamber
- `SMJ/SOP/SYS/08` — Personnel Competence & Training
- applicable `SMJ/SOP/LAB/01/01` through `/01/08` laboratory SOPs

### Tier 4 references that should appear in the manual

Only the key controlled records/templates need direct manual-level reference; the manual should not become a catalog of every form.

Priority manual-level Tier 4 references:

- Master List of Documents
- current competence records/training records
- sample inward/chain-of-custody records
- IQC plan
- environment monitoring record
- equipment maintenance/calibration evidence
- method verification/validation records
- test worksheets
- test report template
- complaint/nonconformance records
- risk register
- internal audit evidence
- management review minutes

### Existing manual references that are broken or weak

The manual currently contains references such as:

- `SMJ/FRM/OPN/03`
- `SMJ/FRM/SYS/10`
- `SMJ/FRM/OPN/04`

but the actual Tier 4 repository contains different identifiers, including:

- `FRM_OPN_03_01`
- no obvious `FRM-SYS-10`
- `FRM_OPN_02` for Control of Non–Conforming Work

These must be reconciled before the manual is approved.

### Exact insertion points for the manual

| Manual location | Add |
|---|---|
| Organizational structure / responsibilities section | `QSP_01`, `QSP_02`, `SOP_HRD_01`, `EXB-HRD-01`, `SOP-SYS-08` |
| Impartiality/confidentiality section | `QSP_01`, `EXB-SYS-04`, `EXB-SYS-02`, `SOP-SYS-01` |
| Personnel/competence section | `QSP_02`, `EXB-HRD-01`, `SOP-SYS-08`, training/competence records |
| Environmental conditions section | `QSP_03`, `SOP-SYS-07`, `FRM_QCD_06` |
| Equipment section | `QSP_04`, `QSP_05`, `QSP_06`, `EXB-SYS-01`, `SOP-SYS-06`, `SOP-SYS-07`, maintenance/check forms |
| Reference materials section | `QSP_07`, `SOP-SYS-04`, `SOP-SYS-05`, `FRM_QCD_09`, `FRM_QCD_10` |
| Procurement section | `QSP_08` plus procurement forms once created/reconciled |
| Methods section | `QSP_09`, lab SOPs, MVR/verification records |
| Measurement uncertainty section | `QSP_11` plus method-specific uncertainty records |
| Validity of results/QC section | `QSP_12`, `EXB-SYS-06`, IQC plan, PT/ILC records |
| Sampling section | `SOP-SYS-03`, COC, sample receipt checklist |
| Test-item handling section | `QSP_10`, `EXB-SYS-05`, inward/COC records |
| Reporting section | `QSP_22`, `FRM_RPT_01`, report review records |
| Complaints section | `QSP_14`, complaint form |
| Nonconforming work section | `QSP_15`, nonconforming work form |
| Risk section | `QSP_18`, risk register |
| Corrective action section | `QSP_19`, corrective-action form |
| Internal audit section | `QSP_20`, audit program/plan/audit record |
| Management review section | `QSP_21`, meeting minutes |
| Records/data section | `QSP_16`, `QSP_17`, `SOP-SYS-01`, Master List |

---

# 6. Procedure-by-Procedure Analysis

The following is the principal document-reference map.

| QSP | Parent/manual requirement | Tier 3 documents that should be referenced | Tier 4 documents that should be referenced | Status / action |
|---|---|---|---|---|
| QSP_01 Impartiality | Manual impartiality/confidentiality | EXB-SYS-04; EXB-SYS-02; SOP_HRD_01; SOP-SYS-08; SOP-SYS-01 | TRG confidentiality/competency records; corrective-action record; complaint record | **High:** several referenced forms (`TRG/04`, `TRG/06`) missing |
| QSP_02 Personnel | Manual competence/HR | EXB-HRD-01; SOP_HRD_01; SOP-SYS-08 | TRG/01, TRG/02, TRG/03, TRG/08 and personnel records | **Critical:** TRG/01, TRG/03, TRG/08 not present; TRG/04 also referenced |
| QSP_03 Environment | Manual environmental control | SOP-SYS-07; EXB-SYS-06; EXB-SYS-01 | QCD/06 environment record; QCD/05 equipment intermediate check; corrective-action record | **High:** QCD/05 and SYS/04 file missing |
| QSP_04 Equipment | Manual equipment management | EXB-SYS-01; EXB-SYS-06; SOP-SYS-06; SOP-SYS-07 | OPN maintenance forms; QCD/05; calibration schedule/records; TRG/08 | **Critical:** QCD/05 and TRG/08 missing; `/XX` refs unresolved |
| QSP_05 Intermediate checks | Manual measurement confidence | EXB-SYS-01; EXB-SYS-06; SOP-SYS-05; SOP-SYS-06; SOP-SYS-07 | QCD/05; relevant maintenance/check records; CRM records | **Critical:** QCD/05 missing |
| QSP_06 Traceability | Manual metrological traceability | EXB-SYS-01; SOP-SYS-04; SOP-SYS-05; SOP-SYS-06; SOP-SYS-07 | QCD/05; QCD/10; report; equipment records | **High:** references use codes that do not always match actual files |
| QSP_07 Reference materials | Manual reference material control | SOP-SYS-04; SOP-SYS-05; EXB-SYS-06 | QCD/09; QCD/10; QCD/05; STR/02 | **Critical:** `FRM/STR/02` missing |
| QSP_08 Procurement | Manual external providers | no Tier 3 procurement SOP currently | PRC/01–04; supplier evaluation records | **Critical:** forms explicitly referenced but absent; master list only has PUR/01 |
| QSP_09 Method verification/validation | Manual methods/technical competence | applicable LAB SOPs; SOP-SYS-04; EXB-SYS-06 | MTH/01, MTH/02; validated-method list; MVR | **Critical:** all three named method-control records missing |
| QSP_10 Test items | Manual sampling/sample handling | SOP-SYS-03; EXB-SYS-05; EXB-SYS-03 | COC; sample inward register; LAB worksheets; preservation/receipt records | **Critical:** `/XX` placeholders; COC code mismatch; preservation/receipt evidence incomplete |
| QSP_11 Uncertainty | Manual measurement uncertainty | applicable LAB SOPs; QSP_06/QSP_12 relationships | method-specific uncertainty records/budgets | **High:** no clearly identified controlled Tier 4 uncertainty record |
| QSP_12 Validity of results | Manual QC/result validity | EXB-SYS-06; all applicable LAB SOPs; SOP-SYS-04/05/06/07 | IQC plan; QCD/05; QCD/06; QCD/07; PT/ILC records | **Critical:** PT/ILC evidence mechanism and QCD/05 need closure |
| QSP_13 Requests/tenders/contracts | Manual client requirement review | EXB-SYS-03; relevant risk/equipment/method controls | request/tender/contract review record; customer communication file | **High:** risk reference is internally inconsistent and contract-review record is not clearly controlled |
| QSP_14 Complaints | Manual customer feedback/complaints | EXB-SYS-03 | MKT/01 feedback; MKT/02 complaint report | **Critical:** complaint form currently carries `MKT/01`, conflicting with QSP14's `MKT/02` |
| QSP_15 Non-conforming work | Manual NCR/CAPA | EXB-SYS-06; EXB-SYS-03 | OPN/02 NCR form; SYS/07 audit/NCR record; SYS/04 CAPA record | **Critical:** references and actual file codes do not align |
| QSP_16 Document/data control | Manual document control | SOP-SYS-01; EXB-SYS-02; EXB-SYS-03 | Master List; document-change/revision records; obsolete/archive records | **Critical:** master list and actual files are not reconciled |
| QSP_17 Records | Manual record retention | SOP-SYS-01; EXB-SYS-02 | SYS/02 archive list; record index; analytical/equipment/audit records | **Critical:** archive list identified in text but not found |
| QSP_18 Risk | Manual risk/opportunity | SOP-SYS-02; EXB-SYS-06; relevant process SOPs | Risk Register | **High:** duplicate `FRM-SYS-17` versions require disposition |
| QSP_19 Corrective Action | Manual continual improvement/CAPA | EXB-SYS-06; EXB-SYS-03 | CAPA record; NCR/audit/complaint records | **Critical:** internal references are wrong namespace and wrong procedure numbers |
| QSP_20 Internal Audit | Manual audit | planned `SOP-SYS-09`; EXB-SYS-06 | Internal Audit Program; Internal Audit Plan; SYS/07 audit record | **Critical:** `SOP-SYS-09` is missing; SYS/07 record file missing |
| QSP_21 Management Review | Manual management review | EXB-SYS-03; all major QSPs as inputs | SYS/14 meeting minutes; risk/customer/audit/CAPA/training evidence | **Critical:** SYS/14 missing |
| QSP_22 NABL Symbol | Manual accreditation/reporting | QSP_16; report-control process | RPT/01; current NABL scope/status reference | **High:** add explicit report-template and scope cross-reference |

---

# 7. Tier 2 Reference Recommendations

The Tier 2 set itself should be treated as the principal process-level map.

### Recommended major sibling relationships

- `QSP_01` → `QSP_18`, `QSP_14`, `QSP_20`, `QSP_21`, `QSP_16`, `QSP_17`
- `QSP_02` → `QSP_17`, `QSP_19` where training deficiencies become corrective actions
- `QSP_03` → `QSP_06`, `QSP_15`, `QSP_17`, `QSP_20`, `QSP_21`
- `QSP_04` → `QSP_05`, `QSP_06`, `QSP_07`, `QSP_17`, `QSP_15`
- `QSP_05` → `QSP_06`, `QSP_07`, `QSP_15`, `QSP_17`
- `QSP_06` → `QSP_04`, `QSP_05`, `QSP_07`, `QSP_08`, `QSP_15`, `QSP_16`, `QSP_17`, `QSP_19`
- `QSP_07` → `QSP_05`, `QSP_06`, `QSP_15`, `QSP_17`, `QSP_18`, `QSP_19`
- `QSP_08` → `QSP_15`, `QSP_19`, `QSP_16`, `QSP_17`
- `QSP_09` → `QSP_07`, `QSP_10`, `QSP_11`, `QSP_12`, `QSP_17`
- `QSP_10` → `QSP_02`, `QSP_16`, `QSP_17`, `QSP_15`
- `QSP_11` → `QSP_05`, `QSP_12`, `QSP_15`
- `QSP_12` → `QSP_09`, `QSP_11`, `QSP_20`, `QSP_03`, `QSP_04`, `QSP_02`, `QSP_10`, `QSP_18`, `QSP_16`, `QSP_15`
- `QSP_13` → `QSP_04`, `QSP_09`, `QSP_18`, `QSP_19`, `QSP_16`, `QSP_17`
- `QSP_14` → `QSP_17`, `QSP_19`
- `QSP_15` → `QSP_19`, `QSP_20`, `QSP_21`, `QSP_17`
- `QSP_16` → `QSP_17`
- `QSP_17` → `QSP_16`, `QSP_20`
- `QSP_18` → QSPs where risk is assessed; at minimum QSP_01, QSP_03, QSP_04, QSP_07, QSP_09, QSP_10, QSP_12, QSP_13
- `QSP_19` → `QSP_15`, `QSP_20`, `QSP_21`
- `QSP_20` → all controlled processes where internal audit evaluates compliance
- `QSP_21` → all major QSPs as management-review input
- `QSP_22` → `QSP_16`, `QSP_17` and report issuance controls

### Broken Tier 2 reference that must be corrected

`QSP_19` currently uses references such as:

- `SMJ/QMS/QSP/15`
- `SMJ/QMS/QSP/21`
- `SMJ/QMS/QSP/22`

This is inconsistent with the actual repository numbering and naming. In particular:

- Internal Audit is `SMJ/QSP/20`, not `/21`
- Management Review is `SMJ/QSP/21`, not `/22`
- The repository does not use the `SMJ/QMS/QSP/...` prefix in the Master List

This should be treated as a **Critical broken-reference finding**.

---

# 8. Tier 3 Reference Recommendations

## Exhibits

| Tier 3 document | Parent process | Where to reference it |
|---|---|---|
| EXB-HRD-01 Skill Requirements | QSP_02 | QSP_02 “Personnel selection criteria” and “Determination of competency requirements” |
| EXB-SYS-01 Calibration Periodicity | QSP_04/05/06 | Equipment “Calibration Schedule”; Intermediate Checks “Preparation”; Traceability “Calibration Program” |
| EXB-SYS-02 Secrecy Rules | QSP_01, QSP_10, QSP_16/17 | Confidentiality, test-item protection, document/data control, records |
| EXB-SYS-03 Communication Processes | QSP_13/14/15/21/22 | Customer communication, complaints, escalation, management review, report issue |
| EXB-SYS-04 Impartiality Policy | QSP_01 | “Impartiality Policy” subsection |
| EXB-SYS-05 Sample Receipt Checklist | QSP_10 | “Sample Recording and Documentation” / “Sample Approval” |
| EXB-SYS-06 IQC Acceptance Criteria | QSP_05/09/12/15/18/19/20 | Internal-check acceptance, validity of results, NCR/CAPA, audit |

## System/HRD SOPs

| Tier 3 document | Parent process(es) |
|---|---|
| SOP_HRD_01 Organizational Structure & Job Descriptions | QSP_01, QSP_02, QSP_18, QSP_20, QSP_21 |
| SOP-SYS-01 Electronic Records Backup | QSP_16, QSP_17 |
| SOP-SYS-02 Laboratory Safety | QSP_03, QSP_04, QSP_18 and general manual safety requirements |
| SOP-SYS-03 Sampling | Manual sampling; QSP_10 |
| SOP-SYS-04 CRM Handling | QSP_07, QSP_06, QSP_05 |
| SOP-SYS-05 CRM Intermediate Checks | QSP_05, QSP_07, QSP_12 |
| SOP-SYS-06 Weighing Balance | QSP_04, QSP_05, QSP_06 |
| SOP-SYS-07 Oven/Furnace/Humidity Chamber | QSP_03, QSP_04, QSP_05 |
| SOP-SYS-08 Personnel Competence & Training | QSP_02 |

## Laboratory SOPs

All laboratory SOPs should have a standard “Related controlled documents” block containing only the relevant controls, normally:

- sample handling: QSP_10 / SOP-SYS-03
- equipment: QSP_04
- intermediate checks: QSP_05
- measurement traceability: QSP_06
- reference materials/CRMs: QSP_07
- method verification/validation: QSP_09
- uncertainty: QSP_11
- result validity/IQC: QSP_12
- safety: SOP-SYS-02
- personnel authorization: SOP-SYS-08
- relevant rough worksheet/final worksheet
- applicable IQC/control record
- test report template where appropriate

### Important laboratory dependency

The Fixed Carbon SOP explicitly depends on:

- Moisture SOP
- Volatile Matter SOP
- Total Ash SOP

This dependency should be retained and made explicit in the “Related SOPs” section.

### Duplicate laboratory SOP problem

The following exist both inside `SOP LAB/` and at the Tier 3 root:

- Moisture in Coal
- Volatile Matter in Coal
- Total Ash in Coal

They should **not remain as two independent controlled documents** unless one is formally designated as obsolete/archive and the other as the approved current version.

Recommended action:

1. Compare the contents and approval metadata.
2. Select one controlled master.
3. Retain the other only as an obsolete/superseded record if required.
4. Remove it from the active document tree or clearly mark it obsolete.
5. Update the Master List and all cross-references.

---

# 9. Tier 4 Reference Recommendations

## Personnel / training

`SOP-SYS-08` and `QSP_02` require:

- annual training plan
- attendance/training record
- induction record
- competence assessment record
- authorization evidence
- personnel qualification records

Currently present:

- `FRM-TRG-02 - Training Report`
- `FRM-HRD-04 - Employees Competence Report`
- `FRM_HRD_04_Personnel Competence Record`

Missing/reconciliatory:

- TRG/01 Annual Training Plan
- TRG/03 Induction Training Report
- TRG/08 Employees Competence Report
- TRG/04 personnel selection evidence referenced by QSP_01/02
- TRG/06 confidentiality agreement referenced by QSP_01/02

## Equipment

Present:

- four preventive-maintenance forms
- environmental condition form
- IQC plan

Missing/weak:

- equipment intermediate-check form (`QCD/05`)
- calibration schedule form (`SYS/10` mentioned by Manual)
- equipment identification/status control if not handled elsewhere
- clear calibration-certificate/verification record index

## CRM/reference materials

Present:

- `FRM_QCD_09` CRM Consumption Report
- `FRM_QCD_10` Reference Material Log

Missing:

- `FRM/STR/02`
- CRM intermediate-check record (`QCD/05` appears intended for equipment, so a separate CRM record may also be needed unless the approved structure defines a common form)

## Testing

Present:

- rough datasheet
- final worksheet
- coal final worksheet
- report template
- retest report
- MVR-Coal
- IQC plan

Missing/weak:

- method validation report
- method verification report
- validated-method master list
- method-specific uncertainty record/budget
- proficiency-testing/interlaboratory-comparison record
- controlled test-request/contract-review record

## Sample handling

Present:

- Chain of Custody
- Sample Inward Register
- Sample Receipt Checklist

Missing/weak:

- controlled sampling record
- preservation record
- sample acceptance/rejection record if not integrated into COC/inward register
- controlled register for deviations/communications where required

## Complaints/customer

Present:

- Customer Feedback Form
- Complaint Report Format

Critical identifier problem:

The complaint file `FRM_MKT_02_Complaint Report Format.docx` contains the identifier `SMJ/FRM/MKT/01`, while QSP14 calls for `SMJ/FRM/MKT/02`. The customer-feedback form also uses `SMJ/FRM/MKT/01`.

Therefore, the complaint form and feedback form cannot both remain controlled as `MKT/01`.

## NCR/CAPA

Present:

- `FRM_OPN_02_Control of Non–Conforming Work.docx`

Missing/weak:

- clear `SYS/04` corrective-action record
- `SYS/07` internal audit/nonconformance record where referenced

## Audit / management review

Present:

- `Internal Audit Plan.docx`
- `Internal Audit Program.docx`

Missing:

- formal Tier 3 `SOP-SYS-09` Internal Audit Program specified by Master List
- `FRM-SYS-07` audit record
- `FRM-SYS-14` management-review minutes

---

# 10. Existing Documents That Need to Be Added as References

The following are already in the repository and should be cross-linked explicitly.

| Existing document | Refer from | Exact location |
|---|---|---|
| EXB-SYS-01 Calibration Periodicity | QSP_04 | Calibration Schedule |
| EXB-SYS-01 | QSP_05 | Preparation / Frequency |
| EXB-SYS-01 | QSP_06 | Equipment Calibration Program |
| EXB-SYS-02 Secrecy Rules | QSP_01 | Confidentiality |
| EXB-SYS-02 | QSP_10 | Confidential handling |
| EXB-SYS-02 | QSP_16/17 | Data/record protection |
| EXB-SYS-03 Communication | QSP_13 | Client communication and contract review |
| EXB-SYS-03 | QSP_14 | Complaint communication |
| EXB-SYS-03 | QSP_21 | Management review communication |
| EXB-SYS-04 Impartiality | QSP_01 | Impartiality Policy |
| EXB-SYS-05 Sample Receipt Checklist | QSP_10 | Sample Recording/Acceptance |
| EXB-SYS-06 Acceptance Criteria | QSP_05 | Review and approval of intermediate checks |
| EXB-SYS-06 | QSP_12 | Internal QC/result validity |
| SOP-SYS-01 Backup | QSP_16/17 | Electronic data/records |
| SOP-SYS-02 Safety | applicable QSPs and all technical SOPs | Safety/Responsibilities |
| SOP-SYS-03 Sampling | QSP_10 | Sampling and sample handling |
| SOP-SYS-04 CRM | QSP_07 | Storage and use |
| SOP-SYS-05 CRM intermediate check | QSP_05 | Intermediate Checks |
| SOP-SYS-06 Balance | QSP_04/05/06 | Equipment use and checks |
| SOP-SYS-07 Oven/Furnace | QSP_03/04/05 | Environmental/equipment controls |
| SOP-SYS-08 Competence | QSP_02 | Training/competence |
| all LAB SOPs | QSP_09/12 | Method and result validity |
| Fixed Carbon LAB SOP | Moisture/VM/Ash LAB SOPs | Procedure |
| Internal Audit Plan/Program | QSP_20 | Audit Planning |
| IQC Plan | QSP_12 | QA/QC controls |
| Environment Condition Report | QSP_03 | Documentation and Record Keeping |
| MVR-Coal | QSP_09/QSP_12 | Validation / validity |
| Reference Material Log | QSP_06/QSP_07 | Reference Materials |
| Test Report | QSP_06/QSP_22 | Test report issuance |
| Complaint Form | QSP_14 | Documentation |
| Customer Feedback Form | QSP_14/QSP_21 | Customer feedback |

---

# 11. Missing Documents That Should Be Created

These are the important missing documents that can be justified by actual references in the repository.

## Critical

### 1. Internal Audit Program — `SMJ/SOP/SYS/09`

**Tier:** 3  
**Parent:** QSP_20  
**Purpose:** Establish planning, frequency, auditor independence, scope, audit execution, reporting, corrective-action follow-up and closure.  
**Reason:** Explicitly listed in the Master List but no file exists.  
**Key contents:** audit programme, annual risk-based planning, auditor selection, preparation, evidence, findings, reporting, follow-up.  
**Mandatory:** Yes  
**Priority:** Critical

### 2. Purchase Requisition / procurement record — `SMJ/FRM/PUR/01` or reconciled PRC-series equivalent

**Tier:** 4  
**Parent:** QSP_08  
**Purpose:** Capture procurement request and specification.  
**Reason:** QSP_08 explicitly refers to a purchase requisition form.  
**Priority:** Critical

### 3. Supplier evaluation / selection / monitoring records — `SMJ/FRM/PRC/01`–`/04`

**Tier:** 4  
**Parent:** QSP_08  
**Purpose:** Provider evaluation, approval, monitoring, re-evaluation and service conformity.  
**Reason:** QSP_08 explicitly references these records, but none are present.  
**Priority:** Critical

### 4. Method Validation Report — `SMJ/FRM/MTH/01`

**Tier:** 4  
**Parent:** QSP_09  
**Purpose:** Record validation protocol/results/conclusion.  
**Priority:** Critical

### 5. Method Verification Report — `SMJ/FRM/MTH/02`

**Tier:** 4  
**Parent:** QSP_09  
**Purpose:** Demonstrate laboratory capability to implement a method.  
**Priority:** Critical

### 6. Master List of Validated Methods — `SMJ/LST/MTH/01`

**Tier:** 4 or controlled list register  
**Parent:** QSP_09  
**Priority:** Critical

### 7. Equipment Intermediate Check Record — `SMJ/FRM/QCD/05`

**Tier:** 4  
**Parent:** QSP_03, QSP_05, QSP_06  
**Priority:** Critical

### 8. Internal Audit Record — `SMJ/FRM/SYS/07`

**Tier:** 4  
**Parent:** QSP_15, QSP_20  
**Priority:** Critical

### 9. Management Review Minutes — `SMJ/FRM/SYS/14`

**Tier:** 4  
**Parent:** QSP_21  
**Priority:** Critical

### 10. Annual Training Plan — `SMJ/FRM/TRG/01`

**Tier:** 4  
**Parent:** QSP_02 / SOP-SYS-08  
**Priority:** Critical

### 11. Induction Training Report — `SMJ/FRM/TRG/03`

**Tier:** 4  
**Parent:** QSP_02 / SOP-SYS-08  
**Priority:** Critical

### 12. Employee competence assessment — `SMJ/FRM/TRG/08`

**Tier:** 4  
**Parent:** QSP_02 / SOP-SYS-08  
**Priority:** Critical

### 13. Confidentiality Agreement — `SMJ/FRM/TRG/06`

**Tier:** 4  
**Parent:** QSP_01 and QSP_02  
**Priority:** Critical

### 14. Corrective Action Report — `SMJ/FRM/SYS/04` (subject to final code reconciliation)

**Tier:** 4  
**Parent:** QSP_01, QSP_02, QSP_03, QSP_15, QSP_19  
**Priority:** Critical

### 15. Record Archive/Archive List — `SMJ/FRM/SYS/02`

**Tier:** 4  
**Parent:** QSP_17  
**Priority:** Critical

### 16. Proficiency Testing / Interlaboratory Comparison record — `SMJ/FRM/QCD/08` or approved equivalent

**Tier:** 4  
**Parent:** QSP_12  
**Priority:** Critical

### 17. Controlled calibration schedule — `SMJ/FRM/SYS/10` or corrected equivalent

**Tier:** 4  
**Parent:** QSP_04/QSP_06/Manual  
**Priority:** Critical

## High

### 18. Sampling field record

**Tier:** 4  
**Parent:** SOP-SYS-03 / QSP_10  
**Purpose:** Record sampling date/time/location, conditions, sampler, equipment, deviations and observations.

### 19. Sample preservation record

**Tier:** 4  
**Parent:** SOP-SYS-03  
**Purpose:** Demonstrate correct preservation and transport conditions.

### 20. Test request / contract review record

**Tier:** 4  
**Parent:** QSP_13  
**Purpose:** Capture requirements, capability, resources, method, risks and acceptance decision.

### 21. Backup verification / restoration record

**Tier:** 4  
**Parent:** SOP-SYS-01 / QSP_16/17  
**Purpose:** Evidence that backups are actually tested and recoverable.

### 22. Controlled communication / report issue record

**Tier:** 4  
**Parent:** EXB-SYS-03 / QSP_13/14/22  
**Purpose:** Track report issue, client communication, changes and critical communications.

### 23. External Standards Register

**Tier:** 4 or controlled external-document register  
**Parent:** QSP_16 / QSP_17 / QSP_09 / QSP_22  
**Purpose:** Identify controlled external standards such as IS/ISO/NABL references without storing copyrighted source files unnecessarily.

---

# 12. Broken / Incorrect / Obsolete References

## Critical broken references

### QSP_19 namespace and numbering

Current references such as:

`SMJ/QMS/QSP/15`  
`SMJ/QMS/QSP/21`  
`SMJ/QMS/QSP/22`

are inconsistent with the actual document structure.

Recommended mapping:

- Control of Non-Conforming Work → `SMJ/QSP/15`
- Internal Audit → `SMJ/QSP/20`
- Management Review → `SMJ/QSP/21`

### QSP_13 risk reference

QSP_13 refers to `SMJ/QSP/14` in a context describing risk assessment. The actual risk procedure is `SMJ/QSP/18`.

Recommended correction:

**Risk Assessment and Mitigation → `SMJ/QSP/18`**

### QSP_11 control-of-nonconforming-work reference

The document contains a reference to `SMJ/QSP/14` in a context labelled as control of nonconforming work. The actual process is QSP_15.

### QSP_15 nonconformance/audit record

QSP_15 uses `SMJ/FRM/SYS/07` for audit/nonconformance records and `SMJ/FRM/SYS/04` for corrective actions. Those files are not currently present and therefore remain open broken references.

### QSP_14 complaint-form identifier

QSP_14 expects:

`SMJ/FRM/MKT/02`

but the actual complaint document contains:

`SMJ/FRM/MKT/01`

while the customer feedback form also uses `SMJ/FRM/MKT/01`.

This is a **direct identifier collision**.

### QSP_17 record numbering example

QSP_17 gives `SMJ/FRM/SYS/03` as a corrective-action example, while other current documents use `SMJ/FRM/SYS/04` for corrective action.

The approved code must be selected and all references reconciled.

### QSP_10 placeholders

The following should not survive into an approved controlled procedure:

- `SMJ/FRM/LAB/01/XX`
- `SMJ/FRM/LAB/02/XX`
- `SMJ/QSP/XX`
- `SMJ/FRM/XX`

### QSP_04 placeholders

`SMJ/FRM/OPN/01/XX` indicates an unresolved generic form code. The repository actually contains four equipment-specific OPN/01 subforms, so the generic placeholder should be replaced by the approved subcodes or controlled parent code.

### Manual `FRM/OPN` references

The manual references `SMJ/FRM/OPN/03` for equipment conformity and `SMJ/FRM/OPN/04` for nonconforming work, while actual files suggest:

- `FRM_OPN_03_01` = Final Worksheet - Coal
- `FRM_OPN_02` = Control of Non-Conforming Work

This must be resolved before manual approval.

### QSP_04 TRG/08

QSP_04 references `SMJ/FRM/TRG/08`, but the file is not present in the current Tier 4 inventory.

---

# 13. Requirement → Manual → Procedure → Work Instruction → Record Traceability Matrix

| Requirement/process | Manual | Tier 2 | Tier 3 | Tier 4/evidence | Chain status |
|---|---|---|---|---|---|
| Impartiality | Yes | QSP_01 | EXB-SYS-04; SOP_HRD_01 | confidentiality/competence/CAPA records | **Incomplete** |
| Confidentiality | Yes | QSP_01/QSP_10/QSP_16/17 | EXB-SYS-02; SOP-SYS-01 | confidentiality agreement; incident records | **Incomplete** |
| Personnel competence | Yes | QSP_02 | EXB-HRD-01; SOP-SYS-08 | TRG records; HRD competence | **Incomplete** |
| Environment | Yes | QSP_03 | SOP-SYS-07; EXB-SYS-06 | QCD/06; QCD/05 | **Incomplete** |
| Equipment lifecycle | Yes | QSP_04 | SOP-SYS-06/07; EXB-SYS-01 | OPN maintenance + calibration records | **Mostly present** |
| Intermediate checks | Yes | QSP_05 | SOP-SYS-05/06/07 | QCD/05 | **Broken at record layer** |
| Metrological traceability | Yes | QSP_06 | relevant system SOPs | QCD/10; calibration records | **Partial** |
| Reference materials | Yes | QSP_07 | SOP-SYS-04/05 | QCD/09/QCD/10 | **Partial** |
| External providers | Yes | QSP_08 | none dedicated | PRC forms | **Incomplete** |
| Method validation | Yes | QSP_09 | Lab SOPs | MTH/01 | **Missing evidence form** |
| Method verification | Yes | QSP_09 | Lab SOPs | MTH/02 | **Missing evidence form** |
| Test-item handling | Yes | QSP_10 | SOP-SYS-03; EXB-SYS-05 | COC/inward/preservation | **Partial** |
| Uncertainty | Yes | QSP_11 | method SOPs | uncertainty budgets/records | **Incomplete** |
| Result validity | Yes | QSP_12 | EXB-SYS-06; Lab SOPs | IQC/MVR/PT/ILC | **Partial** |
| Contract review | Yes | QSP_13 | EXB-SYS-03 | review record | **Incomplete** |
| Complaints | Yes | QSP_14 | EXB-SYS-03 | complaint form | **Broken identifier** |
| Nonconforming work | Yes | QSP_15 | EXB-SYS-06 | OPN/02 + SYS/07 | **Incomplete** |
| Document control | Yes | QSP_16 | SOP-SYS-01 | Master List/change/archive records | **Partial** |
| Record control | Yes | QSP_17 | SOP-SYS-01 | archive/index/retention evidence | **Incomplete** |
| Risk | Yes | QSP_18 | safety/quality SOPs | risk register | **Present but duplicate** |
| Corrective action | Yes | QSP_19 | EXB-SYS-06 | CAPA record | **Broken references** |
| Internal audit | Yes | QSP_20 | SOP-SYS-09 required | plan/program/audit record | **Incomplete** |
| Management review | Yes | QSP_21 | communication support | SYS/14 minutes | **Missing record** |
| NABL symbol | Yes | QSP_22 | report-control process | RPT/01 | **Partial** |

The chain is therefore **not yet closed end-to-end** for several critical processes.

---

# 14. Documentation Gaps

## Gap A — Reference integrity

The repository currently lacks one authoritative relationship between:

- Master List code
- filename
- document title
- revision
- status
- parent document

This is the highest-level control problem.

## Gap B — Evidence closure

Several QSPs describe required actions, but there is no matching controlled evidence mechanism.

Examples:

- method validation
- method verification
- equipment intermediate checks
- management review
- internal audit findings
- annual training planning
- induction
- confidentiality acknowledgement
- supplier evaluation
- corrective action
- records archiving

## Gap C — Sampling evidence

SOP-SYS-03 requires:

- sampling records
- COC
- preservation records
- transportation records

Only the COC and inward register are clearly present.

## Gap D — Method-control evidence

QSP_09 calls for controlled validation/verification records and a validated-method list. These are absent.

## Gap E — PT/ILC evidence

QSP_12 and the IQC framework discuss proficiency testing/inter-laboratory comparison, but a dedicated evidence mechanism is not clearly present.

## Gap F — Management-review evidence

QSP_21 explicitly names `SMJ/FRM/SYS/14`, but no matching file exists.

## Gap G — Internal-audit evidence

QSP_20 explicitly names `SMJ/FRM/SYS/07`, but the file is absent.

## Gap H — Record retention/archive evidence

QSP_17 mentions `SMJ/FRM/SYS/02`; no matching file is present.

---

# 15. Duplicate / Overlapping / Potentially Redundant Documents

## 15.1 Duplicate laboratory SOPs

Three laboratory SOPs occur twice:

- Moisture in Coal
- Volatile Matter in Coal
- Total Ash in Coal

**Disposition:** compare, select current approved version, supersede/remove the other from active control.

## 15.2 Two risk-register documents

- `FRM-SYS-17 - Risk Register new.docx`
- `FRM-SYS-17 - Risk Register.docx`

They use the same apparent identifier but different structures.

**Disposition:** select one as the approved template; formally obsolete the other.

## 15.3 Competence documents

- `FRM-HRD-04 - Employees Competence Report.docx`
- `FRM_HRD_04_Personnel Competence Record.docx`

These may have distinct intended purposes (matrix vs detailed record), but they currently overlap in identifier and content.

**Disposition:** either:
- retain both with different approved identifiers and defined relationships, or
- consolidate into one master competence record plus one summary matrix.

## 15.4 Retest report DOCX/PDF

`FRM_QCD_02_Re-test Report.docx` and `.pdf` appear to represent the same conceptual form.

**Disposition:** treat the DOCX as controlled master/template and PDF as controlled output only if operationally required.

## 15.5 Test report DOCX/XLSX

`FRM_RPT_01_Test report – Coal.docx` and `.xlsx` both represent the same document number.

**Disposition:** decide whether one is:
- the controlled report template, and
- the approved spreadsheet-generation version,

or consolidate them.

## 15.6 Internal Audit Plan vs Internal Audit Program

These can legitimately be different:

- **Program** = annual/periodic audit framework
- **Plan** = individual audit schedule/plan

However, the Master List currently calls for a Tier 3 `SOP-SYS-09` Internal Audit Program, while the actual `Internal Audit Program.docx` is in Tier 4.

**Disposition:** move/reclassify or create the formal SOP, then use the Tier 4 program/plan as records/templates as intended.

---

# 16. Priority Action List

## Critical — do before controlled approval

### C1. Freeze the current document identifiers

Do not create further documents until the code system is reconciled.

### C2. Rebuild the Master List

Every line must have:

- code
- current filename
- title
- tier
- revision
- effective date
- status
- parent document
- superseded document where applicable

### C3. Resolve all duplicate identifiers

At minimum:

- MKT/01 vs MKT/02
- HRD/04 duplicates
- SYS/17 risk register duplicates
- report DOCX/XLSX
- retest DOCX/PDF
- duplicate Lab SOPs

### C4. Correct broken QSP references

Highest priority:

- QSP_13 risk-reference error
- QSP_11 nonconformance-reference error
- QSP_19 all broken QMS/QSP references
- QSP_15/SYS record mappings
- QSP_14 complaint form identifier
- QSP_10 `/XX` placeholders
- Manual OPN/SYS references

### C5. Close evidence gaps

Create or reconcile:

- PRC/PUR forms
- MTH/01
- MTH/02
- validated-method list
- QCD/05
- QCD/08
- SYS/04
- SYS/07
- SYS/14
- SYS/02
- TRG/01
- TRG/03
- TRG/06
- TRG/08
- controlled calibration schedule

### C6. Remove the Word lock file

Delete:

`~$P_06_Traceability of Measurements.docx`

It should never be part of the controlled repository.

## High

### H1. Add explicit Tier 3 references to all QSPs

Each QSP should contain a clear “Related Tier 3 Documents” section.

### H2. Add explicit Tier 4 references

Each QSP should identify the records/forms produced by the process.

### H3. Add parent reference to every Tier 3 SOP

Every Tier 3 document should identify its parent QSP(s).

### H4. Add method-SOP cross-references

Each analytical SOP should identify:

- applicable system QSPs
- equipment SOP
- QC/IQC document
- worksheet
- relevant reference standard
- validation/verification status

### H5. Establish external-reference control

Create a controlled list of external standards/references and their current edition/status.

## Medium

- controlled communication register
- report issue register
- backup verification record
- preservation record
- sampling field record
- equipment status/label control
- controlled obsolete-document archive
- formal document-change request record

## Low

- normalize punctuation/capitalization in filenames
- replace the double period in QSP_13 filename
- normalize “back-up” / “backup”
- normalize en dash/hyphen usage after identifier reconciliation

---

# 17. Recommended Final Documentation Structure

The final active structure should be:

```text
Quality Management/
│
├── Tier 1 - Quality Manual/
│   └── SMJ/QM/01 - Quality Manual
│
├── Tier 2 - Quality System Procedures/
│   ├── QSP_00_Index
│   ├── QSP_01_Impartiality
│   ├── QSP_02_Personnel
│   ├── ...
│   └── QSP_22_NABL_Symbol
│
├── Tier 3 - Exhibits, SOP's and other system documents/
│   │
│   ├── Exhibits/
│   │   ├── EXB-HRD-01
│   │   ├── EXB-SYS-01
│   │   ├── ...
│   │
│   ├── System SOPs/
│   │   ├── SOP_HRD_01
│   │   ├── SOP-SYS-01
│   │   ├── ...
│   │   └── SOP-SYS-09
│   │
│   └── Laboratory SOPs/
│       ├── Index
│       ├── SMJ/SOP/LAB/01/01
│       ├── ...
│       └── SMJ/SOP/LAB/01/08
│
└── Tier 4 - Forms, Formats and Records/
    ├── Master List
    ├── HRD
    ├── TRG
    ├── PRC/PUR
    ├── OPN
    ├── LAB
    ├── QCD
    ├── RPT
    ├── SYS
    └── MKT/COC
```

The physical folders can remain similar to the current structure, but the **master document register must become the authoritative mapping**.

---

# 18. Recommended Cross-Reference Standard

A consistent block should be added to every controlled QSP:

### Related Tier 3 Documents

| Code | Document | Relationship |
|---|---|---|
| ... | ... | Implementation / supporting requirement |

### Related Tier 4 Documents / Records

| Code | Document | Evidence generated |
|---|---|---|
| ... | ... | ... |

### Related QSPs

| Code | Document | Relationship |
|---|---|---|
| ... | ... | Upstream/downstream dependency |

Similarly, every Tier 3 SOP should contain:

- Parent QSP(s)
- Related QSP(s)
- Related Tier 3 documents
- Required Tier 4 forms/records
- External normative references

This will make the document network auditable without requiring the user to infer relationships from narrative text.

---

# 19. Exact Answer to the Most Important Question

## “For each manual and procedure, what Tier 2, Tier 3, and Tier 4 documents should be referenced, which of those references are currently missing, which documents need to be created, and exactly where should each reference be added?”

### Quality Manual

**Reference Tier 2:** all applicable `QSP_01`–`QSP_22`.

**Reference Tier 3:** the HRD, impartiality, secrecy, communication, calibration, sample-receipt, IQC, safety, sampling, CRM, equipment, competence and laboratory SOP documents identified above.

**Reference Tier 4:** only the principal evidence records: Master List, training/competence, equipment/calibration, sampling/COC, IQC, method validation, worksheets, reports, complaints, NCR, risk, audit and management review records.

**Missing:** calibration schedule, method records, audit record, management-review record, archive list and several HRD/TRG/QCD/SYS records.

**Where:** add references within the corresponding manual sections listed in Section 5, and add a consolidated Related Documents table after the manual's QMS/process overview.

### QSP_01

Reference:

- Tier 3: EXB-SYS-04, EXB-SYS-02, SOP_HRD_01, SOP-SYS-08, SOP-SYS-01
- Tier 4: confidentiality agreement, personnel/competence records, corrective-action record, complaint record

**Missing:** `TRG/04`, `TRG/06`, `SYS/04`.

**Add at:** organizational structure, conflict disclosure, confidentiality, training, monitoring/review and document-control subsections.

### QSP_02

Reference:

- Tier 3: EXB-HRD-01, SOP_HRD_01, SOP-SYS-08
- Tier 4: TRG/01, TRG/02, TRG/03, TRG/08, personnel qualification records

**Missing:** TRG/01, TRG/03, TRG/08 and other forms explicitly called by QSP_02.

**Add at:** Personnel selection criteria, Training Needs Identification, Training Implementation, Competency Assessment, Records Management.

### QSP_03

Reference:

- Tier 3: SOP-SYS-07, EXB-SYS-06, EXB-SYS-01
- Tier 4: QCD/06, QCD/05, SYS/04, TRG/02

**Missing:** QCD/05 and SYS/04.

**Add at:** Monitoring and Regulation; Documentation and Record Keeping; Review and Audit; Training and Awareness.

### QSP_04

Reference:

- Tier 3: EXB-SYS-01, EXB-SYS-06, SOP-SYS-06, SOP-SYS-07
- Tier 4: OPN maintenance records, QCD/05, calibration schedule, TRG/08

**Missing:** QCD/05, TRG/08, calibration schedule.

**Add at:** Equipment Handling, Equipment Use, Planned Maintenance, Documentation and Record-Keeping, Calibration.

### QSP_05

Reference:

- Tier 3: EXB-SYS-01, EXB-SYS-06, SOP-SYS-05, SOP-SYS-06, SOP-SYS-07
- Tier 4: QCD/05 and equipment/QC records

**Missing:** QCD/05.

**Add at:** Preparation, Execution, Documentation, Review and Approval.

### QSP_06

Reference:

- Tier 3: EXB-SYS-01, SOP-SYS-04, SOP-SYS-05, SOP-SYS-06, SOP-SYS-07
- Tier 4: QCD/10, QCD/05, calibration/equipment records, RPT/01

**Missing:** some referenced OPN/calibration identifiers must be reconciled.

**Add at:** Equipment Calibration Program, Reference Standards and Materials, Intermediate Checks, Test Standards References.

### QSP_07

Reference:

- Tier 3: SOP-SYS-04, SOP-SYS-05, EXB-SYS-06
- Tier 4: QCD/09, QCD/10, QCD/05 and STR/02

**Missing:** STR/02; possibly dedicated CRM intermediate-check record.

**Add at:** Selection, Initial Verification, Calibration and Traceability, Storage and Handling, Periodic Verification, Documentation and Records.

### QSP_08

Reference:

- Tier 3: no dedicated procurement implementation SOP currently required by content
- Tier 4: PUR/01 and PRC/01–04

**Missing:** procurement/provider forms.

**Add at:** Identification of Procurement Needs, Evaluation, Routine Procurement, Nonconformance.

### QSP_09

Reference:

- Tier 3: applicable analytical SOPs, SOP-SYS-04, EXB-SYS-06
- Tier 4: MTH/01, MTH/02, validated-method list

**Missing:** all three method-control records.

**Add at:** Method Validation, Method Verification, Records.

### QSP_10

Reference:

- Tier 3: SOP-SYS-03, EXB-SYS-05, EXB-SYS-03
- Tier 4: COC, inward register, worksheets, preservation records

**Missing:** preservation/field records and correction of placeholder identifiers.

**Add at:** Test Request Form, Sample Recording, Sample Approval, Sample Flow, Protection, Storage, Disposal/Return, Records.

### QSP_11

Reference:

- Tier 2: QSP_05 and QSP_12
- Tier 3: applicable analytical SOPs and QC criteria
- Tier 4: controlled uncertainty records

**Missing:** clearly controlled uncertainty record/budget framework.

**Add at:** Form/Records subsection.

### QSP_12

Reference:

- Tier 3: EXB-SYS-06; relevant LAB SOPs; SOP-SYS-04/05/06/07
- Tier 4: IQC plan, QCD/05, QCD/06, QCD/07, PT/ILC records

**Missing:** QCD/05 and PT/ILC record mechanism.

**Add at:** QC controls, Documentation and Traceability, Internal Audit.

### QSP_13

Reference:

- Tier 2: QSP_04, QSP_09, QSP_18, QSP_19, QSP_16, QSP_17
- Tier 3: EXB-SYS-03
- Tier 4: contract-review/request record

**Missing:** clearly controlled contract-review record and risk-reference correction.

**Add at:** Review of Completeness, Review of Testing Requirements, Risk Assessment and Mitigation, Documentation and Record Keeping.

### QSP_14

Reference:

- Tier 3: EXB-SYS-03
- Tier 4: MKT/01 feedback, MKT/02 complaint form

**Missing:** nothing conceptually, but the form identifiers are broken.

**Add at:** Documentation, Investigation, Corrective Actions, Records.

### QSP_15

Reference:

- Tier 2: QSP_19, QSP_20, QSP_21
- Tier 3: EXB-SYS-06, EXB-SYS-03
- Tier 4: OPN/02, SYS/04, SYS/07, MKT/01/02

**Missing:** SYS/04 and SYS/07 files.

**Add at:** Non-Conformance Management, Auditing Doubtful Areas, Review Meetings, Record Keeping.

### QSP_16

Reference:

- Tier 2: QSP_17
- Tier 3: SOP-SYS-01, EXB-SYS-02, EXB-SYS-03
- Tier 4: Master List and change/archive records

**Missing:** document-change, obsolete/archive evidence.

**Add at:** Records; Document Controller responsibilities; document distribution and control sections.

### QSP_17

Reference:

- Tier 2: QSP_16 and QSP_20
- Tier 3: SOP-SYS-01, EXB-SYS-02
- Tier 4: archive list, record index, analytical/equipment/audit records

**Missing:** SYS/02 and other indexing/archiving evidence.

**Add at:** Record Indexing System, Retention, Archiving.

### QSP_18

Reference:

- Tier 3: process-specific SOPs and EXB-SYS-06
- Tier 4: Risk Register

**Missing:** no conceptual process missing, but the duplicate Risk Register must be reconciled.

**Add at:** Documentation, Risk Treatment, Risk Monitoring, Reporting.

### QSP_19

Reference:

- Tier 2: QSP_15, QSP_20, QSP_21
- Tier 3: EXB-SYS-06, EXB-SYS-03
- Tier 4: corrective-action record plus NCR/audit/complaint records

**Missing:** corrective-action record.

**Add at:** references section and Documentation section.

### QSP_20

Reference:

- Tier 3: formal SOP-SYS-09
- Tier 4: Internal Audit Plan, Internal Audit Program, SYS/07 audit record

**Missing:** SOP-SYS-09 and SYS/07.

**Add at:** Audit Planning, Audit Preparation, Records.

### QSP_21

Reference:

- Tier 3: EXB-SYS-03 and related QSP inputs
- Tier 4: SYS/14 meeting minutes plus risk/customer/audit/CAPA/training records

**Missing:** SYS/14.

**Add at:** Review Input, Review Output, Meeting Minutes.

### QSP_22

Reference:

- Tier 2: QSP_16/QSP_17
- Tier 3: report-control process
- Tier 4: RPT/01 test report

**Missing:** explicit controlled current accreditation-scope reference if maintained separately.

**Add at:** General Requirements, Usage Guidelines, Verification and Monitoring.

---

# 20. Final Assessment

The repository is now **substantively populated enough to support the intended quality-system hierarchy**, and the Tier 3 and Tier 4 additions are valuable. The primary remaining problem is not lack of documentation volume; it is **document-control coherence**.

The recommended sequence is:

**1. Reconcile Master List and identifiers → 2. remove duplicates/obsolete files → 3. correct broken references → 4. create only the missing evidence forms → 5. add Tier 2↔Tier 3↔Tier 4 cross-links → 6. close the traceability chains → 7. perform a final controlled-document review.**

The repository should not be expanded with additional generic SOPs/forms until this reconciliation is complete. Otherwise the same identifier and parent-child inconsistencies will multiply.

## Priority summary

| Priority | Main actions |
|---|---|
| Critical | Master List reconciliation; fix QSP19/QSP13/QSP11/QSP14/QSP10 references; create missing audit/CAPA/MTH/TRG/QCD/SYS/PRC records; resolve duplicate IDs; delete Word lock file |
| High | Cross-reference all Tier 3 documents; add Tier 4 evidence mapping; close sampling/PT/ILC/uncertainty/back-up evidence |
| Medium | Communication/report issue/backup/preservation supporting records; external-reference register |
| Low | Filename punctuation/capitalization cleanup |

**Bottom line:** the hierarchy now exists, but the **reference graph is not yet closed**. The next controlled revision should be a **documentation-reconciliation revision**, not merely another content-expansion revision.
