# Verification Status

Verification status tracks whether a Knowledge Block is currently valid under defined rules and conditions.

## Purpose

To ensure that a Knowledge Block:

- meets policy requirements
- has valid and current evidence
- is safe to evaluate at runtime

## Status Types

### Pending
- Awaiting review or validation

### Verified
- Meets all defined validation requirements

### Expired
- Evidence or assumptions are outdated

### Invalid
- Fails validation rules or policy checks

## Key Difference from Trust

Trust:
- based on past performance and review

Verification:
- based on current validity

A Knowledge Block can be:
- trusted but expired
- verified but not yet proven in production

## Role in Execution

Before execution:

- verification status is checked
- expired or invalid blocks may be blocked
- valid blocks proceed to runtime revalidation

## Relationship to Execution Control

Verification ensures a block is eligible for execution.

Execution control determines if it is allowed to execute now.

## Key Principle

A Knowledge Block must be both:

- verified (valid)
- and revalidated (current)

before execution is allowed.

## Outcome

Verification status ensures that only valid Knowledge Blocks are considered for execution.
