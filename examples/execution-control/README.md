# Execution Control Examples

This directory demonstrates how AIPA Knowledge Blocks can be evaluated at runtime before action is allowed.

The examples show the difference between a Knowledge Block that remains valid at execution time and one that must be blocked because runtime conditions changed.

---

## Example Files

| File | Purpose |
|---|---|
| [allowed-execution.md](allowed-execution.md) | Narrative example of a block allowed after runtime revalidation |
| [blocked-execution.md](blocked-execution.md) | Narrative example of a block blocked after runtime revalidation fails |
| [allowed-execution.json](allowed-execution.json) | Machine-readable allowed execution example |
| [blocked-execution.json](blocked-execution.json) | Machine-readable blocked execution example |

---

## Core Pattern

Execution control separates approval from runtime authorization.

```text
Approved Knowledge Block → Runtime Revalidation → Allow / Block / Escalate → Audit
```

A Knowledge Block may be valid when approved but unsafe when executed.

Runtime checks may include:

- current system state
- policy consistency
- evidence freshness
- authority validity
- risk posture
- context drift
- required human review

---

## Allowed Execution

Allowed execution occurs when current runtime conditions remain compatible with the approved Knowledge Block.

Typical result:

```text
Decision: ALLOW
Reason: runtime checks passed
Audit: record execution decision and result
```

---

## Blocked Execution

Blocked execution occurs when current runtime conditions violate one or more governance controls.

Typical result:

```text
Decision: BLOCK
Reason: policy mismatch, risk threshold exceeded, context drift, missing authority, or stale evidence
Audit: record block decision and escalation path
```

---

## Important Distinction

Schema validation answers:

> Is the Knowledge Block structurally valid?

Execution control answers:

> Is the Knowledge Block allowed to execute right now?

Both are required in governed AI systems.

---

## Implementation Boundary

These examples are simplified for clarity. Real implementations should align with the formal schemas, governance lifecycle, trust levels, verification status, field definitions, and controlled vocabulary defined in the repository documentation.
