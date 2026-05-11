# Trust Levels

Trust levels define the confidence placed in an AIPA Knowledge Block based on authoring quality, review status, evidence strength, testing, operational history, and governance maturity.

This document is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

Trust levels help classify how much confidence a system or reviewer may place in a Knowledge Block before it is considered for use.

Trust levels support:

- review workflows
- retrieval filtering
- approval decisions
- runtime risk scoring
- escalation requirements
- audit interpretation
- lifecycle management

Trust is not static authority.

A trust level reflects historical confidence. It does not prove that the block remains safe, current, or authorized at runtime.

---

## Core Principle

Trust is based on history.

Execution is based on current conditions.

A highly trusted Knowledge Block can still be unsafe if policy has changed, evidence has expired, authority was revoked, risk increased, or the execution context drifted.

Therefore:

> Trust may influence execution decisions, but it does not guarantee execution approval.

---

## Trust Level Model

The following levels describe a practical maturity path for Knowledge Blocks.

| Trust Level | Meaning | Typical Use |
|---|---|---|
| Draft | Created but not reviewed | Authoring, sandbox, internal discussion |
| Reviewed | Human-reviewed for structure and domain fit | Limited testing, controlled use, reviewer feedback |
| Verified | Evidence-supported and tested against expected behavior | Governed workflows, controlled runtime use |
| Production-Proven | Demonstrated reliable behavior in real operational environments | Higher-confidence production use with ongoing monitoring |
| Deprecated | Previously trusted but no longer recommended for active use | Historical reference, migration support |
| Revoked | Explicitly removed from active trust due to risk, invalidity, or authority failure | Audit only; should not be invoked for execution |

---

## Draft

A Draft Knowledge Block has been created but has not completed review.

Typical characteristics:

- newly authored
- incomplete evidence or logic
- unverified assumptions
- no formal approval
- not safe for production execution

Draft blocks may be useful for design, experimentation, or review preparation, but they should not be treated as operational authority.

Recommended runtime posture:

- block production execution
- allow sandbox-only use if explicitly marked
- require review before indexing into active retrieval systems

---

## Reviewed

A Reviewed Knowledge Block has been evaluated by one or more qualified reviewers.

Typical characteristics:

- structure is understandable
- domain fit has been checked
- obvious errors have been addressed
- governance metadata is present
- evidence may still require stronger validation

Reviewed blocks have limited confidence. They may be suitable for controlled workflows, testing, or non-critical decision support.

Recommended runtime posture:

- require revalidation
- limit to low or moderate-risk contexts
- require audit logging
- escalate for high-impact execution

---

## Verified

A Verified Knowledge Block has supporting evidence and has been tested against expected outcomes.

Typical characteristics:

- evidence supports the block logic
- expected outcomes are documented
- schema validation passes
- review findings have been resolved
- runtime controls are defined
- verification status is current

Verified blocks may be eligible for governed runtime use, subject to trigger conditions, authority requirements, and execution control.

Recommended runtime posture:

- allow controlled execution when runtime checks pass
- require evidence freshness checks
- require authority validation for high-impact actions
- preserve audit records

---

## Production-Proven

A Production-Proven Knowledge Block has demonstrated reliable behavior in real operational environments over time.

Typical characteristics:

- successful execution history
- stable evidence base
- low unresolved incident rate
- consistent audit records
- monitored runtime outcomes
- clear owner and maintenance path

Production-Proven is the highest confidence state, but it is not unconditional permission to execute.

Recommended runtime posture:

- allow production use when current controls pass
- continue runtime revalidation
- monitor drift, incidents, and policy changes
- downgrade if evidence, authority, or outcomes degrade

---

## Deprecated

A Deprecated Knowledge Block was previously valid or useful but is no longer recommended for active use.

Deprecation may occur because:

- a newer version exists
- policy changed
- domain assumptions changed
- schema structure changed
- evidence became stale
- implementation guidance evolved

Deprecated blocks may remain available for historical context, migration, comparison, or audit review, but they should not be selected for new execution unless explicitly permitted under a controlled exception.

Recommended runtime posture:

- block new production use by default
- allow read-only reference
- route users to replacement block when available
- preserve audit history

---

## Revoked

A Revoked Knowledge Block has been removed from active trust.

Revocation may occur because:

- evidence was found incorrect
- policy alignment failed
- authority was withdrawn
- execution caused or could cause harm
- audit findings exposed material defects
- misuse or unsafe invocation was detected
- the owning authority invalidated the block

Revoked blocks should not be invoked for active execution.

Recommended runtime posture:

- block execution
- remove from active retrieval indexes
- preserve for audit and forensic review
- record revocation reason, timestamp, and authority

---

## Promotion Criteria

A block may move to a higher trust level when it satisfies stronger evidence, review, and operational requirements.

Promotion should consider:

- schema validity
- evidence quality
- reviewer approval
- domain expert confirmation
- policy alignment
- test results
- runtime behavior
- audit history
- incident history
- owner accountability

Promotion should be explicit and recorded. Trust should not silently increase because a block has merely existed for a long time.

---

## Downgrade and Review Triggers

Trust levels should be downgraded or reviewed when material conditions change.

Common triggers include:

- policy update
- regulation change
- expired evidence
- failed execution
- unexpected output
- authority revocation
- ownership change
- incident report
- audit finding
- schema migration
- new known risk
- dependency or environment change

A block may move from Production-Proven to Reviewed, Deprecated, or Revoked depending on severity.

---

## Relationship to Verification Status

Trust level and verification status are related but not identical.

**Trust level** describes confidence or maturity.

**Verification status** describes whether current evidence, review, and validation requirements are satisfied.

A block can be high trust but temporarily fail verification because evidence expired.

A block can be verified but still not production-proven because it lacks operational history.

Both values should be considered by execution control.

---

## Relationship to Execution Control

Execution control uses trust level as one input among several.

Other runtime inputs include:

- current context
- policy state
- risk posture
- authority status
- evidence freshness
- system state
- trigger conditions
- human review requirements

This means a trusted block can still be blocked, deferred, degraded, or escalated if current conditions fail.

---

## Practical Rule

Trust levels provide confidence.

Execution control provides enforcement.

The safe operating rule is:

> Do not execute a Knowledge Block because it is trusted. Execute it only when trust, verification, authority, risk, evidence, and current context all permit execution.
