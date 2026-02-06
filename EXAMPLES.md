# Proof of Non-Existence (PNE) — Examples

This document provides concrete examples of Proof of Non-Existence (PNE)
evaluations. Examples are intentionally minimal and factual.

---

## Example 1: Artifact Never Created

**Claim**  
File `backup_2023.tar.gz` never existed on server `B`.

**Scope**
- System: server `B`
- Storage: `/var/backups/`
- Time: system lifetime up to `2025-02-01`
- Observation: filesystem snapshots and creation logs

**Evidence**
- Full directory snapshots
- File creation audit logs

**Result**
`VALID`

**Reason**
No evidence of the file exists within the declared scope.

---

## Example 2: Evidence of Prior Existence

**Claim**  
File `temp_keys.txt` never existed on the system.

**Scope**
- System: application host
- Storage: `/tmp/`
- Time: `2025-01-01T00:00Z` → `2025-01-31T23:59Z`
- Observation: filesystem audit logs

**Evidence**
- Audit log entry showing file creation on `2025-01-12T09:41Z`

**Result**
`INVALID`

**Reason**
Evidence demonstrates the file existed within the declared scope.

---

## Example 3: Insufficient Scope Definition

**Claim**  
Record `session_8841` never existed.

**Scope**
- System: application container only
- Storage: unspecified
- Time: unspecified
- Observation: runtime logs

**Evidence**
- Application logs

**Result**
`OUT_OF_SCOPE`

**Reason**
The scope does not cover sufficient boundaries to evaluate the claim.

---

## Example 4: Invariant Violation

**Claim**  
“No debug artifacts were ever created.”

**Scope**
- System: unspecified
- Storage: unspecified
- Time: unspecified
- Observation: operator assertion

**Evidence**
- Verbal confirmation

**Result**
`REFUSED`

**Reason**
The claim violates PNE invariants:
- No explicit scope
- No concrete target
- Trust-based assertion

---

## Summary

These examples demonstrate all PNE outcomes:
- `VALID`
- `INVALID`
- `OUT_OF_SCOPE`
- `REFUSED`

PNE does not optimize for success.
It optimizes for correctness.
