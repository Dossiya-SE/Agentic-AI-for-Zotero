# Teaching Playbook — Learn to Think Like a Zotero Agentic Systems Engineer

## Teaching objective

The learner should not merely know how to write Zotero JavaScript. They should learn to reason about:

- epistemic authority;
- deterministic state;
- scientific evidence;
- geometry;
- provenance;
- transaction safety;
- rollback;
- independent validation;
- idempotency.

## Weekly sequence

### Module 1 — Zotero internals
Outcome: explain parent, attachment, annotation, key, native fields.

### Module 2 — Read-only source auditor
Outcome: audit ten papers without opening Reader.

### Module 3 — Evidence semantics
Outcome: distinguish author claim, external background, focal method, focal result.

### Module 4 — Geometry
Outcome: reconstruct one highlight and one visual region.

### Module 5 — Fingerprints
Outcome: implement stable canonical hashing.

### Module 6 — Corpus execution
Outcome: continue after paper failure while preserving full-corpus accounting.

### Module 7 — Schema design
Outcome: produce target-state records and classify actions.

### Module 8 — Independent auditor
Outcome: independently reproduce projected final state.

### Module 9 — Transaction engineering
Outcome: create rollback snapshot and precommit plan in a sandbox library.

### Module 10 — Failure injection
Inject:
- wrong PDF SHA;
- unexpected annotation;
- geometry mismatch;
- sync race;
- create failure;
- delete failure.

Learner must predict the correct fail-closed response.

### Module 11 — Recovery
Outcome: restore exact baseline after simulated partial mutation.

### Module 12 — Idempotency
Outcome: certify `I=(N,0,0,0,0)`.

## Mastery rubric

| Competency | Beginner | Competent | Advanced |
|---|---|---|---|
| Zotero model | Knows annotations | Understands keys/parents | Can reconstruct exact native state |
| Evidence | Highlights text | Uses role rules | Separates focality, provenance, atomicity |
| Geometry | Visual | Coordinates | Audited exact geometry authority |
| Hashes | SHA awareness | Canonical JSON | Content-addressed authority chains |
| Failure diagnosis | Reads error | Classifies subsystem | Identifies failed invariant and safest next gate |
| Transactions | Writes annotations | Bounded mutation | Rollback + single-use + crash recovery |
| Auditing | Checks counts | Checks fingerprints | Independent two-path certification |
| Closure | Count equals target | Exact schema match | Idempotency + package-certified release |

## Oral questions for self-testing

1. Why is `673 annotations exist` weaker than idempotency `I=(673,0,0,0,0)`?
2. Why can a metadata-only update be invalid even when the comment is the only thing you intended to change?
3. Why must a single-use authorization be consumed after rollback?
4. Why can Reader geometry segmentation change without PDF source drift?
5. What is the difference between a scientific dual role and a visible duplicate?
6. Why is a runtime PASS not final package closure?
7. What must be captured in a rollback snapshot?
8. Why should create occur before delete?
9. Why must an independent auditor use a different traversal strategy?
10. When should the correct answer be ABSTAIN?
