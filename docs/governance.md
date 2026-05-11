# Governance

Governance defines how AIPA Knowledge Blocks are authored, reviewed, approved, invoked, revalidated, controlled, updated, revoked, and audited over time.

This document is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

The purpose of governance is to ensure that Knowledge Blocks do not become unreviewed, stale, or unauthorized instructions inside AI-assisted systems.

Governance ensures that operational knowledge:

- is reviewed before use
- has visible ownership
- remains aligned with policy
- carries trust and verification status
- can be updated when conditions change
- can be revoked when no longer valid
- is revalidated at runtime before execution
- leaves an auditable record of use

A Knowledge Block should not be treated as executable authority simply because it exists, was retrieved, or was previously approved.

---

## Core Governance Principle

Approval is not the final step.

A block can be approved for use and still fail runtime validation later.

Execution must still be checked against current conditions, including:

- current policy
- current authority
- current evidence
- current system state
- current risk posture
- current review or escalation requirements

The governance model therefore separates **approval** from **execution authorization**.

---

## Governance Lifecycle

A typical Knowledge Block lifecycle looks like this:

```text
Draft → Review → Approved → Indexed → Invoked → Revalidated → Allowed / Blocked / Escalated → Audited → Updated / Revoked / Archived
```

Each lifecycle phase has a distinct purpose.

---

## 1. Draft

A Knowledge Block begins as a draft.

At this stage, the author defines:

- the block purpose
- domain and category
- decision logic
- supporting evidence
- intended trigger conditions
- runtime controls
- expected outcomes
- owner or responsible party

Draft blocks should not be used for production execution unless explicitly marked as safe for sandbox or experimental use.

---

## 2. Review

Review determines whether the block is understandable, complete, evidence-supported, and aligned with policy.

Reviewers may check:

- factual correctness
- domain fit
- evidence quality
- policy alignment
- risk implications
- required authority
- failure behavior
- audit requirements
- human oversight requirements

Review can be performed by domain experts, governance reviewers, compliance reviewers, security reviewers, or operational owners depending on the block type.

---

## 3. Approval

Approval marks a Knowledge Block as eligible for controlled use.

Approval should record:

- approver identity or role
- approval timestamp
- policy basis
- schema version
- trust level
- verification status
- allowed use context
- required runtime controls

Approval does not mean unconditional execution. It means the block may be considered for invocation subject to trigger conditions and runtime validation.

---

## 4. Indexing

After approval, the block may be indexed for discovery.

The Index Layer supports:

- search
- classification
- retrieval
- routing
- version selection
- ownership lookup
- lifecycle status filtering

Indexing should preserve enough metadata to prevent outdated, deprecated, archived, or unauthorized blocks from being selected accidentally.

---

## 5. Invocation

Invocation occurs when a trigger condition, workflow state, system event, or user intent causes the block to be considered for use.

Invocation should be controlled by the Trigger Layer, not by accidental prompt exposure.

A block should become eligible because declared conditions apply, such as:

- a specific workflow state is reached
- a policy condition is met
- a system event occurs
- a manual reviewer selects the block
- a scheduled control check begins
- a relevant operational threshold is crossed

Invocation makes a block eligible for runtime validation. It does not automatically authorize execution.

---

## 6. Runtime Revalidation

Runtime revalidation checks whether the block remains valid under current conditions.

Revalidation may compare:

- decision-time context vs current context
- decision-time policy vs current policy
- expected inputs vs current inputs
- original evidence freshness vs current evidence age
- approved authority vs current authority
- expected risk posture vs current risk posture

If revalidation fails, the system should follow the configured fail-safe behavior.

Common outcomes include:

- **allow** — execution may proceed
- **block** — execution is prevented
- **defer** — execution waits for more information or a safer time
- **degrade** — a reduced-scope action is allowed
- **escalate** — human review is required
- **abort** — execution is stopped entirely
- **audit** — action may proceed with required recordkeeping, depending on risk and policy

---

## 7. Audit

Audit records preserve the trace of governance and execution decisions.

Audit records should answer:

- Which Knowledge Block was used?
- Which version was used?
- Why was it invoked?
- What runtime checks were performed?
- What authority was required?
- What evidence was used?
- What risk posture was observed?
- Was execution allowed, blocked, degraded, deferred, escalated, or aborted?
- Who reviewed or approved the block?
- Were there overrides or exceptions?

Auditability is central to AIPA Knowledge Blocks because it makes governance reviewable after the fact.

---

## 8. Update, Revocation, and Archival

Knowledge Blocks must be maintainable over time.

A block may need to be updated when:

- policy changes
- evidence expires
- system behavior changes
- risk posture changes
- ownership changes
- downstream use cases evolve
- audit findings identify problems
- a better version replaces the current one

A block should be revoked when it is no longer safe, valid, authorized, or aligned with policy.

A block should be archived when it is retained for historical or audit purposes but should no longer be invoked for active use.

Revoked or archived blocks should remain traceable but should not be selected for active execution.

---

## Control Points

Knowledge Block governance relies on several control points:

| Control Point | Purpose |
|---|---|
| Ownership | Defines who is responsible for the block |
| Trust Level | Indicates maturity and confidence |
| Verification Status | Indicates review and evidence state |
| Trigger Conditions | Controls when the block becomes eligible |
| Authority Requirements | Defines who or what may approve execution |
| Runtime Risk Gating | Prevents unsafe execution under changed conditions |
| Evidence Freshness | Prevents stale support from being treated as current |
| Policy Consistency | Blocks or escalates when governing policy changes |
| Fail-Safe Behavior | Defines what happens when checks fail |
| Audit Logging | Preserves accountability and traceability |

---

## Human Oversight

Human oversight should remain visible throughout the governance lifecycle.

A Knowledge Block may support automation, but authority should not disappear behind the model or workflow.

Human oversight may appear as:

- author identity
- reviewer role
- approval authority
- escalation requirement
- override review
- audit investigation
- revocation decision
- policy owner responsibility

The goal is not to prevent automation. The goal is to ensure that automation remains accountable, reviewable, and bounded by declared governance controls.

---

## Relationship to Trust and Verification

Governance works with two related concepts:

- **Trust level** — the confidence or maturity classification of the block
- **Verification status** — the current state of review, evidence, and compliance validation

A high-trust block may still require runtime revalidation.

A verified block may still become invalid if evidence expires, policy changes, or authority is revoked.

Trust and verification improve confidence, but they do not eliminate runtime governance.

---

## Outcome

Governance ensures that Knowledge Blocks are not only correct when created, but controlled throughout their lifecycle.

The intended result is a safer operational pattern:

> Structured knowledge may inform action, but only governed, current, authorized, and auditable knowledge should be allowed to execute.
