# Proof of Non-Existence (PNE) — Formal Specification

This document defines the formal behavior, invariants, and outputs of the
Proof of Non-Existence (PNE) verification primitive.

PNE exists to establish a single claim:

> A specified artifact, state, or execution **never existed** within a
> declared scope.

PNE makes no assumptions about deletion or prior system state.

---

## Definitions

**Artifact**  
Any file, record, state snapshot, execution trace, or derived object that
could be observed within the declared scope.

**Scope**  
An explicit boundary within which the claim applies. A scope must define:
- System boundary
- Time boundary
- Storage boundary
- Observation boundary

Unscoped claims are invalid.

**Evidence**  
Observable facts used to support or refute the claim. Evidence must be:
- Deterministic
- Reproducible
- Scope-bound

---

## Inputs

PNE requires the following inputs:

1. **Target Identifier**
   - The artifact or state claimed to have never existed
   - Must be uniquely specified

2. **Scope Declaration**
   - Explicit system, time, storage, and observation boundaries
   - No implicit assumptions allowed

3. **Evidence Set**
   - Logs, snapshots, receipts, or attestations
   - Must originate within the declared scope

---

## Output Classification

PNE produces exactly one of the following results:

### VALID
Evidence sufficiently demonstrates that the target **never existed** within
the declared scope.

### INVALID
Evidence demonstrates that the target **did exist** within the declared scope.

### OUT_OF_SCOPE
Evidence is insufficient to evaluate the claim within the declared scope.

### REFUSED
Inputs violate PNE invariants or attempt to bypass scope discipline.

---

## Invariants

The following invariants are mandatory:

- No implicit scope
- No probabilistic reasoning
- No time-relative assumptions
- No trust-based assertions
- No silent success
- No partial claims

Violation of any invariant results in `REFUSED`.

---

## Determinism

Given identical:
- Target
- Scope
- Evidence

PNE will always produce the same output classification.

There is no learning, adaptation, or internal state.

---

## Composition

PNE may be composed with other primitives provided:
- Scope boundaries remain explicit
- Output classifications are not softened or reinterpreted
- Failure states propagate without suppression

PNE is atomic and indivisible.

---

## Non-Goals

PNE does not:
- Perform deletion
- Monitor systems continuously
- Infer intent or motive
- Guarantee compliance
- Prevent future creation

PNE verifies non-existence only.

---

## Summary

Proof of Non-Existence is a narrow, deterministic verification primitive.
Its authority comes from refusal, not flexibility.
