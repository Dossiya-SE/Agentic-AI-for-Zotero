# NUS Evidence-to-Decision Audit Method (NUS-E2D-AUDIT)

**Version:** 1.0.0  
**Status:** GOVERNED AUDIT SPECIFICATION  
**Reference workbook:** \`corrections(3).xlsx\`  
**Reference workbook SHA-256:** \`ea283312452fdb83ceeb379e1d9a47f39b7238e61f38f2e742f43c6a2144ab07\`  
**Reference cases:** NUS-15, NUS-172, NUS-18, NUS-187, NUS-48, NUS-59

---

## 0. Purpose

This method audits whether NUS engineering-sustainability synthesis is scientifically traceable from focal-paper evidence to the final decision statement.

It does **not** score prose elegance. It tests whether every compact statement is supported by an explicit evidence/dependency chain.

Core audit object:

\[
\boxed{
\text{Intervention}
\rightarrow
\text{Engineering evidence}
\rightarrow
\text{Acceptability gate}
\rightarrow
\text{Engineering variable consumed}
\rightarrow
\text{Sustainability transformation}
\rightarrow
\text{Outcome}
\rightarrow
\text{Trade-off}
\rightarrow
\text{Decision}
}
\]

The method is fail-closed. Unsupported synthesis, silent conflict repair, invented benchmarks, or mislabelled optimization are blocking failures.

---

# 1. What the reference workbook is actually doing

The workbook contains two scientifically different layers.

## 1.1 Deep evidence layer — \`visual\`

The \`visual\` sheet is not a summary table. It is a structured evidence-and-transformation record.

Its columns are:

1. Paper
2. Purpose / intervention / sustainability inputs
3. Engineering assessment and outputs
4. Engineering outputs used as sustainability inputs
5. Sustainability metric / indicator
6. Engineering performance measured
7. Performance effect
8. Sustainability transformation
9. Baseline / benchmark / comparison / decision rule
10. Environmental outcomes
11. Economic outcomes
12. Social outcomes

Column H is expanded vertically for each paper into role-specific evidence blocks such as:

- Method
- Tool / implementation
- Author-defined equation flow
- Sensitivity / expert weighting, where focal
- Transformation
- Interpretation
- Relevant evidence / visuals
- Verification warning, when required

### Why this layer exists

It preserves the mechanism that connects engineering evidence to sustainability and decision logic. It prevents a final recommendation from becoming an unsupported prose conclusion.

## 1.2 Compact decision layer — \`New\`

The \`New\` sheet compresses the deep record into one row per paper:

1. Paper
2. Simple story / intervention
3. Engineering performance measured
4. Performance effect
5. Engineering acceptability benchmark
6. Engineering output used in sustainability
7. Sustainability method / tool
8. Inputs / variables
9. Transformation
10. Sustainability outcomes
11. Baseline / comparator
12. Trade-off
13. Decision
14. Decision basis
15. Decision type

### Why this layer exists

It is a decision map, not a second independent extraction. No scientific claim should first appear here. Every material statement must be traceable backward to the deep evidence layer and ultimately to focal-paper evidence.

---

# 2. Writing constitution

## R1 — Write by scientific role, not by narrative convenience

Each cell answers one scientific question. Do not merge distinct roles merely because the paper discusses them together.

Examples:

- measured property ≠ output consumed by sustainability;
- comparator ≠ engineering acceptability threshold;
- optimization algorithm ≠ sustainability method unless it optimizes a sustainability output;
- absolute environmental minimum ≠ integrated preferred alternative.

## R2 — Preserve actor and ownership

Use focal-author ownership explicitly when describing what the paper did:

- \`The authors tested...\`
- \`The authors used...\`
- \`The paper reports...\`

Do not convert analyst inference into author claim.

## R3 — Separate author evidence from analyst interpretation

Deep-layer interpretation must contain two explicit states:

\`Author evidence: ...\`

\`Analyst interpretation: ...\`

The labels are controlled. Variants such as \`interpretation:\` or accidental text such as \`a interpretation:\` are non-canonical.

## R4 — Preserve exact uncertainty and contradiction

If the focal paper is internally inconsistent:

- record both author states;
- name the conflict;
- do not choose one silently;
- propagate the conflict into the compact layer if it affects the transformation, outcome, or decision.

Permitted audit state:

\`PASS_WITH_PRESERVED_AUTHOR_CONFLICT\`

Silent repair is always FAIL.

## R5 — Use absence explicitly; never invent completeness

If no focal engineering threshold exists, write:

\`No explicit focal pass/fail engineering threshold...\`

Do not invent a standard merely because a baseline or reference model exists.

Unsupported sustainability dimensions remain blank / NOT_REPORTED. Blank does not mean zero.

## R6 — Quantities remain scientifically bound

A quantitative claim must preserve:

- object;
- alternative;
- age/time;
- condition;
- value;
- unit;
- comparator if a relative change is stated.

Approximation symbols, signs, percentages, and units are meaningful evidence and must not be normalized away.

## R7 — Use plain scientific notation in spreadsheet prose

Prefer:

- \`100 ± 20 mm\`
- \`≈ 30 MPa\`
- \`−18.02%\`
- \`1.08 × 10¹³ sej/m²·yr\`

Do not use raw LaTeX delimiters such as \`\\(...\\)\` inside ordinary spreadsheet prose.

## R8 — Lists are inventories; arrows are mechanisms

Semicolon-separated text is appropriate for inventory-like fields:

\`Fresh density; consistency; setting time; compressive strength\`

Arrows are reserved for causal/computational transformation chains:

\`Design variables → EnergyPlus → operational energy → transformities → emergy\`

Do not use arrows to imply a causal relation that the focal paper does not implement.

---

# 3. The seven distinctions the audit must protect

## D1 — Engineering measurement vs sustainability-consumed engineering output

A property belongs in **Engineering performance measured** if it was measured/modelled.

It belongs in **Engineering output used in sustainability** only if the focal sustainability/economic/integrated method explicitly consumes it.

Required dependency:

\[
E_{\mathrm{eng}} \xrightarrow{\mathrm{consumed\ by}} M_{\mathrm{sus}}
\]

Co-occurrence is insufficient.

## D2 — Baseline vs acceptability gate

**Baseline/comparator** answers: relative to what is performance compared?

**Engineering acceptability benchmark** answers: what criterion determines technical feasibility/pass/fail?

A DOE reference building can be a baseline without being an acceptability gate.

## D3 — Gate vs objective

Passing a standard only establishes admissibility.

\[
\text{Gate pass} \not\Rightarrow \text{optimal}
\]

The final decision may still depend on environmental, economic, durability, or multi-criteria evidence.

## D4 — Sustainability method vs engineering method

Classify a method by the output it generates in the focal workflow.

Examples from the regression set:

- EnergyPlus/BES → engineering simulation;
- emergy conversion → sustainability transformation;
- RSM on CS/STS/FS/ME → engineering optimization;
- AHP/Expert Choice across technical/economic/environmental criteria → integrated decision method.

## D5 — Transformation vs juxtaposition

A valid transformation must expose the implemented mapping, for example:

\[
\text{material mass}
\times
\text{impact factor}
\rightarrow
\text{embodied carbon}
\]

or

\[
\text{chloride diffusion}
\rightarrow
\text{service-life model}
\rightarrow
\text{CO}_2/\text{service-year}
\]

Reporting engineering and sustainability values beside each other is not a transformation.

## D6 — Formal optimization vs comparative selection

Decision type must reflect the actual mathematical/decision procedure.

Controlled families:

- \`COMPARATIVE_SELECTION\`
- \`INDEX_BASED_SELECTION\`
- \`ENGINEERING_OPTIMIZATION_PLUS_SEPARATE_SUSTAINABILITY_COMPARISON\`
- \`FORMAL_SUSTAINABILITY_OPTIMIZATION\`
- \`WEIGHTED_MULTI_PERFORMANCE_RANKING\`
- \`FORMAL_MCDM\`

Do not promote a mechanical RSM optimum into a sustainability optimum.

## D7 — Absolute sustainability minimum vs integrated preferred alternative

The preferred alternative may not minimize every individual burden.

The **Trade-off** field must explain why.

---

# 4. Canonical field-writing rules for \`New\`

## F1 — Simple story / intervention

Required structure:

\[
\text{Intervention}
+
\text{engineering validation}
+
\text{sustainability coupling}
+
\text{selection logic}
\]

It should explain the paper in causal order, not list results.

## F2 — Engineering performance measured

Inventory only. Use semicolon-separated variables. Include time/age when scientifically material.

## F3 — Performance effect

Describe directional/mechanistic response. Use quantitative values only when needed to identify an optimum, threshold crossing, or major trade-off.

## F4 — Engineering acceptability benchmark

Must be one of:

1. explicit focal threshold/standard;
2. design target used by focal authors;
3. explicit statement that no focal pass/fail threshold exists.

Do not convert comparator values into gates.

## F5 — Engineering output used in sustainability

Must name the smallest engineering object actually consumed by the sustainability/economic/integrated calculation.

If direct and indirect couplings both exist, label them.

## F6 — Sustainability method / tool

Name only methods/tools implemented by focal authors in the focal workflow.

Distinguish calculation method from software.

## F7 — Inputs / variables

List variables actually entering the sustainability transformation. Literature provenance values may be listed only if the focal paper adopts/uses them.

## F8 — Transformation

Minimum valid form:

\[
\boxed{
\text{source variable}
\rightarrow
\text{operator/model}
\rightarrow
\text{sustainability/economic output}
}
\]

For a performance-normalized metric, the engineering denominator/numerator must appear explicitly.

## F9 — Sustainability outcomes

Prefer absolute value + relative change + baseline when reported.

Do not insert analyst-reconstructed numbers unless explicitly marked as derived and reproducible.

## F10 — Baseline / comparator

One concise comparator statement. No decision logic.

## F11 — Trade-off

Must identify competing objectives or non-coincident optima.

A trade-off is not merely “performance changed.”

## F12 — Decision

State only the selected alternative/configuration/ranking actually supported by the paper.

## F13 — Decision basis

List the evidence that caused the decision. It must be a subset of already audited evidence.

## F14 — Decision type

Use controlled decision taxonomy. State what the method is **not** when misclassification risk is high.

---

# 5. Cross-layer traceability contract

The compact \`New\` row is derived from \`visual\`; it is not independently authored.

Required mapping:

| Compact field | Required deep-layer source |
|---|---|
| Simple story | Purpose + engineering assessment + interpretation |
| Engineering performance measured | Engineering performance measured |
| Performance effect | Performance effect |
| Engineering acceptability benchmark | Baseline/benchmark/decision-rule field |
| Engineering output used in sustainability | Engineering outputs used as sustainability inputs |
| Sustainability method/tool | Method + Tool/implementation |
| Inputs/variables | purpose/input record + equation flow + method implementation |
| Transformation | Transformation + equation flow |
| Sustainability outcomes | Environmental/economic/social outcomes + relevant evidence |
| Baseline/comparator | Baseline/benchmark field |
| Trade-off | performance effect + outcomes + interpretation |
| Decision | decision-rule field + interpretation + relevant evidence |
| Decision basis | all upstream fields |
| Decision type | implemented decision procedure |

### Critical rule

A claim that exists only in \`New\` and has no audited deep-layer source is a **novel synthesis claim** and fails unless explicitly adjudicated and added to the deep layer first.

---

# 6. Audit statuses

Use only:

- \`PASS\`
- \`PASS_WITH_PRESERVED_AUTHOR_CONFLICT\`
- \`WARN_NONBLOCKING_STYLE\`
- \`ABSTAIN_SOURCE_INSUFFICIENT\`
- \`FAIL\`

No numeric score can override a critical failure.

---

# 7. NUS-E2D audit gates

## A0 — Workbook structure
Expected sheets and required columns are present; compact rows and deep paper blocks are unambiguous.

## A1 — Source identity
Verify paper ID, title, DOI, focal PDF identity and source authority.

## A2 — Focality
Every scientific statement is focal-author evidence, focal-author implementation, or explicitly labelled analyst interpretation.

## A3 — Role correctness
Each statement belongs to the correct semantic field.

## A4 — Engineering acceptability
Verify a true focal gate or explicitly record that none exists.

## A5 — Engineering-to-sustainability dependency
Every engineering output claimed as a sustainability input has an explicit downstream use. Required: \`consumed_by != null\`.

## A6 — Transformation completeness
A transformation specifies source/input, operator/model/equation, and sustainability/economic/integrated output.

## A7 — Equation fidelity
Author equations preserve symbols, factors, denominators, units and scope. No silent repair.

## A8 — Quantitative fidelity
For every material number verify:
\[
Q=(object,alternative,time,condition,value,unit,comparator)
\]

## A9 — Conflict preservation
Known/new author conflicts are first-class and propagated when they affect compact synthesis.

## A10 — Baseline / benchmark / objective separation
Verify these are three distinct scientific objects.

## A11 — Trade-off validity
Trade-off is supported by non-coincident objectives, threshold effects, or competing dimensions.

## A12 — Decision traceability
\[
\text{DecisionBasis}\subseteq\text{AuditedEvidence}
\]

## A13 — Decision-type correctness
The claimed architecture matches the implemented method.

## A14 — Analyst interpretation control
Use exact prefixes \`Author evidence:\` and \`Analyst interpretation:\`. Interpretation cannot manufacture new author facts.

## A15 — Cross-sheet conservation
No new material claim appears only in \`New\`; no material deep-layer conflict affecting a decision is lost.

## A16 — Unsupported-dimension control
No environmental/economic/social outcome is populated without focal evidence. Absence remains blank / NOT_REPORTED.

## A17 — Visual provenance
Figures come from the focal PDF, have exact identity, correct paper block and transformation relevance. Reconstructed figures are never presented as authentic.

## A18 — Independent release audit
A read-only auditor independently reconstructs gate, consumed output, transformation, baseline, trade-off, decision and decision type.

---

# 8. Permanent six-paper regression cases

## NUS-15
MUST treat ASTM C618-22a SAI ≥75% as engineering acceptability; identify 28-day compressive strength as the SI/EI engineering input; distinguish absolute environmental minimum from integrated preferred mix. MUST NOT select 35% solely because EE/GWP is lower or treat gate pass as optimality.

## NUS-172
MUST preserve M25 31.5 MPa and 100 ± 20 mm criteria; preserve printed Eq. (3) versus reported Si mismatch; preserve S20 recommendation. MUST NOT repair Eq. (3) silently or collapse early-age and long-term optima.

## NUS-18
MUST classify DOE medium-office building as baseline, not gate; EnergyPlus output as engineering input to emergy; Taguchi/ANOVA/metamodel as formal design optimization. MUST NOT invent a gate or call EnergyPlus itself the sustainability method.

## NUS-187
MUST preserve engineering/fire compliance before Eq. (22); direct and indirect whole-life pathways; weighted multi-performance ranking after an engineering gate. MUST NOT let weighting replace compliance.

## NUS-48
MUST classify RSM as mechanical multi-response optimization; Eco-Strength Efficiency as performance-normalized carbon; preserve the 32.88 vs 39.42 MPa author conflict. MUST NOT call RSM joint sustainability optimization or choose one conflict value silently.

## NUS-59
MUST preserve service-life modelling, AHP/Expert Choice weights (Technical 66%, Economic 21%, Environmental 13%), and formal MCDM classification. MUST NOT infer final ranking from one criterion or collapse different optima.

---

# 9. Required audit record per paper

\`\`\`text
PaperID
SourceIdentityStatus
DeepLayerStatus
CompactLayerStatus
EngineeringGate
EngineeringOutputConsumed
SustainabilityMethod
Transformation
Baseline
TradeOff
Decision
DecisionBasis
DecisionType
ConflictStatus
FigureProvenanceStatus
CrossSheetTraceabilityStatus
CriticalFailures[]
Warnings[]
FinalStatus
\`\`\`

If \`CriticalFailures.length > 0\`, FinalStatus = FAIL.

---

# 10. Release invariant

A synthesis is releasable only when:

\[
\boxed{A0\land A1\land\dots\land A18}
\]

A preserved focal-author conflict may yield:

\[
\boxed{\text{PASS\_WITH\_PRESERVED\_AUTHOR\_CONFLICT}}
\]

The conflict is not the failure. Hiding, repairing, or losing it is the failure.

---

# 11. Relationship to existing Zotero governance

This method extends, rather than replaces:

- \`SKILL.md\`
- \`TEST_GATES.md\`
- \`WEAKNESS_REGISTER.json\`

The Zotero evidence engine answers:

\`What evidence is canonical?\`

NUS-E2D-AUDIT answers:

\`Does the workbook transform canonical evidence into a scientifically faithful engineering-to-sustainability decision chain?\`
