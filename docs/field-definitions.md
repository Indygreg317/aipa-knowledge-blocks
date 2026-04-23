# Field Definitions

Field Definitions describe the core data elements used across Knowledge Blocks.

They ensure consistency, clarity, and interoperability between authors, validators, and runtime systems.

## Purpose

To provide a shared understanding of:

- what each field represents
- how it should be used
- how it is interpreted at runtime

## Core Fields

### knowledge_block_id
Unique identifier for a Knowledge Block.

Must be:
- unique across the system
- immutable once assigned

Formats may include:
- UUIDs (system-generated)
- structured IDs (human-readable)

Examples:
- 550e8400-e29b-41d4-a716-446655440000
- KB-DEPLOY-001

Used for:
- tracking
- auditing
- referencing across systems
---

### title
Human-readable name for the Knowledge Block.

---

### description
Short explanation of the purpose and scope of the Knowledge Block.

---

### domain
The business or operational domain (e.g., compliance, operations, carbon).

---

### version
Version identifier for tracking changes over time.

---

### tags
Keywords used for classification and discovery.

---

## Runtime Fields

### execution_control
Defines how execution is governed at runtime.

Includes:
- revalidation requirements
- failure behavior
- delta thresholds
- authority constraints

---

### revalidation
Defines how the system checks whether a decision is still valid at execution time.

Includes:
- context comparison
- policy comparison
- risk checks

---

### risk_posture
Represents the current risk environment.

Includes:
- impact
- likelihood
- uncertainty
- system state

---

### state
Defines execution states and transitions.

---

### context
Represents inputs, variables, and environmental conditions.

---

### error_handling
Defines fallback actions and responses to failure conditions.

---

## Governance Fields

### trust_level
Indicates confidence in the Knowledge Block based on review and history.

---

### verification_status
Indicates whether the Knowledge Block is currently valid under defined rules.

---

### audit
Defines logging and traceability requirements.

---

## Key Principle

Fields are not just data.

They define how decisions are structured, validated, and controlled at execution time.

## Outcome

Clear field definitions ensure that Knowledge Blocks are:

- consistent
- interpretable
- enforceable
- auditable
