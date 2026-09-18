# NUS High-Rigor Simple Sheet Design Standard

**ID:** \`NUS-SIMPLE-SHEET\`  
**Version:** 1.0.0  
**Status:** GOVERNED LAYOUT AND INFORMATION-ARCHITECTURE STANDARD  
**Reference workbook:** \`corrections(3).xlsx\`  
**Reference workbook SHA-256:** \`ea283312452fdb83ceeb379e1d9a47f39b7238e61f38f2e742f43c6a2144ab07\`

---

## 0. Purpose

This standard defines how to build a simple spreadsheet that remains scientifically rigorous, easy to scan, easy to compare across papers, and easy to audit.

The design objective is not maximum compactness. It is **maximum retrievability per unit of space**.

The core rule is:

\[
\boxed{
\text{one row}=\text{one paper},
\qquad
\text{one column}=\text{one scientific role},
\qquad
\text{one cell}=\text{one answer to one question}
}
\]

The sheet must preserve the causal reading order:

\[
\text{Identity}
\rightarrow
\text{Intervention}
\rightarrow
\text{Engineering}
\rightarrow
\text{Engineering-to-sustainability bridge}
\rightarrow
\text{Sustainability}
\rightarrow
\text{Comparison}
\rightarrow
\text{Trade-off}
\rightarrow
\text{Decision}
\]

---

# 1. Why the reference simple sheet works

The \`New\` sheet in the reference workbook uses 15 semantic columns:

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

This is effective because the table is **wide rather than vertically nested**.

A reader can compare the same scientific role across papers by moving vertically, while reading one paper causally by moving horizontally.

This dual navigation is mandatory:

- **horizontal reading = one paper's logic**
- **vertical reading = cross-paper comparison of one role**

---

# 2. Semantic column groups

The 15 columns form five functional bands.

## Band A — Identity and intervention

| Column | Role |
|---|---|
| A | Paper |
| B | Simple story / intervention |

Purpose: identify the focal study and explain the intervention in plain causal language.

## Band B — Engineering evidence

| Column | Role |
|---|---|
| C | Engineering performance measured |
| D | Performance effect |
| E | Engineering acceptability benchmark |
| F | Engineering output used in sustainability |

Purpose: distinguish what was measured, what changed, what counts as technically acceptable, and what engineering quantity actually crosses into sustainability.

## Band C — Sustainability mechanism

| Column | Role |
|---|---|
| G | Sustainability method / tool |
| H | Inputs / variables |
| I | Transformation |
| J | Sustainability outcomes |

Purpose: make the sustainability computation reproducible at the conceptual level.

## Band D — Comparison and trade-off

| Column | Role |
|---|---|
| K | Baseline / comparator |
| L | Trade-off |

Purpose: show what the alternative is compared against and why the preferred solution is not necessarily the minimum or maximum of one metric.

## Band E — Decision

| Column | Role |
|---|---|
| M | Decision |
| N | Decision basis |
| O | Decision type |

Purpose: state the selected alternative, the evidence supporting that selection, and the formal nature of the decision procedure.

---

# 3. Reference geometry from the training workbook

The reference simple sheet uses the following approximate widths.

| Col | Role | Width px |
|---|---|---:|
| A | Paper | 235 |
| B | Simple story / intervention | 277 |
| C | Engineering performance measured | 240 |
| D | Performance effect | 248 |
| E | Engineering acceptability benchmark | 248 |
| F | Engineering output used in sustainability | 228 |
| G | Sustainability method / tool | 244 |
| H | Inputs / variables | 268 |
| I | Transformation | 283 |
| J | Sustainability outcomes | 261 |
| K | Baseline / comparator | 197 |
| L | Trade-off | 256 |
| M | Decision | 241 |
| N | Decision basis | 248 |
| O | Decision type | 232 |

Total sheet width is approximately **3707 px**.

The body rows in the six-paper reference range from approximately:

- **200 px**
- to **280 px**

The header is approximately **37 px**.

These dimensions are evidence of a design principle, not immutable constants.

---

# 4. Space allocation rule

Column width must be assigned by **semantic load**, not by the longest observed sentence.

Define three width classes:

## W1 — Compact role
Target: **190–230 px**

Use for:
- Paper
- Baseline / comparator
- Decision type

These fields should contain identification, concise comparison, or classification.

## W2 — Standard analytical role
Target: **230–260 px**

Use for:
- Engineering performance measured
- Performance effect
- Acceptability benchmark
- Sustainability method/tool
- Sustainability outcomes
- Trade-off
- Decision
- Decision basis

## W3 — High-information mechanism role
Target: **260–290 px**

Use for:
- Simple story / intervention
- Inputs / variables
- Transformation

These fields carry the most causal or inventory information and therefore deserve more horizontal space.

### Hard guardrails

- ordinary simple-sheet text column < **190 px**: WARN unless intentionally compact;
- ordinary simple-sheet text column > **320 px**: WARN;
- body column > **400 px**: FAIL unless explicitly justified by a different schema;
- automatic full-content autofit is forbidden for final layout.

---

# 5. Row-height rule

Body row height is controlled by the most demanding cell in that paper row.

Use:

- header: **34–42 px**
- ordinary body: **190–230 px**
- high-density body: **230–280 px**
- > **300 px**: WARN
- > **360 px**: FAIL for the simple sheet; move detail to the deep evidence sheet

The simple sheet must not become a vertically expanded narrative document.

### Density principle

If one paper requires substantially more vertical space than neighboring papers, first ask whether the cell is carrying deep evidence that belongs in \`visual\`.

---

# 6. Cell content budgets

Character count is not a scientific quality metric, but it is a useful layout control.

Recommended body-cell budgets:

| Role | Preferred | Soft maximum |
|---|---:|---:|
| Paper | 50–120 chars | 160 |
| Simple story | 250–500 | 650 |
| Engineering performance measured | 60–160 | 220 |
| Performance effect | 90–190 | 260 |
| Acceptability benchmark | 70–180 | 240 |
| Engineering output used in sustainability | 50–160 | 220 |
| Sustainability method/tool | 60–160 | 220 |
| Inputs/variables | 100–220 | 300 |
| Transformation | 100–230 | 300 |
| Sustainability outcomes | 100–220 | 300 |
| Baseline/comparator | 20–80 | 120 |
| Trade-off | 100–220 | 300 |
| Decision | 40–160 | 220 |
| Decision basis | 80–190 | 260 |
| Decision type | 50–150 | 200 |

### Escalation rule

When a cell exceeds its soft maximum:

1. remove duplicated information;
2. replace repeated prose with role-specific concise wording;
3. move equations, source wording, and detailed evidence to the deep sheet;
4. preserve only the minimum information necessary to understand and audit the decision chain.

Never compress by deleting a scientifically necessary qualifier such as age, unit, condition, comparator, or conflict.

---

# 7. Alignment and wrapping

## Header

- horizontal alignment: center
- vertical alignment: center or top
- wrap text: true
- one header row only
- concise role names

## Body

- horizontal alignment: left
- vertical alignment: top
- wrap text: true

Why top alignment matters:

When rows are 200–280 px high, top alignment keeps the first clause of every cell on the same visual horizon. This materially improves scanning.

### Forbidden

- center-aligned long body prose;
- bottom-aligned analytical prose;
- manual spaces used to create visual alignment;
- manual blank lines used merely to increase cell height.

---

# 8. Text structure inside cells

The simple sheet must not imitate the deep sheet's labelled multi-block structure.

Use three patterns.

## Pattern P1 — Inventory

Use semicolons:

\`Compressive strength; tensile strength; flexural strength; modulus of elasticity.\`

Best for:
- engineering measurements;
- inputs;
- decision basis.

## Pattern P2 — Mechanism

Use arrows only when a real computational or causal chain exists:

\`Material masses + impact factors → embodied carbon → divide by 28-day strength → performance-normalized carbon.\`

Best for:
- Transformation.

## Pattern P3 — Short causal prose

Use 2–4 compact sentences when a field must preserve sequence or qualification.

Best for:
- Simple story;
- Performance effect;
- Trade-off;
- Decision.

### Avoid

- bullet lists inside every cell;
- multi-paragraph essays;
- repeated paper title or method name in several adjacent cells;
- copying full author sentences when a role-specific synthesis is sufficient.

---

# 9. Information non-duplication rule

Each piece of information has one primary home.

Examples:

- the ASTM threshold belongs primarily in **Engineering acceptability benchmark**;
- the transformation equation belongs primarily in **Transformation**;
- the selected mix belongs primarily in **Decision**;
- why it was selected belongs primarily in **Decision basis**.

It is acceptable for the Simple story to mention these objects briefly, but it must not duplicate the full contents of the dedicated cells.

Define:

\[
D_{ij}=\text{material semantic overlap between adjacent cells}
\]

High repeated overlap is a layout defect because it consumes space without increasing retrievability.

---

# 10. Blank-space discipline

Blank cells are legitimate when the focal paper does not report a role.

Never fill a blank merely to make the row look complete.

Use:

- blank when the dimension genuinely does not apply and schema permits blank;
- \`NOT_REPORTED\` when explicit absence must remain auditable;
- \`No explicit focal ...\` when absence itself is scientifically meaningful.

Whitespace is information when it distinguishes **not reported** from **zero**.

---

# 11. Visual formatting standard

For high-rigor research tables:

- use one restrained header style;
- body background should normally remain white;
- use light borders;
- avoid decorative color encoding unless color itself has governed meaning;
- no merged cells in the body data region;
- do not hide scientific meaning in comments only;
- freeze the header row;
- freeze the paper column when horizontal navigation is extensive;
- use consistent font and body size;
- do not shrink text below comfortable reading size to force fit.

The default objective is **clarity before decoration**.

---

# 12. Simple-sheet versus deep-sheet boundary

Move content to the deep \`visual\` layer when it contains:

- full equations;
- several equation steps;
- author wording needed for provenance;
- conflict details;
- figure provenance;
- methodological implementation detail;
- long lists of inventory coefficients;
- external-method provenance;
- multiple competing interpretations.

Keep content in the simple sheet when it answers:

\`What does a reader need to understand this paper's engineering-to-sustainability decision logic in one horizontal scan?\`

---

# 13. Retrieval test

A valid simple sheet must allow a reader to answer each of the following without opening the PDF:

1. What intervention was tested?
2. What engineering performance was measured?
3. Did the paper define a technical pass/fail gate?
4. Which engineering output was actually used in sustainability?
5. Which sustainability method was implemented?
6. What transformation was applied?
7. What sustainability outcome resulted?
8. Compared with what?
9. What trade-off exists?
10. What was selected?
11. Why?
12. What kind of decision procedure was it?

If any answer requires searching several unrelated columns, the information architecture fails.

---

# 14. Cross-paper comparison test

A valid design must also support vertical comparison.

For any one column, a reader should be able to compare all papers without decoding different writing conventions.

Therefore:

- same role → same column;
- same unit concept → consistent notation;
- same absence state → same wording convention;
- same decision family → same controlled terminology.

---

# 15. Layout audit gates

## L0 — Schema integrity
Exactly one paper per body row and one semantic role per governed column.

## L1 — Causal order
Columns follow evidence-to-decision reading order.

## L2 — Width discipline
Widths follow semantic-load classes and hard guardrails.

## L3 — Height discipline
Header/body heights remain within governed limits; oversized rows trigger deep-sheet migration.

## L4 — Wrap/alignment
Header centered; body left/top; wrapping enabled.

## L5 — Density
No cell exceeds soft maximum without adjudicated justification.

## L6 — Non-duplication
Adjacent cells do not repeat the same material claim unnecessarily.

## L7 — Role atomicity
One cell does not combine several incompatible scientific roles.

## L8 — Blank-state integrity
Blank/NOT_REPORTED/no-explicit-gate states are preserved correctly.

## L9 — Notation
Units, symbols, percentages, signs, ages and comparison conditions remain readable and scientifically faithful.

## L10 — Navigation
Header and identity column can remain visible during navigation where supported.

## L11 — Visual restraint
No decorative formatting interferes with comparison or implies scientific ranking.

## L12 — Retrieval test
Twelve retrieval questions can be answered from one row.

## L13 — Vertical comparison test
One role can be compared across papers without reinterpreting writing conventions.

## L14 — Deep/simple boundary
Detailed evidence is not forced into the simple sheet.

## L15 — Independent visual QA
A second reviewer can identify every role and paper without explanation from the author.

---

# 16. Release rule

A simple sheet is release-ready only if:

\[
\boxed{
L0\land L1\land\dots\land L15
}
\]

and the underlying scientific synthesis has already passed \`NUS-E2D-AUDIT\`.

Therefore:

\[
\boxed{
\text{Release}
=
\text{Scientific correctness}
\land
\text{Information architecture correctness}
}
\]

A scientifically correct sheet that is difficult to retrieve from is not considered complete.

---

# 17. Recommended standard layout for future NUS synthesis sheets

Use this fixed left-to-right order unless a versioned schema explicitly changes it:

\`\`\`text
A  Paper
B  Simple story / intervention
C  Engineering performance measured
D  Performance effect
E  Engineering acceptability benchmark
F  Engineering output used in sustainability
G  Sustainability method / tool
H  Inputs / variables
I  Transformation
J  Sustainability outcomes
K  Baseline / comparator
L  Trade-off
M  Decision
N  Decision basis
O  Decision type
\`\`\`

Default width profile in pixels:

\`\`\`text
A 235
B 280
C 240
D 250
E 250
F 230
G 245
H 270
I 285
J 260
K 200
L 255
M 240
N 250
O 230
\`\`\`

Default body row target:

\`\`\`text
200–240 px
\`\`\`

Increase toward 280 px only when scientifically necessary.

---

# 18. Final design principle

The simple sheet should feel simple because the **architecture carries the complexity**.

Do not simplify by removing scientific structure.

Simplify by putting every fact in the one place where the reader expects to find it.
