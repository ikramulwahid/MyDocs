# MyDocs — Run 0 Broken Reference Register

**Run rule:** references are logged; no reference is corrected during Run 0.

| Issue ID | Source document | Reference found | Likely intended document | Evidence | Confidence | Requires decision? |
|---|---|---|---|---|---|---|
| BR-01 | QSP_19 | `SMJ/QMS/QSP/15` | QSP_15 | Current repository sequence and prior audit identify QSP_15 as Nonconforming Work | High | N |
| BR-02 | QSP_19 | `SMJ/QMS/QSP/21` | QSP_20 | Current repository sequence identifies QSP_20 as Internal Audit | High | N |
| BR-03 | QSP_19 | `SMJ/QMS/QSP/22` | QSP_21 | Current repository sequence identifies QSP_21 as Management Review | High | N |
| BR-04 | QSP_13 | QSP_14 in risk context | QSP_18 | Current repository sequence identifies QSP_18 as Risk Assessment | High | N |
| BR-05 | QSP_11 | QSP_14 in nonconforming-work context | QSP_15 | Current repository sequence identifies QSP_15 as Control of Nonconforming Work | High | N |
| BR-06 | QSP_14 | `SMJ/FRM/MKT/02` | Current complaint form | File `FRM_MKT_02_Complaint Report Format.docx` exists, but prior content audit reports its internal ID as MKT/01 | High | Y |
| BR-07 | QSP_17 / related references | corrective-action record numbered as SYS/03 in one context | SYS/04 corrective-action record, or other approved code | Prior audit reports inconsistent SYS/03 vs SYS/04 use | Medium | Y |
| BR-08 | QSP_10 | `SMJ/FRM/LAB/01/XX` | Existing LAB/01/01 or approved parent/subform | Current Tier 4 file exists with LAB/01/01 filename-derived ID | High | N |
| BR-09 | QSP_10 | `SMJ/FRM/LAB/02/XX` | Existing LAB/02/01 or approved parent/subform | Current Tier 4 file exists with LAB/02/01 filename-derived ID | High | N |
| BR-10 | QSP_10 | `SMJ/QSP/XX` | A specific existing QSP | Placeholder is unresolved by definition | High | Y |
| BR-11 | QSP_10 | `SMJ/FRM/XX` | A specific existing Tier 4 form | Placeholder is unresolved by definition | High | Y |
| BR-12 | QSP_04 | `SMJ/FRM/OPN/01/XX` | One or more existing OPN/01 equipment forms | Four OPN/01 subforms exist | High | Y |
| BR-13 | QSP_04 | `SMJ/FRM/TRG/08` | Missing employee competence/training evidence | No matching current file; TRG/08 is identified by prior audit as missing | High | N |
| BR-14 | QSP_07 | `FRM/STR/02` | Missing reference-material record | No matching current file in Tier 4 tree; prior audit identifies it as missing | High | Y |
| BR-15 | QSP_20 | `SOP-SYS-09` | Missing formal Tier 3 internal-audit SOP | Master List reportedly expects SOP-SYS-09, but no file exists | High | Y |
| BR-16 | QSP_20 / audit controls | `SMJ/FRM/SYS/07` | Missing internal-audit record | No matching current file in Tier 4 tree | High | N |
| BR-17 | QSP_21 | `SMJ/FRM/SYS/14` | Missing management-review minutes | No matching current file in Tier 4 tree | High | N |
| BR-18 | QSP_17 | `SMJ/FRM/SYS/02` | Missing archive/record-list evidence | No matching current file in Tier 4 tree | High | N |
| BR-19 | Quality Manual | `SMJ/FRM/OPN/03` | Current/approved worksheet identifier requiring reconciliation | Actual file is `FRM_OPN_03_01`; prior audit identifies mismatch | Medium | Y |
| BR-20 | Quality Manual | `SMJ/FRM/SYS/10` | Calibration schedule / approved equivalent | No obvious matching current file | Medium | Y |
| BR-21 | Quality Manual | `SMJ/FRM/OPN/04` | Current/approved NCR-related record identifier | Actual NCR form is `FRM_OPN_02`; prior audit identifies mismatch | Medium | Y |
| BR-22 | QSP_19 and related QMS references | `SMJ/QMS/QSP/...` namespace | Current QSP naming convention | Repository master list/current filenames use QSP_ numbering, not this namespace | High | N |

## Broken-reference classes

- Wrong namespace: `SMJ/QMS/QSP/...`
- Wrong QSP number: risk/nonconformance contexts
- Phantom Tier 3: SOP-SYS-09
- Phantom Tier 4: SYS/02, SYS/04, SYS/07, SYS/14, TRG/01/03/04/06/08, STR/02, MTH/01/02, etc.
- Placeholder identifiers: QSP_10 and QSP_04 examples above
- Identifier collision: MKT/01 versus MKT/02
- Manual-to-file identifier mismatch: OPN/SYS examples

## Count note

The existing 2026-10-05 audit contains repeated textual mentions of these issues. Run 0 does **not** treat those repeated mentions as separate source-document occurrences. The raw DOCX occurrence count could not be independently extracted through the current connector, so counts are tracked by affected issue/source rather than fabricated as exact document-text totals.

