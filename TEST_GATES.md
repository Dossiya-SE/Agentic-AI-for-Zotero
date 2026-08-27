# Test Gates for Agentic AI for Zotero

These gates are mandatory. Any unresolved weakness in `WEAKNESS_REGISTER.json` blocks mutation.

## T0 — Static Safety
- syntax passes;
- authority hashes embedded correctly;
- forbidden mutation APIs absent from read-only tools;
- corpus count exact;
- expected target count exact;
- production writer rejects V17/additive inventories as final target authority;
- weakness register and contract are present and parseable.

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

## T3 — Scientific Adjudication
- every accepted record has reason;
- focality resolved;
- external scope resolved;
- atomicity resolved;
- role classified by focal function, not method name;
- `INPUT <= USED_IN_FOCAL_METHOD` enforced;
- engineering equations are not promoted to sustainability transformation without an explicit sustainability/economic/integrated output;
- DECISION scope/criteria/candidate set/selected alternative resolved;
- ABSTAIN preserved;
- ontology non-coercive.

## T4 — Canonicalization
- every candidate ends in exactly one of `GOLD_VISIBLE`, `LEDGER_ONLY`, `CONTEXT_ONLY`, `CONFLICT_RECORD`, `SUPERSEDED`, `DUPLICATE`, `REJECTED`;
- semantic duplicate count is zero in Gold layer;
- stronger body evidence supersedes weaker abstract/conclusion repetition unless later evidence adds unique scientific content;
- scientific ledger, Gold visible layer, and context/conflict layer are separated;
- no record survives solely because it existed in an older inventory.

## T5 — Provenance / Dependency / Conflict
- every approved INPUT/OUTCOME provenance is `FG`, `FA`, `LD`, or `HY`;
- every Orange INPUT has at least one explicit `consumed_by` edge;
- every quantified sustainability outcome has `generated_by` or explicit `NOT_REPORTED`;
- author conflicts are first-class records;
- no author wording/unit/value/label is silently repaired;
- known conflict groups such as NUS-172 Si and NUS-48 author inconsistencies are preserved.

## T6 — Geometry
- page index exact;
- native page label exact;
- rectangles valid;
- exact text reanchor or audited fallback;
- native equation regions used instead of OCR reconstruction;
- mixed-role tables/figures are subregion-segmented or replaced by stronger atomic textual evidence;
- region visual QA;
- no `geometry_status=PENDING` target is write-ready.

## T7 — Redundancy / Scientific Fact Signature
- no duplicate visible signatures;
- semantic identity checks object + metric + alternative + time + condition + result + role;
- dual functions preserved externally without duplicate Zotero annotations;
- practical and numerical optima remain separate when scientifically distinct;
- conservation arithmetic.

## T8 — Paper Readiness
For every paper targeted by the writer:
- `GOLD_FROZEN`;
- `GEOMETRY_FROZEN`;
- `QA_PASS`;
- no unresolved blocker from `WEAKNESS_REGISTER.json`;
- NUS-59 cannot pass until full re-extraction is complete;
- NUS-191 cannot pass until full re-extraction is complete.

## T9 — Schema
- permanent EvidenceID independent of Zotero key;
- one record per final target;
- unique target-state fingerprints;
- comments exact;
- colors exact;
- zero tags;
- decision metadata complete for Yellow records;
- target action can reach target fingerprint.

## T10 — Negative Regression
Known MUST-NOT cases pass, including at minimum:
- characterization without downstream consumption MUST NOT become INPUT;
- NUS-48 Table 1 oxide composition MUST NOT become INPUT;
- NUS-48 Table 2 aggregate properties MUST NOT become INPUT;
- NUS-48 Significance claims MUST NOT become focal sustainability outcomes;
- NUS-48 RSM MUST NOT become sustainability optimization when it models only CS/STS/FS/ME;
- NUS-18 EnergyPlus/BES MUST NOT become sustainability method;
- generic/non-focal Taguchi examples MUST NOT become focal method evidence;
- mixed-role surfaces MUST NOT receive one undifferentiated role.

## T11 — Dry Run
- writer independently projects final set;
- auditor independently projects final set;
- writer set = auditor set = canonical schema;
- planned operations are only KEEP/UPDATE/CREATE/DELETE/REPLACE/SPLIT/MERGE authorized by target reconciliation;
- no mutation.

## T12 — Premutation
- entire authority chain exact;
- current baseline fresh enough per contract;
- no unresolved failures;
- explicit mutation authorization still false.

## T13 — Prewrite
- fresh full corpus;
- all source hashes exact;
- all current keys exact;
- all current fingerprints exact;
- live-state fingerprint equals planning fingerprint;
- transaction invariant exact;
- complete rollback snapshot read back successfully.

## T14 — Locked Prewrite
Repeat T13 after acquiring no-sync lock. Abort on any state drift.

## T15 — Transaction
- paper-atomic transaction;
- all creates owned by precommit plan and immediately registered for rollback;
- updates only authorized keys;
- deletes only authorized old keys;
- count conservation;
- no foreign state;
- PDFs unchanged.

## T16 — Rollback Certification
If transaction fails:
- rollback executes;
- exact pre-write keyset restored;
- exact pre-write fingerprints restored;
- newly created keys removed;
- failed single-use authorization consumed.

## T17 — Final Exact State
- exact keyset per paper;
- exact EvidenceID↔Zotero-key correspondence;
- exact target fingerprint per schema record;
- exact final count;
- no extras;
- old deleted keys absent;
- no missing Gold-visible record.

## T18 — Independent Audit
- auditor is read-only;
- auditor does not trust writer report;
- independently recomputes text/comment/color/type/page/position/geometry/tag fingerprints;
- missing = 0;
- extra = 0;
- wrong role/color/comment/text/page/geometry = 0;
- unauthorized mutation = 0.

## T19 — Idempotency

\[
I=(NOOP,CREATE,UPDATE,REPLACE,DELETE)
\]

Require:

\[
I=(N,0,0,0,0)
\]

Any nonzero mutation on the second run is a failure.

## T20 — Package Audit
- actual bytes;
- manifest;
- hashes;
- sizes;
- per-paper shards;
- report;
- authority lineage;
- weakness-remediation report;
- negative-regression report.

## T21 — Final Release
- immutable final release manifest;
- final package SHA;
- state marked mutation-closed unless a new governed change request is created.
