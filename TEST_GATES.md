# Test Gates for Agentic AI for Zotero

## T0 — Static Safety
- syntax passes;
- authority hashes embedded correctly;
- forbidden mutation APIs absent from read-only tools;
- corpus count exact;
- expected target count exact.

## T1 — Source Authority
- exact parent;
- exact attachment;
- title normalized equality;
- DOI normalized equality;
- PDF SHA exact;
- native page labels exact.

## T2 — Baseline
- exact current annotation keyset;
- exact count;
- exact annotation fingerprints;
- no unauthorized extras.

## T3 — Scientific
- every accepted record has reason;
- focality resolved;
- external scope resolved;
- atomicity resolved;
- ABSTAIN preserved;
- ontology non-coercive.

## T4 — Geometry
- page index exact;
- native page label exact;
- rectangles valid;
- exact text reanchor or audited fallback;
- region visual QA.

## T5 — Redundancy
- no duplicate visible signatures;
- dual roles preserved externally;
- conservation arithmetic.

## T6 — Schema
- one record per final target;
- unique target-state fingerprints;
- comments exact;
- colors exact;
- zero tags;
- target action can reach target fingerprint.

## T7 — Dry Run
- writer independently projects final set;
- auditor independently projects final set;
- writer set = auditor set = schema;
- no mutation.

## T8 — Premutation
- entire authority chain exact;
- current baseline fresh enough per contract;
- no unresolved failures;
- explicit mutation authorization still false.

## T9 — Prewrite
- fresh full corpus;
- all source hashes exact;
- all current keys exact;
- all current fingerprints exact;
- transaction invariant exact.

## T10 — Locked Prewrite
Repeat T9 after acquiring no-sync lock.

## T11 — Transaction
- all creates owned by precommit plan;
- updates only authorized keys;
- deletes only authorized old keys;
- count conservation;
- no foreign state;
- PDFs unchanged.

## T12 — Final Exact State
- exact keyset per paper;
- exact target fingerprint per schema record;
- exact final count;
- no extras;
- old deleted keys absent.

## T13 — Idempotency
\[
I=(NOOP,CREATE,UPDATE,REPLACE,DELETE)
\]
Require:
\[
I=(N,0,0,0,0)
\]

## T14 — Package Audit
- actual bytes;
- manifest;
- hashes;
- sizes;
- per-paper shards;
- report;
- authority lineage.

## T15 — Final Release
- immutable final release manifest;
- final package SHA;
- state marked mutation-closed unless a new governed change request is created.
