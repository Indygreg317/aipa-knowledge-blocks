# Verification Status

Verification status tracks whether an AIPA Knowledge Block currently satisfies defined validation, evidence, policy, and governance requirements.

This document is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

Verification status helps determine whether a Knowledge Block is eligible to be considered for use.

It ensures that a block:

- has been reviewed against defined requirements
- has valid and current evidence
- remains aligned with applicable policy
- satisfies required schema and governance checks
- has not expired, failed validation, or been invalidated
- can be safely considered by runtime execution control

Verification is about current validity.

It is not the same as trust, production history, or execution authorization.

---

## Core Principle

Verification answers:

> Is this Knowledge Block currently valid under the rules used to evaluate it?

Execution control answers:

> Is this Knowledge Block allowed to execute right now under current runtime conditions?

A verified block may still be blocked at runtime if authority, risk, policy, evidence, or context conditions fail.

---

## Status Types

| Status | Meaning | Typical Runtime Treatment |
|---|---|---|
| Pending | Awaiting review, evidence check, or validation | Do not execute outside controlled review or sandbox |
| Verified | Meets defined validation requirements | Eligible for runtime revalidation and controlled execution |
| Expired | Evidence, assumptions, policy basis, or review window is outdated | Block, defer, or require re-verification |
| Invalid | Fails validation, policy, evidence, schema, or governance requirements | Block execution and remove from active use |
| Superseded | Replaced by a newer valid version | Route to replacement block; preserve for audit |
| Revoked | Explicitly withdrawn by an authorized party | Block execution and preserve for audit/forensics |

---

## Pending

A Pending Knowledge Block has not yet completed validation.

Pending may mean:

- evidence has not been reviewed
- domain review is incomplete
- schema validation is incomplete
- policy alignment has not been confirmed
- required approvers have not signed off
- runtime controls are not fully specified

Recommended handling:

- do not permit production execution
- allow review workflows
- allow sandbox evaluation only when clearly marked
- require completion of missing validation steps

---

## Verified

A Verified Knowledge Block currently satisfies defined validation requirements.

Verification may include:

- schema validation
- evidence review
- policy alignment
- domain expert review
- required authority confirmation
- runtime control completeness
- expected outcome testing
- audit metadata completeness

Recommended handling:

- allow eligibility for runtime revalidation
- require runtime checks before action
- record schema version and verification timestamp
- monitor evidence freshness and policy changes

Verified means eligible for controlled use. It does not mean automatically executable.

---

## Expired

An Expired Knowledge Block was previously valid but has exceeded a defined freshness, review, evidence, or policy window.

Expiration may be caused by:

- evidence aging beyond its allowed freshness window
- review period ending
- policy basis changing
- regulation changing
- domain assumptions becoming stale
- runtime environment changing
- required periodic verification not occurring

Recommended handling:

- block production execution by default
- require re-verification
- preserve historical audit records
- allow read-only reference when appropriate

Expired does not always mean wrong. It means the block should not be treated as currently valid without renewed review.

---

## Invalid

An Invalid Knowledge Block fails one or more validation requirements.

Invalidation may result from:

- failed schema validation
- missing required fields
- incorrect evidence
- policy conflict
- unsafe runtime behavior
- failed test results
- audit finding
- authority mismatch
- known harmful or misleading logic

Recommended handling:

- block execution
- remove from active retrieval or invocation paths
- record validation failure reason
- require correction before reconsideration

Invalid blocks should not be used as operational authority.

---

## Superseded

A Superseded Knowledge Block has been replaced by a newer version.

Supersession may occur when:

- a policy is updated
- a schema changes
- a better evidence set becomes available
- a safer runtime control model is introduced
- an improved version of the block is approved

Recommended handling:

- route new use to the replacement version
- preserve the old version for traceability
- prevent accidental invocation of outdated versions
- maintain version history for audit review

Superseded blocks may remain important for explaining past decisions, but they should not be selected for new execution unless explicitly allowed.

---

## Revoked

A Revoked Knowledge Block has been explicitly withdrawn from active validity by an authorized person, team, process, or governance body.

Revocation may be required when:

- the block is unsafe
- the owning authority withdraws approval
- evidence is proven false
- policy alignment fails
- execution caused or could cause harm
- misuse is detected
- audit review identifies material failure

Recommended handling:

- block execution
- remove from active indexes
- preserve revocation record
- preserve audit and forensic history
- require new review before any future use

Revoked is stronger than expired. Expired means validity lapsed. Revoked means validity was actively withdrawn.

---

## Key Difference from Trust

Trust and verification are related but distinct.

**Trust level** describes confidence and maturity based on review, testing, and operational history.

**Verification status** describes whether the block currently satisfies validation requirements.

Examples:

- A Production-Proven block can become Expired if its evidence ages out.
- A Verified block may not yet be Production-Proven because it lacks real-world execution history.
- A high-trust block can become Invalid if a policy conflict is discovered.
- A low-trust block can still be Pending even if its author believes it is correct.

Trust is historical confidence.

Verification is current validity.

---

## Role in Execution

Before execution, a system should check verification status.

General rules:

- Pending blocks should not execute in production.
- Verified blocks may proceed to runtime revalidation.
- Expired blocks should be blocked or sent for re-verification.
- Invalid blocks should be blocked.
- Superseded blocks should route to the current version.
- Revoked blocks should never execute unless a new approved version is created.

Verification status determines whether a block is eligible for runtime consideration.

Execution control determines whether it is allowed to execute under current conditions.

---

## Verification Evidence

Verification should record the basis for validity.

Useful verification metadata includes:

- verifier identity or role
- verification timestamp
- evidence sources
- evidence freshness window
- policy version or reference
- schema version
- test results
- review notes
- expiration date or review interval
- known limitations
- required runtime controls

This information helps later reviewers understand why a block was considered valid and when that validity should be rechecked.

---

## Re-Verification Triggers

A block should be re-verified when material conditions change.

Common triggers include:

- evidence expiration
- policy change
- regulation change
- schema change
- domain assumption change
- owner change
- dependency change
- failed runtime execution
- audit finding
- incident report
- new risk signal
- updated replacement block

Re-verification prevents old validity from being mistaken for current authority.

---

## Relationship to Execution Control

Verification status is an input to execution control.

Execution control may also evaluate:

- authority status
- risk posture
- system state
- trigger conditions
- current context
- evidence freshness
- policy consistency
- human review requirements
- fail-safe behavior

A block must be structurally valid, currently verified, and runtime-authorized before execution is allowed.

---

## Practical Rule

Verification status ensures that only currently valid Knowledge Blocks are considered for execution.

The safe operating rule is:

> A Knowledge Block should be verified before it is considered, and revalidated before it is allowed to act.
