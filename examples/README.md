# Examples

This directory contains practical examples for **AIPA Knowledge Blocks**.

The examples show how structured knowledge can be represented, invoked, revalidated, allowed, blocked, escalated, and audited.

AIPA public material is available at [aipa.network](https://aipa.network).

---

## Purpose

Examples help connect the Knowledge Block framework to implementation practice.

They are intended to show:

- how a Knowledge Block can represent an operational decision
- how trigger and runtime conditions affect execution
- how approval differs from execution authorization
- how runtime revalidation can allow or block action
- how audit records preserve traceability

Examples are not production-ready policies. They are reference artifacts for learning, testing, and adaptation.

---

## Current Example Sets

| Example Set | Purpose |
|---|---|
| [Execution Control](execution-control/) | Demonstrates allowed and blocked runtime execution decisions |

---

## Planned Example Sets

Future example sets may include:

| Example Set | Purpose |
|---|---|
| Compliance | Regulatory review, evidence checks, approval chains, and audit workflows |
| Operations | Deployment, scheduling, capacity, incident response, and escalation decisions |
| Carbon and Sustainability | Emissions methods, reporting validation, supplier data review, and audit preparation |
| AI Governance | Human oversight, high-risk action routing, policy exceptions, and tool-use controls |
| Security | Access approval, privileged actions, containment workflows, and incident classification |

---

## How to Read the Examples

Each example should clarify:

1. What decision or action is represented
2. What was true at approval or decision time
3. What changed at runtime
4. What revalidation checks were performed
5. Whether execution was allowed, blocked, deferred, degraded, escalated, or aborted
6. What audit record should remain

---

## Implementation Boundary

These examples are simplified reference artifacts.

Before using a Knowledge Block in a real environment, teams should confirm:

- schema validity
- domain expert review
- policy alignment
- evidence freshness
- trust level
- verification status
- runtime controls
- authority requirements
- audit requirements
- applicable legal, compliance, safety, or security review

---

## Core Rule

A Knowledge Block should not execute merely because it exists or was previously approved.

It should execute only when current trust, verification, authority, evidence, risk, context, and policy conditions permit execution.
