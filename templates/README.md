# Templates

This directory contains starter templates for creating **AIPA Knowledge Blocks**.

Templates provide reusable starting structures for authors who need to package operational knowledge, decision logic, evidence, runtime controls, and governance metadata in a consistent format.

AIPA public material is available at [aipa.network](https://aipa.network).

---

## Purpose

Templates help authors create Knowledge Blocks without starting from an empty file.

They provide common field groups for:

- identity and discovery
- trigger conditions
- execution control
- runtime revalidation
- risk posture
- decision logic
- supporting evidence
- expected outcomes

Templates are not finished Knowledge Blocks. They are starting points that must be reviewed, completed, validated, and governed before use.

---

## Available Templates

| Template | Purpose |
|---|---|
| [blank-knowledge-block.json](blank-knowledge-block.json) | General starter template for a new Knowledge Block |
| [compliance-template.json](compliance-template.json) | Starter template for compliance, policy, audit, and regulatory decision control |
| [operations-template.json](operations-template.json) | Starter template for operational decisions, deployment controls, and execution governance |
| [carbon-template.json](carbon-template.json) | Starter template for carbon, sustainability, emissions, and reporting validation workflows |

---

## How Templates Relate to the Framework

Templates are designed to align with the main Knowledge Block architecture:

```text
Index Layer → Trigger Layer → Runtime Layer → Logic / Evidence / Outcomes → Auditability
```

A template should help authors define:

1. **What the block is** — identity, title, domain, owner, version, and status
2. **When it should activate** — trigger type, source, conditions, and preconditions
3. **How it is controlled** — execution control, authority, revalidation, risk, and fail-safe behavior
4. **What it knows** — decision logic, evidence, and expected outcomes
5. **How it can be reviewed** — trust, verification, and audit expectations

---

## Recommended Authoring Flow

A practical template workflow:

```text
Choose template → Fill identity fields → Define trigger conditions → Add logic → Add evidence → Configure runtime controls → Define outcomes → Validate schema → Review governance → Assign trust and verification status
```

Do not treat a filled template as production-ready until it has passed review and validation.

---

## Template Selection

### Blank Template

Use `blank-knowledge-block.json` when:

- the domain is new
- no specialized template exists
- the block is exploratory
- the author needs a neutral starting structure

---

### Compliance Template

Use `compliance-template.json` when the block involves:

- policy review
- regulatory checks
- audit workflows
- approval chains
- evidence sufficiency
- exception handling

Compliance templates usually require strict authority checks, evidence freshness, policy consistency, and audit logging.

---

### Operations Template

Use `operations-template.json` when the block involves:

- deployment control
- incident response
- capacity or scheduling decisions
- maintenance windows
- configuration changes
- operational escalation

Operations templates usually require state comparison, runtime risk checks, execution windows, fail-safe behavior, and audit records.

---

### Carbon Template

Use `carbon-template.json` when the block involves:

- emissions reporting
- sustainability workflows
- methodology validation
- supplier data review
- reporting evidence checks
- carbon or ESG audit preparation

Carbon and sustainability templates usually require methodology versioning, evidence freshness, verification status, and careful audit trails.

---

## Required Completion Before Use

Before a template becomes a usable Knowledge Block, authors should complete or confirm:

- `knowledge_block_id`
- `title`
- `description`
- `version`
- `domain`
- `category`
- `owner`
- `status`
- `trigger_conditions`
- `preconditions`
- `required_authority`
- `allowed_actions`
- `prohibited_actions`
- `logic`
- `evidence`
- `outcomes`

Some fields may be intentionally empty during drafting, but they should not remain empty for production or governed runtime use.

---

## Validation Expectations

Templates should be validated against the schemas in [`../schema/`](../schema/).

Recommended validation checks:

- structure matches the relevant schema
- required fields are present
- enum values are valid
- authority requirements are explicit
- risk posture is defined
- audit logging is configured
- evidence is present or explicitly marked as pending
- runtime behavior is clear

Schema validity is only one step. Governance review and runtime authorization are still required.

---

## Relationship to Examples

Templates are starting structures.

Examples are demonstrations.

| Type | Purpose |
|---|---|
| Template | Helps authors create new Knowledge Blocks |
| Example | Shows how a Knowledge Block behaves in a scenario |
| Schema | Defines machine-readable validation rules |
| Documentation | Explains the governance model and terminology |

See [`../examples/`](../examples/) for reference examples.

---

## Implementation Boundary

Templates are not legal, compliance, security, operational, environmental, or safety advice.

They provide structure for governed AI and operational workflows. Real deployment should be reviewed by appropriate domain, legal, compliance, security, privacy, safety, or operational authorities.

---

## Core Rule

A completed template is not automatically executable.

A Knowledge Block created from a template should be reviewed, verified, and revalidated before it is allowed to act.
