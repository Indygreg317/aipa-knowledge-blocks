# Schema

This directory contains JSON Schema files for **AIPA Knowledge Blocks**.

The schemas define the machine-readable structure used to represent governed operational knowledge, trigger conditions, runtime controls, revalidation behavior, risk posture, state, context, evidence, outcomes, and audit-related fields.

AIPA public material is available at [aipa.network](https://aipa.network).

---

## Schema Files

| Schema | Purpose |
|---|---|
| [`knowledge-block.schema.json`](knowledge-block.schema.json) | Core Knowledge Block schema that composes the major block sections |
| [`index-layer.schema.json`](index-layer.schema.json) | Identity, ownership, metadata, lifecycle status, classification, and discovery fields |
| [`trigger-layer.schema.json`](trigger-layer.schema.json) | Trigger type, source, conditions, preconditions, and priority |
| [`runtime-layer.schema.json`](runtime-layer.schema.json) | Execution control, revalidation, risk posture, state, context, and error handling |
| [`full-layer.schema.json`](full-layer.schema.json) | Integrated schema for a fully specified Knowledge Block |

---

## Canonical Schema Identity

The canonical schema identity pattern is:

```text
https://aipa.network/schema/<schema-file-name>
```

Examples:

```text
https://aipa.network/schema/knowledge-block.schema.json
https://aipa.network/schema/index-layer.schema.json
https://aipa.network/schema/trigger-layer.schema.json
https://aipa.network/schema/runtime-layer.schema.json
https://aipa.network/schema/full-layer.schema.json
```

Local `$ref` values are intentionally kept relative where possible so validators can resolve files within this repository layout.

---

## Validation Boundary

Schema validation answers:

> Is this Knowledge Block structurally valid?

Runtime validation answers:

> Is this Knowledge Block allowed to execute right now?

Both matter.

A Knowledge Block can be structurally valid but still blocked at runtime because evidence is stale, authority is invalid, policy changed, risk increased, or context drifted.

---

## Recommended Use

Builders should:

1. Validate authored blocks against the appropriate schema.
2. Preserve schema version and schema ID information in audit records where practical.
3. Validate templates and examples after schema changes.
4. Treat schema validation as a prerequisite, not as execution authorization.
5. Use runtime controls to determine whether an action may proceed under current conditions.

---

## Relationship to Documentation

For more explanation, see:

- [`../docs/schema.md`](../docs/schema.md)
- [`../docs/architecture.md`](../docs/architecture.md)
- [`../docs/field-definitions.md`](../docs/field-definitions.md)
- [`../docs/execution-control.md`](../docs/execution-control.md)
- [`../docs/controlled-vocab.md`](../docs/controlled-vocab.md)

---

## Core Rule

A valid schema structure is necessary, but not sufficient.

A Knowledge Block should be structurally valid, currently verified, properly authorized, and runtime-safe before it is allowed to act.
