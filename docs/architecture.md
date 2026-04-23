# Architecture

The framework separates structured decision representation from execution-time enforcement.

## Layers

### Index Layer
Defines identity, metadata, classification, and discovery fields.

### Trigger Layer
Defines when a Knowledge Block should be evaluated or activated.

### Runtime Layer
Defines execution control, revalidation, risk posture, state, context, and failure behavior.

### Full Layer
Combines the layers into an integrated schema for a fully specified Knowledge Block.

## Runtime emphasis

The runtime layer is the enforcement point.

A Knowledge Block may be valid when authored and invalid when executed.

For that reason, execution control checks:

- context drift
- policy mismatch
- evidence freshness
- authority requirements
- runtime risk posture

## Result

A decision is not executed simply because it exists.

It is executed only if it remains valid under current conditions.
