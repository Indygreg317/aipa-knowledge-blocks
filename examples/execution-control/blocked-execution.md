# Blocked Execution Example

This example shows an AIPA Knowledge Block that was approved earlier but blocked at runtime because current conditions no longer satisfied its governance requirements.

Companion machine-readable example: [blocked-execution.json](blocked-execution.json)

---

## Scenario

A Knowledge Block defines a controlled operational action:

- **Action:** Deploy configuration update
- **Domain:** Operations
- **Environment:** Production
- **Authority:** DevOps Engineer
- **Trust level:** Verified
- **Verification status:** Verified at approval time
- **Runtime control:** Revalidation required
- **Audit requirement:** Audit log required

At approval time, all required conditions were valid.

---

## Knowledge Block Identity

Example identity fields:

```text
knowledge_block_id: AIPA-KB-DEPLOY-BLOCK-001
title: Blocked Configuration Deployment
domain: operations
category: deployment-control
owner: operations-team
status: active
```

These fields make the block discoverable, reviewable, and traceable.

---

## Trigger Conditions

The block becomes eligible when:

- a configuration update is requested
- the target environment is production
- a deployment request has already been approved
- an authority token is present
- audit logging is available

Invocation does not automatically authorize execution. It only makes the block eligible for runtime revalidation.

---

## Approval-Time State

At the time of approval:

- System state: Stable
- Risk posture: Low
- Policy: Deployments allowed
- Authority: Valid DevOps Engineer
- Evidence status: Fresh

The block was approved for controlled use under these conditions.

---

## Runtime Execution Attempt

At runtime, the deployment pipeline attempts to execute the Knowledge Block.

Current runtime conditions:

- System state: Production incident active
- Risk posture: High
- Policy: Deployments blocked during incident
- Authority: DevOps Engineer still valid
- Evidence status: Fresh

Authority remains valid, but authority alone is not enough. Policy, risk, and context also matter.

---

## Runtime Revalidation

Execution control performs runtime checks:

| Check | Result |
|---|---|
| Context comparison | FAILED |
| Policy comparison | FAILED |
| Input validation | PASSED |
| Risk posture check | FAILED |
| Evidence freshness check | PASSED |
| Authority validation | PASSED |

The current conditions no longer match the approved execution assumptions.

---

## Decision

```text
Decision: BLOCK
```

Reason:

- context drift detected
- policy mismatch detected
- runtime risk exceeded threshold

The system blocks execution even though the original block was approved and the DevOps authority remains valid.

---

## Fail-Safe Behavior

Configured fail behavior:

- block deployment
- escalate to incident response team
- record audit event

The safest action is to prevent the deployment during the active incident.

---

## Execution Outcome

The configuration update does not deploy.

Expected outcomes:

- configuration update not deployed
- incident response team escalated
- audit record created

---

## Audit Record

The audit record should capture:

- Knowledge Block ID
- version
- trigger source
- runtime timestamp
- authority checked
- revalidation checks performed
- failed checks
- decision result
- reason for block
- escalation path

Example summary:

```text
Knowledge Block ID: AIPA-KB-DEPLOY-BLOCK-001
Decision: BLOCK
Reviewer: system
Reason: context drift, policy mismatch, risk threshold exceeded
Audit: recorded
```

---

## Key Insight

The Knowledge Block was valid at approval time.

At runtime, production entered an active incident state and deployment policy changed.

Execution control detected the mismatch and blocked the action.

---

## Principle

If a Knowledge Block cannot be revalidated under current conditions, it must not execute.
