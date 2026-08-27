# Agentic AI for Zotero Skill Package

This package converts the complete Frozen-37 Zotero engineering process into a reusable skill for future Zotero automation projects.

## Files

- `SKILL.md` — governing skill and full reusable architecture.
- `ZOTERO_AGENTIC_WEAKNESS_CORRECTIVE_ACTION_CONTRACT.md` — **mandatory weakness-and-correction contract**. Defines W01–W24, paper-specific Core-7 weaknesses, exact corrective actions, fail-closed blockers, readiness states, and the required path to a canonical Gold Zotero target.
- `WEAKNESS_REGISTER.json` — machine-readable weakness register and Core-7 write-readiness controls.
- `ERROR_FAIL_WIN_TAXONOMY.json` — machine-readable failure/win taxonomy.
- `STATE_MACHINE.json` — governance state transitions.
- `TEST_GATES.md` — reusable validation gates.
- `TEACHING_PLAYBOOK.md` — learning curriculum and mastery rubric.
- `NUS_FROZEN37_CASEBOOK.md` — real incidents and lessons.
- `PROMPT_LIBRARY.md` — prompts for future Agentic Zotero tasks.
- `QUICK_REFERENCE.md` — compact field guide.
- `MANIFEST.json` — package inventory and provenance metadata.

## Mandatory governance rule

The production Zotero writer must **not** treat an additive evidence inventory such as V17 as the final mutation target.

Required architecture:

```text
Full paper
→ scientific adjudication
→ canonical evidence
→ Gold/ledger/context/conflict separation
→ native geometry proof
→ validated mutation plan
→ backup
→ paper-atomic Zotero mutation
→ readback
→ independent audit
→ second-run idempotency
```

The agent must fail closed on unresolved focality, role, provenance, units, author conflicts, duplicates, mixed-role geometry, missing `generated_by`, missing `consumed_by` for INPUT, missing native geometry, PDF-hash mismatch, or live Zotero state drift.

## Core-7 production status

The machine-readable authority is `WEAKNESS_REGISTER.json`. At the current governance stage, production mutation remains disabled until the seven papers reach `GOLD_FROZEN + GEOMETRY_FROZEN + QA_PASS`.

In particular:

- NUS-172 — canonicalization, semantic deduplication, decision-scope and Si-conflict control required.
- NUS-18 — geometry and duplicate/mixed-surface review required.
- NUS-15 — characterization pruning, decision subtypes, SDG-link status and provenance refinement required.
- NUS-187 — mixed-surface segmentation, provenance and Eq. (22) integrated-transformation control required.
- NUS-48 — author-conflict handling, Table 3 final-role resolution, RSM boundary and dual-optimum separation required.
- NUS-59 — full re-extraction required.
- NUS-191 — full re-extraction required; current sparse historical evidence is not production authority.

## Intended use

Use `SKILL.md` as the main system/playbook instruction, but apply the weakness contract and machine register as **mandatory governance extensions** before any annotation mutation. Use the casebook for diagnosing failures. Use the state machine and test gates to decide whether an operation is permitted.

The package intentionally teaches the agent to recognize both **wins** and **failures**, and now additionally requires explicit correction of known scientific-annotation weaknesses before live Zotero writes.
