# Agentic AI for Zotero

**Skill ID:** `agentic-ai-for-zotero`  
**Version:** `1.0.0`  
**Purpose:** Build, diagnose, audit, authorize, execute, recover, and certify high-rigor Zotero automation workflows without confusing scientific reasoning, annotation geometry, current Zotero state, or transaction execution.

---

## 0. Operating Constitution

1. **Evidence before action.** Never mutate Zotero before the scientific target state is explicit.
2. **Separate science from mechanics.** Scientific inclusion, geometry, visible schema, transaction planning, execution, and post-write certification are different gates.
3. **Fail closed.** If an invariant is not proven, stop before mutation.
4. **Never patch expected hashes to make a failed run pass.** Fix the defect or revise the versioned contract transparently.
5. **A prior PASS is diagnostic evidence, not a substitute for a required fresh corpus-wide certification run.**
6. **Mutation authorization is separate from scientific approval, schema approval, and dry-run approval.**
7. **Minimize live Zotero executions, not checks.** Capture enough low-level state in one live run, then do as much reasoning offline as possible.
8. **Every mutation must be bounded.** Exact attachments, exact old keys, exact target states, exact counts, exact fingerprints.
9. **Single-use transactions require rollback and recovery architecture.**
10. **Post-write idempotency is mandatory.** A completed workflow must prove that rerunning the target-state comparison would perform no work.

Core architecture:

```text
Source Authority
→ Scientific Authority
→ Geometry Authority
→ Visible-State Schema
→ Dry Run
→ Explicit Mutation Authorization
→ Transactional Write
→ Independent Post-Write Audit
→ Idempotency
→ Final Freeze
```

---

# 1. Six Different Truths

A Zotero automation project becomes dangerous when different kinds of truth are collapsed.

## 1.1 Source truth

What PDF, parent item, attachment, DOI, title, page labels, and PDF bytes are authoritative?

Typical authority tuple:

```text
S_i = (
  library_i,
  parentKey_i,
  attachmentKey_i,
  DOI_i,
  title_i,
  PDFSHA_i,
  pageLabels_i
)
```

## 1.2 Scientific truth

What evidence should exist and why?

This includes:

- exact author wording;
- focal vs external ownership;
- scientific role;
- outcome dimension;
- input/use relationship;
- method/result/decision distinctions;
- uncertainty and contradiction flags;
- whether a visual object is scientifically necessary.

Scientific truth must not be inferred from current Zotero annotations merely because those annotations already exist.

## 1.3 Geometry truth

Where exactly should the annotation be?

For text:

```text
G_t = (pageIndex, rect_1, ..., rect_n)
```

For visual regions:

```text
G_v = (pageIndex, regionRects)
```

Geometry can be correct even when current Zotero geometry differs. Conversely, visually similar rectangles are not automatically exact target-state equality.

## 1.4 Visible-state truth

What must the native annotation look like in Zotero?

```text
V_a = (
  type,
  text,
  comment,
  color,
  pageLabel,
  position,
  tags
)
```

Example visible convention:

```text
annotation text = exact author wording
comment = Semantic label: exact author wording
color = role color
tags = []
```

## 1.5 Current live truth

What does Zotero contain *right now*?

Fingerprint each live annotation:

```text
F_live = H(
  paperID,
  annotationKey,
  type,
  text,
  comment,
  color,
  pageLabel,
  position,
  tags
)
```

## 1.6 Transaction truth

What exact operations transform current live state into desired final state?

Possible actions:

```text
KEEP_EXISTING_UNCHANGED
UPDATE_EXISTING_METADATA
CREATE_EXACT_GEOMETRY_REPLACEMENT_AFTER_DELETE_OLD
CREATE_EXACT_GEOMETRY_AND_METADATA_REPLACEMENT_AFTER_DELETE_OLD
CREATE_CORRECTED_REPLACEMENT_AFTER_DELETE_OLD
CREATE_ATOMIC_SPLIT_CHILD_AFTER_DELETE_PARENT
CREATE_NEW
RETIRE_NOT_FINAL
```

A transaction plan is correct only if each action can actually produce the target fingerprint.

---

# 2. Reusable Stage Architecture

## Stage A — Source discovery and identity freeze

Objectives:

- locate exact parent and PDF attachment;
- verify DOI/title;
- freeze PDF SHA-256;
- capture page count and native page labels;
- capture current native annotation keysets;
- establish canonical corpus order.

Do not do scientific mutation here.

**PASS:** every corpus unit has one unambiguous authoritative source.

## Stage B — Complete source capture

Capture enough source information in one or very few Zotero executions to avoid repeated Reader dependence.

Useful capture:

- PDF text;
- Reader character geometry if available;
- page boxes;
- structural surface candidates;
- native annotation state;
- page labels;
- source identifiers.

Rule:

```text
minimize Zotero executions, not checks
```

Treat the live application as an acquisition environment. Move most reasoning offline.

## Stage C — Scientific adjudication

Determine the scientifically accepted evidence set.

Required decisions:

- focal vs external;
- include/exclude/split/abstain;
- atomicity;
- scientific role;
- ontology dimensions;
- contradiction awareness;
- transformation linkage;
- input actually used vs merely discussed;
- evidence provenance.

Golden rules:

```text
Citation presence ≠ citation scope
paper-level co-occurrence ≠ explicit claim linkage
```

Use `ABSTAIN` rather than inventing a scientific relationship.

## Stage D — Human scientific approval

Human approval freezes the scientific evidence universe.

This approval does **not** authorize Zotero mutation.

Record:

- evidence-set hash;
- count;
- paper coverage;
- role counts;
- unresolved exceptions;
- explicit non-authorizations.

## Stage E — Exact geometry acquisition

Bind each accepted evidence unit to exact text or region geometry.

Rules:

- page index and native page label both matter;
- exact author wording must be preserved;
- line-group geometry is not automatically a stable cross-runtime invariant;
- geometry should be versioned and independently audited;
- region annotations need visual QA;
- a visually plausible crop can still be incomplete.

For visual regions check:

- complete object;
- caption policy;
- no clipping;
- no neighbor contamination;
- correct table/figure/equation identity.

## Stage F — Final redundancy and target adjudication

Once geometry is known, detect duplicate visible targets.

```text
scientific dual role ≠ need for two identical visible annotations
```

If two evidence records have identical paper, page, exact wording, and geometry, retain one visible annotation and preserve secondary semantics in the external analytical ledger.

## Stage G — Final Zotero target schema

Each schema record should contain at minimum:

```text
schema_record_id
paper_id
library_id
parent_key
attachment_key
pdf_sha256
annotation_type
role
secondary_analytical_roles
page_index
native_page_label
annotation_text
exact_author_wording
visible_comment
color
tags
position
position_sha256
current_annotation_key
current_annotation_expected_fingerprint_sha256
target_state_fingerprint_sha256
desired_final_state_action
```

Target fingerprint:

```text
F_target = H(
  library,
  parent,
  attachment,
  PDFSHA,
  type,
  text,
  pageLabel,
  position,
  color,
  comment,
  tags
)
```

## Stage H — Schema-bound human approval

Human approval must bind to the exact schema hash.

Approval should state explicitly:

```text
This is schema-bound approval only.
It does not authorize mutation.
```

If any approved transaction action changes, issue a new schema version and obtain new approval.

## Stage I — Writer dry-run + independent auditor dry-run

The writer dry-run simulates the planned transaction without mutation.

A separately implemented auditor independently reconstructs:

- current-state classifications;
- create/delete/update counts;
- projected final target fingerprints;
- conservation arithmetic.

Require:

```text
Projected_writer = Projected_auditor = Schema
```

This stage should catch transaction-action misclassification before mutation.

## Stage J — Independent premutation certification

Check the complete authority chain:

```text
scientific approval
geometry closure
final target set
schema approval
current baseline
writer dry-run
independent auditor dry-run
immutability
zero unresolved failures
```

Premutation certification permits asking for mutation authorization. It is **not** mutation authorization.

## Stage K — Explicit single-use mutation authorization

Bind authorization to:

- exact schema;
- exact live baseline;
- human schema approval;
- premutation certification;
- transaction counts;
- exact scope.

Example constraints:

```text
single_use = true
pdf_mutation_authorized = false
partial_execution_forbidden = true
failed_paper_only_execution_forbidden = true
target_substitution_forbidden = true
```

## Stage L — Transactional writer

Before first mutation:

1. verify all authority hashes;
2. fresh full-corpus prewrite;
3. acquire sync lock;
4. second fresh full-corpus prewrite;
5. freeze rollback snapshot;
6. freeze create-key plan;
7. perform final mutation-boundary verification;
8. consume the single-use authorization.

Safe mutation order:

```text
CREATE new
→ UPDATE metadata
→ DELETE old
→ VALIDATE exact final state
```

This preserves old evidence until new targets have been created.

## Stage M — Rollback / crash recovery

A serious agentic writer must be able to fail after mutation begins.

Rollback:

```text
delete transaction-owned creations
→ restore changed/deleted baseline records
→ verify complete original baseline
```

The authorization is consumed even if rollback succeeds.

Crash recovery must first ask:

> Did the exact final target state already commit?

If yes, preserve it. If no, restore baseline.

Never blindly rerun a single-use writer after a crash.

## Stage N — Independent post-write audit and idempotency

Use a **read-only** auditor developed separately from the writer.

Require two independent full-corpus passes.

Final audit:

- exact source identities;
- exact PDF SHA values;
- exact native annotation keysets;
- exact target fingerprints;
- zero tags if required;
- deleted old keys absent;
- no extras.

Idempotency vector:

```text
I = (NOOP, CREATE, UPDATE, REPLACE, DELETE)
```

Perfect closure:

```text
I = (N, 0, 0, 0, 0)
```

---

# 3. Failure Taxonomy

See `ERROR_FAIL_WIN_TAXONOMY.json` for the machine-readable version.

## F01 — Syntax / runtime-language failure

Examples:

- JavaScript syntax error;
- missing comma or malformed pasted JSON;
- unsupported syntax in Zotero runtime.

Response:

1. no mutation;
2. static syntax check outside Zotero;
3. version bump;
4. fresh full-corpus rerun if certification scope requires it.

## F02 — Authority failure

Examples:

```text
DOI_DRIFT
TITLE_DRIFT
PDF_SHA_DRIFT
PARENT_ATTACHMENT_MISMATCH
ANNOTATION_KEYSET_DRIFT
CURRENT_FINGERPRINT_DRIFT
```

Interpretation: the program is no longer operating on the certified world.

Response:

```text
ABORT BEFORE MUTATION
```

Do not repair by changing expected authority inside the writer.

## F03 — Reader/UI dependency failure

Example:

```text
tab is undefined
Reader document authority unavailable
```

Lesson: source authority must not depend on UI navigation.

## F04 — Cross-compartment/Xray failure

Example:

```text
Permission denied to access property "map"
```

Repair:

```text
JSON.stringify(privilegedObject)
→ cross boundary
→ JSON.parse(contentSide)
```

## F05 — Floating-point / canonicalization failure

If one path hashes raw IEEE-754 values and another rounds, the same scientific geometry can produce different hashes.

Freeze:

- coordinate units;
- rounding precision;
- rectangle ordering;
- text normalization;
- JSON key ordering.

Never patch expected hashes after seeing actual outputs.

## F06 — Over-specified runtime invariant

Reader segmentation can change while PDF bytes, exact text, page authority, and audited geometry remain unchanged.

Not every runtime representation deserves authority status.

## F07 — Scientific overreach

Examples:

- external literature values treated as focal results;
- inferring coupling from co-occurrence;
- converting a paper-level SDG mention into an outcome→SDG link;
- coercing dimensions into an unsupported integrated category.

Repair: ABSTAIN, split, or exclude.

## F08 — Atomicity failure

If one annotation contains scientifically independent claims, retire/supersede the non-atomic parent and create exact atomic children.

## F09 — Visible duplicate / dual-role collision

Same text + same geometry + multiple scientific roles does not necessarily require multiple visible highlights.

Use one visible target and preserve secondary semantics externally.

## F10 — Transaction-action classification failure

A target marked `KEEP_EXISTING_UNCHANGED` must already equal the target-state fingerprint.

A target marked `UPDATE_EXISTING_METADATA` may not conceal differences in:

- annotation type;
- annotation text;
- page label;
- geometry.

Otherwise classify as replacement.

## F11 — Partial transaction risk

Wrong:

```text
delete old before all replacements are safely created
```

Right:

```text
CREATE → UPDATE → DELETE → VALIDATE
```

## F12 — Sync race

Mitigation:

- require sync idle;
- acquire no-sync lock;
- repeat full prewrite under lock;
- fail if sync becomes active during transaction.

## F13 — Unexpected foreign mutation

If an unexpected annotation appears mid-transaction, fail and rollback. Do not absorb it silently.

## F14 — Rollback failure

Critical state:

```text
CRITICAL_PARTIAL_STATE_ROLLBACK_INCOMPLETE
```

Response:

- stop;
- preserve data directory;
- no new writer;
- recovery controller only;
- independently inspect current state.

## F15 — Package / provenance failure

A runtime PASS is insufficient if uploaded package hashes do not match.

A stage closes only when:

```text
runtime result
+ actual artifact bytes
+ manifest
+ independent package audit
```

all agree.

---

# 4. Failure Severity

| Level | Meaning | Mutation allowed? |
|---|---|---|
| L0 | Diagnostic warning | Maybe later |
| L1 | Scientific ambiguity | No affected target |
| L2 | Authority/schema inconsistency | No |
| L3 | Prewrite transaction failure | No |
| L4 | Mutation-time failure with successful rollback | Authorization consumed; no rerun |
| L5 | Partial-state / failed rollback | Critical stop |

---

# 5. Win Taxonomy

- **W01 SOURCE_PASS** — identities/PDF hashes/page labels proven.
- **W02 SCIENTIFIC_PASS** — accepted evidence resolved without blockers.
- **W03 GEOMETRY_PASS** — every target has authoritative geometry.
- **W04 SCHEMA_PASS** — one exact target fingerprint per desired annotation.
- **W05 DRYRUN_PASS** — writer and independent auditor reconstruct same final schema.
- **W06 PREMUTATION_PASS** — all preconditions for asking authorization satisfied.
- **W07 TRANSACTION_PASS** — exact authorized mutation completed.
- **W08 POSTWRITE_PASS** — persisted Zotero state equals schema.
- **W09 IDEMPOTENCY_PASS** — `I=(N,0,0,0,0)`.
- **W10 PACKAGE_CERTIFIED_PASS** — reports, manifests, hashes, sizes, and shards agree.

---

# 6. Error Recognition Decision Tree

```text
1. Did mutation begin?
   ├─ No  → diagnose safely.
   └─ Yes → is rollback complete?
            ├─ Yes → authorization consumed; versioned repair.
            └─ No  → critical recovery only.

2. Is source authority still identical?
   ├─ No → source drift incident.
   └─ Yes

3. Is scientific authority unchanged?
   ├─ No → reopen governed scientific adjudication.
   └─ Yes

4. Is desired geometry unchanged?
   ├─ No → geometry version/reapproval.
   └─ Yes

5. Is target state unchanged?
   ├─ No → schema version/reapproval.
   └─ Yes

6. Is only transaction classification wrong?
   ├─ Yes → correct actions, prove fingerprints unchanged, reapprove actions.
   └─ No

7. Is failure runtime representation only?
   ├─ Yes → redefine volatile diagnostic vs stable authority.
   └─ No → implementation defect.

8. After repair:
   fresh required full-corpus certification run.
```

---

# 7. Conservation-Law Mindset

Corpus conservation:

```text
N_corpus = PASS + FAIL
```

Target conservation:

```text
N_input = N_retain + N_redundant + N_superseded
```

Transaction conservation:

```text
N_final = N_current - N_deleted + N_created
```

Metadata updates are count-neutral.

Idempotency:

```text
N_final = NOOP + CREATE + UPDATE + REPLACE + DELETE
```

Exact closure:

```text
N_final = NOOP
CREATE = UPDATE = REPLACE = DELETE = 0
```

---

# 8. Independent Auditor Design

An auditor must not simply echo the writer.

Bad:

```text
if writer says PASS:
    PASS
```

Good:

- independently enumerate current annotations;
- independently recompute hashes;
- independently map old state to actions;
- independently reconstruct projected/final state;
- independently check counts;
- compare with writer only at the end.

Prefer different traversal directions:

```text
Writer: target-first
Auditor: live-state-first
```

This reduces common-mode failure.

---

# 9. Hashing and Canonicalization

Freeze:

1. Unicode normalization;
2. whitespace policy;
3. numeric precision;
4. rectangle ordering;
5. key ordering;
6. null vs omitted fields;
7. tag ordering;
8. color case;
9. page label type;
10. annotation type representation.

Canonical JSON concept:

```text
sort object keys recursively
retain array order where semantically meaningful
encode UTF-8
SHA-256
```

Do not treat ZIP container hashes as equivalent to internal artifact hashes.

---

# 10. Zotero-Native Annotation Data Model

Understand the difference between:

- parent bibliographic item;
- PDF attachment;
- native annotation item;
- highlight;
- image/region annotation;
- annotation key;
- attachment parent relationship;
- annotation text;
- comment;
- color;
- page label;
- sort index;
- position;
- tags.

A native target must be bound to an attachment, not merely a paper title.

Example highlight target:

```json
{
  "annotation_type": "highlight",
  "annotation_text": "exact author wording",
  "pageLabel": "12",
  "position": {"pageIndex": 11, "rects": [[0,0,1,1]]},
  "color": "#5fb236",
  "comment": "Engineering output: exact author wording",
  "tags": []
}
```

For a visual region, annotation text can be null while region geometry and exact-author wording in the approved comment remain authoritative.

---

# 11. Full-Corpus Rule

For a corpus certification stage:

```text
Every executable certification run attempts the entire governed corpus.
```

Do not:

- rerun only failed papers;
- reuse prior PASS papers as current certification;
- stop at first paper failure;
- vertically advance some papers while others remain at earlier gates.

A crash before corpus completion means `INCOMPLETE`, not partial PASS.

---

# 12. Live Execution Minimization

Use Zotero only when the answer requires current Zotero state.

Example architecture:

```text
L0 source/identity
L1 comprehensive source snapshot
offline science
L2 exact geometry/visual acquisition
offline schema
L3 dry-run current-state certification
L4 transactional mutation
L5 post-write certification
```

Every question answerable from frozen artifacts should be answered offline.

---

# 13. Human Authorization Model

Use four distinct human decisions.

## H1 — Scientific approval

“I approve these evidence interpretations.”

## H2 — Schema approval

“I approve these exact visible target states.”

## H3 — Mutation authorization

“I authorize this exact hash-bound transaction.”

## H4 — Final release acceptance

“I accept this certified final frozen state.”

Never infer H3 from H1 or H2.

---

# 14. Transaction Safety Architecture

A robust single-use writer should contain:

```text
authority binding
fresh prewrite 1
sync lock
fresh prewrite 2
rollback snapshot
precommit creation-key plan
mutation-boundary full validation
single-use authorization marker
create phase
update phase
delete phase
final exact validation
transaction report
manifest
stop
```

Rollback snapshot must contain enough native state to recreate every changed old annotation:

```text
key
type
text
comment
color
pageLabel
sortIndex
position
tags
attachment identity
```

Generate all future native keys before mutation and verify they are unique and absent.

---

# 15. Recovery Rules

## Caught mutation failure

Rollback automatically.

If rollback succeeds:

```text
FAIL_TRANSACTION_ROLLED_BACK_AUTHORIZATION_CONSUMED
```

Do not rerun.

## Application crash

Use a separate recovery controller.

First:

```text
if exact final target state exists:
    preserve it
    mark commit recovered
else:
    remove transaction-owned created keys
    restore rollback snapshot
    prove baseline
```

A recovery controller must never silently issue new authorization.

---

# 16. Post-Write Certification

Do not trust a writer's own success result as final evidence.

Use a separately authored read-only auditor.

### Pass 1 — target-first exact audit

For every schema record:

- mapped key exists;
- correct attachment;
- exact fingerprint;
- tags;
- PDF SHA.

### Pass 2 — live-first idempotency audit

For every live annotation:

- maps to exactly one final target;
- exact target-state match;
- independently classify any difference.

Then check missing targets and extras.

Require:

```text
pass1 fingerprints = pass2 fingerprints
```

---

# 17. Teaching Curriculum

See `TEACHING_PLAYBOOK.md` for the full curriculum.

Suggested levels:

1. Zotero object model
2. Hashes and provenance
3. Evidence engineering
4. PDF/annotation geometry
5. Read-only agents
6. Schema engineering
7. Independent auditing
8. Transaction systems
9. Idempotency and final certification

Mastery means being able to explain not just how to mutate Zotero, but when **not** to mutate it.

---

# 18. Reusable Prompt for Future Zotero Projects

```text
Act as a high-rigor Agentic AI for Zotero.

Operate using a fail-closed staged workflow.

First determine the current stage and frozen authorities. Never infer mutation
authorization from scientific approval, schema approval, or a previous dry-run.

Separate:
1. source identity/PDF authority;
2. scientific evidence authority;
3. exact geometry authority;
4. visible Zotero target schema;
5. current live Zotero baseline;
6. transaction action plan;
7. mutation authorization;
8. post-write certification.

For every stage:
- define exact invariants;
- define PASS/FAIL/ABSTAIN states;
- use SHA-256 provenance;
- use exact corpus arithmetic;
- continue through the complete governed corpus to expose all defects;
- never reuse prior PASS records as a substitute for a required fresh run;
- never patch expected hashes to force a PASS;
- version every repair;
- independently audit important outputs.

Minimize Zotero executions, not checks. Do as much reasoning offline as possible.

Before any mutation:
- require an exact schema;
- exact current-state fingerprints;
- writer dry-run;
- independent auditor dry-run;
- premutation certification;
- separate explicit hash-bound mutation authorization;
- fresh complete-corpus prewrite;
- sync lock;
- second complete-corpus prewrite;
- rollback snapshot;
- precommit key plan.

Mutation order:
CREATE → UPDATE → DELETE → FINAL VALIDATION.

After mutation:
use a separately implemented read-only auditor and require idempotency:
NOOP=N, CREATE=UPDATE=REPLACE=DELETE=0.

If a failure occurs, classify it before repairing it. Explain:
- what invariant failed;
- whether mutation started;
- whether source/science/geometry/schema changed;
- whether rollback is required;
- whether authorization is consumed;
- what exact fresh certification is required next.
```

---

# 19. Incident-Analysis Prompt

```text
Analyze this Zotero run as an incident, not as a generic error message.

Return:
1. Stage and authority context
2. Exact failing invariant
3. Failure class (F01-F15)
4. Whether mutation began
5. Whether the failure compromises source, science, geometry, schema, transaction plan, or persisted Zotero state
6. Evidence proving the classification
7. Forbidden shortcuts
8. Minimal correct repair
9. Required version bump
10. Required regression test
11. Whether a fresh all-corpus rerun is mandatory
12. Exact PASS condition after repair

Never patch an expected hash simply because the actual hash differs.
```

---

# 20. Stage-Closure Prompt

```text
Independently audit this stage package.

Do not trust the runtime PASS status.

Verify:
- exact expected artifact set;
- file hashes and sizes;
- manifest integrity;
- corpus arithmetic;
- canonical paper order;
- authority hash chain;
- zero unauthorized mutation;
- all per-paper shards;
- no missing or substituted PASS records;
- exact next-gate semantics.

Return a machine-readable audit plus a concise closure report.
Only close the stage if every required invariant passes.
```

---

# 21. Agent Self-Questions

Before saying PASS, ask:

```text
What exactly did I prove?
What did I not prove?
Am I relying on a stale PASS?
Did I independently recompute anything?
Is this source truth, scientific truth, geometry truth, or transaction truth?
Does the arithmetic conserve?
Does the hash bind the intended object?
Could two different implementations share the same defect?
Was mutation reachable?
If mutation started, is rollback/recovery proven?
Is the authorization still valid and unused?
Would a second run do zero work?
```

---

# 22. Core Lessons from Frozen-37

## Lesson A — A failure can be evidence of rigor

The S10→S11 transaction-action defect was a success of the architecture: dry-run validation blocked a transaction that could not have reached exact approved geometry.

A system that never fails before mutation is often under-tested.

## Lesson B — Geometry is not “just presentation”

If geometry participates in the target fingerprint, geometry changes affect transaction class.

## Lesson C — Runtime implementation details must not become false scientific authority

Reader segmentation, UI tabs, compartment wrappers, and float formatting are implementation details. Separate them from source facts.

## Lesson D — Count equality is insufficient

`673 annotations exist` is weaker than:

```text
673 exact mapped keys
673 exact target fingerprints
zero extras
68 old keys absent
two independent passes equal
idempotency = (673,0,0,0,0)
```

## Lesson E — Human governance needs typed approvals

Scientific approval, schema approval, mutation authorization, and final certification are separate concepts.

## Lesson F — The strongest agent is not the one that mutates fastest

The strongest agent is the one that can prove when **not** to mutate.

---

# 23. Final Certification Standard

A Zotero agentic workflow is fully closed only if all exist:

```text
[ ] source identity freeze
[ ] scientific evidence approval
[ ] exact geometry authority
[ ] final redundancy adjudication
[ ] exact target schema
[ ] schema-bound human approval
[ ] frozen live baseline
[ ] writer dry-run
[ ] independently implemented auditor dry-run
[ ] premutation certification
[ ] explicit hash-bound single-use mutation authorization
[ ] fresh prewrite under current Zotero state
[ ] transactional writer with rollback
[ ] transaction artifact package audit
[ ] independent read-only post-write audit
[ ] idempotency NOOP=N
[ ] final package audit
[ ] final immutable release manifest
```

Until the last items pass, distinguish:

```text
runtime PASS
stage PASS
package-certified PASS
final release closure
```

They are not the same thing.
