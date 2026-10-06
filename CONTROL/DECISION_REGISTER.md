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

## Human decisions required before execution

### DEC-01 — Moisture in Coal duplicate survivor
Documents: SOP LAB/SOP-LAB-01-Moisture in Coal.docx and Tier 3-root SOP-LAB-01-Moisture in Coal.docx.
Decision: select one active survivor or formally identify one as historical/obsolete.
Evidence: same subject/apparent identifier; approval/revision/content comparison is not independently available through current connector.
Recommended option: use approval, revision and effective-date evidence first; filename alone is insufficient.
Risk: two active controlled documents for one method.
Human decision: Yes.

### DEC-02 — Volatile Matter duplicate survivor
Documents: SOP LAB/SOP-LAB-02-Volatile Matter in Coal.docx and Tier 3-root copy.
Decision: select one active survivor or formally archive one.
Recommended option: approval/revision/content evidence first.
Human decision: Yes.

### DEC-03 — Total Ash duplicate survivor
Documents: SOP LAB/SOP-LAB-03-Total Ash in Coal.docx and Tier 3-root copy.
Decision: select one active survivor or formally archive one.
Recommended option: approval/revision/content evidence first.
Human decision: Yes.

### DEC-04 — Risk Register duplicate
Documents: FRM-SYS-17 - Risk Register.docx and FRM-SYS-17 - Risk Register new.docx.
Decision: select the authoritative active file, consolidate useful content if necessary, and retain history only where justified.
Evidence: same apparent identifier; 'new' is not proof of controlled status.
Human decision: Yes.

### DEC-05 — HRD-04 competence architecture
Documents: FRM-HRD-04 - Employees Competence Report.docx and FRM_HRD_04_Personnel Competence Record.docx.
Decision: consolidate or prove two distinct roles (e.g. summary matrix versus detailed record) and then assign distinct identifiers if needed.
Evidence: overlapping identity/subject; detailed function distinction requires content review.
Human decision: Yes.

### DEC-06 — Format-pair control model
Documents: QCD-02 DOCX/PDF, QCD-04 XLSX, RPT-01 DOCX/XLSX.
Decision: define whether each file is a controlled template, calculation workbook, generated output or record.
Recommended option: one logical controlled identity per controlled function; outputs are not automatically second templates.
Human decision: Yes.

### DEC-07 — MKT complaint versus feedback
Documents: FRM_MKT_01 Customer Feedback Form.docx; FRM_MKT_02 Complaint Report Format.docx.
Decision: maintain distinct complaint and feedback functions with unique IDs; likely feedback MKT/01 and complaint MKT/02, subject to content confirmation.
Evidence: QSP_14 expects MKT/02, while prior content audit reports the complaint document internally carries MKT/01.
Human decision: Yes.

### DEC-08 — Internal Audit Program architecture
Documents: Internal Audit Program.docx, Internal Audit Plan.docx, Master List expectation for SOP-SYS-09.
Decision: determine whether the existing unnumbered Program is the Tier 3 process document or a Tier 4 programme/record requiring a separate SOP-SYS-09.
Recommended option: separate process SOP from annual programme/plan only if current content does not already fulfil the process SOP function.
Human decision: Yes.

### DEC-09 — Corrective-action record identifier
Issue: inconsistent SYS/03 versus SYS/04 corrective-action references.
Decision: select the identifier established by the approved current form/function after comparison.
Human decision: Yes.

### DEC-10 — Calibration schedule identity
Issue: Quality Manual reportedly references SYS/10, but no matching current file exists.
Decision: confirm whether EXB-SYS-01 plus equipment calibration records are sufficient, or whether a separate controlled schedule is needed.
Human decision: Yes if a separate schedule is required.

### DEC-11 — Master List authority
Issue: baseline reports divergence between the Master List and the live file tree.
Decision: accept the Stage 2 Final Document Register as the architecture worklist; update the controlled Master List only during later execution after human approval.
Human decision: Yes for final controlled Master List acceptance.

### DEC-12 — Dedicated procurement Tier 3 SOP
Issue: QSP_08 exists but no dedicated procurement SOP is present.
Recommended architecture: retain procurement control at QSP_08 and use Tier 4 records unless actual laboratory content proves a separate Tier 3 SOP is necessary.
Human decision: Only if laboratory implementation requires a separate operational procedure.

### DEC-13 — Method validation/verification record architecture
Issue: MTH/01, MTH/02 and validated-method list are referenced but absent.
Recommended architecture: separate validation report, verification report and approved-method list unless actual control design proves a combined record sufficient.
Human decision: Yes before creation.

### DEC-14 — Equipment intermediate-check architecture
Issue: QCD/05 is referenced but absent.
Recommended architecture: one common controlled record only if it supports all applicable equipment; otherwise distinct records by equipment family.
Human decision: Yes before creation.

### DEC-15 — Sampling evidence architecture
Issue: COC, inward register and receipt checklist exist, but field/preservation evidence is not clearly closed.
Decision: inspect those existing records first; create separate field/preservation records only for evidence that remains unsupported.
Human decision: Yes.

### DEC-16 — PT/ILC evidence
Issue: QSP_12 addresses PT/ILC but no dedicated evidence mechanism is apparent.
Decision: establish a controlled PT/ILC record where applicable unless another existing QC record demonstrably fulfils the function.
Human decision: Yes.

### DEC-17 — Management-review evidence
Issue: QSP_21 reportedly references SYS/14 but no file exists.
Decision: approve final management-review minutes record identifier before creation.
Human decision: Yes.

### DEC-18 — Internal-audit evidence
Issue: QSP_20 reportedly references SYS/07 but no file exists.
Decision: approve final audit-record identity after DEC-08.
Human decision: Yes.

### DEC-19 — External standards register
Issue: external standards are referenced, but a standalone register is not conclusively required by current evidence.
Decision: determine whether Master List/external-reference controls are sufficient before creating a separate register.
Human decision: Yes.

### DEC-20 — Word lock file
Issue: ~$P_06_Traceability of Measurements.docx.
Resolution: no controlled ID; remove from active tree in a later execution run. No architecture change to controlled documents.
Human decision: No.

## Execution gate

Mass editing must not start while any active-document identity remains ambiguous. Later agents must use FINAL_DOCUMENT_REGISTER.xlsx plus this register and the migration plan as the authoritative architecture worklist.