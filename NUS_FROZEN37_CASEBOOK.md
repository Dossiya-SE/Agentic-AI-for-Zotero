# Casebook — Frozen-37 Lessons

This file records reusable incidents from the NUS Frozen-37 implementation.

## Case 1 — UI-tab dependence broke document authority

Symptom:

```text
TypeError: can't access property "type", tab is undefined
```

Problem:
A supposedly authoritative source-access path still depended on Reader UI state.

Lesson:
Document/PDF authority must be UI-independent.

---

## Case 2 — Cross-compartment array caused `.map` permission error

Symptom:

```text
Permission denied to access property "map"
```

Repair:
Serialize array through `JSON.stringify`, cross the boundary, then `JSON.parse`.

Lesson:
Privilege boundaries change what JavaScript objects safely support.

---

## Case 3 — Raw float geometry hashes disagreed with canonical rounded hashes

Symptom:
Many papers reported `TEXT_GEOMETRY_DRIFT`.

Diagnosis:
The same scientific geometry was being hashed using different floating-point canonicalization.

Repair:
Freeze six-decimal PDF-point canonicalization.

Lesson:
Never interpret a hash mismatch before verifying both sides use the same canonicalization contract.

---

## Case 4 — Runtime Reader representation was too strong an invariant

Later geometry differences appeared after hundreds of targets passed.

The correct response was not to patch hashes. The architecture was revised so:
- PDF SHA;
- exact text;
- page authority;
- independently audited frozen geometry

remained authoritative, while volatile Reader segmentation became diagnostic.

Lesson:
A stable source fact and a volatile application representation are not the same thing.

---

## Case 5 — Visual region was scientifically valid but geometrically incomplete

Two regions in NUS-172 clipped meaningful table boundaries/captions.

Lesson:
A native annotation can exist and still fail independent visual QA.

---

## Case 6 — Two same-span records did not require two visible highlights

Two pairs of evidence records were identical in wording/page/geometry but had dual analytical roles.

Repair:
One visible annotation, secondary role in external ledger.

Lesson:
Do not confuse analytical multiplicity with visible-annotation multiplicity.

---

## Case 7 — S10 transaction-action classification defect

The approved target state was scientifically correct, but:
- 45 targets marked KEEP had geometry differences;
- 10 targets marked metadata-only update also had geometry differences.

S11 dry-run failed closed.

No target state changed. Only action classification was repaired and reapproved.

Lesson:
A transaction action is part of the schema's operational correctness.

---

## Case 8 — Runtime PASS required package audit

S11 and S13 runtime results were not treated as formal closure until:
- package uploaded;
- exact artifact set checked;
- report and manifest hashes verified;
- all per-paper shards audited.

Lesson:
Claims about a run and the persisted audit package are separate evidence layers.

---

## Case 9 — Transaction safety

The S13 writer required:
1. fresh full-37 prewrite;
2. sync lock;
3. second full-37 prewrite;
4. rollback snapshot;
5. precommit unique keys;
6. mutation-boundary verification;
7. single-use authorization consumption.

Then:
`CREATE → UPDATE → DELETE → VALIDATE`.

Lesson:
Agentic mutation requires systems engineering, not just API calls.

---

## Case 10 — Final S14 runtime idempotency

S14 reported:

```text
37/37 PASS
final_live_count = 673
validated_target_count = 673
NOOP_EXACT = 673
CREATE = 0
UPDATE = 0
REPLACE = 0
DELETE = 0
pass1_pass2_fingerprint_sets_equal = true
old_deleted_keys_absent_count = 68
zotero_mutation_performed = false
pdf_mutation_performed = false
```

This is the target pattern for future final-state certification.

Note:
At the moment this skill package was created, the S14 runtime PASS had been accepted, while the final S14 output-package byte audit remained a separate final closure gate.
