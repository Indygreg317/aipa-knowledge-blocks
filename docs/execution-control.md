# Execution Control

## Overview

Knowledge Blocks do not stop at structured knowledge representation. They also support execution-time control, revalidation, and runtime governance. A Knowledge Block is valid at authoring and decision time, but execution time brings new conditions, new information, and new risks. This document defines how execution control ensures that structured knowledge remains safely actionable at runtime.

## Why Execution Control Matters

A system may be valid at evaluation time and invalid at execution time.

Between the moment a decision is approved and the moment it executes, the world changes:

- **State drift**: System configuration, data, or environment may differ from what was assumed
- **Policy evolution**: Compliance rules, organizational constraints, or regulatory requirements may shift
- **Risk escalation**: New threat signals, alerts, or operational indicators may alter the risk profile
- **Authority revocation**: Permissions, trust status, or delegated authority may be withdrawn
- **Evidence decay**: Supporting information may age beyond acceptable freshness windows

Trust must be revalidated under current conditions. Execution should not proceed only because a prior evaluation passed. Execution should proceed only when authority remains valid at runtime.

## Core Idea

Structured knowledge is a snapshot of human expertise frozen in time. At execution time, that snapshot must be validated against live conditions.

The control framework ensures:

1. **Authority is continuously verified** — not just at decision time, but again at execution time
2. **Conditions are compared** — decision-time state is compared against execution-time state
3. **Risk remains acceptable** — current risk profile is scored and gated against tolerance thresholds
4. **Evidence is fresh** — supporting facts have not aged beyond acceptable limits
5. **Policy is consistent** — organizational and regulatory constraints have not changed
6. **Failures are safe** — deterministic fail behaviors ensure systems degrade gracefully, not catastrophically

## Runtime Control Concepts

### Execution-Time Revalidation

Revalidation means running decision-time checks again, in real time, before allowing execution to proceed.

A Knowledge Block specifies what should be checked:

- **compare_context**: Are current conditions still compatible with decision-time assumptions?
- **compare_policy**: Are organizational policies still the same?
- **compare_inputs**: Are the inputs still within expected ranges?
- **compare_risk_posture**: Has the risk profile changed?
- **compare_evidence**: Are supporting facts still valid and fresh?

If revalidation detects a mismatch, the system responds according to the `on_mismatch` setting: **block** (fail closed), **escalate** (request human review), **fallback** (switch to safe mode), or **warn** (log and continue).

### Delta-State Comparison

Delta is the difference between two states. Delta-state comparison measures drift between decision-time and execution-time conditions.

**Decision-time state**: The world as understood when a Knowledge Block was authored or a decision was made.

**Execution-time state**: The world as measured when execution is about to occur.

If delta exceeds the configured threshold, authority to proceed may no longer be valid.

Example: A compliance decision was made when budget utilization was at 60%. At execution time, it is at 85%. If `delta_threshold` is 0.2, this 25% drift exceeds the threshold, and revalidation blocks execution.

Delta-state comparison is not a binary pass/fail. Different fields carry different weight:

- **Material fields** (e.g., compliance status, risk score, policy version) — even small deltas may trigger revalidation
- **Immaterial fields** (e.g., timestamp, log entry count) — large deltas may be tolerated

The framework allows configuration of which fields matter for delta calculation.

### Evidence Freshness

Evidence is the fact or data that justifies a decision. Evidence ages. Old evidence may no longer be reliable.

`evidence_freshness_window` defines the maximum age evidence can have before revalidation is required. The format is ISO 8601 duration (e.g., `P30D` = 30 days, `PT6H` = 6 hours).

If evidence exceeds this window at execution time, the system:
- Automatically revalidates (if configured)
- Escalates to a human (if configured)
- Blocks execution (if configured)
- Warns and continues (if configured)

Freshness windows are stricter in high-risk contexts and more lenient in low-risk contexts.

### Policy Consistency

Policies are the rules under which an organization operates. Policies change:

- New regulations are enacted
- Organizational strategy shifts
- Threat landscapes evolve
- Vendor requirements change

A Knowledge Block captures the policy state at decision time. `block_on_policy_mismatch` controls whether execution should block if current policy differs from decision-time policy.

Set to `true` for compliance-critical knowledge blocks. Set to `false` for operations that can tolerate policy drift.

### Risk Posture

Risk posture is the current tolerance for downside under present conditions.

Risk posture is different from risk level. A decision may have been made under low-risk conditions with narrow failure tolerance. At execution time, conditions may have changed:

- System may be in sandbox vs. production (exposure differs)
- User load may be higher (blast radius differs)
- Organizational capacity for incident response may be reduced (recovery risk differs)

Risk posture captures these runtime dimensions:

**Impact**: Severity of failure (low, medium, high, critical).

**Likelihood**: Probability of failure (0.0 to 1.0).

**Uncertainty**: Confidence penalty reflecting unknown unknowns (0.0 to 1.0). Higher uncertainty means the system is less sure of its risk estimate.

**System state**: Current environment (sandbox, testing, staging, production, restricted). Production carries higher risk than sandbox.

**Exposure window**: How long the effect persists. Transient effects (seconds to minutes) carry less risk than persistent effects (hours, days, or indefinite).

**Max allowed score**: The threshold. If computed risk score exceeds this, execution is blocked or escalated.

Risk posture is assessed at execution time, not decision time. If conditions have changed, risk tolerance changes.

### Authority Gating

Authority is permission to act. Authority can be gated (controlled) at three levels:

**Strict**: Authority is revalidated at execution time. If the authorizing entity's status has changed, execution is blocked. Used for high-impact decisions (payment, policy change, access grant).

**Conditional**: Authority is revalidated under specific conditions (e.g., if risk exceeds a threshold, if execution window is open, if human is present). Used for moderate-impact decisions (recommendation, configuration change).

**Advisory**: Authority was valid at decision time; execution does not require re-checking. Used for low-impact decisions (log entry, metric update, notification).

Authority mode is a configuration choice. High-risk knowledge blocks should use `strict`. Low-risk knowledge blocks can use `advisory`.

### Fail-Safe Behavior

What happens when execution control checks fail?

The framework defines four fail behaviors:

**block**: Execution is prevented. The action does not proceed. A blocked execution is safe but may leave systems in an incomplete state.

**degrade**: Execution proceeds in a reduced-capability mode. Full functionality is unavailable, but a safer subset is allowed. Example: Read-only mode instead of read-write; limited scope instead of full scope.

**warn**: Execution proceeds with logging. A warning is issued, and the action continues. Logs create an audit trail of the risk taken. The system accepts the risk but documents it.

**fallback**: Execution proceeds with a fallback action. Instead of the original action, a safer alternative is used. Example: Instead of executing immediately, escalate to a queue for human review.

Different control checks can have different fail behaviors:

- Authority check fails → block
- Risk score exceeds threshold → degrade
- Evidence is slightly stale → warn
- Policy has changed → escalate (a type of fallback)

## Governance Connection

Execution control connects to three existing governance concepts:

**Trust levels**: Trust is not one-time validation. A Knowledge Block may be authored at high trust level, but authority to execute is revalidated at runtime. If the authorizing entity's trust level has been downgraded, execution blocks (under strict mode) or escalates (under conditional mode).

**Verification status**: Verification confirms that a Knowledge Block is accurate at the time of verification. But verification is a snapshot. Execution control requires re-verification of inputs and conditions at execution time.

**Audit logging**: Execution decisions (approved, blocked, escalated, degraded) are logged. Logs create a record of:
- What was decided and when
- What conditions changed between decision and execution
- Why execution was approved, blocked, escalated, or degraded
- Who authorized execution and under what authority mode

This audit trail is the foundation of accountability and forensics.

## Practical Result

Structured knowledge becomes actionable only when runtime checks confirm authority is still valid.

A Knowledge Block is:

1. **Authored** by a domain expert
2. **Verified** by a trust authority
3. **Classified** with a trust level
4. **Governed** by policies and constraints
5. **Templated** for reuse
6. **Evaluated** at decision time

But until execution time, it is inert. Execution control activates it:

7. **Revalidated** against current conditions
8. **Risk-gated** against current risk tolerance
9. **Authority-checked** under current authority status
10. **Policy-verified** against current rules
11. **Evidence-validated** for freshness
12. **Executed** or safely blocked/escalated

This is the difference between structured knowledge and controlled execution. The framework ensures that knowledge remains knowledge—defensible, auditable, and safe.
