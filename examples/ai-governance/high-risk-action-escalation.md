# High-Risk AI Action Escalation Example

This example shows how an AIPA Knowledge Block can govern an AI-assisted workflow when a model or agent proposes a high-impact action that requires human review before execution.

Companion machine-readable example: [high-risk-action-escalation.json](high-risk-action-escalation.json)

---

## Scenario

An AI-assisted workflow proposes an action that could materially affect a user, customer, system, account, record, or operational process.

The Knowledge Block defines when that proposed action must be escalated for human review instead of being executed automatically.

Example action:

- **Action:** Execute high-impact AI-assisted recommendation
- **Domain:** AI governance
- **Environment:** Production
- **Authority:** AI governance reviewer
- **Trust level:** Reviewed
- **Verification status:** Verified
- **Runtime control:** Human review required for high-impact actions
- **Audit requirement:** Audit log required

---

## Knowledge Block Identity

Example identity fields:

```text
knowledge_block_id: AIPA-KB-AIGOV-ESCALATE-001
title: High-Risk AI Action Escalation
domain: ai-governance
category: human-oversight
owner: ai-governance-team
status: active
```

These fields make the block discoverable, reviewable, and traceable.

---

## Trigger Conditions

The block becomes eligible when:

- an AI system proposes an action
- the action is classified as high impact
- the action affects a user, customer, system, account, or operational record
- the workflow is running in a production or restricted environment

Invocation does not authorize execution. It only triggers evaluation of whether human review is required.

---

## Approval-Time State

At approval time, the governance rule is valid under these assumptions:

- High-impact AI actions require human review
- External tool execution is not allowed without authorization
- Audit logging is available
- Escalation path exists
- AI governance reviewer role is defined

The block is approved for controlled use, but runtime conditions still matter.

---

## Runtime Execution Attempt

At runtime, the AI-assisted system proposes an action.

Current runtime conditions:

- Proposed action: high-impact recommendation execution
- User impact: material
- System state: production
- Model confidence: medium
- Policy: human review required for high-impact AI actions
- Authority: no reviewer approval yet
- Audit logging: available

---

## Runtime Revalidation

Execution control performs runtime checks:

| Check | Result |
|---|---|
| Context comparison | PASSED |
| Policy comparison | PASSED |
| Input validation | PASSED |
| Risk posture check | FAILED FOR AUTO-EXECUTION |
| Evidence freshness check | PASSED |
| Authority validation | FAILED FOR AUTO-EXECUTION |
| Human review requirement | REQUIRED |

The action is not allowed to execute automatically because the risk and authority conditions require human review.

---

## Decision

```text
Decision: ESCALATE
```

Reason:

- proposed action is high impact
- production environment increases risk
- model confidence is not sufficient for autonomous execution
- required human authority has not approved the action
- policy requires human review

---

## Fail-Safe Behavior

Configured fail behavior:

- prevent automatic execution
- escalate to AI governance reviewer
- preserve proposed action for review
- record audit event

The system does not discard the recommendation. It prevents automatic action and routes the decision to a responsible reviewer.

---

## Execution Outcome

The proposed action does not execute automatically.

Expected outcomes:

- automatic action blocked
- human review task created
- proposed action preserved for reviewer context
- audit record created

---

## Audit Record

The audit record should capture:

- Knowledge Block ID
- version
- trigger source
- proposed action
- risk classification
- model confidence or uncertainty signal
- policy basis
- authority requirement
- decision result
- escalation target
- timestamp
- reviewer or pending reviewer role

Example summary:

```text
Knowledge Block ID: AIPA-KB-AIGOV-ESCALATE-001
Decision: ESCALATE
Reviewer: ai-governance-reviewer required
Reason: high-impact action requires human review before execution
Audit: recorded
```

---

## Key Insight

The AI system may produce a plausible recommendation, but plausibility is not execution authority.

For high-impact actions, the governance boundary requires human review before action.

---

## Principle

AI-generated recommendations should not become high-impact actions unless they remain governed, authorized, reviewable, and auditable at runtime.
