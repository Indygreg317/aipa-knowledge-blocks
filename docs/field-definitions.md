# Field Definitions

Field definitions describe the core data elements used across AIPA Knowledge Blocks.

They provide a shared vocabulary for authors, validators, reviewers, runtime engineers, auditors, and governance teams.

This document is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

Field definitions ensure that Knowledge Blocks are interpreted consistently across systems and workflows.

They clarify:

- what each field represents
- how the field should be used
- where the field appears in the architecture
- how the field may affect retrieval, governance, validation, execution, or audit
- whether the field is descriptive, controlling, or evidentiary

A field is not merely a label. In a governed system, a field may affect whether knowledge is discoverable, eligible, trusted, verified, executable, blocked, escalated, or auditable.

---

## Field Categories

AIPA Knowledge Block fields can be grouped into several categories:

| Category | Purpose |
|---|---|
| Identity Fields | Identify and version the block |
| Discovery Fields | Support indexing, classification, and retrieval |
| Trigger Fields | Define when a block becomes eligible for evaluation |
| Runtime Fields | Control execution, revalidation, risk, state, and failure behavior |
| Governance Fields | Track review, authority, trust, verification, and lifecycle state |
| Evidence Fields | Record the basis for decisions or validation |
| Audit Fields | Preserve accountability and traceability |

---

## Identity and Discovery Fields

### `knowledge_block_id`

Unique identifier for a Knowledge Block.

Expected properties:

- unique across the system or repository
- stable once assigned
- suitable for references, audit records, and cross-system lookup

Example formats:

```text
550e8400-e29b-41d4-a716-446655440000
KB-COMPLIANCE-001
AIPA-KB-RUNTIME-GOV-001
```

Used for:

- retrieval
- audit records
- version lineage
- validation reports
- execution records
- references from other systems

Governance note: once a block has been used in review, audit, or execution, its ID should not be casually changed. Create a new version instead.

---

### `title`

Human-readable name for the Knowledge Block.

Used for:

- reviewer understanding
- documentation
- search results
- dashboards
- audit summaries

A title should be concise but specific enough to distinguish the block from related blocks.

---

### `description`

Short explanation of the block's purpose, scope, and intended use.

A good description should clarify:

- what the block covers
- what it does not cover
- why it exists
- what kind of system or workflow may use it

The description should not contain hidden execution instructions. Execution behavior belongs in runtime fields.

---

### `version`

Version identifier for tracking changes over time.

Examples:

```text
v0.1
v1.0.0
2026-05-10
```

Used for:

- change tracking
- compatibility checks
- schema migration
- audit records
- rollback or supersession workflows

Governance note: when logic, evidence, authority, or runtime behavior changes materially, a new version should be created.

---

### `domain`

The business, technical, operational, or policy domain the block belongs to.

Examples:

- compliance
- operations
- carbon management
- security
- incident response
- AI governance
- healthcare
- finance

Used for:

- routing
- reviewer assignment
- access control
- search filtering
- policy matching

---

### `category`

A narrower grouping within the domain.

Examples:

- evidence review
- access control
- deployment approval
- policy exception
- risk assessment
- runtime gating

Used for organizing related blocks and making retrieval more precise.

---

### `tags`

Search and discovery keywords.

Tags should be controlled where possible to avoid inconsistent naming.

Examples:

```text
runtime-control
human-review
audit-required
policy-sensitive
high-risk
```

Used for:

- retrieval
- filtering
- grouping
- analytics
- governance reports

---

### `owner`

Person, team, role, or function responsible for maintaining the block.

Examples:

- compliance-team
- security-owner
- AI-governance-reviewer
- operations-lead

Used for:

- review routing
- escalation
- update responsibility
- revocation authority
- audit follow-up

Governance note: a block without a clear owner should not be considered mature enough for production execution.

---

### `status`

Lifecycle state of the block.

Common values may include:

- draft
- active
- deprecated
- archived

Status helps systems avoid selecting blocks that are not eligible for current use.

---

## Trigger Fields

### `trigger_type`

Primary mechanism that causes a Knowledge Block to become eligible for evaluation.

Common values include:

- manual
- event
- schedule
- state_change

Used for determining how invocation begins.

---

### `trigger_source`

System, workflow, user, role, or process that initiates the trigger.

Examples:

- deployment-pipeline
- compliance-review
- incident-response-system
- human-reviewer
- scheduled-audit

Used for traceability and invocation control.

---

### `trigger_conditions`

Conditions that must be true before the block is evaluated.

Examples:

- risk_score_above_threshold
- policy_review_requested
- production_deploy_pending
- evidence_update_detected

Trigger conditions help prevent accidental or context-free invocation.

---

### `preconditions`

Conditions expected to hold before execution can proceed.

Preconditions are stronger than general relevance. They define assumptions that must be satisfied for safe evaluation or action.

Examples:

- human_reviewer_available
- evidence_present
- target_system_in_staging
- authority_token_valid

---

### `priority`

Relative importance or urgency of the trigger context.

Common values:

- low
- medium
- high
- critical

Priority may affect queueing, escalation, review timelines, and alert behavior.

---

## Runtime Fields

### `execution`

Basic execution parameters and constraints.

May include:

- execution engine
- timeout
- retries
- execution window
- parallel execution setting
- human review requirement

Execution settings describe how the block may be operationalized. They do not replace governance checks.

---

### `execution_control`

Defines runtime controls enforced before execution is allowed.

May include:

- `requires_revalidation`
- `required_authority`
- `authority_mode`
- `delta_threshold`
- `delta_mode`
- `evidence_freshness_window`
- `block_on_policy_mismatch`
- `fail_behavior`
- `allowed_actions`
- `prohibited_actions`
- `audit_log_required`

This is one of the most important runtime field groups. It defines whether and how the system should gate action.

---

### `requires_revalidation`

Indicates whether the block must be checked against current conditions before execution.

Recommended default for governed systems: `true`.

If false, the block may still require other controls depending on risk and authority.

---

### `required_authority`

List of roles, systems, reviewers, or authorities required for execution.

Examples:

- compliance-officer
- security-admin
- policy-owner
- human-reviewer

Used for enforcing who or what may authorize the action.

---

### `authority_mode`

Defines how strongly authority must be checked at runtime.

Common modes:

- `strict` — authority must be revalidated at execution time
- `conditional` — authority is revalidated under defined conditions
- `advisory` — authority is recorded but not strongly rechecked

High-impact blocks should use strict or conditional authority modes.

---

### `delta_threshold`

Maximum tolerated drift between decision-time and execution-time state.

Typically represented as a number from `0.0` to `1.0`.

Used for detecting whether context changed enough to require block, escalation, or revalidation.

---

### `delta_mode`

Defines how aggressively drift should be interpreted.

Common values:

- `strict`
- `tolerant`

Strict mode should be used where small changes can create material risk.

---

### `evidence_freshness_window`

Maximum allowed age of supporting evidence before revalidation is required.

Example values may use ISO 8601 duration format:

```text
P30D
PT6H
```

Used to prevent stale evidence from being treated as current.

---

### `block_on_policy_mismatch`

Indicates whether execution must stop when current policy differs from the policy basis used at decision time.

Recommended value for compliance-sensitive systems: `true`.

---

### `fail_behavior`

Default behavior when runtime checks fail.

Common values:

- block
- degrade
- warn
- fallback
- escalate
- abort
- defer

Fail behavior should be explicit. Governed systems should not silently proceed when controls fail.

---

### `allowed_actions`

Actions explicitly permitted during execution.

This acts as an allowlist.

If present, the runtime should prevent actions outside the allowed list unless another authorized override mechanism applies.

---

### `prohibited_actions`

Actions explicitly forbidden during execution.

This acts as a blocklist for unsafe, out-of-scope, or unauthorized behavior.

---

### `audit_log_required`

Indicates whether execution decisions and outcomes must be logged.

Recommended default for governed systems: `true`.

Audit logging should capture allow, block, escalation, degradation, fallback, abort, override, and error conditions.

---

### `revalidation`

Defines what should be checked again at runtime.

May include:

- context comparison
- policy comparison
- input comparison
- risk posture comparison
- evidence comparison
- mismatch behavior

Revalidation is the bridge between prior approval and current authorization.

---

### `risk_posture`

Represents the current risk environment for execution.

May include:

- impact
- likelihood
- uncertainty
- system state
- exposure window
- max allowed score

Risk posture helps determine whether execution remains acceptable under current conditions.

---

### `state`

Defines execution states and allowed transitions.

Used for:

- state machines
- workflow control
- permitted actions by state
- transition validation
- replay and audit review

---

### `context`

Represents runtime inputs, variables, outputs, and environmental conditions.

Context is important because a decision may be valid in one environment but invalid in another.

---

### `error_handling`

Defines responses to runtime failures or exceptions.

May include:

- error handlers
- fallback actions
- retry behavior
- escalation paths
- abort conditions

Error handling should preserve safe failure and auditability.

---

## Logic, Evidence, and Outcome Fields

### `logic`

Decision logic, rules, or structured reasoning statements represented by the block.

Logic should be clear enough for review and structured enough for implementation.

---

### `evidence`

Evidence, references, sources, or supporting facts used to justify the block.

Evidence should be reviewable and should include freshness expectations when relevant.

---

### `outcomes`

Expected results, allowed result states, or permitted outcomes.

Outcomes help reviewers and runtime systems distinguish expected behavior from unexpected or unsafe behavior.

---

## Governance Fields

### `trust_level`

Indicates confidence in the Knowledge Block based on review, testing, and operational history.

Trust describes maturity and confidence. It does not automatically authorize execution.

---

### `verification_status`

Indicates whether the Knowledge Block currently satisfies validation, evidence, policy, and governance requirements.

Verification describes current validity. It does not automatically authorize execution.

---

### `audit`

Defines logging, traceability, and accountability requirements.

Audit fields may include:

- who approved the block
- when it was verified
- what schema version was used
- why execution was allowed or blocked
- which evidence supported the decision
- whether override or escalation occurred

---

## Field Interpretation Rule

A field may serve more than one function.

For example:

- `domain` helps retrieval and reviewer routing
- `owner` supports accountability and escalation
- `verification_status` affects eligibility
- `risk_posture` affects runtime authorization
- `audit_log_required` affects compliance recordkeeping

In AIPA Knowledge Blocks, fields should be read as part of a governed operational system, not as isolated metadata.

---

## Key Principle

Fields are not just data.

They define how knowledge is structured, discovered, validated, governed, controlled, executed, and audited.

---

## Outcome

Clear field definitions ensure that Knowledge Blocks are:

- consistent
- interpretable
- enforceable
- reviewable
- auditable
- safer to reuse across AI-assisted systems
