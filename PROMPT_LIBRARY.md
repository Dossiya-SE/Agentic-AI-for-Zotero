# Prompt Library — Agentic AI for Zotero

## A. Start a new project

```text
Build an Agentic AI for Zotero workflow for this corpus.

Do not mutate anything yet.

First produce:
- source authority model;
- canonical corpus order;
- current-live inventory;
- scientific evidence contract;
- stage state machine;
- failure taxonomy;
- required human approval gates;
- exact artifact/hash strategy;
- minimum-Zotero-execution acquisition plan.

Separate source, science, geometry, schema, live state, transaction, and final certification.
```

## B. Diagnose a failed run

```text
Classify this failure using the Agentic AI for Zotero taxonomy.

Do not propose a patch until you identify:
- failed invariant;
- authoritative layer;
- whether mutation began;
- whether authority changed or only runtime representation changed;
- whether rollback is required;
- whether authorization is consumed;
- whether target fingerprints remain valid;
- whether human reapproval is required.

Then give the minimal versioned repair and regression test.
```

## C. Audit a target schema

```text
Independently audit every target state.

Check:
- scientific role;
- exact author wording;
- visible comment;
- role color;
- zero tags;
- page label;
- exact geometry;
- current native key mapping;
- current-state fingerprint;
- target-state fingerprint;
- transaction-action reachability.

A KEEP must already equal the target fingerprint.
A metadata-only update must have no geometry/page/type/text difference.
```

## D. Construct a transactional writer

```text
Construct a single-use, hash-bound Zotero transaction controller.

Before first mutation require:
1. full-corpus prewrite;
2. sync lock;
3. second full-corpus prewrite;
4. rollback snapshot;
5. precommit unique-key plan;
6. exact mutation-boundary recheck;
7. authorization consumption.

Use CREATE → UPDATE → DELETE → FINAL VALIDATION.
No PDF mutation.
No unbounded deletion.
No partial-paper execution.
Provide automatic rollback and a separate crash-recovery controller.
```

## E. Final audit

```text
Create an independently implemented read-only post-write auditor.

Pass 1: target-first exact verification.
Pass 2: live-first idempotency derivation.

Require:
- exact final keysets;
- exact PDF hashes;
- exact target fingerprints;
- no extras;
- deleted old keys absent;
- zero tags;
- pass1 fingerprint set = pass2 fingerprint set;
- idempotency NOOP=N, CREATE=UPDATE=REPLACE=DELETE=0.

Do not use mutation APIs.
```
