# Controlled Vocabulary

The Controlled Vocabulary defines standardized terms used across the Knowledge Block framework.

It ensures consistency between authors, validators, and runtime systems.

## Purpose

To eliminate ambiguity and ensure that:

- terms are used consistently
- decisions are interpreted correctly
- runtime behavior is predictable
- audit and compliance are clear

## Core Terms

### Knowledge Block
A structured representation of a decision, including context, logic, and execution control.

---

### Execution Control
The mechanism that determines whether a Knowledge Block is allowed to execute at runtime.

Includes:
- revalidation
- risk gating
- authority enforcement
- failure behavior

---

### Revalidation
The process of checking whether a Knowledge Block remains valid under current conditions at execution time.

---

### Context
The set of environmental, system, and input conditions used to evaluate a Knowledge Block.

---

### State
The current condition of the system at execution time.

---

### Risk Posture
The current level of risk based on impact, likelihood, and uncertainty.

---

### Authority
The permissions or roles required to execute a Knowledge Block.

---

### Trust Level
A classification of confidence based on past review, testing, and operational history.

---

### Verification Status
The current validity of a Knowledge Block based on evidence, policy, and defined rules.

---

### Policy
Rules or constraints that govern what actions are allowed under specific conditions.

---

### Decision
The outcome of evaluating a Knowledge Block at runtime.

Common values:
- ALLOW
- BLOCK
- ESCALATE
- DEFER

---

### Delta
The difference between decision-time conditions and execution-time conditions.

---

### Audit
A record of decisions, actions, and outcomes for traceability and compliance.

---

## Key Principle

A shared vocabulary is required for consistent decision-making and reliable execution control.

## Outcome

The controlled vocabulary ensures that all components of the framework:

- speak the same language
- interpret decisions consistently
- behave predictably at runtime
