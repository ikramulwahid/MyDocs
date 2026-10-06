# MyDocs — Stage 2 Cross-Reference Migration Plan

Purpose: define later reference migration. No replacements are executed in Stage 2.

## Safe migrations

| Found reference | Final target | Source(s) | Confidence | Priority |
|---|---|---|---|---|
| SMJ/QMS/QSP/15 | SMJ/QSP/15 | QSP_19 and any repeated source | High | Critical |
| SMJ/QMS/QSP/21 | SMJ/QSP/20 | QSP_19 and any repeated source | High | Critical |
| SMJ/QMS/QSP/22 | SMJ/QSP/21 | QSP_19 and any repeated source | High | Critical |
| QSP_14 in QSP_13 risk context | SMJ/QSP/18 | QSP_13 | High | Critical |
| QSP_14 in QSP_11 nonconforming-work context | SMJ/QSP/15 | QSP_11 | High | Critical |
| SMJ/FRM/LAB/01/XX | SMJ/FRM/LAB/01/01 or applicable approved LAB subform | QSP_10 | High | High |
| SMJ/FRM/LAB/02/XX | SMJ/FRM/LAB/02/01 or applicable approved LAB subform | QSP_10 | High | High |
| SMJ/FRM/OPN/01/XX | Applicable SMJ/FRM/OPN/01/01–04 | QSP_04 | High | High |

## Decision-dependent migrations

| Found reference | Planned target | Source | Blocker |
|---|---|---|---|
| SMJ/FRM/MKT/02 | Approved complaint-form ID | QSP_14 | DEC-07 |
| SYS/03 corrective-action reference | Approved CAPA ID | QSP_17 and related sources | DEC-09 |
| SMJ/FRM/SYS/10 | Approved calibration schedule ID, or no separate ID if EXB-SYS-01 satisfies the function | Quality Manual | DEC-10 |
| SMJ/FRM/OPN/03 | Approved worksheet ID | Quality Manual | Identifier reconciliation |
| SMJ/FRM/OPN/04 | Approved NCR-related record ID | Quality Manual | Identifier reconciliation |
| SMJ/FRM/TRG/08 | Approved competence record ID | QSP_02/QSP_04 | Missing-record architecture |
| FRM/STR/02 | Approved reference-material evidence ID | QSP_07 | Missing-record architecture |
| SOP-SYS-09 | Approved Tier 3 internal-audit process ID | QSP_20/Master List | DEC-08 |
| SMJ/FRM/SYS/07 | Approved internal-audit record ID | QSP_15/QSP_20 | DEC-18 |
| SMJ/FRM/SYS/14 | Approved management-review minutes ID | QSP_21 | DEC-17 |
| SMJ/FRM/SYS/02 | Approved archive/record-list ID | QSP_17 | Record architecture decision |

## Cross-reference additions

Later execution should add where absent:

- Tier 2 → Related Tier 3 Documents
- Tier 2 → Related Tier 4 Forms/Records
- Tier 3 → Parent QSP(s)
- Tier 3 → Related QSPs
- Tier 3 → Required Tier 4 records
- Tier 4 → Parent QSP / Parent SOP where applicable

## Execution sequence

1. Resolve ambiguous duplicate/identifier decisions.
2. Freeze FINAL_DOCUMENT_REGISTER.
3. Migrate safe legacy QSP references.
4. Migrate approved form references.
5. Add controlled parent/child reference blocks.
6. Re-scan for phantom identifiers and /XX.
7. Perform post-migration reference audit.