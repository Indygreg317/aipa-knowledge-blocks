# Schema

The Knowledge Block framework is defined through layered JSON schemas.

These schemas provide a structured, machine-readable representation of decisions and their execution controls.

## Schema Layers

### Index Layer
Defines identity, metadata, classification, and lifecycle information.

### Trigger Layer
Defines when a Knowledge Block should be evaluated or activated.

### Runtime Layer
Defines execution control, revalidation, risk posture, state, and failure behavior.

This is the most critical layer for enforcing safe execution.

### Full Layer
Combines all layers into a complete Knowledge Block specification.

## Purpose

The schema ensures:

- consistent structure across all Knowledge Blocks
- enforceable validation rules
- compatibility with runtime systems
- traceability and auditability

## Key Design Principle

Schemas do not just describe data.

They define how decisions are represented, validated, and controlled at execution time.
