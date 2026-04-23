# Blocked Execution Example

## Scenario

A Knowledge Block defines an approved operational action:

- Action: Deploy configuration update
- Environment: Production
- Risk posture: Low (at approval time)
- Authority: DevOps Engineer
- Trust level: Verified

At the time of approval, all conditions were valid.

---

## Execution Attempt

At runtime, the system attempts to execute the Knowledge Block.

### Current conditions:

- System state: Production under active incident
- Risk posture: High
- Policy update: No deployments allowed during incidents
- Authority: Valid

---

## Revalidation

Execution control performs runtime checks:

- Context comparison: FAILED (system state changed)
- Policy comparison: FAILED (deployment restriction active)
- Risk posture: EXCEEDS threshold

---

## Decision

Execution is **BLOCKED**

Reason:
- Policy mismatch
- Elevated risk
- Context drift from approval state

---

## Fail Behavior

Configured fail behavior:

- block execution
- escalate to incident response team
- log audit event

---

## Audit Record

- Knowledge Block ID: KB-DEPLOY-001
- Execution timestamp: 2026-XX-XX
- Decision: BLOCKED
- Reason:
  - Policy mismatch
  - Risk threshold exceeded
- Reviewer: System

---

## Outcome

No deployment occurred.

System integrity preserved.

---

## Key Insight

The Knowledge Block was valid at approval time.

Execution control ensured it was **still valid at runtime**.

Because it was not, execution was prevented.

---

## Principle

If a decision cannot be revalidated under current conditions, it must not execute.
