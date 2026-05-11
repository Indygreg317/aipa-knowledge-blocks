# Controlled Vocabulary

The controlled vocabulary defines standardized terms used across AIPA Knowledge Blocks.

It ensures that authors, reviewers, validators, runtime engineers, auditors, and governance teams use consistent language when describing structured knowledge, invocation, verification, execution control, and audit behavior.

This document is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

Controlled terminology reduces ambiguity.

It helps ensure that:

- terms are used consistently across documentation and schemas
- Knowledge Blocks are interpreted correctly
- runtime behavior is predictable
- governance decisions are explainable
- audit records can be reviewed after execution
- trust, verification, and execution authorization are not confused

In governed AI systems, vague terms can create unsafe behavior. A controlled vocabulary gives builders and reviewers a shared operational language.

---

## Naming Standard

Preferred public name:

```text
AIPA Knowledge Blocks
```

Full organization name:

```text
Artificial Intelligence Partnership Association
```

Public website:

```text
https://aipa.network
```

Avoid using older or ambiguous names as the primary label. Older terms may appear in legacy schema IDs or historical references, but current documentation should prefer **AIPA Knowledge Blocks**.

---

## Core Terms

### Knowledge Block

A structured, machine-readable unit of operational knowledge.

A Knowledge Block may contain identity metadata, trigger conditions, decision logic, evidence, runtime controls, governance status, trust level, verification status, and audit requirements.

Preferred usage:

> A Knowledge Block defines structured operational knowledge that can be governed, invoked, revalidated, and audited.

Avoid treating a Knowledge Block as merely a prompt, note, text snippet, or static document.

---

### Structured Knowledge

Knowledge represented with defined fields, schemas, relationships, evidence, and governance metadata.

Structured knowledge is different from loose context because it can be validated, searched, versioned, reviewed, and audited.

---

### Operational Knowledge

Knowledge intended to guide or influence real decisions, workflows, policies, reviews, or system behavior.

Operational knowledge requires stronger governance than general informational content because it may affect action.

---

### Decision Unit

A Knowledge Block treated as a reviewable unit of decision logic, policy, evidence, or operational guidance.

The term emphasizes that the block can influence decisions, but does not automatically authorize execution.

---

### Index Layer

The layer that defines identity, metadata, ownership, classification, versioning, lifecycle status, and discovery information.

The Index Layer answers:

> What is this block, who owns it, and how should it be found?

---

### Trigger Layer

The layer that defines when a Knowledge Block becomes eligible for evaluation or invocation.

The Trigger Layer answers:

> Under what conditions should this block become active or relevant?

---

### Runtime Layer

The layer that defines execution control, revalidation, authority, risk posture, state, context, and fail-safe behavior.

The Runtime Layer answers:

> Even if this block is relevant, is it still allowed to execute right now?

---

### Full Layer

The complete integrated representation of a Knowledge Block, combining index, trigger, runtime, logic, evidence, outcomes, and governance fields.

---

## Governance Terms

### Governance

The process of controlling how Knowledge Blocks are authored, reviewed, approved, invoked, revalidated, updated, revoked, archived, and audited.

Governance ensures that structured knowledge remains accountable throughout its lifecycle.

---

### Approval

A governance decision that marks a Knowledge Block as eligible for controlled use.

Approval does not mean unconditional execution authorization.

Preferred distinction:

```text
Approval = eligible for controlled use
Execution authorization = allowed to act under current runtime conditions
```

---

### Authority

The person, role, process, system, or governance body permitted to approve, review, invoke, or authorize execution of a Knowledge Block.

Authority should be explicit and auditable.

---

### Human Oversight

Visible human responsibility within the lifecycle of a Knowledge Block.

Human oversight may appear through authorship, review, approval, escalation, override, audit review, revocation, or policy ownership.

Human oversight does not require humans to manually perform every step. It means responsibility and escalation paths remain visible.

---

### Trust Level

A maturity or confidence classification based on review, testing, and operational history.

Trust level is historical confidence. It does not guarantee current validity or execution approval.

Preferred distinction:

```text
Trust = confidence based on history
Verification = current validity
Execution control = runtime authorization
```

---

### Verification Status

The current validity state of a Knowledge Block based on schema checks, evidence, policy alignment, review requirements, and governance rules.

Verification status determines whether a block is eligible for runtime consideration.

---

### Revocation

The explicit withdrawal of a Knowledge Block from active use by an authorized party or governance process.

A revoked block should not be invoked for execution and should remain available only for audit, forensic, or historical review.

---

### Supersession

Replacement of one Knowledge Block version with a newer or preferred version.

A superseded block may remain traceable but should not be selected for new active use unless explicitly allowed.

---

## Runtime Terms

### Execution Control

The mechanism that determines whether a Knowledge Block is allowed to execute under current runtime conditions.

Execution control may include:

- revalidation
- risk gating
- authority enforcement
- evidence freshness checks
- policy consistency checks
- state comparison
- fail-safe behavior
- audit logging

---

### Execution Authorization

A runtime decision that permits a block or action to proceed under current conditions.

Execution authorization is stronger than approval. Approval makes a block eligible. Execution authorization allows action now.

---

### Revalidation

The process of checking whether a Knowledge Block remains valid under current runtime conditions.

Revalidation may compare decision-time and execution-time conditions, including context, policy, inputs, evidence, authority, risk posture, and system state.

---

### Runtime

The moment or environment in which a Knowledge Block is evaluated for use or action.

Runtime may include the active workflow, system state, user intent, policy context, risk posture, and available authority.

---

### Context

The relevant environmental, system, user, input, workflow, policy, or operational conditions used to evaluate a Knowledge Block.

Context can change between approval and execution.

---

### State

The current condition of the system, workflow, environment, or execution process.

State may include lifecycle state, machine state, deployment state, incident state, or policy state.

---

### Delta

The difference between decision-time conditions and execution-time conditions.

Delta is used to detect drift.

---

### Drift

A meaningful change in context, state, policy, evidence, authority, or risk between the time a block was approved and the time it is considered for execution.

Drift may require block, escalation, fallback, or renewed review.

---

### Risk Posture

The current risk environment for execution.

Risk posture may include impact, likelihood, uncertainty, system state, exposure window, and maximum allowed risk score.

---

### Evidence Freshness

The degree to which supporting evidence remains current enough to justify use.

Evidence that exceeds its freshness window may cause a block to expire or require revalidation.

---

### Policy Consistency

Alignment between the policy basis used when a block was approved and the current policy state at runtime.

Policy mismatch may block or escalate execution.

---

### Fail-Safe Behavior

The configured behavior used when runtime checks fail, required data is missing, authority is invalid, risk is too high, or evidence is stale.

Common fail-safe behaviors include block, defer, degrade, fallback, escalate, abort, and audit.

---

## Standard Decision and Outcome Values

Use consistent decision values where possible.

| Value | Meaning |
|---|---|
| `ALLOW` | Execution or use may proceed under current conditions |
| `BLOCK` | Execution or use is prevented |
| `DEFER` | Execution is postponed until required conditions are satisfied |
| `DEGRADE` | A reduced-scope or safer form of execution is allowed |
| `FALLBACK` | A safer alternate action is used |
| `ESCALATE` | Human or higher-authority review is required |
| `ABORT` | Execution is stopped entirely |
| `AUDIT` | Recordkeeping is required; may be paired with another decision |
| `WARN` | Warning is logged; continuation depends on policy and risk |

Implementation note: schemas may use lowercase enum values while documentation may use uppercase values for readability. Implementations should normalize values consistently.

---

## Status Terms

### Draft

Created but not yet reviewed or approved.

---

### Reviewed

Evaluated by qualified reviewers, but not necessarily fully verified or production-proven.

---

### Verified

Currently satisfies defined validation, evidence, policy, and governance requirements.

---

### Production-Proven

Demonstrated reliable behavior in real operational environments over time.

---

### Pending

Awaiting review, validation, evidence check, approval, or other required governance action.

---

### Expired

Previously valid but no longer current due to evidence age, review window, policy change, or assumption drift.

---

### Invalid

Fails validation, policy, evidence, schema, safety, or governance requirements.

---

### Deprecated

No longer recommended for active use, usually because a better or newer version exists.

---

### Superseded

Replaced by a newer or preferred version.

---

### Revoked

Explicitly withdrawn from active use by an authorized party or governance process.

---

### Archived

Retained for historical, audit, or reference purposes, but not intended for active invocation.

---

## Avoided Ambiguity

The following distinctions should remain clear:

| Do Not Confuse | Difference |
|---|---|
| Approval vs Execution Authorization | Approval makes a block eligible; execution authorization permits action under current runtime conditions |
| Trust vs Verification | Trust is historical confidence; verification is current validity |
| Retrieval vs Invocation | Retrieval finds a block; invocation makes it eligible for evaluation |
| Invocation vs Execution | Invocation considers a block; execution acts on it |
| Schema Validity vs Runtime Validity | Schema validity confirms structure; runtime validity confirms current authorization |
| Deprecated vs Revoked | Deprecated means no longer recommended; revoked means explicitly withdrawn |
| Evidence vs Audit | Evidence supports a decision; audit records what happened |
| Context vs State | Context is surrounding conditions; state is current system/workflow condition |

---

## Preferred Language

Use:

- “governed Knowledge Block” instead of “prompt snippet”
- “runtime revalidation” instead of “double check”
- “execution authorization” instead of “permission” when discussing runtime action
- “evidence freshness” instead of “recent enough”
- “authority requirement” instead of “who says yes”
- “fail-safe behavior” instead of “error handling” when discussing control outcomes
- “audit record” instead of “log” when governance traceability matters

---

## Key Principle

A shared vocabulary is required for consistent governance and reliable execution control.

The central language rule is:

> Do not collapse knowledge, trust, verification, approval, invocation, and execution into the same concept.

Each term represents a different governance boundary.

---

## Outcome

The controlled vocabulary ensures that all components of the framework:

- use the same language
- interpret decisions consistently
- distinguish confidence from authority
- distinguish validity from execution permission
- behave predictably at runtime
- produce clearer audit and compliance records
