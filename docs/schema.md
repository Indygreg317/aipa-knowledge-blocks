# Schema Reference

AIPA Knowledge Blocks are defined through layered JSON Schemas.

These schemas provide a structured, machine-readable representation of operational knowledge, trigger conditions, runtime controls, risk posture, state handling, and execution governance.

This schema reference is part of the **Artificial Intelligence Partnership Association (AIPA)** Knowledge Blocks architecture. Public AIPA material is available at [aipa.network](https://aipa.network).

---

## Purpose

The schemas make Knowledge Blocks consistent, reviewable, implementable, and auditable.

They are intended to support:

- repeatable Knowledge Block authoring
- machine-readable validation
- governed retrieval and invocation
- runtime revalidation
- risk-aware execution control
- authority enforcement
- audit-ready implementation records

A schema does not merely describe data. In this framework, schema structure helps define how operational knowledge is represented, validated, controlled, and reviewed before it is allowed to influence action.

---

## Schema Files

The repository currently defines the following primary schema files:

```text
schema/
├── knowledge-block.schema.json
├── index-layer.schema.json
├── trigger-layer.schema.json
├── runtime-layer.schema.json
└── full-layer.schema.json
```

Each schema corresponds to a different architectural concern.

---

## Layer Summary

| Layer | Schema File | Purpose |
|---|---|---|
| Index Layer | `index-layer.schema.json` | Identity, ownership, metadata, lifecycle status, classification, and discovery |
| Trigger Layer | `trigger-layer.schema.json` | Conditions, events, sources, preconditions, and activation rules |
| Runtime Layer | `runtime-layer.schema.json` | Execution control, revalidation, authority, risk posture, state, context, and failure behavior |
| Full Layer | `full-layer.schema.json` | Complete integrated Knowledge Block structure |
| Core Knowledge Block | `knowledge-block.schema.json` | Primary schema that composes the major Knowledge Block fields |

---

## Index Layer

The Index Layer defines the discovery and identity surface of a Knowledge Block.

It includes fields such as:

- `knowledge_block_id`
- `title`
- `description`
- `version`
- `domain`
- `category`
- `tags`
- `owner`
- `status`
- `created_at`
- `updated_at`

The Index Layer allows a system to locate, classify, version, and route Knowledge Blocks without loading the entire governed artifact.

Use this layer when the main question is:

> What is this block, who owns it, and how should it be discovered?

---

## Trigger Layer

The Trigger Layer defines when a Knowledge Block should be evaluated or activated.

It currently supports trigger types such as:

- `manual`
- `event`
- `schedule`
- `state_change`

The Trigger Layer can describe:

- trigger source
- trigger conditions
- preconditions
- priority

Use this layer when the main question is:

> Under what conditions should this Knowledge Block become active or eligible for use?

This layer is important because governed knowledge should not be invoked accidentally just because it appears in context. Invocation should follow declared conditions.

---

## Runtime Layer

The Runtime Layer is the enforcement layer.

It defines the controls that determine whether a Knowledge Block remains safe and authorized at execution time.

Runtime schema areas include:

- `execution`
- `execution_control`
- `revalidation`
- `risk_posture`
- `state`
- `context`
- `error_handling`

The Runtime Layer can express requirements such as:

- whether revalidation is required
- which authorities must approve or remain valid
- how much state drift is allowed
- whether stale evidence should block execution
- whether policy mismatch should stop execution
- what fail-safe behavior should apply
- whether audit logging is required

Use this layer when the main question is:

> Even if this block is relevant, is it still allowed to execute right now?

---

## Core Knowledge Block Schema

`knowledge-block.schema.json` composes the major Knowledge Block fields.

It references the layered schemas and currently includes major sections such as:

- `index`
- `trigger`
- `execution`
- `execution_control`
- `revalidation`
- `risk_posture`
- `state`
- `context`
- `error_handling`
- `logic`
- `evidence`
- `outcomes`

This schema is useful when validating a Knowledge Block as a complete operational decision unit rather than as a standalone layer.

---

## Full Layer Schema

`full-layer.schema.json` is intended to represent a complete integrated Knowledge Block.

Use this schema when a block is ready for full review, publication, implementation testing, or artifact exchange.

The Full Layer should be treated as the most complete representation of a governed Knowledge Block, while individual layer schemas remain useful for authoring, partial validation, indexing, and runtime-specific implementations.

---

## Suggested Validation Flow

A practical validation flow can look like this:

```text
1. Validate Index Layer
   Confirm identity, ownership, version, lifecycle status, and discovery metadata.

2. Validate Trigger Layer
   Confirm activation rules, trigger source, preconditions, and priority.

3. Validate Runtime Layer
   Confirm execution controls, authority requirements, revalidation rules, risk posture, and fail-safe behavior.

4. Validate Full Knowledge Block
   Confirm that all layers compose into a complete governed artifact.

5. Record Validation Result
   Store validation status, reviewer, timestamp, schema version, and any warnings or failures.
```

This flow separates authoring validation from runtime authorization. A block can be structurally valid and still not authorized to execute under current conditions.

---

## Runtime Validation vs Schema Validation

Schema validation answers:

> Is this Knowledge Block structurally valid?

Runtime validation answers:

> Is this Knowledge Block still allowed to execute right now?

Both are required.

A Knowledge Block may pass JSON Schema validation while failing runtime execution control because:

- evidence is stale
- authority was revoked
- policy changed
- current system state drifted
- risk posture increased
- human review is now required

The schema defines what information must be available. Runtime validation evaluates that information against current conditions.

---

## Schema Identity Note

Some schema `$id` values may still reference earlier project naming. Future schema identity cleanup should align canonical schema IDs with the AIPA Knowledge Blocks public identity and the AIPA domain structure.

Recommended direction:

```text
https://aipa.network/schema/knowledge-block.schema.json
https://aipa.network/schema/index-layer.schema.json
https://aipa.network/schema/trigger-layer.schema.json
https://aipa.network/schema/runtime-layer.schema.json
https://aipa.network/schema/full-layer.schema.json
```

This should be handled carefully because schema `$id` values may affect validators, references, and downstream tooling.

---

## Implementation Guidance

Builders should treat schemas as implementation contracts, not as loose documentation.

Recommended implementation practices:

- validate blocks before publication
- validate again before runtime use
- preserve schema version information in audit records
- log validation failures and warnings
- distinguish structural validity from execution authorization
- do not allow model output alone to bypass runtime controls
- fail safely when required schema fields or runtime controls are missing

---

## Design Principle

The central schema design principle is:

> A Knowledge Block should be structured enough to discover, controlled enough to invoke safely, and explicit enough to audit after execution.

Schemas make that possible by defining the machine-readable boundary between knowledge, governance, and action.
