# MyDocs — Run 0 Identifier Map

**Baseline:** main @ `79428117f4d6b8280a78e25d6e4fb65150c25e65`

## Identifier families observed

| Family | Observed use | Current state |
|---|---|---|
| QSP_00–QSP_22 | Tier 2 Quality System Procedures | Coherent file sequence; content-level references contain numbering errors in places |
| EXB-HRD-01 | Tier 3 HRD exhibit | Existing |
| EXB-SYS-01–06 | Tier 3 system exhibits | Existing |
| SOP-SYS-01–08 | Tier 3 system SOPs | Existing; SOP-SYS-09 expected by Master List but missing |
| SOP_HRD_01 | Tier 3 HRD SOP | Existing |
| SOP-LAB-01–08 | Tier 3 laboratory SOP subjects | 01–03 duplicated at two physical locations |
| FRM-HRD-04 / FRM_HRD_04 | HRD competence documentation | Identifier collision/overlap candidate |
| FRM-SYS-01-02 | Master List | Existing |
| FRM-SYS-17 | Risk Register | Two files use same apparent identifier |
| FRM-TRG-02 | Training Report | Existing |
| FRM/COC/01 | Chain of Custody | Existing |
| FRM/LAB/01/01, FRM/LAB/02/01 | Laboratory worksheets | Existing filename-derived identifiers |
| FRM/MKT/01 | Customer Feedback; also reported inside complaint document | Collision |
| FRM/MKT/02 | Complaint Report expected by QSP_14 | File exists, but its internal identifier is reported as MKT/01 |
| FRM/MKT/03 | Sample Inward Register | Existing |
| FRM/OPN/01/01–04 | Equipment PM checkpoints | Existing |
| FRM/OPN/02 | Nonconforming Work form | Existing |
| FRM/OPN/03/01 | Coal final worksheet | Existing |
| FRM/QCD/01, 02, 03, 04, 06, 07, 09, 10 | QCD forms/records | Existing |
| FRM/RPT/01 | Coal test report | Both DOCX and XLSX use same conceptual identifier |
| TRG/01, TRG/03, TRG/04, TRG/06, TRG/08 | Referenced personnel/training records | Several referenced identifiers have no matching file |
| SYS/02, SYS/04, SYS/07, SYS/10, SYS/14 | Referenced system records/schedules | Several are phantom/missing at current file level |
| STR/02 | Referenced reference-material record | No matching current file |
| MTH/01, MTH/02 | Method validation/verification records | No matching current file |

## Critical identifier conflicts

### 1. QSP namespace conflict

QSP_19 reportedly references:

- `SMJ/QMS/QSP/15`
- `SMJ/QMS/QSP/21`
- `SMJ/QMS/QSP/22`

The current repository uses the QSP numbering without the `SMJ/QMS/` namespace.

Known correct procedural mapping by current repository sequence:

- Nonconforming Work → QSP_15
- Internal Audit → QSP_20
- Management Review → QSP_21

**Status:** broken reference; correction deferred to remediation.

### 2. Risk assessment reference conflict

QSP_13 reportedly uses QSP_14 in a risk context.

The current procedure sequence identifies Risk Assessment as QSP_18.

**Status:** broken reference; decision not required unless the approved architecture differs.

### 3. Nonconforming-work reference conflict

QSP_11 reportedly references QSP_14 for nonconforming work.

Current repository sequence identifies Nonconforming Work as QSP_15.

### 4. Complaint form collision

QSP_14 expects `SMJ/FRM/MKT/02`.

The repository contains `FRM_MKT_02_Complaint Report Format.docx`, but the existing audit reports that its internal identifier is `SMJ/FRM/MKT/01`.

The customer-feedback form also uses `SMJ/FRM/MKT/01`.

**Status:** direct collision; requires architectural decision.

### 5. Corrective-action numbering conflict

The repository audit reports inconsistent use of `SMJ/FRM/SYS/03` versus `SMJ/FRM/SYS/04` for corrective-action-related records.

**Status:** unresolved.

### 6. Manual OPN/SYS numbering conflicts

The Quality Manual reportedly references:

- `SMJ/FRM/OPN/03`
- `SMJ/FRM/SYS/10`
- `SMJ/FRM/OPN/04`

while current files include:

- `FRM_OPN_03_01` — Final Worksheet - Coal
- no obvious SYS/10 file
- `FRM_OPN_02` — Control of Non–Conforming Work

**Status:** unresolved mapping.

### 7. QSP_10 placeholder identifiers

Reported unresolved placeholders include:

- `SMJ/FRM/LAB/01/XX`
- `SMJ/FRM/LAB/02/XX`
- `SMJ/QSP/XX`
- `SMJ/FRM/XX`

### 8. QSP_04 placeholder

Reported unresolved:

- `SMJ/FRM/OPN/01/XX`

Actual repository provides four OPN/01 equipment-specific files.

## Important distinction

This map records **identifiers observed or reported in current content/reference analysis**. It does not assign final replacement identifiers during Run 0.

