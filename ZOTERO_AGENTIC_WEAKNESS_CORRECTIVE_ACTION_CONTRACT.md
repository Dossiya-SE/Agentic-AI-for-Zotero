# Zotero Agentic — Weakness & Corrective-Action Contract

**Status:** mandatory governance extension  
**Version:** 1.1.0  
**Scope:** NUS Core-7 scientific annotation reconciliation and all future Zotero mutation workflows

This contract converts known annotation-system weaknesses into mandatory detection, correction, and acceptance gates. It is not a discussion note. A Zotero agent must fail closed whenever a required correction is unresolved.

## Governing architecture

```text
Full paper
→ scientific adjudication
→ canonical evidence
→ geometry proof
→ mutation plan
→ Zotero mutation
→ independent audit
→ second-run idempotency
```

Forbidden architecture:

```text
old annotations + new discoveries → keep everything
```

## Canonical evidence terminal states

Every candidate evidence object must end in exactly one state:

```text
GOLD_VISIBLE
LEDGER_ONLY
CONTEXT_ONLY
CONFLICT_RECORD
SUPERSEDED
DUPLICATE
REJECTED
```

Core invariant:

```text
scientifically useful ≠ necessarily visible in Zotero
```

---

## Global weakness register

| ID | Weakness | Mandatory corrective action | Hard acceptance gate |
|---|---|---|---|
| W01 | Additive merging instead of reconciliation | Build one canonical target state per paper. Re-adjudicate all old/new evidence into a terminal state. | No record survives merely because it existed before. |
| W02 | Annotation count mistaken for annotation quality | Optimize for unique scientific information and apply semantic deduplication before write. | `semantic_duplicate_count = 0` in Gold layer. |
| W03 | Gold annotations, full scientific ledger, and context/conflict evidence mixed together | Maintain three separate layers: Gold visible, scientific ledger, rejected/context/conflict ledger. | Every evidence object has exactly one visibility state. |
| W04 | Multi-function sentence assigned one role | Split evidence atomically by scientific function. | One visible annotation has one dominant controlled role. |
| W05 | Role frozen too early during sequential reading | Allow deferred role promotion after full-paper downstream-use analysis. | Final role is assigned only after dependency analysis. |
| W06 | Characterization incorrectly promoted to INPUT | Enforce `INPUT <= USED_IN_FOCAL_METHOD`. | Every Orange INPUT has at least one explicit `consumed_by` edge. |
| W07 | Engineering method confused with sustainability method | Classify by what the method generates in the focal study, not the generic method name. | Every method has `generated_output_type`. |
| W08 | Engineering equation confused with sustainability transformation | Require an explicit conversion into sustainability/economic/integrated output. | Transformation has source → procedure/equation → sustainability result. |
| W09 | Different DECISION scopes collapsed together | Encode decision subtype, scope, criteria, candidate set, selected alternative, and basis. | Every Yellow record has complete decision metadata. |
| W10 | Author inconsistencies silently repaired | Preserve exact author text and create first-class conflict records. | Conflicts are linked; no silent normalization or correction. |
| W11 | Zotero key used as scientific identity | Use permanent `EvidenceID` independent of Zotero annotation key. | Split/recreate operations preserve EvidenceID lineage. |
| W12 | Duplicate detection too text-based | Use semantic identity: scientific object + metric + alternative + time + condition + result + role. | Abstract/body/conclusion/table/figure duplicates are recognized semantically. |
| W13 | Provenance inconsistently encoded | Require `FG`, `FA`, `LD`, `HY`, or `UNRESOLVED`. | No approved INPUT/OUTCOME has missing provenance. |
| W14 | Sustainability outcomes lack HOW_GENERATED lineage | Build backward dependency graph `S <- F <- I/P`. | Each quantified sustainability outcome has `generated_by` or explicit `NOT_REPORTED`. |
| W15 | Scientifically approved evidence lacks native Zotero geometry | Separate scientific approval from write readiness. | No write without verified page, span/region, and geometry. |
| W16 | Mixed tables/figures colored as one role | Segment rows/cells/subregions or use stronger textual evidence. | No one-color region contains incompatible roles. |
| W17 | Equations reconstructed from OCR or flattened text | Use exact native PDF equation regions. | Equation annotation points to verified native PDF geometry. |
| W18 | No negative regression corpus | Encode MUST-NOT examples from adjudicated papers. | All negative regression tests pass before mutation. |
| W19 | Writer can mutate an incomplete paper | Add paper readiness state and disable write until fully frozen. | Only `GOLD_FROZEN + GEOMETRY_FROZEN + QA_PASS` may mutate. |
| W20 | Writer and auditor can repeat the same logic/error | Keep auditor independently implemented and read-only. | Auditor reconstructs target↔live correspondence independently. |
| W21 | Partial writes can leave corrupt Zotero state | Use paper-atomic transactions, complete backup, immediate rollback registration. | Failed transaction restores exact pre-write fingerprint. |
| W22 | Zotero/manual edits can invalidate a plan during execution | Recompute live-state fingerprint immediately before write. | Abort on any state drift. |
| W23 | First successful run treated as closure | Mandatory second-run idempotency certification. | Second run yields `NOOP=N` and `CREATE=UPDATE=REPLACE=DELETE=0`. |
| W24 | V17 treated as authoritative Gold target | Treat V17 only as evidence inventory/reference; construct a new canonical Gold target. | Production writer must not ingest V17 directly as final target. |

---

# Paper-specific weaknesses and required corrections

## NUS-172

### W172-01 — excessive visible engineering/mechanism evidence
Create a `ScientificFactSignature`. Repeated pozzolanic/C-S-H/pore-refinement explanations without a new value, alternative, time, condition, or causal distinction become `DUPLICATE` or `LEDGER_ONLY`.

### W172-02 — multiple S20 optima can be conflated
Each Yellow record must encode:

```text
decision_scope
decision_criteria
candidate_set
selected_alternative
decision_basis
robustness_status
```

Mechanical, sulphate, integrated environmental-engineering, robustness, and practical-applicability decisions remain distinct.

### W172-03 — Si unit conflict not machine-controlled
Use:

```text
unit_status = AUTHOR_UNIT_CONFLICT
conflict_group = NUS172-SI-UNIT
```

Never normalize the paper's conflicting forms such as `kgCO2-eq/m3`, `kgCO2-eq/m3.MPa`, and `kgCO2-eq/MPa` into one invented author unit.

### W172-04 — context mixed with Gold evidence
Characterization, limitations, and future work default to `LEDGER_ONLY` or `CONTEXT_ONLY` unless deliberately approved for visible Zotero.

---

## NUS-18

### W18-01 — approved evidence with unresolved geometry
Use separate fields:

```text
scientific_status = APPROVED
geometry_status = VERIFIED | PENDING
```

Only `APPROVED + VERIFIED` becomes `WRITE_READY`.

### W18-02 — appendix/body/abstract repetition
Use preference hierarchy:

```text
primary body implementation
> appendix repetition
> abstract repetition
> conclusion repetition
```

Later evidence remains visible only if it adds a new parameter, equation, validation, decision, boundary, or otherwise unique scientific object.

### W18-03 — mixed-role figures/tables
Example: `ΔEUI` is engineering output while `ΔEmconstruction` and `ΔEmbuilding` are sustainability outcomes. Create atomic subregions. If reliable geometry cannot be proved, fail closed and use stronger textual evidence.

### W18-04 — BES/BEMA/MMD method-role contamination
Freeze functional classification:

```text
BES / EnergyPlus = ENGINEERING_METHOD
BEMA / emergy accounting = SUSTAINABILITY_METHOD / TRANSFORMATION
MMD / Taguchi-regression = classified by its focal emergy-assessment/optimization function
```

---

## NUS-15

### W15-01 — characterization overrepresented
Raw PSD, XRD, SEM, aggregate grading, and basic characterization default to `LEDGER_ONLY` unless they provide a unique focal engineering result necessary to the paper's argument.

### W15-02 — Yellow decisions have different meanings
Keep one visible Yellow ontology role but encode subtypes:

```text
ENGINEERING_APPLICATION_DECISION
ENVIRONMENTAL_DECISION
ECONOMIC_DECISION
ENV_ENGINEERING_DECISION
INTEGRATED_DECISION
FINAL_RECOMMENDATION
APPLICATION_BOUNDARY_DECISION
```

### W15-03 — explicit SDG link treated like measured sustainability performance
Encode:

```text
sdg_link_status = EXPLICIT_AUTHOR_LINK
measurement_status = NON_QUANTIFIED_LINKAGE
```

An SDG statement is not equivalent to quantified GWP, EE, SI, EI, or cost evidence.

### W15-04 — adopted coefficients and focal calculations mixed
Encode provenance by stage:

```text
input provenance = FA or LD
calculation provenance = FG
outcome provenance = HY
```

---

## NUS-187

### W187-01 — heterogeneous Table 2 risks one-role overclassification
Map columns by downstream function instead of assigning one undifferentiated role:

```text
compressive strength -> structural model
density -> module weight / transport
thermal conductivity -> operational energy
carbonation coefficient -> service-life model
fire residual strength -> overall-performance score
```

### W187-02 — Table 8 mixes engineering and sustainability parameters
Only annotate the downstream rows/subregions consumed by operational-energy/carbon/cost transformations. Do not color the full mixed table as one Orange object.

### W187-03 — adopted vs generated properties insufficiently separated
Each property must encode:

```text
value_origin
citation_scope
implemented_in_focal_model
generated_or_adopted
```

A literature-derived value may be a valid focal INPUT when explicitly consumed, but never a focal-generated OUTPUT.

### W187-04 — decision scopes mixed
Differentiate component, reinforcement, material, circular-economy, and integrated system decisions in metadata.

### W187-05 — Eq. (22) under-specified
Encode Eq. (22) as:

```text
transformation_subtype = INTEGRATED_WEIGHTED_AGGREGATION
integration_level = EXPLICIT
weights_origin = AUTHOR_SELECTED
```

It aggregates mechanical, fire, economic, energy, and carbon performance into overall module performance.

---

## NUS-48

### W48-01 — author-internal inconsistencies
Create first-class QA states:

```text
AUTHOR_INTERNAL_INCONSISTENCY
AUTHOR_VALUE_CONFLICT
AUTHOR_UNIT_CONFLICT
AUTHOR_LABEL_CONFLICT
```

Each conflict record stores:

```text
conflicting_evidence_ids
preferred_analytical_authority
reason_for_preference
no_silent_correction = true
```

Known regression cases include Wheat Straw Ash/WSA labels, modulus-of-elasticity location conflict, MPa/GPa inconsistency, and inconsistent R² reporting.

### W48-02 — Table 3 has design and downstream INPUT functions
After Eq. (1) and Eq. (3) prove consumption of material masses, the final visible canonical role is `INPUT` (Orange). Preserve:

```text
secondary_function = DESIGN_MATRIX
```

Do not create duplicate Blue and Orange annotations for the same table.

### W48-03 — RSM may be incorrectly classified as sustainability optimization
Freeze:

```text
RSM_NUS48 = ENGINEERING_METHOD
```

The formal RSM responses are CS, STS, FS, and ME. The sustainability branches are separate:

```text
Wi + EC factor -> EC
28-day CS + EC -> ESE
Wi + unit price -> Cost
```

### W48-04 — practical and numerical optima may be collapsed
Keep distinct:

```text
10.24% CCA + 0.52% JF = ENGINEERING_RSM_OPTIMUM
10% CCA + 0.50% JF = FINAL_PRACTICAL_RECOMMENDATION
```

### W48-05 — equation reconstruction risk
Eqs. (1)–(3) use exact native PDF regions. Machine-readable graph may encode semantic transformations, but visible Zotero evidence must not reconstruct equation typography from flattened text.

---

## NUS-59

### W59-01 — insufficient depth under current protocol
Until full re-extraction is completed:

```text
paper_status = REEXTRACTION_REQUIRED
write_enabled = false
```

Required full pass includes purpose, alternatives, expert elicitation, engineering inputs, sustainability methods, transformations, environmental/economic/social outcomes, weighting/integration, decision, validation, uncertainty, limitations, geometry, provenance, and deduplication.

Only then may status advance to `GOLD_FROZEN`.

---

## NUS-191

### W191-01 — largest Core-7 readiness gap
Until full re-extraction is completed:

```text
paper_status = FULL_REEXTRACTION_REQUIRED
write_enabled = false
```

Reconstruct the focal chain from the full paper:

```text
seismic engineering performance
→ resilience
→ sustainability assessment
→ decision
```

Historical sparse records are not sufficient authority for production mutation.

---

# Mandatory paper-readiness state machine

```text
DISCOVERED
↓
FULL_TEXT_AVAILABLE
↓
SCIENTIFIC_EXTRACTION_COMPLETE
↓
HUMAN_ADJUDICATED
↓
CANONICALIZED
↓
GOLD_FROZEN
↓
GEOMETRY_FROZEN
↓
MUTATION_PLAN_VALIDATED
↓
WRITE_READY
↓
WRITTEN
↓
INDEPENDENT_AUDIT_PASS
↓
IDEMPOTENCY_PASS
↓
CLOSED
```

Any unresolved weakness sends the paper to:

```text
BLOCKED
```

with a machine-readable reason.

# Mandatory per-evidence state machine

```text
CANDIDATE
↓
FOCALITY_CHECK
↓
ATOMICITY_CHECK
↓
ROLE_CHECK
↓
DOWNSTREAM_USE_CHECK
↓
PROVENANCE_CHECK
↓
DUPLICATE_CHECK
↓
CONFLICT_CHECK
↓
GEOMETRY_CHECK
↓
FINAL_STATE
```

# Fail-closed blockers

The agent must refuse to write on any of:

```text
UNKNOWN_ROLE
UNKNOWN_FOCALITY
UNKNOWN_PROVENANCE
UNKNOWN_UNIT_STATUS
UNRESOLVED_AUTHOR_CONFLICT
MISSING_GEOMETRY
MIXED_ROLE_REGION
DUPLICATE_UNRESOLVED
MISSING_GENERATED_BY
MISSING_CONSUMED_BY_FOR_INPUT
PAPER_NOT_GOLD_FROZEN
LIVE_ZOTERO_STATE_DRIFT
PDF_HASH_MISMATCH
```

Core rule:

```text
uncertainty -> abstain
```

Never:

```text
uncertainty -> nearest available classification
```

# Required next program state

Do not create another additive V18 as production authority.

Required sequence:

```text
V17 + Five-Paper Master + full PDFs
→ Canonical Gold Target V1
→ complete NUS-59
→ complete NUS-191
→ freeze Core-7
→ geometry proof
→ dry-run reconciliation
→ backup
→ paper-atomic mutation
→ readback
→ independent audit
→ second-run Δ=0
```

The production Zotero reconciler remains disabled until all paper-level and evidence-level gates above pass.