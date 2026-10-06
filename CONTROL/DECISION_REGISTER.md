# MyDocs — Run 0 Decision Register

**Purpose:** architecture/control decisions that must be resolved before mass editing.  
**Rule:** Run 0 records questions; it does not decide final replacements unless the evidence is already structurally unambiguous.

| Decision ID | Question | Evidence / trigger | Current position | Priority |
|---|---|---|---|---|
| DEC-01 | Which of the duplicate Moisture in Coal SOPs is the approved current document? | Same subject exists under `SOP LAB/` and Tier 3 root | Compare content + revision/approval metadata | Critical |
| DEC-02 | Which of the duplicate Volatile Matter in Coal SOPs is current? | Same as DEC-01 | Unresolved | Critical |
| DEC-03 | Which of the duplicate Total Ash in Coal SOPs is current? | Same as DEC-01 | Unresolved | Critical |
| DEC-04 | Are the two FRM-SYS-17 Risk Register files separate controlled versions or duplicate/draft files? | Same apparent ID, one named “new” | Unresolved | Critical |
| DEC-05 | Are HRD-04 competence documents legitimately a summary matrix + individual record, or duplicates? | Two different filenames with overlapping identifier/subject | Unresolved | Critical |
| DEC-06 | How should DOCX/PDF and DOCX/XLSX format pairs be controlled? | QCD-02 and RPT-01 pairs; QCD-04 overlap | Define template/output/record model | High |
| DEC-07 | What is the approved complaint/feedback identifier split? | MKT/01 collision with complaint document content; QSP_14 expects MKT/02 | Decide distinct identifiers and parent relationships | Critical |
| DEC-08 | Is Internal Audit Program a Tier 3 SOP-SYS-09 process document, with Tier 4 Program/Plan records? | Master List reportedly expects SOP-SYS-09, while file exists at Tier 4 | Decide final hierarchy | Critical |
| DEC-09 | What is the approved corrective-action record identifier (SYS/03 vs SYS/04)? | Conflicting references in source documents | Unresolved | Critical |
| DEC-10 | What is the approved calibration schedule identifier? | Quality Manual reportedly references SYS/10; no obvious current matching file | Unresolved | Critical |
| DEC-11 | What is the authoritative Master List mapping? | Existing Master List reportedly diverges from actual tree | Reconcile code/title/tier/file/revision/status/parent | Critical |
| DEC-12 | Should a dedicated procurement Tier 3 SOP exist, or is QSP_08 sufficient with Tier 4 records? | QSP_08 exists; no dedicated procurement SOP file | Content/architecture review required | High |
| DEC-13 | What is the approved evidence structure for method validation/verification? | QSP_09 calls for MTH/01, MTH/02 and validated-method list; files absent | Decide record hierarchy before creation | Critical |
| DEC-14 | What is the approved equipment intermediate-check record structure? | QSP_03/05/06 require QCD/05, no current file | Decide common vs equipment-specific records | Critical |
| DEC-15 | What is the approved sampling evidence structure? | Existing COC/inward/checklist; field/preservation evidence incomplete | Decide whether separate forms or integrated records are appropriate | High |
| DEC-16 | What is the approved PT/ILC evidence record? | QSP_12 discusses PT/ILC; no clearly matching current Tier 4 file | Decide whether dedicated record is necessary | High |
| DEC-17 | What is the approved management-review evidence record? | QSP_21 reportedly expects SYS/14; file absent | Create after identifier decision | Critical |
| DEC-18 | What is the approved internal-audit evidence record? | QSP_20 reportedly expects SYS/07; file absent | Create/reconcile after hierarchy decision | Critical |
| DEC-19 | Which external-document/register convention is authoritative? | External standards are referenced but a current controlled register is not apparent | Decide scope and control method | High |
| DEC-20 | How should the Word lock file be handled operationally? | `~$P_06_Traceability of Measurements.docx` exists; `.gitignore` contains `~$*.docx` | Record for removal in later remediation; no action in Run 0 | Medium |

## Known structural non-decisions

The following are **not** decided in Run 0:

- final identifier replacements;
- active versus obsolete status for duplicate documents;
- document moves between tiers;
- creation of missing controlled forms/SOPs;
- wording of corrected references.

Those belong to later remediation runs.

