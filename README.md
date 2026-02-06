# Proof of Non-Existence (PNE)

Proof of Non-Existence (PNE) is a deterministic verification primitive that
produces evidence that a specified artifact, state, or execution **never
existed** within a declared scope.

PNE makes no assumptions about prior deletion.
It answers one question only: **did this ever exist within scope, yes or no?**

---

## What PNE Guarantees

- Explicit scope declaration
- Deterministic verification
- Verifiable outcome classification:
  - `VALID`
  - `INVALID`
  - `OUT_OF_SCOPE`
- Evidence artifacts suitable for audit and review

If proof cannot be established, PNE refuses.

---

## What PNE Does NOT Do

- No deletion or remediation
- No probabilistic claims
- No trust-based assertions
- No background monitoring
- No inference of intent

PNE verifies non-existence only.

---

## Failure Modes

- **INVALID** — Evidence shows the target existed
- **OUT_OF_SCOPE** — Scope is insufficient to evaluate the claim
- **REFUSED** — Inputs violate PNE invariants

---

## Scope Discipline

All claims are scope-bound.
Unscoped claims are rejected by design.

---

## Relationship to StealthEye

Proof of Non-Existence is a core StealthEye verification primitive.
Other tools may compose with PNE, but PNE depends on nothing else.

---

## Reference

Canonical specification, guarantees, and examples are defined in this repository.

https://stealtheyellc.itch.io/pne
