# Allowed Execution Example

This example shows an AIPA Knowledge Block that is approved, invoked, revalidated at runtime, and allowed to execute because current conditions still satisfy its governance requirements.

Companion machine-readable example: [allowed-execution.json](allowed-execution.json)

---

## Scenario

A Knowledge Block defines a controlled operational action:

- **Action:** Deploy configuration update
- **Domain:** Operations
- **Environment:** Production
- **Authority:** DevOps Engineer
- **Trust level:** Verified
- **Verification status:** Verified
- **Runtime control:** Revalidation required
- **Audit requirement:** Audit log required

At approval time, all required conditions were valid.

---

## Knowledge Block Identity

Example identity fields:

```text
knowledge_block_id: AIPA-KB-DEPLOY-ALLOW-001
title: Allowed Configuration Deployment
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

The block is approved for controlled use, but approval is not the final governance step.

---

## Runtime Execution Attempt

At runtime, the deployment pipeline attempts to execute the Knowledge Block.

Current runtime conditions:

- System state: Stable
- Risk posture: Low
- Policy: No deployment restrictions active
- Authority: Valid DevOps Engineer
- Evidence status: Fresh

---

## Runtime Revalidation

Execution control performs runtime checks:

| Check | Result |
|---|---|
| Context comparison | PASSED |
| Policy comparison | PASSED |
| Input validation | PASSED |
| Risk posture check | PASSED |
| Evidence freshness check | PASSED |
| Authority validation | PASSED |

The current conditions remain compatible with the approved Knowledge Block.

---

## Decision

```text
Decision: ALLOW
```

Reason:

- context remained valid
- policy remained consistent
- risk stayed within threshold
- authority remained valid
- evidence remained fresh

---

## Execution Outcome

The configuration update is allowed to proceed.

Expected outcomes:

- configuration update deployed
- system state updated
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
- decision result
- reason for decision
- final outcome

Example summary:

```text
Knowledge Block ID: AIPA-KB-DEPLOY-ALLOW-001
Decision: ALLOW
Reviewer: system
Reason: runtime revalidation passed
Audit: recorded
```

---

## Key Insight

The Knowledge Block was valid at approval time.

Execution control confirmed it remained valid at runtime.

Because current conditions still satisfied the governance requirements, execution was allowed.

---

## Principle

A Knowledge Block should execute only when current trust, verification, authority, evidence, policy, risk, and context conditions permit execution.
