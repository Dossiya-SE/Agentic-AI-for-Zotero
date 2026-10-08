# Agentic AI for Zotero — Quick Reference

## Never collapse these layers
`SOURCE → SCIENCE → GEOMETRY → SCHEMA → LIVE STATE → TRANSACTION → POSTWRITE`

## Never infer mutation authorization
Scientific approval ≠ schema approval ≠ mutation authorization.

## Core equations

Corpus:
`attempted = PASS + FAIL`

Targets:
`input = retain + redundant + superseded`

Transaction:
`final = current - delete + create`

Idempotency:
`I = (NOOP, CREATE, UPDATE, REPLACE, DELETE)`

Perfect:
`I = (N, 0, 0, 0, 0)`

## Failure response
- Before mutation: stop, diagnose, version repair.
- After mutation + rollback succeeds: stop; authorization consumed.
- Rollback incomplete: critical stop; recovery controller only.
- Runtime PASS: package audit still required.
- Final count correct: fingerprint/idempotency audit still required.

## Golden rule
**Never patch an expected hash to make a run pass.**

## Evidence-dense communication standard
- **Quality is not length:** prioritize correctness, relevance, traceability, and decision value.
- Lead with the answer; retain only the few strongest supported findings and the immediate next action.
- Preserve essential quantities, units, conditions, source anchors, provenance, and verification state.
- Distinguish **verified**, **inferred**, and **unresolved**; never turn an uncertainty into a claim.
- Omit repetition, speculation, unnecessary taxonomy, and decorative complexity.
- **Brevity never weakens scientific, safety, authorization, or audit gates.** Keep full records in the ledger rather than the response.
