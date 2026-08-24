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
