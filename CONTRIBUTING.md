# Contributing to AIPA Knowledge Blocks

Thank you for your interest in contributing to **AIPA Knowledge Blocks**.

This repository is maintained as part of the **Artificial Intelligence Partnership Association (AIPA)** open governance work. Public AIPA material is available at [aipa.network](https://aipa.network).

AIPA Knowledge Blocks are intended to help AI-assisted systems represent operational knowledge in a structured, governed, reviewable, runtime-aware, and auditable form.

---

## Guiding Principles

Before contributing, please align with the core intent of the framework:

- **Open and voluntary** — designed for collaboration and practical adoption
- **Non-prescriptive** — intended to complement existing systems, not replace them
- **Governance-oriented** — focused on structure, traceability, accountability, and reviewability
- **Runtime-aware** — approval and execution authorization are treated as separate concerns
- **Human-accountable** — human oversight, authority, escalation, and audit should remain visible
- **Safety-conscious** — uncertain or invalid conditions should block, defer, degrade, or escalate rather than silently proceed

---

## What You Can Contribute

We welcome contributions in the following areas.

### 1. Knowledge Block Examples

Examples help show how Knowledge Blocks work in practice.

Useful contributions include:

- new example Knowledge Blocks
- allowed and blocked execution examples
- domain-specific scenario examples
- audit record examples
- human review or escalation examples
- improved explanation of existing examples

Examples should make the governance logic clear, not just show data structure.

---

### 2. Templates

Templates help authors create new Knowledge Blocks consistently.

Useful contributions include:

- new domain templates
- improvements to existing templates
- better default runtime controls
- clearer evidence fields
- safer fail-behavior defaults
- stronger audit expectations

Templates should be treated as starting points, not production-ready policies.

---

### 3. Schema Improvements

Schemas define the machine-readable structure of Knowledge Blocks.

Useful contributions include:

- JSON Schema refinements
- validation rule improvements
- clearer field definitions
- controlled enum updates
- better references between layer schemas
- schema examples that pass validation

Schema changes should be made carefully because they may affect downstream validators, examples, templates, and documentation.

---

### 4. Documentation

Documentation should help builders, reviewers, and governance teams understand the framework.

Useful contributions include:

- clarification of concepts
- diagrams or visual explanations
- better onboarding material
- domain-specific guidance
- implementation notes
- terminology improvements
- examples of review or audit workflows

Documentation should preserve the distinction between knowledge, approval, trust, verification, invocation, execution authorization, and audit.

---

### 5. Governance and Review Patterns

Governance contributions help define how Knowledge Blocks should be reviewed, approved, verified, revoked, superseded, and audited.

Useful contributions include:

- review checklists
- verification workflows
- trust-level guidance
- revocation criteria
- evidence freshness guidance
- authority and escalation models
- audit record patterns

---

### 6. Runtime and Execution Control

Runtime contributions help define how systems decide whether a Knowledge Block is allowed to act under current conditions.

Useful contributions include:

- revalidation patterns
- delta comparison methods
- risk posture models
- authority validation patterns
- fail-safe behavior examples
- audit logging approaches
- examples of block, defer, degrade, fallback, escalate, or abort behavior

---

## How to Contribute

1. Fork the repository.
2. Create a new branch with a clear name.
3. Make your changes.
4. Check related docs, templates, examples, and schemas for consistency.
5. Submit a Pull Request with:
   - a clear title
   - a description of what changed
   - why the change improves the framework
   - any validation performed
   - any known limitations or follow-up work

Example branch names:

```text
add-compliance-example
update-runtime-schema
improve-governance-docs
add-carbon-template
```

---

## Contribution Checklist

Before submitting, consider whether your contribution:

- uses **AIPA Knowledge Blocks** naming consistently
- follows the controlled vocabulary in [`docs/controlled-vocab.md`](docs/controlled-vocab.md)
- aligns with the architecture in [`docs/architecture.md`](docs/architecture.md)
- uses fields consistently with [`docs/field-definitions.md`](docs/field-definitions.md)
- respects trust-level guidance in [`docs/trust-levels.md`](docs/trust-levels.md)
- respects verification guidance in [`docs/verification-status.md`](docs/verification-status.md)
- distinguishes approval from execution authorization
- includes audit expectations where relevant
- avoids implying that templates or examples are production-ready without review
- preserves human oversight and escalation paths where appropriate

---

## Example Contribution Requirements

When contributing a new example, please include:

- a clear scenario
- Knowledge Block identity fields
- trigger conditions
- approval-time or decision-time state
- execution-time state when relevant
- revalidation checks
- decision outcome
- reason for the outcome
- audit expectations
- implementation boundary or safety note when appropriate

Examples should clarify why a block was allowed, blocked, deferred, degraded, escalated, or aborted.

---

## Template Contribution Requirements

When contributing a new template, please include:

- `index` fields
- `trigger` fields
- `execution_control` fields
- `revalidation` fields
- `risk_posture` fields
- `logic`
- `evidence`
- `outcomes`

Templates should use AIPA-style IDs where possible, such as:

```text
AIPA-KB-DOMAIN-001
```

Templates should not include hidden production assumptions. Required domain review should be stated clearly.

---

## Schema Contribution Requirements

When contributing schema changes, please explain:

- what field or rule changed
- why the change is needed
- whether templates or examples need updates
- whether validation behavior changes
- whether existing references may break
- whether schema `$id` or `$ref` values are affected

Schema changes should preserve compatibility where possible or clearly document breaking changes.

---

## Review Process

All contributions will be reviewed for:

- alignment with AIPA principles
- clarity and usability
- consistency with controlled vocabulary
- relevance to real-world AI-assisted systems
- governance and auditability
- runtime safety implications
- schema/template/example consistency

Feedback may be provided before merging.

---

## Code of Conduct

- Be respectful.
- Assume positive intent.
- Focus on improving the work, not individuals.
- Keep feedback specific, practical, and grounded in the framework.
- Avoid turning open governance work into personal attacks, hype, or gatekeeping.

---

## License

By contributing, you agree that your contributions will be part of this open framework and governed by the repository's license.

---

## Final Note

AIPA is evolving.

This is not a fixed standard. It is a shared effort to make AI systems more understandable, traceable, accountable, and reliable.

The core idea is simple:

> Structured knowledge should not become action unless it remains governed, current, authorized, and auditable.

If you are thinking deeply about those problems, you are in the right place.
